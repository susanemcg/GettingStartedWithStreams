# GettingStartedWithStreams

1. Show a stream with curl:
curl -s http://developer.usa.gov/1usagov

2. Pipe the output of that into jq:

curl -s http://developer.usa.gov/1usagov | jq .

But nothing shows up! Because of the buffer.

3. Try again with "no buffer" parameter:

curl --no-buffer -s http://developer.usa.gov/1usagov | jq .

4. Use jq to target a specific piece of the object. Let's go for the url (in the JSON schema it's called "u". Experiment with your own!):

curl --no-buffer -s http://developer.usa.gov/1usagov | jq .

5. Now let's put that stuff in a file!

curl --no-buffer -s http://developer.usa.gov/1usagov | jq .u >>tester.txt

6. What if we want multiple parameters?

curl --no-buffer -s http://developer.usa.gov/1usagov | jq '.u,.ll' >>multiple.txt

7. What if we don't like buffering?

curl --no-buffer -s http://developer.usa.gov/1usagov | jq --unbuffered '.u,.ll' >>multiple2.txt

8. What if we want a series of arrays? 

curl --no-buffer -s http://developer.usa.gov/1usagov | jq --unbuffered --compact-output '[.u,.ll[]]' >>multiple4.txt

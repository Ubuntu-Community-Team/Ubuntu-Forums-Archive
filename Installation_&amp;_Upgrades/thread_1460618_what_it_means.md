---
title: "what it means?"
date: 2010-04-23
forum: Installation &amp; Upgrades
---

### Post by asad.buntu on 2010-04-23
while installing something this error occurs ....
:(

**E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)**

what does it mean..? n how can i overcome .............
help mw out plzzzzzzzz

---

### Post by Alan James on 2010-04-23
If you are trying to install something from the terminal while Synaptic is running you will get this error because they are both trying to run the program “dpkg” which only allows one program at a time to run it. Close Synaptic or any other program used to install applications and it should work through the terminal.

---

### Post by asad.buntu on 2010-04-23
thanxxxx  budyy!

i would be very thankful if u plz telme something about synaptic.

 :)

---

### Post by Alan James on 2010-04-24
I would be happy to tell you anything you ask about Synaptic but you will have to ask a question first. Here is a link to a Wikipedia page in the meantime.
 [URL="http://en.wikipedia.org/wiki/Synaptic_%28software%29"]
[/URL]
[http://en.wikipedia.org/wiki/Synaptic_(software)]("http://en.wikipedia.org/wiki/Synaptic_%28software%29")

---

### Post by asad.buntu on 2010-04-28
oka i have got a bit about synaptic....

actually i want to install some packages.... but i couldn't found em....
while working in fedora these packages were available.....
 m basically doing telecom engineering n m doing my final year project ... which is linux based software ........
for that i want some packages

-autotools
-libyaml
- libssl
- libevent

now if i use apt-get install :

root@ubuntu:/home/falcon# apt-get install libyaml
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libyaml

if i use yum install :

root@ubuntu:/home/falcon# yum install libyaml
Setting up Install Process
Parsing package install arguments
No package libyaml available.
Nothing to do

how do i sort out this problem..... plzzzzzzzz help...

---


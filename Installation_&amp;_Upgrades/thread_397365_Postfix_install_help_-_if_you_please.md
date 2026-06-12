---
title: "Postfix install help - if you please"
date: 2007-03-30
forum: Installation &amp; Upgrades
---

### Post by Ray Paradise on 2007-03-30
I am relatively new to Linux (I have successfully installed Ubuntu 6.10 and have been liking it for several months). I have used this forum on my way up the learning curve and want to say "thanks" generally to those I have not thanked specifically...

I recently installed Postfix on my Dell Dimension 4400 box (based on this documentation: [https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)) and successfully tested it. Yeah!

I then tried to install Courier POP (based on this documentation: ([https://help.ubuntu.com/community/PostfixBasicSetupHowto](https://help.ubuntu.com/community/PostfixBasicSetupHowto)) and got this error: "E: Couldn't find package courier-pop"

Can someone give a new guy some help? Why can't it find it? Where do I get it and get the system to see it?

FYI: I may reply with some silly questions, as I am still learning...

Thanks.

Ray

---

### Post by orb9220 on 2007-03-30
When you opened a term and: sudo apt-get install courier-pop  is when you recieve the error when connected to internet?

---

### Post by Ray Paradise on 2007-03-30
Yes.

Here's the error: 

Reading package lists...done.
Building dependency tree
Reading state information...done.
E: Couldn't find package courier-pop.

Ray

---

### Post by Ray Paradise on 2007-03-30
I figured it out...

I had forgotten to run:

sudo apt-get install mailx

...which installs the mail utility program and the mail command...


Ray

---


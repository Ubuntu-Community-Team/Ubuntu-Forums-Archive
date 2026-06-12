---
title: "first try at system fixing"
date: 2008-08-26
forum: Installation &amp; Upgrades
---

### Post by MarkX on 2008-08-26
Is there some helpful soul to tell an absolute beginner how to manually run dpkg--configure-a' ? I am trying to use kino in hardy heron and have weird colours , failure to retrieve, want to uninsall and install but get above error message. Have reported that E:_cache->open() failedfix error, kino, hardy heron

---

### Post by Pumalite on 2008-08-26
At the Terminal:
sudo dpkg --configure -a

---

### Post by manishtech on 2008-08-26
If this doesnt work properly,or you still facing some problems then check out this link

[http://www.linuxquestions.org/questions/ubuntu-63/dpkg-configure-a-error-361965/](http://www.linuxquestions.org/questions/ubuntu-63/dpkg-configure-a-error-361965/)

It covers many many different types of errors which dpkg can throw :confused:

---

### Post by MarkX on 2008-08-26
Thanks. but it's not so easy to teach an old dog new tricks; how do I get to the terminal? I appreciate that it's not easy for you clever people to fathom the depths of a beginners ignorance!

---

### Post by MarkX on 2008-08-26
Dear manishtech,much appreciate your help from India, maybe better stick with first answer for a bit. Problem is that the real Mark X fixed up my computer on the condition that it was for Linux, I'm interested in video editing, Mark has gone on holiday, there is this error, and I myself don't  know the first thing about computer programming!

---

### Post by Pumalite on 2008-08-26
Applications>Accessories>Terminal:
sudo dpkg --configure -a
sudo apt-get -f install 
sudo apt-get update
sudo apt-get dist-upgrade
(one at the time. Press 'Enter' after each one)

---

### Post by MarkX on 2008-08-27
Thanks I shall be a while with this as there is a lot of stuff to read at terminal! Like the bit about enter, I was very pleased with myself last week when the new computer would not respond to user name and I eventually  all on my own thought to press enter! Unfortunately sudo dpkg--configure-a   evokes   command not found     Thanks, "for no man is an island, sufficient unto himself"

---

### Post by MarkX on 2008-08-27
I've now tried several times. Once it asked for password but nothing worked. If I ignore the response and just type in all the commands with enter between, end up  with  E: dpkg was interrupted, you must manually run 'dpkg--configure-a' which is of course what I was trying to do in the first place.      "A change is as good as a rest"  I'll do something else for a bit.

---

### Post by Pumalite on 2008-08-27
Post output in its entirety.

---

### Post by MarkX on 2008-08-28
Doneit!Like magic it really got working this time, I slept on it then it ocurred to me that the spaces might count as bits so typed it in most carefully, things happened, I followed instructions, have now uninstalled and reinstalled Movie Player Xine without error message, but still have reversed colours, e.g. pale blue egg yolk when playing some clips (but not all) What was it Robert the Bruce said when he watched the spider?  Last quote maybe should have compleat instead of sufficient. Lots of thanks o master

---

### Post by Pumalite on 2008-08-28
Glad you got it working. Good luck!.Use the Thead Tools and mark it as Soved please.

---

### Post by meihua on 2008-08-31
Last thankyou to pumalite.I learned a lot from that and went on to fix incorrect colours with help from  cor2y and have now registered on my own account in the above rather fanciful name since all my ordinary names are already in use by others!

---


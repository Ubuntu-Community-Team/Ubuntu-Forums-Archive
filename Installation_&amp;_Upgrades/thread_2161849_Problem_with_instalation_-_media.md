---
title: "Problem with instalation - media"
date: 2013-07-12
forum: Installation &amp; Upgrades
---

### Post by piotrbb1 on 2013-07-12
Hello,

I have Ubuntu on both my laptops. Recently I changed my 2GB ram for 4GB in my netbook (Acer Aspire AO722 - one slot). I decided to change the 32 bit to 64 to use the whole of ram. After searching the forum I decided that the best thing to do is set up the system again. I installed Ubuntu 13 as an upgrade (and shifted from 32 to 64). It worked fine but after a few days I decided that I wanted to switch back to 12.04 - which I have on my Lenovo G550 laptop because it is the most stable system ever while Ubuntu 13 gave me some pains. Sometimes the browsers (both Mozilla and Firefox) would shut down by themselves. I also discovered that it tends to happen when I have, let's say 5 windows opened and I open another. Another thing is the HDMI sound - Ubuntu 13 did not detect it and I found on the forum that it is already a bug. So I thought it would be best to set the stable version of the system, from the scratch. Since yesterday I have been trying Ubuntu 12.04 in Polish version and the English one, downloaded the iso from different locations: ubuntu.com, ubuntu.pl (I am Polish) and every time, sooner or later I come across this problem with the media. In the middle of set up it says - error, sends it to ubuntu helpcentre and then tells me that there is a problem with the CD/DVD. Well, it's a netbook, so I use live usb, I have tried different sticks, different slots in my computer and I am at a loss. I was even able to use the Ubuntu from the stick and was able to download the iso to hard-drive but this is as far as it goes. Please help. I never try to bother the forum crew with my problems and mostly find the answers to my questions in the already existing thread but this is new for me and was alwas able to boot normally until yesterday.

Please, please help :-)

---

### Post by piotrbb1 on 2013-07-12
One more thing, if there was a problem with the live usb would I be able to use ubuntu from usb without setting it up?

---

### Post by piotrbb1 on 2013-07-12
As I thought it might be a problem with the way the live usb is created I tried the usb creator gtk and usb creator kde. The same problem. Problem with the media CD/DVD

---

### Post by grahammechanical on 2013-07-12
Could you please confirm a few things that are not clear from your post?

1) you have installed and are running Ubuntu 13.04 64bit?
2) you have run the 12.04 live session in both Polish and English?
3) during installation of 12.04 you get an error and the installation does not finish?
4) what does the error message say? 

There are two ways we can install Ubuntu from DVD/USB


a) From the live session. We allow the live session to load and awe are asked to TRY -INSTALL Ubuntu. We select TRY UBUNTU and at the live session desktop we click the Install Ubuntu icon.
b) At the first purple screen we press Enter. At the Language screen we select a language and press Enter. At the next screen we select INSTALL Ubuntu and press Enter.


Have you tired both ways of installing. I ask because twice recently I had an installation of Ubuntu fail at the point that the process was copying files. The error message siad that there was not enough disk space when there was 10GB available. But when I started the installation from the live session desktop the installation did not fail. So, I suggest that you try using one of the other methods.

Regards.

---

### Post by piotrbb1 on 2013-07-12
Ok, thanks for the hint, I'll try it. First I had Ubuntu 12.04 32 bit because I had 2GB RAM
Then I put in 4GB RAM and decided to change for Ubuntu 64bit - I chose Ubuntu 13.
Then I had trouble with HDMI bug and browsers shutting down.
Then I decided to go back to stable Ubuntu 12.04. Here problems started and since then I was not able to set up the system.
Then I tried downloading from different sited: Ubuntu.com and Ubuntu.pl - the same result.
Then I discovered that running ubuntu from USB works OK.
Now I am experimenting with switching back to 2GB RAM and setting up the system (if, for some reason the extended new RAM is interfering with the system set up). If that doesn't work I'll try your trick. :-) I hope I was clear. Sorry about being chaotic in my previous post.

---

### Post by piotrbb1 on 2013-07-12
Well, what do you know. Everything went smoothly. RAM was the culprit but the boot fail report suggested  something was wrong with CD/DVD source. That also explains the browsers shutting down. Now I just have to run a RAM check and pay a visit to the computer shop I got my RAM from:-)

Thanks a lot for your advice. Case solved.

---


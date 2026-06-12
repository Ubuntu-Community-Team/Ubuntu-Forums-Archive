---
title: "Display is all distorted when trying to run Ubuntu"
date: 2013-10-25
forum: Installation &amp; Upgrades
---

### Post by rencemc on 2013-10-25
Hi,

  I have been trying to run Ubuntu Live on my HP Pavillion DV6736nr. When it loads, the display is all distored and stretched out
and is unusable. I know I have run a live version on this laptop before, but I am perplexed as to why this is happening now. I realize
that if I did an install, it MIGHT pull in 3rd party drivers that may help solve the issue, but I can't do anything with the screen like that.
I tried a handfull of different distributions but they all yield the same results. The only one option that I was able to get to come up
was the low graphic option for Fedora (it comes up with a menu when loading) - the screen was OK then.

  Any ideas why I am seeing this now when I have run in the past ? 32bit vs 64bit differences ? 

  Thanks in advance for your input.

     Rence

---

### Post by rencemc on 2013-10-25
Is there a way to somehow add drivers to the bootable media maybe ?

---

### Post by su:bhatta on 2013-10-25
Have you trying booting with the 'nomodeset' kernel arg?

---

### Post by rencemc on 2013-10-25
I haven't tried that. Do I have to get to a command prompt to do that ?

---

### Post by su:bhatta on 2013-10-25
Command prompt not required. Here is the page with screenshots that shows you how to use the 'nomodeset' :

[http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it/162076#162076](http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it/162076#162076)

Have a go and see if it helps.

Also, maybe it will help if you provide the system specification like Graphics card, CPU etc.

---

### Post by rencemc on 2013-10-26
[**[COLOR=#000000]That did the trick, bhattabhishek[/COLOR]**]("http://ubuntuforums.org/member.php?u=1819052") !

---

### Post by su:bhatta on 2013-10-27
Rencemc, Glad to be of help. 


Stick to Opensource drivers but maybe, you have to install proprietary drivers if you are using  AMD/ATI or Nvidia cards, in case you don't get right screen resolution & graphics acceleration with open source drivers. ( I have that problem) !

---


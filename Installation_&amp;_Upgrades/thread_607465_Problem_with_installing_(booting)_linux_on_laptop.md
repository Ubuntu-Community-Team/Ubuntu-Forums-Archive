---
title: "Problem with installing (booting) linux on laptop"
date: 2007-11-08
forum: Installation &amp; Upgrades
---

### Post by therille on 2007-11-08
Hello everyone.
My English is not the best, but I think we will understand eachother.
Here is my problem: I want to install linux on my laptop Fujitsu Siemens Esprimo Mobile V5545 (intel dual 2 core 2GHz). I have downloaded a few versions of linux (suse 10.3, fedora 7, mandriva, ubuntu 7.10) and I burned them on CD's (3CD for each). I have 3 partitions on my HDD including Windows Vista on the first, formated with NTFS. The problem is that my laptop wan't boot any of theese CD's, just starts windows without any asking. CD ROM works fine and BIOS is configured well too, first to boot from CD/DVD (I had no booting troubles at all when I installed Vista). I also burned CD's correctly (not one ISO file on them).
I have red some topics on this forum that seems to me can solve my problem, but I got no answers. Any help...please...

---

### Post by hardyn on 2007-11-08
the images must be burnt as images NOT AS FILES!
burning an image will have a unique option in your CD writing program.

there are instructions on how to do this at the ubuntu.com website.

---

### Post by bulldog on 2007-11-09
The ubuntu cd should be just one cd-rom not three.
Or did you burned extra copies and flavors.

---

### Post by Pumalite on 2007-11-09
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)
Most of all, do md5sum on iso, burn at 4x as 'image'

---

### Post by therille on 2007-11-09
I will try to burn them slowly as iso image and I will let you know what I have done. I have 2 ubuntu cd's (ubuntu desktop and ubuntu server).
What is the md5sum?

---

### Post by Pumalite on 2007-11-09
Read the link I gave you.

---

### Post by Pumalite on 2007-11-09
[http://en.wikipedia.org/wiki/Md5sum](http://en.wikipedia.org/wiki/Md5sum)

---

### Post by therille on 2007-11-09
Thanks for the link. I burnt CD as you said, but nothing happend. Still wont boot, just starts Vista without any choice. Do you have any other solutions?

---

### Post by Pumalite on 2007-11-09
Make sure CD is first in boot order in BIOS.

---

### Post by therille on 2007-11-09
IT IS. I even tryed to disable booting from other devices (HDD, USB,...) and only left CD/DVD. In that case nothing without black screen appeared.

---

### Post by therille on 2007-11-10
Hey... IT WORKS. Thanks everyone. I downloaded Infra Recorder and i burned iso image on a minimum speed as you told me. That was a problem! Nero does not have an option to burn CDs at 1x and 2x. Thanks everyone again. I have just one more question: I installed open SUSE 10.3 twice because I first installed it on a partition wich I won't. BUT after first installation, when I started open SUSE I could use my WHOLE HDD (including partitions that belongs to Windows Vista), and after second I couldn't algthout I think that I do installation in the same way as first. Linux just don't see them (only see it's owen partitions what I think it's right). Do anyone know how is that possible and how Linux could access Vista's partitions at firs time? I know that it is ubuntu forum, but I think that someone of you might have a same situation and can answer.

---

### Post by Pumalite on 2007-11-10
You are welcome. Good luck. (Gutsy comes with ntfs-3g prepackaged)

---

### Post by richyp96 on 2008-04-25
I've had exactly the same problem with a CD I know works on a Dell laptop. Have you managed to solve this one yet?

---

### Post by richyp96 on 2008-04-25
Sorry, just read the last two posts, duuh.

---


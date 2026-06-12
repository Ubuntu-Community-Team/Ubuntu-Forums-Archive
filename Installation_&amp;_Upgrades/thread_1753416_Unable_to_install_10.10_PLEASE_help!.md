---
title: "Unable to install 10.10 PLEASE help!"
date: 2011-05-08
forum: Installation &amp; Upgrades
---

### Post by trolol on 2011-05-08
Hello, first I only joined these forums today so yeah sorry if I ask any noob question..

Anyway, I am on an HP mini netbook running Windows 7 starter edition. But recently, I somehow managed to brake it. Now the OS and everything even the hard drive is corrupted (or idk_. So yeah I am trying to install Ubuntu 10.10. I try to install it from a live CD using an external CD drive. I have 160gb HDD and 1gb ram btw. And whenever I try to install it it gives me the same error. 

What happens is when I click install, it goes through all the installing but gets stuck at the part where it says "creating ext4 file system...." then it stops the installation and gives me that "input output" error (idk what it exactly says sorry the netbook isnt near me right now). I tried like over 20 methods to try and fix this. I tried playing around in gParted, making like 6 different partitions and just doing completely random things and hope it works, but nothing. I even tried making an ext3 and ext2 and all other ones instead of the ext4. But still nothing> I have been getting the same error for over a week now and I wanna install ubuntu ! I dont wanna go back to Windows coz it seems unstable and it broke my laptop several times already. So yeah. Also the internet cant connect while I am installing ( however I know how to get the internet after installing). Also I am sorry for the possibly bad explanation of things I am only 14 years old lol and english isnt really my first language so if someone can help me install ubuntu in the simplest way possible that would be great. :) thank you in advance I hope to see some help please 
:D:popcorn::KS

---

### Post by Quackers on 2011-05-09
Welcome to UF :-)
Firstly, have you checked the md5sum of the downloaded iso file (that you burned to cd)? Here's how
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If that checks out ok (or maybe first if you want) when booting from the cd and at the first purple screen (the one with the little stickman at the bottom) press any key. Then choose your language and on the next screen choose the "check for errors" option.
If that check finds any errors at all the disc is no good.
If you then check the md5sum of the downloaded iso (as above) and it looks ok you may need to burn the iso image to disc again at the slowest possible speed.

---


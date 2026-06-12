---
title: "frozen screen on ubuntu 64 install"
date: 2006-10-11
forum: Installation &amp; Upgrades
---

### Post by sandbagger on 2006-10-11
Hey everyone.
I've installed linux on a couple of my computers now since being a linux virgin up until 3 months ago. I even got ubuntu running with beryl on my work pc today! wow!
Anyway, I'm trying to install ubuntu on my home desktop now and i'm completly stumped. The pc I'm installing on is an athlon 64 x2 with nvidia pcie 6600le video in sli mode. 120gb raid 0 hdd with xp x64 installed on one big ntfs partition. 2gb ram. nforce 4 mainboard
I downloaded ubuntu 6.06 64 bit live dvd and whacked it in the drive. It gets to the boot menu withthe countdown and my keyboard and mouse don't work (works fine in xp (and in ubuntu on vmware on the same pc)). Since I can't make a selection it just procedes to load up to the point with the flashing underscore. After a few seconds it stops flashing, then after a further 10 or 15 seconds I hear the ubuntu startup sound.
I've tried both x64 & x86 discs.
Can anyone help?
btw, my partitions were wiped when installing ubuntu on my office computer the other day. Is that going to happen again?

---

### Post by Kacey on 2006-10-11
I posted this in another thread as well, I too am having the same problem. With a suse install I was able to fix this by editing the xorg.conf file but in ubuntu I am unable to do so. Heres the deal, this is a issue with SLI I have searched this forum for a few days now and I have seen that this is happending to EVERYONE with SLI. I am still trying to find a fix for this. I am also about to install ubuntu on a 32 bit with a ATI card, once this is done I will have a better look at how the xorg.conf file looks in ubuntu. I will keep you posted.

---

### Post by chrisjentys on 2006-10-11
Hi, Im having exactly the same problem. As far as ive figured out its because the 6600 card isnt supported by the open source nv drivers. 
I found a suggested fix which involved installing from the alternate installer cd, booting into recovery console then running; 

dpkg-reconfigure xserver-xorg

then setting the gfx driver to vesa or vga, neither of these worked for me.

Im new to linux too so sry if thats all a bit vague.

Good luck,

Chris.
 

heres a link to my post
[http://ubuntuforums.org/showthread.php?t=275561](http://ubuntuforums.org/showthread.php?t=275561)

---

### Post by Kacey on 2006-10-11
That could be but I use two 6800xt's. It seemd to happen to alot of sli users with diffrent cards. I have read that some people have got it to work, but there is not fix that I have seen. I think that someone knows but has not posted it. I am going to start another thread for this and I hope to get some more light shead on this.

*EDIT* 
Here is the link to the new thread I made, I think it would be best to continue this conversation over there as we all seem to face the same issue. 
[http://http://www.ubuntuforums.org/showthread.php?p=1605984#post1605984]("http://www.ubuntuforums.org/showthread.php?p=1605984#post1605984")
*edit* Sorry about the link, at work and was rushing my self.

---

### Post by chrisjentys on 2006-10-11
You sure that links correct?

---

### Post by Kacey on 2006-10-11
Sorry about that. Its fixed now.

---


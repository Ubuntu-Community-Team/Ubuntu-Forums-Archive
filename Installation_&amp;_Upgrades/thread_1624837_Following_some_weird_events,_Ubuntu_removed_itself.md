---
title: "Following some weird events, Ubuntu removed itself from the GRUB menu."
date: 2010-11-18
forum: Installation &amp; Upgrades
---

### Post by InTheMarket on 2010-11-18
And I'm in despair.
 --Yesterday-- 
Trying to make wine work, used POL, and etc. I managed to make wine run with Roller Coaster Tycoon. I didn't install anything major. It may be relevant that I was downloading a torrent before (legal, free torrent, PWO in case you were wondering) Then, as my daily-work-on-ubuntu work drew to a close, I hit update manger or whatever it's called, and it basically tells me it broke itself and only wants to do partial updates. I was like, okay, fine, no biggie, the partial updates will probably fix it. They didn't, and it kept freezing. PLUS it removed wine for whatever evil reason. So I do it again, and it says it has more partial upgrades to install. And again. At this point, I googled how to fix it. I did all the standard stuff to troubleshoot this. All that stuff in terminal said nothing was amiss, and I was tired, so I called it a day.  
When my sister wanted on windows, Ubuntu did not want to restart. I did ctrl+alt+delete+delete and it restarted, and windows worked fine. 

--This Morning-- 
I booted up the computer and Ubuntu is no longer on the GRUB menu. Only windows 7 and two memory tests. I did not install any large files or new versions, I've been using Ubuntu 10.10 since I switched from windows like two weeks ago. Reading up, I learned that Partial upgrades can really eff up my system, so I'm guessing they are the culprit (thanks for the heads up, update manager >.>)   
What can I do at this point to get Ubuntu back with as much of my data as possible?

---

### Post by dino99 on 2010-11-18
updating/upgrading is a serious thing, thats why reading doc and sticky threads is mainly a good idea, specially for noobs that hold down "enter" without watching the warnings .

[http://newyork.ubuntuforums.org/showthread.php?t=1581099](http://newyork.ubuntuforums.org/showthread.php?t=1581099)

---

### Post by oldfred on 2010-11-18
Use dino99's link to drs305 way to chroot into your system from liveCD.

Then you need to run these and maybe some other commands to add whatever else you deleted.

apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
apt-get -f install

---

### Post by InTheMarket on 2010-11-18
Pretty sure Chroot  fried my hard drive.

Now all I got is the GRUB command line. Sigh.

EDIT: Got it to boot using the live CD. Really starting to hate GRUB. I'll try chroot again -.-'

---

### Post by drs305 on 2010-11-18
Nothing in the 'chroot' command or what *oldfred* recommended would have damaged your system.

From the grub rescue prompt, run these commands:
**ls **
then, if it sees your Ubuntu partition (hd0,1)=sda1; (hd1,5)=sdb5, etc  Use the appropriate values instead of X,Y in the following commands.
**ls (hdX,Y)/boot**
Can you see any kernels/initrd images (vmlinuz...; initrd.img...)?
**ls (hdX,Y)/boot/grub**
Can you see lots of '.mod' files?

---


---
title: "Upgrade to 10.04 failed"
date: 2010-08-24
forum: Installation &amp; Upgrades
---

### Post by doihavetodothis? on 2010-08-24
I have a dual boot PC, the windows partition still works. 
The upgrade from 8.04LTS to 10.04 LTS has failed. I can't boot up - in one of the modes it tells me:
mount:/mounting none of /dev failed no such device
etc....
dropping to a shell
Busy Box v1.13.3

I now have four or five new kernels and recovery lines when i boot up, so in the beginning it all looks good. 

But when I boot up it won't, or in recovery mode it says something like this: 
General error mounting file systems, a maintenance shell will now be started
root@karin-desktop:~#
(fsck says dev/sda3 clean)
you must manually run sudo dpkg --configure -a
When I run this it says:
W:not using locking for read only lock file /var/lib/apt/lists/lock
error security.ubuntu.com
error za.archive.ubuntu.com
unable to access dpkg status area: read only file system

(In brief - I haven't written down every line.)
(If you can tell me where to go to get the info you need... )

In the meantime 8.04 has disappeared off my system. Is there a way to revert to it without losing all my info? I really don't want to do a clean install and don't have a live CD. Or is there a way to save the new install and my info? 

Thanks.

---

### Post by mörgæs on 2010-08-24
Does the machine work well, if you boot with a 10.04 live CD?

---

### Post by doihavetodothis? on 2010-08-24
I don't have a live CD :(

---

### Post by mörgæs on 2010-08-24
You can burn a CD from the files here:
[http://www.releases.ubuntu.com/](http://www.releases.ubuntu.com/)

---

### Post by doihavetodothis? on 2010-08-24
> **mörgæs said:**
> You can burn a CD from the files here:
[http://www.releases.ubuntu.com/](http://www.releases.ubuntu.com/)


Thank you. I am downloading the  alternate install CD- is that the right one to use?

As I have XP on my PC as well....

---

### Post by mörgæs on 2010-08-24
As far as I know the alternate CD is only for installation, not for live testing. The 'desktop' version works for both testing and installation, if there is enough memory on the machine.

---

### Post by doihavetodothis? on 2010-08-24
Ok, will download the desktop and see what happens tomorrow - it's going to take around 6 hours...

---

### Post by doihavetodothis? on 2010-08-25
Have used the live CD and it works. So that's good. Now how do I rescue my info from Hardy Heron and keep my windows partition? Thank  you....

---

### Post by mörgæs on 2010-08-25
Good. Now when booting the live CD you can rescue the files from /home to a USB stick.

---

### Post by doihavetodothis? on 2010-08-25
> **mörgæs said:**
> Good. Now when booting the live CD you can rescue the files from /home to a USB stick.

:) ok, how do I do that? Can you give me more details? Would that be in the terminal window or some other way?

---

### Post by mörgæs on 2010-08-25
A terminal or Nautilus, as you please. You should be able to see the whole file system both ways.

---

### Post by doihavetodothis? on 2010-08-25
> **mörgæs said:**
> A terminal or Nautilus, as you please. You should be able to see the whole file system both ways.
That's great! I found both my drives and I can copy most of the info across - except that some files are locked and permission is denied - they are fairly ordinary things like some open office documents, some pictures, some mp3's downloaded from the internet... any idea why they should be read only/can't be copied?

---

### Post by mörgæs on 2010-08-25
This thread should explain it all.
[http://ubuntuforums.org/showthread.php?t=1552258](http://ubuntuforums.org/showthread.php?t=1552258)

---

### Post by doihavetodothis? on 2010-08-25
Thanks for all your help - I'll do this all later when I have time but it looks like I am sorted.

---


---
title: "not booting &quot;problem activating swap&quot; terminated with status 255"
date: 2012-10-01
forum: Installation &amp; Upgrades
---

### Post by arifalisyed on 2012-10-01
Hi There,
         I recently installed Xubuntu on my Intel Pentium 4 PC as dual boot option. 
I already had Windows XP SP3 pre-installed. my intend was i will slowly get away with Windows,
if we get hang on Xubuntu 

For more than two weeks everything worked fine. Xubuntu was my default OS and everyone in my family including 3 year old kid, got use to of it.
Now it has stopped booting.

it says "problem activating swap"
Please find the screenshot of of what error message is thrown during boot. 
[http://dl.dropbox.com/u/70034945/IMAG0695.jpg](http://dl.dropbox.com/u/70034945/IMAG0695.jpg)
[IMG]http://dl.dropbox.com/u/70034945/IMAG0695.jpg[/IMG]

I suspect it could also be because of power failure ( improper shutdown) .
I do not have UPS, so now whenever there is any power failure..boom..boom.

Can that be reason behind this? 
how do i recover from it now?

When I installed Xubuntu Grub had a repair mode.
I tried that repair mode boot also.
a) enabled networking
b) check file syste,
c) repaired packages, everytime it downloads some irrelated langauges packs and Google chrome browsers packages .. 
d) and when i say resume normal boot then from repair mode itself it tries to launch XFCE ...and able to launch sometime ....


Now even after repair mode and step a) b) c) and d) its not at all showing up the XFCE desktop.
What can be done other than re-formatting? 

[I hope cross posting is allowed here, as  i have already posted this on launchpad, just trying out my luck everywhere]

---

### Post by arifalisyed on 2012-10-03
I was wondering if my this post is at all visible? 

this is "test reply", please respond if its visible

---

### Post by oldfred on 2012-10-03
Better to upload using paperclip icon in edit panel above message. Then it is not so large as to be unreadable. :)

Usually when there is an issue with swap it still boots? 

So you may have other issues also. 

If you had a power failure and it closed system abnormally, you may need fsck on your ext partition(s). It cannot be run on swap as that really is just unformated space, unless you have encryption on. With encryption on /home then swap is also encrypted. 

#From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---


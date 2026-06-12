---
title: "Fresh Install Problem"
date: 2007-06-05
forum: Installation &amp; Upgrades
---

### Post by pbhill on 2007-06-05
I'm having a problem with an older  Sager  laptop that has had a second chance at life by having Ubuntu installed. I'm now trying to do a clean install using the live Feisty CD, but I can't for the life of me get it to Boot from the CD. It keeps going straight to the hard drive. I've hit F12 and selected "CD" as the boot option. Is there another way? 
I can't boot up my current installation, after the password is entered it asks me to use the terminal to boot. ...I don't know much about that.

---

### Post by ugm6hr on 2007-06-05
> **pbhill said:**
> I can't for the life of me get it to Boot from the CD. It keeps going straight to the hard drive. I've hit F12 and selected "CD" as the boot option. Is there another way? 


Did you burn the .iso , or merely copy the .iso file onto a blank CD?  Which program (and at what speed) did you burn with?  Have you checked the MD5 checksum?  This might explain (Doing a Checksum / Burning the ISO section):
[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

If you know you did that properly - try the CD in a different computer.  Might be your CD drive doesn't work?

---

### Post by dabl on 2007-06-05
> **pbhill said:**
>  It keeps going straight to the hard drive. 

It sounds like the BIOS is set to boot from the hard drive first.  You need to enter BIOS during the startup process for the laptop -- there should be some indicator of how you do that shortly after you turn it on.  Then you need to find the screen in BIOS that sets the device boot sequence, and you need to change it so that it boots first from the CD, and second from the hard drive.

:D

---

### Post by pbhill on 2007-06-05
The CD is OK, as I used it with another setup. Tell me more about MD5 Checksum... I'm not familiar with this.

---

### Post by ugm6hr on 2007-06-06
> **pbhill said:**
> The CD is OK, as I used it with another setup. Tell me more about MD5 Checksum... I'm not familiar with this.

If the CD works on a different computer, then the MD5 must be OK.

When you press F12 - does that enter BIOS, or give a temporary boot option?  Might be worth changing it in BIOS - try the other F keys (F2 is common) at bootup.  Make sure you save the BIOS changes to boot.

> I can't boot up my current installation, after the password is entered it asks me to use the terminal to boot. ...I don't know much about that.

And what does this mean?  You've got a current HD installation of Ubuntu?  Did someone else install it for you?

---

### Post by pbhill on 2007-06-06
F12 gets me to BIOS, and it's set to boot from CD 1st. Just doesn't do it... goes straight to hdd.
I have feisty installed, its been good until the other day.  I thought a clean install would get me back to square one, but now Im  stuck!
My problem was on startup, after the password I get the error: 
  "Your session only lasted less than 10 seconds. If you have not logged out, this could mean that there is some installation problem or you may be out of diskspace. Try logging in with one of the failsafe sessions to see if you can fix this problem."
Not wanting to mess around any longer in failsafe where I really was lost, I thought it was time for a fresh install! Now I just can't use that machine at all. 
I read a post that talked about the  fbdisk.exe to copy  a boot file image to a floppy, but it won't work in WinXP, which is all I have at the moment...

---

### Post by ugm6hr on 2007-06-07
Only explanation I can think of is that your CD drive is dead.  So I think even booting from a floppy will not help.

Presumably you booted from the same CD drive when you first installed Feisty?  Can't have been that long ago - have you made any hardware changes since then?

Never tried failsafe mode - does it have a GUI? If so - try the CD drive out in it.

---

### Post by Wim Sturkenboom on 2007-06-07
Was your previous install on this laptop from the same CD? Or did you burn a new iso?.

The problem that you can not login using the GUI might be caused by a HD or partition that's full. If I understand your post correctly, you can get to a console. Login and run the following commands:
```

df -h
sudo du --max-depth=1 /

```
Post the result of each command here so we can determine were the space is used.

---

### Post by pbhill on 2007-06-07
I have tried the same one and alo a new download.
I can reach the failsafe terminal screen.

I'll have to copy manually... 

"$ df -h
Filesysystem        Size     Used     Avail     Use%      Mounted On
/dev/hda1           36G      8.3G     26G      25%          /
varrun                 126M    204k    125M    1%            /var/run
varlock                126M    4k         126M    1%            /var/lock
procbususb         126M    100K    126M     1%           /proc/bus/usb
udev                   126M   100K     126M     1%           /dev
devshm               126M   0           126M     0%           /dev/shm
1rm                     126M    34M      92M      27%         /lib/modles/2.6.20-16-386/volatile

$ sudo du --max-depth=1 /
48           /lost + found
384376    /var
12048      /etc
12           /media
4640        /bin
66404      /boot
132          /dev
4950064   /home
4              /initrd
509948     /lib
4              /mnt
122268     /opt
0              /proc
6508         /root
9388         /sbin
4              /srv
0              /sys
40            /tmp
2514108   /usr
8589180   /

---

### Post by pbhill on 2007-06-07
Ok, so now I've done a bit of Googling and have tried a file called "bcdl150z". I copied it to a floppy with WinImage. This actually finds the CD Drive and requests a boot from it, but I still can't. Have tried several Bootable CD's of different sorts (Gparted, Clonezilla,Ununtu 6.06) I'm thinking a bad CD drive at this point... 
Is there away to boot this old box with a  thumb drive? I also have a USB CD Drive. LAN?

Thanks for your help!

---

### Post by pbhill on 2007-06-10
All hail Super Grub! [URL="http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html"]   After much heartache I found Super Grub to do what no other has done! After burning it to an iso disc and running the simple utility , I was able to boot from  CD's again. I solved my log in problem by reinstalling the whole kit and kaboodle. It's good to be Ubuntuing again!

---

### Post by ugm6hr on 2007-06-10
Bizarre....

Can't think how SuperGRUB would be able to resurrect your CD-booting.

But, if it works :)

Well done for solving it.

---

### Post by pbhill on 2007-06-21
Sheer Luck? But it worked. Thanks for the support.

---


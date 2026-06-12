---
title: "install on virgin machine"
date: 2010-04-29
forum: Installation &amp; Upgrades
---

### Post by trolleyman on 2010-04-29
I just built a new computer and tried to install Ubuntu on a virgin hard-drive. The comp will boot and run from the usb thumb-drive but i can't get the OS to install on the hard-drive.  This is my 1st time using Ubuntu, so any help would be greatly appreciated.  Thanks in advance.

---

### Post by limey_rick on 2010-04-29
Can you provide some more information? 

[LIST]
[*]Does the Ubuntu installation program start?
[*]If it stops at a particular point in the installation, can you let us know where that is?
[*]64-bit or 32-bit installation?
[*]Do you have a Live CD of Ubuntu? Can you boot and run this?
[/LIST]

---

### Post by mjitkop on 2010-04-29
It is not clear to me if the OP means that Ubuntu boots only if the USB drive is present. In which case it would mean that GRUB got installed on the USB drive.

:confused:

Was the installation of Ubuntu done while the USB drive was present in the computer?

---

### Post by trolleyman on 2010-04-29
When I boot-up the machine it reads the thumb-drive and offers a install command. When I run the install, it starts, then finds a missing file and boots to shell. I can't remember what the missing command is but I'll retry and let you know. And, no, I don't have a CD, would that help?

---

### Post by trolleyman on 2010-04-29
When I run the install it stops w/ this message:

Gave up waiting for root device

- Boot args (cat /proc/cmdline)
    - check rootdelay= (did system wait long enough?)
    - check root= )did system wait for right device?)
- missing modules (cat /proc/moduls; ls /dev)

ALERT! does not exist. dropping to shell!

---

### Post by limey_rick on 2010-04-29
So this is not my experience when running an installation of Ubuntu, that is, I don't remember seeing an install command. 

Normally you would see a splash screen that asks if you want to install try without installaling (if you have the Live CD version).

Could you check this page: [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

You should have a CD image first and from this you create the USB installation and boot form it. Sorry if you have already done this, but I can't tell from your post. 

One quick question - are you installing from the WUBI install program instead of the Linux installation ISO? If so, WUBI install needs to be run within windows.

---

### Post by trolleyman on 2010-04-29
I'm not sure how the USB thumb-drive was made. I got it from an IT friend of mine. He uses Ubuntu on a lot of the machines at his work. I'll check with him. Also, the splash screen is where I try to install from. (Sorry if I'm vague, I'm a newbie at this!) I checked the link, and I couldn't find anything having to do w/ a virgin install, I just found install instructions for machines w/ existing OS (Windows, MAC, etc.). Did I miss something?

Also, is there a site to download Ubuntu directly from the web? I could access the web from the thumb drive and direct the install to the hard-drive.

---

### Post by limey_rick on 2010-04-29
The link for the USB document was intended to help you understand how a USB install should be done. As your friend did this for you, its probably not that helpful.

One quick question? Is the installation you got from a friend a 64 bit version and you have a 32 bit machine? 

It might be better to download an ISO image, burn this to CD and then use the CD to boot your machine and try out Ubuntu first, to see if it works. 

If you want to download a ISO image, you can get the latest from the Ubuntu.com home page, but download times now will be slow (new release just out).

Make sure you burn the ISO image correctly to a CD. See here for details:

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by trolleyman on 2010-04-29
I downloaded Ubuntu version 9.1 but when I double-click on the downloaded file it auto-connects to Power2Go for writing to the cd. I don't know if it's not burning properly or not, but I'm not showing anything on the cd when I put it in a different comp. Is there anyway to move the iso to my desktop so I can burn the program from there?

---

### Post by trolleyman on 2010-05-01
Thanks for all the time from everyone. It appears the problem was with how Firefox did the download. I got the problem solved by downloading the ISO from Opera, which allowed me to download directly to my desktop. That allowed me to access the ISO from a burning program and burn a CD. It is installing on my new comp. as I type. Again, thanks for all the help.

---


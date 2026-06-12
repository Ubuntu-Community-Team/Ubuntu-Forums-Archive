---
title: "Install Probs"
date: 2010-02-15
forum: Installation &amp; Upgrades
---

### Post by linuseless on 2010-02-15
Self confessed non-geek, trying to breathe life into old laptop before scrapping it. 
Have installed Ubuntu 9.10 from disk supplied with a LINUX magazine. Checked disk, no errors. Tried OS from disk, ran OK albeit slowly, liked the look so installed over windows XP on IBM Thinkpad R40e (2.4gh, 384RAM, 30gbHD). All well, watched all the files loading, almost an hour, until reboot, when presented with option screen: 

----------------------------------------------

GN GRUB version 1.97~beta4

Ubuntu, Linux 2.6.31-14-generic
Ubuntu, Linux 2.6.31-14-generic (recovery mode)
memory test (memtest86+)
memory test (memtest86+, serial console 115200)

----------------------------------------------

regardless of which option selected, hitting enter gives the following :

----------------------------------------------

error: no such device: efbd0088-1bbb5-4911-ba50-070f27961c57

----------------------------------------------

hitting enter reverts to the former screen; every option taken sends me in circles. 

Boots OKagain from CD for trial version.

Anything obvious (to ubuntu people) that I have missed?
Thanks in advance.

:confused:

---

### Post by linuseless on 2010-02-15
should qualify that: 
if "memtest" selected, then a memory test does take place: no errors found.
Ta

---

### Post by Satoru-san on 2010-02-15
Ubuntu uses uuid's instead of device roots like most operating systems do. You will have to fix this problem from the liveCD. I will need some help from others to help you, but I can get you started.


Boot the live cd and choose to use without change to system.

Then when it has booted open up a terminal it is in the applications menu

type this

```
sudo mkdir /mnt/ubuntu
sudo mount /dev/sda1 /mnt/ubuntu
sudo chroot /mnt/ubuntu
```
Now if you could then connect to the internet on there and log into the forums. We will need you to post some things for us maybe. like your /etc/defaults/grub

Basically what that code did was bypass booting (as the livecd did that) and throw you into your systems enviornment, if you got no errors then your system is working:p

You will probably have to reconfigure grub/reinstall grub.

**Dont give up**

---

### Post by linuseless on 2010-02-18
Thanks for that.
I'll try it over the weekend when I have a little time, even though I am already mystified:-?

---


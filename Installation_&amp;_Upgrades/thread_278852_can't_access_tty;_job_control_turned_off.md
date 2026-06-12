---
title: "can't access tty; job control turned off"
date: 2006-10-17
forum: Installation &amp; Upgrades
---

### Post by H080J03 on 2006-10-17
i had installed Ubuntu edgy, it was working great for a little while, until i installed some sort of update, now the system won't boot, it just gives my a busybox shell instead, it is not very useful. after sraeching for a couple of days, i still have no luck, some people say its trying to load the root file system some others say it has to do with some pci config thingy. any ideas on whats happening, or any on how to solve it would help a bunch.


i don't think its the root file system, i can access it form the busybox shell

i don't think its the kernel, i tried the alternative versions that Ubuntu come with, no luck, i tried recovery mode, no luck

also i downloaded the latest edgy live cd, i pop it in and it just gives me a busybox term as well.(i had been using the live cds from breezy)

so any ideas on how to make a new live cd work or my system, would be the best

---

### Post by H080J03 on 2006-10-17
bump

---

### Post by Gegglambi on 2007-02-15
This being my first post I hope that I'm giving relevant information and that it's not completely malplaced (correct me then and move the post please). 

- - - - - - - - -

I'm having the same problem myself (I think, that's why trying the same thread). _Was_ running Edgy Desktop until tuesday (13/2) morning when the power went in the entire area (spike according to the electrical company, and luckily I have spike-protection). I had upgraded Ubuntu before that and saw that it needed a reboot and thought that could reboot it during tuesday evening. After the un-wanted reboot the computer never came back to life. 

It says 'can't access tty; job control turned off'. A friend who knows more about linux (I'm just getting started myself, working with hardware and windows at work) was here looking at it and couldn't make it work. 

It doesn't seem to be a hardware problem (luckily?). Read below if you still think that. 

* * * Regarding the problem being hardware-related * * * 

So I thought it was a hardware problem (because of the electrical problems) and started searching for errors. I can fsch.ext3 a-OK on both hard drives but I don't seem to be able to kick in a Ubuntu 6.10 Live-CD without the computer hanging giving: 
hda: ide_intr: huh? expected NULL handler on exit 

I can see files on my primary HDD when in the GRUB prompt, so the system appears to be ok. 

Tried Knoppix cd as well and got an error that I don't remember at first but after that it worked and I did the ext3 file system check. The Ubuntu cd should be fine because I can start it on another computer (both with an Athlon64 processor so same image, tried 6.06 too without better luck). 

So, I wanted to know if the hardware really was ok so I took a spare HDD and installed Windows XP (can you say that without being thrown out a window in here?=) and upgraded all drivers and did a stress test. No problems whatsoever. Therefor I don't think it's a hardware problem. 

Now I'm having a Kernel Panic over this myself ._.

---

### Post by serlex on 2007-02-15
Im getting same error here, but I'm trying to install Linux(ubuntu) for the first time on my HD (dual boot).

---

### Post by mmjtech on 2007-02-15
Im getting this error as well.. but only after a larger number of I/O errors. During a live CD start

---

### Post by Gegglambi on 2007-02-16
I haven't gotten any clarity in the problem, but I can boot from a live-cd now. Or I have been able to the whole time, I just have to wait 10 minutes for all the hda_ide huh?-messages. After that, Ubuntu boots on the live-cd. 

I mounted all the partitions and moved all my data to one of the disks. Next step is to reinstall Ubuntu on the first disk. If I manage, I'll be reinstalling only the /-partition (root? boot?) and keep the swap and /home. In any case, I won't be loosing any data :guitar: 

I'll post here when I've tried Ubuntu again with all the updates. Perhaps it's the update that's the problem. Gonna run synaptics till its saturated. 

Was running and going to run Edgy Desktop (with Multiverse updates) on an Athlon64 3500+, 4x256DDR(PC3200), 2 HDD (Seagate Barracuda and Samsung Spinpoint), a GF7300LE crap-graphics card and an MSI Neo4 motherboard (built-in sound & gigabit lan) in case anyone else with the same problems recognize anything. 
Had installed amarok, irssi, django, mysql, ventrilo_srv, proftpd, alsamixer and a few other programs on it. 

Thinking on trying the Server edition if the Desktop version gives the same error again, as I'm mostly using it as a server (ftp, ventrilo, irc(through ssh) and music). 

Good luck to you all.

---

### Post by zacbarton on 2007-02-16
I had this problem but solved it with the help of this link [https://launchpad.net/ubuntu/+source/initramfs-tools/+bug/67256](https://launchpad.net/ubuntu/+source/initramfs-tools/+bug/67256)

---

### Post by serlex on 2007-02-16
> **zacbarton said:**
> I had this problem but solved it with the help of this link [https://launchpad.net/ubuntu/+source/initramfs-tools/+bug/67256](https://launchpad.net/ubuntu/+source/initramfs-tools/+bug/67256)

Thanks for that link, seems like command
```
 sudo update-initramfs -u -k 2.6.17-10-generic
```
works

but that works with systems with Ubuntu all ready installed, im trying to install Ubuntu for the first time. Dapper Live cd works fine, but something new in Feisty doesnt :( :confused:

---

### Post by simonfoley on 2007-02-18
I am having the same problem it seems.  Hmm. 

I am trying to remove XP on an old machine and install kubuntu

Any ideas anyone?

S

---

### Post by Physonius on 2007-02-19
As I discovered yesterday, I remounted my HDA5 after booting to the install CD, and then used the minimal install feature and after I rebooted, I had normal Ubuntu operation again.

Single Ubuntu OS using VMWare...and for me the OS somehow broke, because a security update failed, and wiped out my SBIN/INIT stuff.

---


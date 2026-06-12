---
title: "Installing Ubuntu on Lenovo Ideapad s205"
date: 2011-08-12
forum: Installation &amp; Upgrades
---

### Post by -=AntY=- on 2011-08-12
Hi.

I'm trying to install Ubuntu on my new laptop. Unfortunately it doesn't work very well. The guide that I've found is [http://helms-deep.cable.nu/~rwh/blog/?p=177]("http://helms-deep.cable.nu/~rwh/blog/?p=177") . (Only difference is that I'm not into that dual-booting thing ;) )

The problem appears when trying to remove GRUB2 to install GRUB legacy. I get the following error message

```
root@ubuntu:/#sudo apt-get purge grub-pc
sudo:unable to resolve host ubuntu
Reading package list... Done
Building dependency tree
Reading state information... Done
Virtual packages like 'grub-pc' can't be removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@ubuntu:/#
```

I've spent hours trying to use google to solve this but obviously my google-fu isn't strong enough.

Appreciate all help!

---

### Post by gordintoronto on 2011-08-12
What version of Ubuntu are you playing with?

That guide is extremely suspect. You should be using grub2, not grub legacy.

You say you aren't dual booting, does that mean Ubuntu will be the only OS? If so, you can partition the hard drive "properly." (Boot, root, swap, home.)

---

### Post by -=AntY=- on 2011-08-13
Version 11.04.

First off I tried to just press the "wipe the hard drive and install ubuntu"-alternative. Everything got formatted Ext4 and it was bootable. When I connected to the internet it said it was updating from GRUB 1.98 or something like that to GRUB2.

After the update was done and I tried to boot i just came to the GRUB "rescue"-console. All the alternatives when using ls was (hd0, gpt1) (hd0,gpt2) and so on for all the partitions made by the installation.

Did some googling and found that guide. Thought it was the same problem that I was experiencing.

How should I make a proper partitioning? Do I have to link something from the root to the boot or vice versa? How big should the boot and root partition be? The swap should be equal to about 2x RAM, right? The HDD is 160 and the RAM is 3 GB.

Thanks for the answer! :D

---

### Post by -=AntY=- on 2011-08-13
Tried to do as you suggested and made the partitions as following:
```
sda1	2048	/boot	Ext4
sda2	18944	/	Ext4
sda3	132905	/home	Ext4
sda4	6144	SWAP
```

This time I was connected to the internet and chose "download and install updates" when I made the installation. Now the computer won't boot. Can only get the live session going.

Seems as BIOS can't find GRUB for some reason. :S

---

### Post by gordintoronto on 2011-08-13
I'm sorry, your drive arrangement sounds wonderful. I can't figure out why you're having a problem. For what it's worth, I avoid being connected to the Internet during installation, but I doubt this caused the problem.

Grub 1.98 is considered "grub2." My system is completely up to date, and it has Grub 1.99 installed.

I'm puzzled.

---

### Post by steve11911 on 2011-08-15
This page is worth a look:

[http://forums.lenovo.com/t5/Linux-Discussion/Ubuntu-amp-Lenovo-S205/m-p/467093/message-uid/467093#U467093](http://forums.lenovo.com/t5/Linux-Discussion/Ubuntu-amp-Lenovo-S205/m-p/467093/message-uid/467093#U467093)

3 pages...

[http://ubuntuforums.org/showthread.php?t=1763994](http://ubuntuforums.org/showthread.php?t=1763994)

Youtube video looks at BIOS settings...

[http://www.youtube.com/watch?v=ij9To78Wt3w](http://www.youtube.com/watch?v=ij9To78Wt3w)

If your googalage covered these I apologize-but for those who may wander here...

---


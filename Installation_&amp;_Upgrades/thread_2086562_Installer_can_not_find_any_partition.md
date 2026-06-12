---
title: "Installer can not find any partition"
date: 2012-11-21
forum: Installation &amp; Upgrades
---

### Post by Wombacik on 2012-11-21
I'm trying to install ubuntu server on a machine with windows xp. Ubuntu installer can not see any partitions (there are two, C: 50GB and D: 60GB). At the screen, where description says "review changes in partitions" is only one option - connect to iSCSI. I cant see any existing partition or even create new. Nothing. 

PC is quite old, built by acer. HDD connected by wide ide cable, not sata. What can i do to install ubuntu?

---

### Post by darkod on 2012-11-21
Do you want to overwrite XP or not?

In any case, boot the ubuntu cd in live mode (Try Ubuntu), open terminal and post the output of:
```
sudo parted -l
```

---

### Post by Wombacik on 2012-11-21
> **darkod said:**
> Do you want to overwrite XP or not?
Nope. I want to decrease size of sda2 (D:) partition and install ubuntu next to windows.

> **darkod said:**
>  boot the ubuntu cd in live mode (Try Ubuntu)

Sorry, impossible. I'm doing it on computer on my work place and i can use only cd with ubuntu server.

---

### Post by darkod on 2012-11-21
Without booting any live cd you can hardly see what the problem is or investigate. It could be that the server cd doesn't have the driver to recognize the disk, but usually the server cd is very good at recognizing storage.

Also, I don't see much point installing a server OS as dual boot with XP (or any dual boot). A server is meant to be online all the time, or most of the time. Not to be dual booted.

If this is only for testing or learning purposes, you better consider installing something like Virtual Box in XP and making the ubuntu server as VM.

---

### Post by Wombacik on 2012-11-22
> **darkod said:**
> Without booting any live cd you can hardly see what the problem is or investigate. It could be that the server cd doesn't have the driver to recognize the disk, but usually the server cd is very good at recognizing storage.

i dit this:
At partitioning screen i switched to another console and /dev/sda(1,2,5) is available and i was able to mount them and view files. Only installer doesnt show any disk.

> **darkod said:**
> Also, I don't see much point installing a server OS as dual boot with XP (or any dual boot). A server is meant to be online all the time, or most of the time. Not to be dual booted.
Its meant to be a test server. Whats more, this computer is normally a backup workstation, so thats why we need to keep XP on it.

> **darkod said:**
> 
If this is only for testing or learning purposes, you better consider installing something like Virtual Box in XP and making the ubuntu server as VM.
Yep, its for tests, but this computer is quite old and doesnt have enough memory to run any virtual machine, CPU is slow one to so we decided to install ubuntu next to windows.

---

### Post by oldfred on 2012-11-23
If it is that old are you into the PAE issue?

New versions of Ubuntu assume you have a newer computer chip with PAE extensions. Most Pentium chips or newer have that, so computer has to be very old not to have PAE.
       
[http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension)
PAE is provided by Intel Pentium Pro and above CPUs, including all later Pentium-series processors (except most 400 MHz-bus versions of the Pentium M)

            [http://ubuntuforums.org/showthread.php?t=1951653](http://ubuntuforums.org/showthread.php?t=1951653)
Ubuntu, Kubuntu, and probably Edubuntu will ship with the PAE kernel in 12.04, but both Lubuntu and Xubuntu will ship with non-pae

---


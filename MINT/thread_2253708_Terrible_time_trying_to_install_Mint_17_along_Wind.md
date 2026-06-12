---
title: "Terrible time trying to install Mint 17 along Windows 7"
date: 2014-11-21
forum: MINT
---

### Post by sports fan Matt on 2014-11-21
Folks, I'm a bit discouraged. For the last three weeks spending roughly three hours each time, with two different blank discs trying to install Linux Mint 17..Problems ranged from the installer stalling out right after resizing the partition to not being able to create an admin account. Why does this seem so hard to install?

---

### Post by ibjsb4 on 2014-11-21
What is your install method?

I installed Mint and Mate on my desktop using the ppa's and today I installed Mate on my laptop again using the ppa and both have win7 (no uefi, TG).

My install method is a bit out of the norm.  I start with a Ubuntu "terminal only" install and then add the ppa (these are 14o4 installs).  This has worked for me in both cases and if you have the bandwidth (and no uefi, mini iso does not support uefi.  Maybe the server iso will, don't know) you may want to give it a try.

I also created a free space on my hdd before the install.  I do not trust the installer :)

Could it be something else?  Are you burning at low speed?  Checksums?

---

### Post by sports fan Matt on 2014-11-21
I created a 125 GB partition ..I burned it at the lowest speed just to make sure it would burn successfully.  I have a 640 GB Hard drive

---

### Post by ibjsb4 on 2014-11-21
I don't like using four letter words, but are you running uefi?

---

### Post by sports fan Matt on 2014-11-21
I was not aware Windows 7 had a UEFI...

---

### Post by ibjsb4 on 2014-11-21
I do not know as I do not use it.  What do you think about my install method?

---

### Post by sports fan Matt on 2014-11-21
Anything is possible, I have no idea why it failed :)

---

### Post by ibjsb4 on 2014-11-21
Yep, funny :)  But it works for me.

---

### Post by sports fan Matt on 2014-11-21
What if I burned it at 4 x?

---

### Post by ibjsb4 on 2014-11-21
Could be worth a try, but I fine anything under 16x works for me.

---

### Post by ibjsb4 on 2014-11-21
Let me know what happens .. signing off for tonight .. good luck

---

### Post by sports fan Matt on 2014-11-21
Will do..I have everything where I want it, but unsure what partition I want it as...

---

### Post by buzzingrobot on 2014-11-22
> **sports fan Matt said:**
> Will do..I have everything where I want it, but unsure what partition I want it as...

The image shows Mint will be installed on the /dev/sda5 partition, using /dev/sda6 as the swap partition. Looks like you have one drive, /dev/sda.

BTW, Mint, like Ubuntu, has no 'root' (admin) user by default, so you won't be able to create one. When you need to, the GUI will prompt you for the password for *your* account, or, in a terminal, preface the command with "sudo", which will then prompt for your password. This temporaily gives you root authority.  You don't lose any capability, and not creating a root user by default can prevent both catastrophic mistakes and seemingly inexplicable problems when people try to run a normal session as root.

Problems with a DVD usually are down to a bad ISO image (try another download and do a checksum), or bad burning of the image to the DVD, or a dirty/scratched DVD.

---


---
title: "Ubuntu setup unable to find harddrive"
date: 2010-12-07
forum: Installation &amp; Upgrades
---

### Post by aevare on 2010-12-07
When I start the Live CD I can see my harddrive and access it.
But when I start the setup, it cant find the harddrive and I can not choose it.
Ive tryed more than one cd's and another distro (built on Ubuntu).

The hard drive works fine, Ive got Windows 7 already on it (help me change back to linux).
I know the computer works fine as I once used another computer to install ubuntu on the harddrive and then moved the harddrive to my computer.

Has anyone else had this problem?

---

### Post by pricetech on 2010-12-07
May be an issue with the drive controller in Ubuntu.  Check your BIOS and see if there are different modes for the drive and try them.

Might also look at a BIOS update, which could help.

---

### Post by Quackers on 2010-12-07
Do you currently have a raid setup or has the hard drive ever been used in a raid array?
Have you recently resized or changed any Windows partitions?
How many primary partitions are already on the hard drive?

---

### Post by Old_Grey_Wolf on 2010-12-07
Also, what version of Ubuntu are you trying to install? The installer for Ubuntu 10.10 is different from 10.04 and earlier versions.

---

### Post by aevare on 2010-12-11
> **Quackers said:**
> Do you currently have a raid setup or has the hard drive ever been used in a raid array?
Have you recently resized or changed any Windows partitions?
How many primary partitions are already on the hard drive?


Ive tried both 10.10 and older. 
I did manage to setup arch linux and then ubuntu server 9.4 over it. 
That isnt what I was looking for though.. 
Now when I do os-prober I get error.. isw: wrong # of devices in RAID set "some name" [1/2] on /dev/sda..
So Im guessing that meens this disk has been in a raid array.

---

### Post by Quackers on 2010-12-11
Beware, if you are using a raid array (and don't know it) this command will destroy it and may lose your data/OS

In a terminal enter
```
sudo dmraid -rE /dev/sda
```

Is anything reported in the terminal screen?

---

### Post by sikander3786 on 2010-12-11
Try switching your HDD mode from Bios menu. Switch the HDD mode to 'ahci' or 'compatible' instead of 'IDE' or 'Raid' and try installation again.

**Added:** Before switching the HDD mode from Bios, it'd be better to post the output of this command from Applications > Accessories > Terminal.

```
sudo fdisk -l
```

---

### Post by aevare on 2010-12-11
> **Quackers said:**
> Beware, if you are using a raid array (and don't know it) this command will destroy it and may lose your data/OS

In a terminal enter
```
sudo dmraid -rE /dev/sda
```Is anything reported in the terminal screen?

This worked! thank you all very much :)

---

### Post by Quackers on 2010-12-11
Aha! That's excellent news :-)
Enjoy yourself!

---


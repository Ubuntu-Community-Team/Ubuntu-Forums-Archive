---
title: "Newbie with a Win7 dual boot issue"
date: 2011-08-26
forum: Installation &amp; Upgrades
---

### Post by rollerman2006 on 2011-08-26
I recently installed Ubuntu 11.04 on a laptop with Win7 for dual boot.   I love it and I now want to also install Ubuntu on my primary laptop (HP Pavilion DV6 with 4GB & 280GG) also with Win7.

When I boot the HP with Ubuntu, it prompts me for a new install.  I select the option to install along side another operating system (dual boot).

It then leaves me to partition the drive myself, which I don't want to do or don't have enough knowledge to do.

So I viewed several tutorials that suggest to first shrink the drive via Windows Computer Management, which I did creating a 5GG un-allocated partition on the HP's hard drive.

I then boot the HP back up with Unbuntu, and launch GParted.  That's where I'm lost.  

How do I get Gparted to select the unallocated partition, and install Ubunutu on it as well install the Grub Boot loader.

I thought I was getting the hang of this...but I don't want to have to re-install Win7 again.

Thank you...I am loving Ubuntu...what took me so long?

---

### Post by derekeverett on 2011-08-26
Gparted is a partitioning tool, and it sounds like you've already created your partition with the Windows tools. So I don't think you need it any longer.

You should be able to boot with your Ubuntu CD and install alongside Windows now.. just choose to put Ubuntu in the partition you have created for it when you are asked about it. GRUB will install automatically with Ubuntu for you.

EDIT:If I remember correctly the Ubuntu installer will recognize the "unallocated space" created when you shrunk your Windows volume. Install Ubuntu there.. formatting the partition etc. will happen automatically.

---

### Post by Hakunka-Matata on 2011-08-26
You might want to have a closer look at your partitioning before letting ubuntu (Install alongside).
It sounds like you can boot ubuntu with the liveCD and 'try ubuntu without installing". 
If so, to start with please post the output of ```
sudo fdisk -lu
```

---

### Post by rollerman2006 on 2011-08-26
I ran the WUBU installer and I believe I achieved the dual-bootability is was looking for.

Is their any downside to installing Ubuntu this way?

---

### Post by Hakunka-Matata on 2011-08-26
I will answer Yes, there is a downside.  It is generally accepted that a Wubi install serves the purpose of acquainting the new user with ubuntu.  If and when you decide to use Ubuntu as a full OS, then you should install it as a stand-alone OS.  This is not difficult to achieve. It is a totally different feeling experience, AND it un-tethers the user completely from Windows.  Many or most of us run Ubuntu to get away from Windows and it's bad behavior.

Here's a link to a forum thread titled "Why Wubi?"  [http://ubuntuforums.org/showthread.php?t=1780245](http://ubuntuforums.org/showthread.php?t=1780245)

---

### Post by Mark Phelps on 2011-08-27
> **jeff.ehmann@gmail.com said:**
> I ran the WUBU installer and I believe I achieved the dual-bootability is was looking for.

Is their any downside to installing Ubuntu this way?

The main downsides are two:
1) Since Ubuntu resides INSIDE a Windows NTFS partition, if you run into boot or filesystem problems in Windows, that can prevent you from booting into Ubuntu.
2) If you really did allocate only 5GB for Ubuntu, that is way too small to be useful.  You'll run out of room in notime -- and enlarging Wubi installations is a LOT of work.

---


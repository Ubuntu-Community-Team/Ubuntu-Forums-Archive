---
title: "Installing windows :("
date: 2010-04-28
forum: Installation &amp; Upgrades
---

### Post by zolf42 on 2010-04-28
I need to either uninstall ubuntu and install windows (I have bootable disk), or just install ubuntu (I have Gparted) how do I do this?

---

### Post by spydeyrch on 2010-04-28
If you want to install windows:

Make sure you back up any files you have in your ubuntu system. Preferibly to a DVD or external drive.

Boot off of your Windows CD and go through with the normal installation. windows will re-format your HDD and get rid of ubuntu and install windows.

------------

I am a little confused about the second option. I am assuming that you already have ubuntu installed on your computer per option #1

> 
I need to either uninstall ubuntu and install windows (I have bootable  disk) So if you already have ubuntu on your machine, why would you want to re-install it? Also, if you are going to re-install it, how did you get it on your machine in the first place and why not just leave it on your machine if it is already there?

It almost sounds to me like you might have a dual boot system. If you do have a dual boot system setup, both ubuntu and windows on the same machine, and you just want one or the other, then it is a little more in depth, depending on which os you want. But don't misunderstand me, it is not the scary kind of "a little more in depth". Pretty simple actually and we can help you through it. :)

Would you kindly clarify what you would like and how your system is currently setup? Thank you.  :)

-Spydey:lolflag:

---

### Post by zolf42 on 2010-04-28
I want a duel boot but I know how to do that if windows is installed.

---

### Post by vgrisham on 2010-04-28
A little more detail would help your helpers here. However, if you're running with Windows 7, I strongly recommend installing Windows 7 first and then installing Ubuntu via WUBI. Get Windows installed and going with it's own full partition(s). Don't worry about partitioning separately. Then insert your Ubuntu cd. Run the .exe to install Ubuntu. WUBI will configure everything. It's very easy and you'll be up in no time. You'll see some gripes about disk performance with a WUBI install, but I haven't noticed any lag after using ext4 exclusively for the last 14 months. Also, since everything is in one NTFS partition, it is VERY easy to access your Documents, Pictures, Videos, Music, etc from either OS. WUBI rocks.

Aside: I love how fast one can install Ubuntu. Windows 7 installation takes about 4 times as long and then you get to wrestle with drivers. Ubuntu's installation has gotten so simple and fast.

---

### Post by spydeyrch on 2010-04-28
> **zolf42 said:**
> I want a duel boot but I know how to do that if windows is installed.

Ok, so you want a dual boot. And Ubuntu is currently installed on your system where as windows is not, right? Just want to make sure I understand you correctly. Is ubuntu the only OS on your computer right now?

Also, how long have you had it installed on your computer? I ask because presumably if you have had it on your system for some time, you probably have a number of programs on it that you will want if or when you re-install ubuntu and we could potentially make a backup of those programs for easy re-installation of them.

Also:

> 
installing Windows 7 first and then installing Ubuntu via WUBI. Get  Windows installed and going with it's own full partition(s). Don't worry  about partitioning separately. Then insert your Ubuntu cd. Run the .exe  to install Ubuntu. WUBI will configure everything. It's very easy and  you'll be up in no time. 

It is true that WUBI is wonderful for a no hassle installation of ubuntu but it comes with it's disadvantages too. And depending upon personal opinion, they can be quite large or small. for example, one of the major downsides to WUBI, in my opinion is that because it is installed within the NTFS system and, to windows, it is a program, if your windows system goes down for some reason, so does your ubuntu OS. You won't have access to it.

Where as if you install windows first then install ubuntu second, with it's own partitions, they can coexist on a machine and if one goes down, the other still survives. As long as it is not a hardware failure.

So WUBI is great for testing ubuntu and getting your toes wet but I personally wouldn't recommend it for longtime use. Some people would disagree with me thought and like I said, it is all based upon personal preference.

-Spydey :lolflag:

---

### Post by spydeyrch on 2010-04-28
> **zolf42 said:**
> I want a duel boot but I know how to do that if windows is installed.

Also, what version of Windows do you have? XP, Vista, 7, etc. Is it x32 or x64?

How many internal hard drives do you have and how big are they?

What are your other hardware specs too:

CPU
RAM
GPU
HDD
ODD

For example, my specs:

AMD Phenom 9950 2.6GHz o'cd 3.2GHz
4GB DDR2 1066
ATI HD 3870 512MB in crossfire
1TB, 3 x 500GB
DVD/CD burner
Windows 7 Pro x64
Mint 8 x64
Ubuntu 9.10 x64

This will help to plan for any future issue and resolutions to those issues.

-Spydey:lolflag:

---

### Post by vgrisham on 2010-04-28
> **spydeyrch said:**
> Ok, so you want a dual boot. And Ubuntu is currently installed on your system where as windows is not, right? Just want to make sure I understand you correctly. Is ubuntu the only OS on your computer right now?

Also, how long have you had it installed on your computer? I ask because presumably if you have had it on your system for some time, you probably have a number of programs on it that you will want if or when you re-install ubuntu and we could potentially make a backup of those programs for easy re-installation of them.

Also:



It is true that WUBI is wonderful for a no hassle installation of ubuntu but it comes with it's disadvantages too. And depending upon personal opinion, they can be quite large or small. for example, one of the major downsides to WUBI, in my opinion is that because it is installed within the NTFS system and, to windows, it is a program, if your windows system goes down for some reason, so does your ubuntu OS. You won't have access to it.

Where as if you install windows first then install ubuntu second, with it's own partitions, they can coexist on a machine and if one goes down, the other still survives. As long as it is not a hardware failure.

So WUBI is great for testing ubuntu and getting your toes wet but I personally wouldn't recommend it for longtime use. Some people would disagree with me thought and like I said, it is all based upon personal preference.

-Spydey :lolflag:

I've done the dual boot thing just about every way it can be done in the last 5 years, and I still say WUBI rocks. If windows 7 won't boot, you choose Ubuntu in the bootloader. If the bootloader is hosed, whether it's Grub or Windoze, you've got problems anyway. To each his own though.

If you go Spydey's route, Lifehacker has a really great [step-by-step tutorial]("http://lifehacker.com/367714/run-windows-apps-seamlessly-inside-linux") that works really well.

Sydey's right though. You've gotta give us more info.

---

### Post by spydeyrch on 2010-04-28
> **vgrisham said:**
> I've done the dual boot thing just about every way it can be done in the last 5 years, and I still say WUBI rocks. If windows 7 won't boot, you choose Ubuntu in the bootloader. If the bootloader is hosed, whether it's Grub or Windoze, you've got problems anyway. To each his own though.

I would agree, to each his own. And I say that having run ubuntu via wubi for about 18 months and enjoyed it. There were some issues that wubi caused on my system that a true install fixed. But it could have been just isolated to my system specs. Don't know. :confused:

Yes, more info on specs, current setup, and eventual goal of doing this. :)

-Spydey :lolflag:

---


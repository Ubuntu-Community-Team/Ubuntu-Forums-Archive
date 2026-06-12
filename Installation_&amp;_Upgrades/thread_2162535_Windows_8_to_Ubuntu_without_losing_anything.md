---
title: "Windows 8 to Ubuntu without losing anything?"
date: 2013-07-14
forum: Installation &amp; Upgrades
---

### Post by eLyUKayEe on 2013-07-14
I have a problem (no duh, I wouldn't be posting to this forum if I didn't)

It would seem that I have grown incredibly disgusted with Windows 8 for my laptop (not this recently. It came with my laptop) and have evaluated Ubuntu as a suitable replacement. However, I have a ton of stuff on my computer that I don't want to lose (data hoarder much, heh). Is there a way to install Ubuntu where I get rid of Windows but keep all of my stuff where I can evaluate what I should keep in a decent-working OS?

If specs will help, I have an HP Envy dv7 (let the "mine's bigger" jokes commence) with a 750 GB HDD, 8 GB RAM, nVidia GeForce GT graphics 650M and an intel Core i7 processor.

---

### Post by Snowhog on 2013-07-14
Standard answer is "backup what you want to keep" to an external device before you do anything. You are also going to want to read up on UEFI and Secure Boot and confirm what your laptop mobo has.

---

### Post by fantab on 2013-07-15
If you intend to remove Windows 8 completely then you don't need to worry about 'Secure Boot'. This is Microsoft feature. However Ubuntu since version 12.04.2 can boot with 'Secure Boot' enabled, but this applies only if you are dual booting.
If I were you I would **Dual-Boot Ubuntu with Windows8**, until such time I no longer need Windows. This is because there are certain software & applications that only run on Windows and that there could no good alternative in Linux. Then there are games that just don't work on Linux and there are no linux versions available. So, it will be good idea to dual boot if you are a Linux beginner. 

**BackUp** all your data that you don't want to lose, preferably to an external disk.

Ubuntu can read from and write to NTFS partitions. So If you have your DATA on a separate partitions than 'C' then you can save that partition, meaning don't have to format it and use it in ubuntu.

You might find instructions **[HERE]("http://ubuntuforums.org/showthread.php?t=2160668&page=2&p=12722555#post12722555")** useful, and give you an idea how to go about Backing Up, and dual booting Ubuntu & Windows.
For More info on UEFI etc, see** [THIS]("http://ubuntuforums.org/showthread.php?t=2147295&p=12657352#post12657352")**.

If you have any doubts get back here first.
Good Luck...

---

### Post by eLyUKayEe on 2013-07-15
In truth, I do NOT want to dual boot, I hate Windows enough as is. And I also do NOT want to get an external hard drive if I don't have to.

In addition, I would like to know what programs to keep (I know that a majority of Valve-made games work, as Steam is Linux-compatible) and which ones to get rid of if there isn't an emulator available to use.

---

### Post by snowpine on 2013-07-15
You should have a backup of your important data, whether you are planning to switch to Ubuntu or not. Otherwise your data must not be very important to you.

It is highly likely that many of your favorite applications and games will not run natively in Linux. 

Why not dual boot? Best of both worlds. :)

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

Please note that the first step is "Back Up Your Data."

---

### Post by eLyUKayEe on 2013-07-16
I tried dual booting with 13.04, but either I lack the ability to do so successfully or the UEFI is just too much of a b****. Not to mention the thing is a laptop where the F1, etc. keys don't really do the actual F-key functions without the Fn key (plus, the startup screen for Windows 8 is just a bit too...empty. Doesn't say "press this to go to the startup menu").

So, I'm guessing I'm going with backup to a portable HDD. Anybody know a good emulator or decent replacement software or is this the wrong forum?

---

### Post by fantab on 2013-07-17
Emulator for what? to backup? There are a lots of applications that can help you do a backup. You can try '[Macrium Reflect]("http://www.macrium.com/reflectfree.aspx")' (to make/clone an image of you entire HDD as its is now/ factory settings), this will help in restoring your Windows to its factory state. Could come in handy if and when you want to resell your laptop, or need to restore windows.
Also using a Windows utility create a '[Recovery/Repair disk]("http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html")' for your Windows8. This should help you repair windows if need be.

> HP Envy dv7 with a 750 GB HDD, 8  GB RAM, nVidia GeForce GT graphics 650M and an intel Core i7 processor

While you are in Windows post a screenshot of your HDD and its partitions from Windows Disk Management.
If you have an Ubuntu install disc ready then boot with it, 'Try Ubuntu without installing', let the desktop load, Open Terminal (Ctrl+Alt+T) and run the following commands:
```
sudo parted -l
sudo fdisk -l
```
...and post the outputs here. This should give us an overview of your present HDD partition scheme, which is important if we are install Ubuntu in dual-boot. Dual booting Ubuntu in UEFI is not too difficult. Give it a try. We can always remove windows later. 
But first make good backups.

---

### Post by cybrsaylr on 2013-07-17
Have to agree a dual boot is the best of both worlds. I dual boot all my PCs but as you noted it can be a pain setting up. You learn doing it one way for one version, then the next upgrade makes a change or two that throws you off....lol

Another good point about dual booting is you can go into the Windows partition when using Linux and view your Windows files and drag & drop many into your Linux partition if you desire.

In any event if your W8 files are important and worth saving, put them on an external HDD....they are cheap.

---


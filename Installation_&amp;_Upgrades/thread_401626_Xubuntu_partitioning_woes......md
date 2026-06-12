---
title: "Xubuntu partitioning woes....."
date: 2007-04-04
forum: Installation &amp; Upgrades
---

### Post by bjnix04 on 2007-04-04
Ok, I got my CD burned and I though I was all set......
I got to the Live CD and started the install, everything was fine until I decided to resize the partition for my HD.(it's the first option....the one with the slider) 
The partition I set was for 78% (20 G) was for windows, and the rest (about 7 G)  was for Xububtu. So I pressed next and the little busy cursor came up so I went back to my game of GTA LCS....then after about 2 minutes (or less) The little busy cursor was gone and the next button was out, so I pressed it again and it froze (I think) The installer didn't move and my HD light wasn't blinking (meaning nothing HD related was being done) and the CD drive had stopped. 
So I exited and taking that as an omen I decided to go to manual editing, I set up the Partitions as follows:

Resize (windows) from 27 G to 20 G

20 G for windows
2 G   Ext 3
256  swap
5 G   Ext 3

It looked Like it was working and then I get an error message telling me it  couldn't resize the partition. 

Now I was a little ticked, so the last thing I did I used the option "use the largest amount of continuous free space" clicked it and after about 20 seconds I get the screen that says everything is ready, however there were no OS setting or any partitions.

So to check if anything had been done, I rebooted my computer expecting to see the screen saying it needed to check the HD for errors, nothing.

So nothing had been done and I missed a call from a girl I'm trying to get to be my girlfriend :wink: 

So, I need your help to help me install linux on my computer.

My system info is:


OS Name	Microsoft Windows XP Home Edition
Version	5.1.2600 Service Pack 2 Build 2600
OS Manufacturer	Microsoft Corporation
System Name	***********
System Manufacturer	Hewlett-Packard
System Model	HP nx9005 (DK992A)
System Type	X86-based PC
Processor	x86 Family 6 Model 8 Stepping 1 AuthenticAMD ~1788 Mhz
BIOS Version/Date	Phoenix Technologies Ltd. KAM1.44, 6/23/2003
SMBIOS Version	2.3
Windows Directory	C:\WINDOWS
System Directory	C:\WINDOWS\system32
Boot Device	\Device\HarddiskVolume1
Locale	**********
Hardware Abstraction Layer	Version = "5.1.2600.2180 (xpsp_sp2_rtm.040803-2158)"
User Name	**********
Time Zone	***********
Total Physical Memory	[COLOR="Red"]256.00 MB[/COLOR]
Available Physical Memory	[COLOR="Red"]18.71 MB[/COLOR]
Total Virtual Memory	[COLOR="Red"]2.00 GB[/COLOR]
Available Virtual Memory	[COLOR="Red"]1.96 GB[/COLOR]
Page File Space	[COLOR="Red"]465.36 MB[/COLOR]
Page File	C:\pagefile.sys



* = censored

Someone PLEASE help me!<br /><br />
----------------------------------------<br />

----------------------------------------<br />

---

### Post by mssever on 2007-04-05
Can you still boot into Windows? If so, do a scandisk and a defrag. Then try the manual partition resize in Xubuntu again. You might also want to try the [GParted LiveCD]("http://gparted.sourceforge.net/livecd.php"). If you still can't resize the partition, you might have a non-resizable partition. I had one of those once.

If you can't resize your partition, you have several options:[LIST=1]
[*]Try a Windows tool such as Partition Magic
[*]Buy a second hard drive
[*]Backup Windows, then reformat and repartition your entire hard drive; reinstall Windows, install Linux[/LIST]None of these options is great. I hope somebody can suggest something better.

---

### Post by bjnix04 on 2007-04-05
Alright I'll try...........

---


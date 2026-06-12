---
title: "Ubuntu 11.04 will not start"
date: 2011-11-18
forum: Installation &amp; Upgrades
---

### Post by gertcher on 2011-11-18
I installed Ubuntu some weeks ago along side XP, it was working fine and I stated to experiment. A few days ago I was playing with CCSM to stop the launcher from popping out all the time and reduce the size of the icons, got them to work no problem. Then tried some other stuff and that is where I got lost and things went wrong.  Got to the point where the luncher disappeared and I could not get it back, in fact everything disappeared including the stop button so could not turn the computer off.

I reinstall ubuntu as a fix, that did not work, then as a reinstall still along side XP, all I get now is a pink screen with ubuntu written across is and a row of dots. It just hangs there and nothing happens.

I have far too much on XP to wipe the disc.  I am very familiar with XP but I could not find the installed ubuntu files, I thought I could delete them so there was nothing for an install to fall over.

I know next to nothing about Linux and the syntax is totally alien to me, as well as the file structure, even ubuntu abbreviations are almost meaningless, everything is so different to XP.

I can follow instructions but please do not expect any previous knowledge.  Any help will be gratefully accepted

Thanks Greg

---

### Post by gordintoronto on 2011-11-18
Did you install Ubuntu this way: with Windows running, insert the Ubuntu CD? That is called a Wubi install. You should be able to remove it using Windows, Add/Remove Programs.

BTW, it's always a good idea to have backup of all your files, and a Windows XP install disc. When you install an operating system, there are moments when you are one click away from losing everything.

---

### Post by darkod on 2011-11-18
Windows can't see linux files and partitions. Not by default. From within windows you will not be able to see any files. Most that you are able to see is unknown partitions in Disk Management.

To get a better idea what you have in your system, follow the link in my signature and run the boot info script. Post the results as explained there. That will show more details.

---

### Post by gertcher on 2011-11-18
I installed from a CD from cold. 

I must say I am very trusting of software, if it says it will install along side I believe it, on this occasion it did. I will do a back up before I go any further. Its not so much my documents its the loads of programs as well and I don't think I have enough disc space to back up everything, I will work on it so I can.

I will follow your link

Although ubuntu worked out of the box it seems very flake and a bit clunky, and if you try to make adjustments it falls over. Am I expecting too much, should I wait a bit until it is more stable, are there other means of adjustment other than CCSM, or are there other versions of Linux that don't break so easily? 

Lots of questions I know, I need to catch up and forums seems to be the only answer, Just don't want to be reliant on M$ especially as they will pull the plug on XP in a year or so.

Greg

---

### Post by darkod on 2011-11-18
In this case, trusting too much is not good. As much effort as the ubuntu developers make, when you are trying to combine two different OSs it's not easy.
If you had unpartitioned unallocated space on the HDD, there is no problem to use the side by side option if it does NOT need to resize your XP partition.
It is not recommended to use the ubuntu installer to resize the XP parition to make unallocated space, because after it's resized XP want to boot few times to run disk checks. But the ubuntu installer of course continues with the installation which might create issues booting XP successfully.

But in your case, you seem to have issues with ubuntu, not XP. Changing settings is fine, but it's always better to read as much as you can on the forums and google, because you can easily break it. :)

If you have any data on your ubuntu that you want to get out, and it douesn't boot, you should be able to access it from live mode without any issues. Just open the Home folder, that opens Nautilus, the file browser. On the left side you should be able to see all partitions on the HDD. Clicking on your ubuntu root partition (you can guess by the size) will mount it and should open it if it's readable. You should be able to copy files from it to external HDD for example.
You can use the same process to get data out of windows if it can't boot. Even if ubuntu was never installed on a computer. Load live mode from the cd and it can open the partitions on the HDD and read the data.

---

### Post by gordintoronto on 2011-11-19
I have read that CCSM can break Unity, but I don't know any details.

---


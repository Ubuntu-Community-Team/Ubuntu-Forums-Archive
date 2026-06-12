---
title: "Vista won't boot after install Ubuntu through Wubi"
date: 2009-11-22
forum: Installation &amp; Upgrades
---

### Post by Yohsoog on 2009-11-22
Hello,

I have this problem and after looking for days for similar problems and solutions I decided to ask for help myself.

I recently installed Ubuntu through Wubi since I did that a while ago and I liked it a lot but that laptop crashed and I got a new one. Anyway, I installed it on my Vista, followed the procedure, but now my Vista won't boot anymore. It does show up in the initial bootmenu from Windows, and even in the GRUB bootloader that shows up if i choose for Ubuntu in the Windows bootmenu. But when i choose the vista option, it starts to load with the green processbar on the bottom but then just reboots the complete computer again. As far as Ubuntu goes, it loads just fine and i can access my windows partition through /host and my recover partition shows up in the file browser.
Now, if I start through the windows bootoption, I get the message from windows bootloader (or whatever it is called, the place where you can choose for 'safe mode' etc.) that I should insert the Vista disc to repair some files. Now I did not try that, because I only have a recover disc and not a real Vista disc because I have an OEM version and I read from someone that his entire system was restored, losing all his data that way.
So now I wonder if any of you can help me out. Do you think I should try to use the disk? Is there another way? Is there a certain windows file that I can restore for this maybe? I am just out of ideas and I don't want to lose all my data because I am one of those that only thinks of backups when it is too late...

Extra question: totally unrelated, but i have another extra question. If I boot into Ubuntu, then I shut down my laptop. Next time I try to restart it, the first time it always immediately shuts itself down as if the laptop doesn't have enough power. The second restart everything goes smooth again. Any ideas on this? Not a big problem, but still makes me wonder.

Thanks in advance!

---

### Post by darkod on 2009-11-22
You are right, your recovery disc will probably just delete all the data on the computer. Usually those discs make the computer as it was when bought.
Depending which version is your vista you can download from torrent ISO file, burn it on dvd and see if you can do the repair.
When booting from the dvd there will be option like Repair This Computer. Not sure if it will work because you didn't install vista from that image, but you can try.

PS. It is not illegal to download from torrent when you have legally purchased license. They should have given you vista dvd too exactly for situations like this, not just recovery disc which deletes all your data.

---

### Post by Bigadada_saba on 2009-11-22
Hi I only dual-boot and i don't install via wubi because vista is NOT reliable enough that's the real reason that we all are turning to linux or osx. my advice is to boot start the ubuntu and backup all ur data to DVD or external hard drive and then restore the windows partition then shrink the partition so as to make room for ubuntu and your swap partitions. Then boot from your ubuntu live cd and install ubuntu to your unallocated partition. during installation make sure to check the box to import stuff from your windows partition.

hope this helps

---

### Post by Bigadada_saba on 2009-11-22
> **darkod said:**
> You are right, your recovery disc will probably just delete all the data on the computer. Usually those discs make the computer as it was when bought.
Depending which version is your vista you can download from torrent ISO file, burn it on dvd and see if you can do the repair.
When booting from the dvd there will be option like Repair This Computer. Not sure if it will work because you didn't install vista from that image, but you can try.

PS. It is not illegal to download from torrent when you have legally purchased license. They should have given you vista dvd too exactly for situations like this, not just recovery disc which deletes all your data.





Also most of the time  when vista diteks that windows boot loader is replaced by Grub it will try to rewrite windows boot laoder an that will mess up grub. so just follow my last instructions its the least difficult and safest way.

---

### Post by Mark Phelps on 2009-11-22
> **Bigadada_saba said:**
> Also most of the time  when vista diteks that windows boot loader is replaced by Grub it will try to rewrite windows boot laoder an that will mess up grub. so just follow my last instructions its the least difficult and safest way.

Reinstalling an MS Windows OS always overwrites the MBR, regardless of what was installed earlier.  You make it sound like MS Windows is going out of its way to find and remove non-MS-Windows stuff, which is not the case.

If, instead, you install GRUB to a Linux partition, MS Windows will not touch it, but most folks install GRUB to their MBR -- which DOES get overwritten.

---

### Post by darkod on 2009-11-22
@Mark

You're absolutely correct. However, shipping windows OS disc instead of recovery disc/partition would allow the customer to just reinstall windows without "killing" another OS on the drive (not just the bootloader). And probably all of his data in the process.

For that, I think they're wrong.

---

### Post by Yohsoog on 2009-11-22
@Mark: But the thing here is that I installed ubuntu through wubi and the problem doesn't have to do with GRUB since that is working like it should. Or did I misunderstand you?

Ok, so i will try to backup all of my data (do you recommend a program or just copying all of the files?). Then I will try to recover the windows mbr first, if that fails, i will have to reinstall through the recovery disk.

---

### Post by oldfred on 2009-11-22
restore boot loaders Ubuntu Win xp Vista
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista Recovery Disc 
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista will not repair XP(they create the boot sectors differently)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

How to restore the Windows Vista bootloader
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

### Post by Mark Phelps on 2009-11-23
> **Yohsoog said:**
> @Mark: But the thing here is that I installed ubuntu through wubi and the problem doesn't have to do with GRUB since that is working like it should. Or did I misunderstand you?
No, you didn't misunderstand me.  I was commenting on the poster that seemed to think that MS Windows went out of its way to hunt down Linux/GRUB stuff and remove it.

> Ok, so i will try to backup all of my data (do you recommend a program or just copying all of the files?). Then I will try to recover the windows mbr first, if that fails, i will have to reinstall through the recovery disk.

You can recover the MS Windows MBR by booting from a Vista install DVD and running Startup Repair at least three times.

oldfred has provided you some great links ...

---

### Post by Yohsoog on 2009-11-23
Lol @ run startup repair at least 3 times :)

And yes, thank you for all the links oldFred, I will look into it and will try to fix everything tonight. I will let you all know how it ended afterwards.

---

### Post by Yohsoog on 2009-12-15
It has been a while, but I couldn't fix the problem. I tried every trick i could find, but the best chance I had didn't work. The problem probably didn't came from installing ubuntu through wubi but instead was because of the install of the vista servicepack. I was just a coincidence the two installations went together i think... The fix consisted of restoring a previous restore point through the vista boot disc, but i tried several times (even for 36h+) but it just kept on "finalizing restoration"... 
In the end, i grabbed a ubuntu live disc, transeferred all of my data to an external hdd and installed Windows 7 alongside Ubuntu 9.10 in a perfect dual boot.

I am much happier now :D

Thanks a lot everyone, trying to help me fix my problem. I did also learn some things so it wasn't a waste of time ;)

---


---
title: "GRUB Error 18 - But How to Fix It?"
date: 2007-01-26
forum: Installation &amp; Upgrades
---

### Post by Aktrop on 2007-01-26
Hi,

I'm brand new to Linux and Ubuntu, and I'm not a particularly sophisticated user. I've installed Ubuntu on my Thinkpad T41, which also runs Windows XP Pro. When I boot up I GRUB gives me error #18. I have never been able to boot successfully, and I can't get into Windows either.

Now I've searched the web, and I know that the problem is because the BIOS isn't looking at the right place, and the kernel has to be within blah of the HD, etc. etc. But what I don't know is how to actually go about fixing this, step by step.

I have the latest BIOS installed (2006-6-12). 

Any help or pointers would be greatly appreciated!

-Aktrop

---

### Post by drr422 on 2007-01-26
You should try to reinstall the Grub bootloader, as explained here: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Follow the instructions titled: Using the Desktop/LiveCD and Overwriting the Windows bootloader.  This should repair the grub bootloader, which is causing the problem you are describing.

---

### Post by Aktrop on 2007-01-26
Hi,

Thanks for pointing me to that great resource!!

I did as you suggested but I get the following message:

"The file /mnt/root/boot/grub/stage2 not read correctly".

Again, any help would be awesome...

Best,

-Aktrop

---

### Post by drr422 on 2007-01-26
My only other suggestion would be to reinstall Ubuntu, delete the Linux partitions you have already created and remake them in the installer software. Basically see if reinstalling it would help.  Good Luck and let me know how it turns out.

---

### Post by confused57 on 2007-01-26
You can find a description & possible solutions to grub error 18 here:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Grub_Errors](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Grub_Errors)

One that you might look into is to "enable" LBA in bios, or if it's already enabled then set it to normal.

Of course, you might try reinstalling Ubuntu & if you continue to get error 18 you can try the above.

---

### Post by Aktrop on 2007-01-26
Hi people,

Thanks for taking the time to share your expertise.

Unfortunately, I'm now in deep trouble - things aren't going well.

1. I tried re-installing Ubuntu, but I STILL got error #18

2. I managed to get a copy of SuperGrub. Despite all manner of fiddling, I can neither get into Linux nor Windows - all manner of error messages crop up, too numerous to mention. All my work is currently locked behind Windows and I can't get to it. (Yes, yes, it's all backed up on another external drive, but in .wbk format... please tell me Ubuntu can read that...)

3. I've also poked around in the BIOS, but can't find anything about an LBA. 

Please help. You guys are the one bright spot in what is turning out to be an my open-source nightmare...

-Aktrop

---

### Post by confused57 on 2007-01-27
The Super Grub Disk can be used to boot Windows or Linux, as well as restore your Windows mbr:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#situtions_where_sgd_is_useful](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#situtions_where_sgd_is_useful)

If you have a floppy drive or a Windows install cd(not a recovery cd), you can also restore Windows mbr:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

Hopefully, you can just restore the mbr & not have to reinstall.  I'm still not sure what's going on with the error 18.

---

### Post by rumli on 2007-02-14
Try booting into recovery mode and then commenting out the "savedefault" line in /boot/grub/menu.lst.  See here: [http://ubuntuforums.org/showpost.php?p=2156493&postcount=3]("http://ubuntuforums.org/showpost.php?p=2156493&postcount=3").

---

### Post by kwatts on 2007-06-21
Since this was the first return for "T41 grub error 18" on google, the answer to this can be found at,

[http://ubuntuforums.org/showthread.php?t=33811](http://ubuntuforums.org/showthread.php?t=33811)

Basically -

"It turns out the Thinkpad bios has an option to protect the special 4.5G setup non-partition at the end of the disk (Accessed under "Security" options). When set to "normal" this hides the last 4.5G of the disk. It seems Linux is not tricked by this, and sees the whole disk, so LILO and grub get installed with the whole disk geometry. However, when booting, LILO and grub use the BIOS, which reports the fake geometry minus the 4.5G, causing both LILO and grub to barf.

Setting the bios setting to "disabled" makes the bios geometry match the real geometry, allowing LILO or grub to boot..."

---


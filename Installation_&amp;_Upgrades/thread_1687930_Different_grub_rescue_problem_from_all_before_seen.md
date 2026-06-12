---
title: "Different grub rescue problem from all before seen...."
date: 2011-02-14
forum: Installation &amp; Upgrades
---

### Post by ubuntster on 2011-02-14
Hello! 

Basically i have read every topiv in internet about grub rescue and no answers for my problem, so hope someone can help:smile:

So i start with the story...

I have in my home very old PC and i installed Ubuntu on it. This  computer was used by my mom and brother and they didn't like it so they  asked me to install back windows xp home. I DO NOT HAVE NOTHING TO DO  WITH DOUBLE BOOT OR SOMETHING LIKE THAT. There was ONLY ubuntu and i  wanted to format the hard drive and then install XP. When i insrted  original XP  CD, i was not able to boot, i checked boot sequences and  everything possible and nothing. Then i decided to remove the hard drive  and but it into a console which would make it an externial drive. I  connected it to my LAP TOP(win 7) and formatted it in lap top and  afterwards it showed that the disk is empty and its in NTFS format. I  was hooping that if i know connect it im able to boot the XP cd up and  install it but...... When i re-connected the hard drive to PC and  powered it ON i got a message :
[I]
error: unknown filesystem
grub rescue[/I]>

I AM VERY VERY VERY STUPID IN LINUX STUFF so only thing i came up was to try boot cd-s and so on.

i also read differenet grub rescue threads, but the help that was in  there was requireing LIVE CD-S or some typing in it and either way i was  stuck

And now after a week of research im in point where i cant boot no live cd-s, win xp cd, usb sticks... ANYTHING!

hope this information is enought to get this topic going and im very  happy to get any reply and im willing to answer any questions

Thank You!

Taavi M.

---

### Post by grahammechanical on 2011-02-14
It sounds like the machine is trying to boot from the hard disc when it is supposed to boot from the CD drive. When you installed Ubuntu it put the boot loader (GRUB) is a special part of the disc. As you only had Ubuntu on the disc the GRUB boot menu was never displayed. You have removed Ubuntu by formatting it but the GRUB boot loader is still in the part of the hard disc called Master Boot Record (MBR) and it is looking for Ubuntu and cannot find it. Hence the error message.

You need to restore the MBR to a state that Windows will recognise. Then you will get an error message saying "no operating system" because there is not one on the disc at all. This should not matter if the machine was set up to boot from the CD drive. I do not think that it is set up that way. I think that it is still set up to boot from the hard disc. In my opinion, that is your problem.

Regards.

---

### Post by ubuntster on 2011-02-15
Hmm, thats definetly something new i hear...but how to i use MBR....i still cant boot anything so basically only way that i see is that i need to give commands in grub rescue(the screen that comes up when i turn PC on)...

---

### Post by drs305 on 2011-02-15
> **ubuntster said:**
> Hmm, thats definetly something new i hear...but how to i use MBR....i still cant boot anything so basically only way that i see is that i need to give commands in grub rescue(the screen that comes up when i turn PC on)...

No, you need to get the system to look for the CD first during boot. You can do nothing from the grub rescue prompt because you have no files on the computer for Grub to use. 

The MBR is trying to point to a nonexistent partition and will continue to do so. You need to get a bootable CD of some sort - Ubuntu LiveCD, Windows installation/repair CD, etc.

To get the computer to boot the CD, you need to change the BIOS to look first to your CD drive. To do this, you have to enter the BIOS setup utility. Normally this is accomplished by pressing one of the function keys (F1-f12), the DEL or ESC key just after you turn the power on. The computer screen may tell you which key to press, or do a search for your specific computer model.

Once you have the BIOS set correctly, your CD will boot and you will be able to repair your system.

---

### Post by ubuntster on 2011-02-15
i went to BIOS before and but cd rom in first and still when i restart it wont boot it goes directly to 

[I]error: unknown filesystem
grub rescue
[/I]
ive tried to boot live cd-s , windows xp cd(which is bootabel since i have booted with it it loads of times before!)

---

### Post by drs305 on 2011-02-15
> **ubuntster said:**
> ive tried to boot live cd-s , windows xp cd(which is bootabel since i have booted with it it loads of times before!)

Do you hear the CD spin up first? Have you tried a different CD?

If set to CD first, the BIOS will attempt to boot the CD. You should hear it spinning. If it fails to boot the CD, it will revert to the second choice (your hard drive). 

What you describe probably means that 1) the BIOS is still trying to boot the hard drive first, or 2) the CD is either damaged or not a bootable one to begin with, or 3) your CD drive isn't working properly.

If you have another computer, try the CD in that one to see if it boots properly. That might rule out the CD as being the problem.

---

### Post by ubuntster on 2011-02-15
tried with another cd rom and with lap top and the cd-s are working every where exept in pc...cd rom and cd are all fine

BUT THERES ONE UPDATE

i removed the hard drive and no i got

[I]boot failure
insert BOOT diskette in A:
press any key when ready

[/I]I dont have any floppys and also in boot sequence i dont have my HDD(logical) but i also dont have my cd rom listed...

And one other wierd thing is that...i pressed any key although i dont have disk in floppy and it started windows setup(cd is in cd rom) so im a little bit confused now...

So i was someway able to boot through floppy device...dont ask!

i put the HDD back and i was able to reach windows set up but now i am in the screen where i need to create partition under unpartitioned space nad now hear this

- it shows that i have 2064902 MB of unpartitioned space although the disk is only like 75000mb and no matter what i choose i wont be able to create partition in that space.

---


---
title: "Question about Dual booting"
date: 2006-06-05
forum: Installation &amp; Upgrades
---

### Post by jerrygofixit on 2006-06-05
I have a dual boot system right now, Windows 2k and XP, 2k on drive C: and XP on D: (I know it's dumb, don't ask). But if I were to format C: to load Ubuntu, do you think the Installation would still recognize/load XP considering the boot loader(I believe) is on C: ?

---

### Post by llamakc on 2006-06-05
Even if it did not you can easily add an entry to the /boot/grub/menu.lst file so that you could boot into Windows on /dev/hdb (D:\)

---

### Post by jerrygofixit on 2006-06-05
But wouldn't windows need the boot files? Like NTLDR and NTDETECT and such?

---

### Post by llamakc on 2006-06-05
I'm sorry I don't know the answer to that. I figured the D:\ installation would have those files also.

What about installing Ubuntu to /dev/hdb (D:\) instead?

---

### Post by jerrygofixit on 2006-06-05
D: is my main XP operating system, I was just using C: to occasionally troubleshoot D: when it messed up. C: is seldom used but D: is very important, my main XP operating system. (They are 2 seperate hard drives, C: being a 30 gig maxtor IDE and D: being split up into 2 partitions, D: and I:, 200 gig SATA maxtor.)

---

### Post by t0mc4t on 2006-06-05
I have a question related to this matter, but my situation is different.
What about at this moment I already installed Ubuntu. After this I want to restore my computer (Windows XP). I'm sure that Windows will overwrite the MBR to boot the Windows only. How is the way I install the GRUB back to MBR without reinstalling the Linux? Since I can't boot to linux after I installed the Windows.
Thanks...

---

### Post by catlett on 2006-06-05
I would assume that XP has it's boot.ini. There doesn't have to be anything on the MBR from windows to boot it. As long as XP's boot.ini is installed in it's partition then grub can boot it. Grub is going to rewrite the mbr anyway so it doesn't matter if grub does it or you reformat the drive and get rid of the mbr. Grub boots to the partition not the mbr.
BUT. If you really want to make sure you can do this. Go inside XP and get to the device manager. It is buried inside the control panel. Get to administrative tasks and then to the device manager and finally to disk manager (or something like that I haven't been in windows in months). The point is you can get to a disk manager that lets you see your drives in a partitioner setting. This is where you can also defrag your disk. Anyways choose drive C and format it. C will be wiped and repartitioned. 
Then go to the start menu and get a command line from programs<accessories and enter ```
fixmbr
``` This will rewrite the mbr for XP. Now go through the ubuntu installation and put ubuntu on C and keep XP on D (obviously). I don't think you need to do this but if you feel more comfortable this will let you know that C is gone and XP on D is still bootable before the ubuntu install.

---

### Post by t0mc4t on 2006-06-05
Thanks for the reply. Anyway, I'm still quite confuse with your reply. Here are I explain again my situation in sequence..

1. I have installed Windows and Ubuntu with GRUB as my bootloader (detect both Linux and Windows).

2. I want to restore my computer (Windows XP) with recovery cd
-> based on my experience, in step 2, the Windows will overwrite the GRUB loader and won't detect the Linux OS, so that only boot the Windows only

3. I want GRUB to be my bootloader again without reinstalling the Linux
-> at this time, I believe I can't boot to Linux because Windows bootloader not detecting the Linux.


Is that posible? Thanks again.. :)

---

### Post by catlett on 2006-06-06
Sorry I thought your issue was you had win2k on C and winXP on D. You wanted to put Ubuntu on C but you were concerned that XP wouldn't boot from Ubuntu if installed Ubuntu to C because Win2k was the OS that was booting both Win systems and you felt that C had the MBR for XP. That's why I mentioned the above. I didn't think it was necessary but it would have made XP on D bootable from the MBR before you installed UBuntu.
If you have just installed Ubuntu and it sounds like you are going to restore XP from a recovery cd, then I wouyld recommend reinstaling Ubuntu after XP. It is the sinplest way to get grub back. There are other methods that you can search but this is the easiest and if you just installed, there is nothing important on your ubuntu install.

If you don't want to reinstall after thw windows recovery you can search the ubuntu wiki, it has a section about how to restore grub after windows but I don't recommend it. It's not simple and it is time consuming. For an extra half hour you can have a frexh install setup up perfectly for dual boot.
Good luck I'm off to work.

---

### Post by jerrygofixit on 2006-06-09
[QUOTE=catlett]Sorry I thought your issue was you had win2k on C and winXP on D. You wanted to put Ubuntu on C but you were concerned that XP wouldn't boot from Ubuntu if installed Ubuntu to C because Win2k was the OS that was booting both Win systems and you felt that C had the MBR for XP. That's why I mentioned the above. I didn't think it was necessary but it would have made XP on D bootable from the MBR before you installed UBuntu.
If you have just installed Ubuntu and it sounds like you are going to restore XP from a recovery cd, then I wouyld recommend reinstaling Ubuntu after XP. It is the sinplest way to get grub back. There are other methods that you can search but this is the easiest and if you just installed, there is nothing important on your ubuntu install.

If you don't want to reinstall after thw windows recovery you can search the ubuntu wiki, it has a section about how to restore grub after windows but I don't recommend it. It's not simple and it is time consuming. For an extra half hour you can have a frexh install setup up perfectly for dual boot.
Good luck I'm off to work.[/QUOTE]

It was, that other guy stole my thread, that answered my question but not his. Thanks for the help.

---


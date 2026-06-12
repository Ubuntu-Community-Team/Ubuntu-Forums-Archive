---
title: "Hard drive/computer head ache.. GRUB"
date: 2009-11-15
forum: Installation &amp; Upgrades
---

### Post by mexicanmusicman on 2009-11-15
Hi, i have quite a novel problem.:lolflag:

I had ubuntu 9.10 and windows xp dual booted for a while, and everything was peachy. Then i got another hard drive... (the exact same kind as i had before, so i know its compatible.) My goal was to put ubuntu on one hard drive and then windows xp on the other... well it didn't work out so well.:mad:

I got into ubuntu and deleted all the stuff off both of the hard drives, and then turned my computer off and booted from the windows cd. It gave me the error 0x0000007B

I then tried to install ubuntu, and the installation went fine, until i turned off the computer. When it gets past the "DELL" screen, it goes to a black screen that just has the word GRUB on the top left corner and it freezes there.:confused:

I then tried to boot ubuntu onto the other hard drive and it wouldnt install becuase of one of three reasons (it wasnt sure which one.)

1)Faulty CD
2)FAulty CD/DVD drive
3)Faulty hard drive. 

I want my computer back, and would love to solve my problem.

If Needed, i have a dell optiplex 330 with no special things installed so you can get the specs on the webiste

THANKS IN ADVANCE :popcorn:

---

### Post by mexicanmusicman on 2009-11-15
Anyone

---

### Post by mandarin77 on 2009-11-15
Recommendation:
Remove the other hard drive while installing Linux.
Remove the other hard drive while installing Windows.
 
Do not try to use grub to dual boot.
Use the BIOS boot menu. (easiest, from a "everything works with no troubleshooting" perspective)
 
If you run the computer with windows on HDD 0, and ubuntu on HDD 1, your menu.lst file sets up HD(1,0), but when you choose HDD1 to boot ubuntu, the BIOS sets it to HDD 0.
So you need to change your menu.lst to show HD(0,0). And after every upgrade, you might need to re-change your menu.lst again.
 
Have fun re-installing both operating systems!
If you think you have CD drive problems (older drive doesn't read correctly) get a new one.
The hard drive might neeed to be "wiped" after a bungled install. I recommend the HD install CD that came with your HD. There should be a setup utility on the CD that will restore the HD to factory (wipe off the strange crap) and then install a file system (say NTFS). Try to install Linux onto the drive. It will find the file system, and you can delete it during the Ubuntu setup process.
 
And for a simple check (don't know your expertise level), make sure your HD jumpers are set right - Master and Slave if on the same IDE channel (not an issue for SATA drives), and that includes the CD/DVD drive as well.
 
mandarin

---

### Post by mexicanmusicman on 2009-11-15
i dont know what the menu.lst is, but ill try taking the other out. HOw can i get rid of grub?

---

### Post by rapsodia on 2009-11-15
I had the exact problem and it turned out to be to jumpers on the back of the HD. Sorry to hear that it screwed up both your drives dual booting will work fine with a good set up I can help you do that. first, this is what you need to do. just to be sure plug in the hard drive where you wanna install ubuntu and only that one. then boot in with your live cd( assuming it can read the disk) then once the live cd booted go under system/administrator and find the partition manager its called gparted that way you can reformat your entire drive clearing any problems. format it in fat32. 
after this is done go ahead and install ubuntu. after it installs test it make sure its working without any issues ( let me know if you couldnt install it at all ). once ubuntu its installed unplug that HD and plug in the one for windows and go ahead and install windows after both OS's are installed, plug them in both ( make sure that in your bios  ubuntu was set to boot first ) once in ubuntu you can set up your grub to dual boot I can instruct you on this and I will post the exact steps but first let me know if you completed the above once I get home I will post the rest.

---

### Post by mexicanmusicman on 2009-11-15
When i try to install windows, it still gives me the 0x0000007B error.

i tried with only the hard drive i want to install windows on plugged in

Its the exact same hard drive i dont understand why it isnt working please help

---

### Post by rapsodia on 2009-11-15
Have you tried formatting the entire HD you can do this with the ubuntu live cd like a mentioned before

---

### Post by mexicanmusicman on 2009-11-16
I changed it to FAT 32 and it still gave me the error

---

### Post by oldfred on 2009-11-16
Windows XP should work with FAT32 but NTFS is better. Fat will not accept files over 4GB and has no recovery from errors.

Microsoft's explanation of your error:
[http://support.microsoft.com/kb/324103](http://support.microsoft.com/kb/324103)

If the drive still has some ext3 or Ubuntu stuff Windows may see it as a virus.

---

### Post by PRC09 on 2009-11-16
You could check in the bios of your machine and  I think it is under the hard drive settings(or configuration setting) try  setting it for Auto (ATA). Have seen this setting cause problems because I think the default is for raid. This windows error could also point to a drive controller error (I think I read that somewhere). there are other settings for the hard drive  as well so you may have to try them one at a time and see if any of them work......

---

### Post by mexicanmusicman on 2009-11-16
Thanks for all your input guys i will try this tomorrow

---

### Post by mandarin77 on 2009-11-16
You don't get rid of grub. It installs and boots Ubuntu, but you don't want to use it to boot to Windows, just use the BIOS boot options for simplicity.

Use the HD CD to clean the HD off.

---

### Post by alexfish on 2009-11-16
> **mexicanmusicman said:**
> Hi, i have quite a novel problem.:lolflag:

I had ubuntu 9.10 and windows xp dual booted for a while, and everything was peachy. Then i got another hard drive... (the exact same kind as i had before, so i know its compatible.) My goal was to put ubuntu on one hard drive and then windows xp on the other... well it didn't work out so well.:mad:

I got into ubuntu and deleted all the stuff off both of the hard drives, and then turned my computer off and booted from the windows cd. It gave me the error 0x0000007B

I then tried to install ubuntu, and the installation went fine, until i turned off the computer. When it gets past the "DELL" screen, it goes to a black screen that just has the word GRUB on the top left corner and it freezes there.:confused:

I then tried to boot ubuntu onto the other hard drive and it wouldnt install becuase of one of three reasons (it wasnt sure which one.)

1)Faulty CD
2)FAulty CD/DVD drive
3)Faulty hard drive. 

I want my computer back, and would love to solve my problem.

If Needed, i have a dell optiplex 330 with no special things installed so you can get the specs on the webiste

THANKS IN ADVANCE :popcorn:
  look at this thread
[http://ubuntuforums.org/showthread.php?p=8328294#post8328294](http://ubuntuforums.org/showthread.php?p=8328294#post8328294)

---

### Post by darkod on 2009-11-16
Using BIOS to boot is anything but simple. There is nothing simpler than selecting which OS you want to be default in grub, setting timeout of 15sec for example, and control the boot like that.
Not to mention that the BIOS option is actually restarting your pc twice every time because exiting BIOS restarts the pc.
Just my humble personal opinion. :)

PS. The idea to unplug drives sometimes can do more damage than help. If you are just troubleshooting that's fine. But when the installation time comes you want both drives plugged in to see if they work OK. First install windows on one, don't unplug it and ubuntu installation will detect it and create the grub menu automatically for you. If even the windows installation with only one drive doesn't work then you know you have another problem not related to ubuntu at all.

---

### Post by alexfish on 2009-11-21
> **darkod said:**
> Using BIOS to boot is anything but simple. There is nothing simpler than selecting which OS you want to be default in grub, setting timeout of 15sec for example, and control the boot like that.
Not to mention that the BIOS option is actually restarting your pc twice every time because exiting BIOS restarts the pc.
Just my humble personal opinion. :)

PS. The idea to unplug drives sometimes can do more damage than help. If you are just troubleshooting that's fine. But when the installation time comes you want both drives plugged in to see if they work OK. First install windows on one, don't unplug it and ubuntu installation will detect it and create the grub menu automatically for you. If even the windows installation with only one drive doesn't work then you know you have another problem not related to ubuntu at all.


thanks
good advice

---


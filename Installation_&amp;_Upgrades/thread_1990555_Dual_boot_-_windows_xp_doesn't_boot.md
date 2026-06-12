---
title: "Dual boot - windows xp doesn't boot"
date: 2012-05-29
forum: Installation &amp; Upgrades
---

### Post by oldfred on 2012-05-29
I do not see anything wrong. Script shows NTFS partition look ok and you have the 3 Windows XP boot files, one is boot.ini and it looks ok also. Sometimes you just need a chkdsk from a Windows repair CD or the XP install CD. Occasionally one of the boot files is corrupted and can be replaced.

 Description of the Windows XP Recovery Console for advanced users list of commands
[http://support.microsoft.com/kb/314058/](http://support.microsoft.com/kb/314058/)
To run the Recovery Console from the Windows XP startup disks or the Windows XP CD-ROM, follow these steps:
1.    Insert the Windows XP startup disk into the floppy disk drive, or insert the Windows XP CD-ROM into the CD-ROM drive, and then restart the computer.

Click to select any options that are required to start the computer from the CD-ROM drive if you are prompted.
2.    When the "Welcome to Setup" screen appears, press R to start the Recovery Console.
3.    If you have a dual-boot or multiple-boot computer, select the installation that you must access from the Recovery Console.
4.    When you are prompted, type the Administrator password. If the administrator password is blank, just press ENTER.
5.    At the command prompt, type commands one at a time.

FIXMBR  C:  #do not run if you still want grub in the MBR
FIXBOOT  C:
BOOTCFG  /rebuild  # rebuilds boot.ini
chkdsk c: /r

If files are still missing you can do this to copy from CD to C:\:
COPY [CDDRIVE]:\I386\NTLDR  C:\
COPY [CDDRIVE]:\I386\NTDETECT.COM  C:\
Where [CDDrive] is location of cd or D: etc.
or:
Can you boot into Ubuntu? If so you can mount your Windows drive and navigate to C:\windows\ServicePackFiles\i386 folder and copy
ntdetect.com and ntldr to root of C:\.

---

### Post by mystmaiden on 2012-05-29
I installed Ubuntu Precise beside windows xp just following along the instructions on the cd. Ubuntu boots, xp does not (though it is shown on the list of boot options.)  I installed boot-repair via the live cd and ran it as 'recommended' . I still have the original problem.

The url that boot repair returned is [http://paste.ubuntu.com/1013708/](http://paste.ubuntu.com/1013708/) 
I wasn't sure about the using boot info script because the instructions I saw for it were for Natty and Karmic.  The computer is used and I just got it, so I'm not real familiar with the system. What system info would be helpful?

thanks in advance,

mystmaiden

---

### Post by oldfred on 2012-05-29
I moved my answer from the other thread and somehow it became first. Do not know how to renumber.

---

### Post by mystmaiden on 2012-05-29
Thanks so much for  the reply. I can boot Ubuntu, it's working well. Its been an age since I fiddled with windows xp. I will try your suggestions and post my results (crossing my fingers). 

mystmaiden

---

### Post by mystmaiden on 2012-05-29
I ran Windows in recovery mode and used these three commands:

FIXBOOT C:
BOOTCFG /rebuild
chkdsk c: /r

I've never successfully done this before but I assume I do want grub in the mbr?

Anyway, those commands didn't fix my dilema. How do I find c drive from Ubuntu? I tried gksudo nautilus, (checked show hidden folders) but I didn't find it from there. EDIT: I left out something important here by way of info. One of the commands asked me to enter the load identifier (I chose 1 which was windows) and it asked me to enter the OS load options. I had no idea what to put there so if the commands did not work, it was definitely my fault.

mystmaiden

---

### Post by oldfred on 2012-05-29
Is the issue you cannot boot Windows from grub's menu or that you cannot see the Windows files in Nautilus.

Nautilus should show it in the left panel, but it may have the size as the name. Or just 136GB or whatever size it is. I like to label my partitions in gparted or Disk Utility, so then any unmounted partitions appear by my label.

If it still needs chkdsk it may not show.

---

### Post by mystmaiden on 2012-05-30
It is both, really. Windows does not boot so I was going to try copying ntldr and netdetect from the cd to the root of c as you suggested but I can not find c drive to do that. I am using gnome classic so maybe its showing up differently but when I use gksudo nautilus theres nothing to indicate its there. No size like you mentioned or anything like that - just home, desktop, file system and trash.

I just realized the problem, I was using gksudo nautilus when all I had to do was click on computer and go from there...
EDIT - I finally managed to copy the files properly, I apologize for my confusion. Windows still does not boot. What should I have entered when windows recovery asked me to enter the load identifier and when it asked me to enter the OS load options? Maybe if I tried that again and put in the right answers it would help? In the end, if I have to start all over, I can - everything is backed up but I'd still like to fix this if possible.

thanks so much for all the help

---

### Post by mystmaiden on 2012-05-30
I decided to run chkdsk again since I had replaced the files and I noticed chkdsk was getting to around 70% and then dropping back to 50% and starting over. I don't know why it would do that but it seemed like a problem with the computer itself or with something else on the windows install. I decided to do a clean install of both os. I installed windows and made sure it was fully updated, then installed Precise and updated it. Rebooted into Ubuntu, then booted into Windows xp. XP ran chkdsk on its own, rebooted and voila` I have a dual boot system in working order. 
Thank you so much for your patience and help, I wouldn't have gotten this far without it,

mystmaiden
Ps Could you mark this as solved, I don't seem to have the option (maybe cause your post is first on the list)

---

### Post by oldfred on 2012-05-30
Sometimes reinstall is quicker, but you do have to have good backups. 

Glad you got it working. Changed to solved.

---


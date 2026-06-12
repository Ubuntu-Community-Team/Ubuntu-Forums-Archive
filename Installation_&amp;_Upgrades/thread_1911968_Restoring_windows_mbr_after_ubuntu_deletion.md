---
title: "Restoring windows mbr after ubuntu deletion"
date: 2012-01-19
forum: Installation &amp; Upgrades
---

### Post by choclo on 2012-01-19
Hello there, my friend took ubuntu off of his girlfriends computer before he went away and now it won't boot windows.
All that comes up is ->

error: no such partition.
grub rescuee>

I have found threads on how to restore grub but only if there is a ubuntu partition.

Now I'm asking is there a way to restore grub to just have the option of windows or is there another way to restore the windows mbr using a live cd. (I have a 10.04 live cd)

The computer won't connect to the internet as its a dell inspiron 1521 and needs extra drivers. Another question, can i install these drivers through the live cd and get it working maybe?

Thanks in advance
the choc

---

### Post by darkod on 2012-01-19
According to this you can download a bootable Boot-Repair CD:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

It also says it has Advanced options about MBR restore.

---

### Post by Buntumatic on 2012-01-19
[GAG]("http://gag.sourceforge.net/") may just do it, never tried it in this situation, though.

---

### Post by oldfred on 2012-01-19
Darko's suggestion of Boot Repair is probably the easiest.

You can also manually install the lilo boot loader which will boot Windows..

Restore basic windows boot loader - universe enabled
Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. Close that window and click on reload before installing lilo with Synaptic or command line.
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader.

---

### Post by choclo on 2012-01-20
Boot repair won't boot from the cd for some disgusting reason, am gonna try the install lilo manually thing. I actually tried to do that but when it prompted for dependencies to be met I assumed it wouldn't work without them. Other than that I could try that GAG thing.

Thanks for the replies you guys ill let you know what happens

---

### Post by darkod on 2012-01-20
The lilo commands will work but as long as you have internet working. Because you said internet doesn't work, I suggested the boot-repair cd option since it doesn't depend on internet.

That lilo commands will give you some warning about the config, etc, just ignore them and continue since you will not actually be using lilo all the way. It can just pass on to booting windows.

---

### Post by oldfred on 2012-01-20
LiveCd's almost always connect to Internet if using Ethernet. Many have issues with wi-fi and have to download extra drivers. Try a direct wired connection.

Also many other repair LiveCDs include lilo in the CD. Boot-Repair can be download into the Ubuntu liveCD or has a full liveCD download.

---

### Post by nipunshakya on 2012-01-20
Hi. I will attach it here itself......I Had a similar scenario with me while downgrading from 11.10 to 11.04, but as i wanted dual boot, i just ignored the grub rescue and went on with 11.04's fresh installation, it worked perfectly. 

However, similar querry as choclo was striking my mind on howto get rid of grub rescue stuff when only windows is in the machine.... Would it be possible to do a startup repair via the windows 7 installation cd or rescue disk of windows 7 for repairing the startup stuff??



Regards,WinuxUser

---

### Post by oldfred on 2012-01-20
@WinuxUser
That's the Windows way.:)

Actually if only using Windows it probably is the better way. But a user has to have a full install Windows Cd/DVD, which few have as systems do not provide install media anymore. And the restore partition on new systems is just an image and usually will not do repairs either.

But if Windows 7 or Vista you can run the auto repair 3 times or run the BootRec.exe /FixMBR command. From XP you have to run the fixMBR command.

How to Boot to the System Recovery Options in Windows 7
[http://www.sevenforums.com/tutorials/668-system-recovery-options.html](http://www.sevenforums.com/tutorials/668-system-recovery-options.html)

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

All users should have a liveCD or repairCD for every current version of system installed. Windows or Ubuntu. And if in Ubuntu and have upgraded, you still should download the liveCD.

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by Sopalajo de Arrierez on 2012-01-22
> **Buntumatic said:**
> [GAG]("http://gag.sourceforge.net/") may just do it, never tried it in this situation, though.

   I have checked the SourceForge site, but it is not clear if this program works with Windows 7 boot loader.
   Does anyone know about it?

---

### Post by choclo on 2012-01-23
Hey I just remembered to get back to you guys, GAG didn't work cuz I tried that first. A windows 7 recovery disc and some bootrec.exe /fixmbr etc worked perfect so thanks oldfred!!! And the rest of you guys of course, i appreciated the input. Thanks again, peace

---

### Post by oldfred on 2012-01-23
Glad that worked. 

I just noticed I had the wrong command. FixMBR fixes the MBR and fixBoot fixes the PBR or partition boot sector. Often with fixBoot a chkdsk is also required. I will edit instructioins in post above just in case some else finds this thread.

---


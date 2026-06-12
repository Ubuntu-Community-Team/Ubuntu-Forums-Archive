---
title: "GRUB Error 21"
date: 2008-05-18
forum: Installation &amp; Upgrades
---

### Post by Errors suck! &quot;Kairu&quot; on 2008-05-18
Hi there,

last night i had tried to instull xubuntu on a 2.2GB external HDD, now i was pretty sure i told the xubuntu to install on my external beacause i selected the 2.2GB partition. the instulation got to 94% and stoped, so i shut down my computer removed the disk and eternal HDD and i got this,

"GRUB Loading stage1.5.

GRUB loading, please wait...
Error 21
_"

i then rebooted my computer and went to my bios setings and selected the drive i want, the onley one listed (windows xp), and still the same "Error". i then put my External HDD in to see what would happen and i got this,

"GRUB loading, plese wait...
Error 15
_"

i then went to try and reinstull xubuntu on my external HDD on a computer runing ubuntu. againe insull stapped at 94%, but when i went to start the computer it was fine, unlike my computer running XP.

i tried to fix my problem by reparing win XP. still same error.

pleaes if annybody could help, it would be greatly appreciated.

                   thankyou, Kairu. and please excuse my spelling of the word install.

---

### Post by ajgreeny on 2008-05-18
>  instull xubuntu on a 2.2GB external HDDSorry, but I don't think 2.2GB is enough to install a full xubuntu OS, so you will have to think again to end up with a usable xubuntu.  To get back your windows for the moment at least you should reboot with the windows CD in the drive and chose "Recovery module" or something like that.  Wait till it finds your windows install, then chose that and when it gets to a command prompt, type "fixmbr" without the quotation marks.  Don't worry about the warnings that show; you can't boot now anyway, so you can't make things worse.

When you've done that, shutdown, remove the CD and reboot.  You should go now straight into windows.

---

### Post by Errors suck! &quot;Kairu&quot; on 2008-05-20
thank you so mutch. but more problems orrise. windows wants to keep installing, i dident take the disk out. i might figure it out ill just re write the windows files befor the install disk wipes my drive.

---

### Post by VMC on 2008-05-20
> **Errors suck! "Kairu" said:**
> thank you so mutch. but more problems orrise. windows wants to keep installing, i dident take the disk out. i might figure it out ill just re write the windows files befor the install disk wipes my drive.

Like ajgreeny said, it's the recovery disk. When the Windows disk is inserted you have an option to recover your system. There is a XP recover iso somewhere on the internet, and I use that one. You must have push a key when it said about installing Windows. If you look carefully there is a F key, maybe F6, not sure right now, but look closely. Then do fixmbr. It should take you to a Windows command prompt. NOT dos prompt. They look the same, but there not.

---

### Post by Errors suck! &quot;Kairu&quot; on 2008-05-21
yes i know, i did do "fixmbr" and windows said it was sucsesfull, but now windows wants to re install the oporating system. when i start up "restoring system setup......." or somthing along thos lines, then it quick gos to another window with an "OK" button and shuts down. i tried redirecting the boot operations with "BOOTCFG /somthingoranother" and i tried seting up a new boot pargmentor. yet i get the same screen.

---

### Post by Errors suck! &quot;Kairu&quot; on 2008-05-23
Please, do not answer my thread, i got all my files back. thank you.

---


---
title: "how to install PLOP boot manager...??"
date: 2011-03-14
forum: Installation &amp; Upgrades
---

### Post by meTroubled on 2011-03-14
i'm currently using windows vista and want to boot ubuntu10.10 from my usb drive but my BIOS doesn't support it.
i got to know that PLOP boot manager might help me.
please explain steps to install it on vista hard-disk,i'm getting confused following steps posted on their website

---

### Post by ronnielsen1 on 2011-03-14
> **Run from CD with an ISO file**

        Download the current boot manager  [plpbt-5.0.11-2.zip]("http://download.plop.at/files/bootmngr/plpbt-5.0.11-2.zip").     Extract it to get the iso file plpbt.iso. 
  **Windows:**      
[INDENT]          You can use [Nero]("http://www.nero.com/"), or the free program     [CDBurnerXP]("http://www.cdburnerxp.se/"), or any other program     that can burn ISO images.     
               Use the option like burn ISO on CD or     burn ISO Image. Then choose the boot manager ISO and burn it.     
     [/INDENT]

or:


> **Run from the Windows boot menu (2K, XP, VISTA and Win7)**

        Download the file [plpgenbtldr-0.8.zip]("http://download.plop.at/files/bootmngr/plpgenbtldr-0.8.zip")     and extract it.
  
[LIST]
[*]     Create a directory like c:\plop. You can use any directory you want.     
[*]     Copy plpbt.bin and plpgenbtldr.exe to your c:\plop directory.     
[*]     As administrator/with administrator rights open a command shell.     
     Hint VISTA/Win7: Use right click at the command shell menu entry and choose "Run as administrator"     
          change to c:\plop with cd \plop     
[*]     Then run plpgenbtldr
    This program searches for the file plpbt.bin in the currrent directory.
    plpgenbtldr generates the file plpbtldr.bin.      
[*]     Adding to the boot menu. Windows 2K and XP is different to Windows VISTA and Windows 7     

[LIST]
[*]	Windows 2K, XP
 	    add the line below to your c:\boot.ini
 	    c:\plop\plpbtldr.bin="Plop Boot Manager"
[*]Windows VISTA
 	    open notepad as administrator and create a file c:\boot.ini
		add those lines
 [boot loader]
[operating systems]
c:\plop\plpbtldr.bin="Plop Boot Manager"
[/LIST]
[/LIST]

[http://www.plop.at/en/bootmanager.html#runcd](http://www.plop.at/en/bootmanager.html#runcd)



or I have also used Hirens boot manager (Which also has plop)

[http://www.hirensbootcd.org/files/Hirens.BootCD.13.1.zip](http://www.hirensbootcd.org/files/Hirens.BootCD.13.1.zip)


[http://www.hirensbootcd.org/download/](http://www.hirensbootcd.org/download/)

---

### Post by ronnielsen1 on 2011-03-16
Did it work?

---

### Post by meTroubled on 2011-03-17
> **ronnielsen1 said:**
> Did it work?
can i install plop boot manager on my hard disk and then when i reboot my computer,will i be shown plop boot menu so that i can boot from my usb?
i just want that a option must be added in my bios to boot from usb pendrive,which is originally not present.
if i can do that with plop boot manger than please explain me how to install it on windows vista,
i'm not getting steps from,"change to c:\plop with cd \plop"

---


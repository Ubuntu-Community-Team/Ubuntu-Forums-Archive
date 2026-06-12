---
title: "I think GRUB won't let me boot from CD - Help!"
date: 2006-06-12
forum: Installation &amp; Upgrades
---

### Post by F0CUS on 2006-06-12
Hi all,

I am trying to install Ubuntu Dapper over Warty (not upgrading). I currently have dual booth (win + ubuntu on partitions) with GRUB. 

I have burnt Dapper to a CD and have been trying to boot from it...

I have a toshiba laptop and can set the boot sequence using a toshiba app in windows control panel. I have set the priority to CD first.

For some reason it doesn't boot from the CD, instead it just seems to open GRUB and I can't seem to get into my BIOS (by pressing del/F8/ESC) anymore (I don't think I have tried entering BIOS since I installed GRUB so I am figuring that GRUB is somehow not allowing me to enter BIOS (is this possible??)



Some usefull information about my system:

1 - I do not have a floppy drive (laptop)
2 - I have a USB HDD
3 - I have a 1GB CF card in my PCMCIA adapter and have tried booting from that but to no avail... I just copied the files from the CD to the CF card and changed the boot sequence to boot form PCMCIA


So, can anyone give me any suggestions on what to do? I really want to get Dapper installed! :D 

Thanks guys!

---

### Post by DJ Scribblinni on 2006-06-12
GRUB isn't loaded till **after** your BIOS has gone through what it needs to, I've never used a Toshiba, so obviously I don't know the keys to press to get into BIOS.  But what I do know is that every computer company uses a different key setting to get into the BIOS, sometimes that information is displayed while BIOS is loading.  I hope that quick info gets you started...somewhere...

---

### Post by F0CUS on 2006-06-12
Yeah, I have now tried every single key on boot... Can't get into BIOS.

I have been reading the Installation/FromWindows ([https://wiki.ubuntu.com/Installation/FromWindows](https://wiki.ubuntu.com/Installation/FromWindows)) but am worried about installing Grub For Dos since I already have Grub installed... Is there any way to install the using my existing GRUB if I copy the files to my c:\ drive (windows partition)?

---

### Post by confused57 on 2006-06-12
Try going to the Toshiba website or doing a google search for Toshiba bios...you may have to press a couple of keys, e.g. esc+F1, etc.

---

### Post by F0CUS on 2006-06-13
OK, finnaly figured this out... I managed to get into BIOS with ESC+F1... but that didn't really d anything becasue  Ijust verified that CD was set to boot first.

The problem was that I had used Winrar to unrar the installation file which is an .iso (yes Winrar can open .iso files) I then unpacked the files into a folder and burnt them to the CD as files. For some reason my PC couldn't boot off of this CD(even though the auto-run was working fine in Windows). I just reburnt the ISo direclty to the CD and then I was able to boot.


Thanks!

---

### Post by Joeb on 2006-06-14
Your method of creating your original CD was the same as copying the files from the CD.  However, to be a bootable CD, certain files have to be in exactly the right spot on the CD.  The ISO is a direct image of the CD, so when you made the new copy, it had everything physically in the right location.  That's why it worked but your original didn't.

---

### Post by %hMa@?b&lt;C on 2006-06-15
try to boot with a grub flopy
[http://i30www.ira.uka.de/~ud3/mkgrubdisk/](http://i30www.ira.uka.de/~ud3/mkgrubdisk/)
see if that helps

or this
[http://www.nu2.nu/bootdisk/cdrom/](http://www.nu2.nu/bootdisk/cdrom/)
try that one first

---


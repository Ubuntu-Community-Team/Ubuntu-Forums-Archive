---
title: "Installing Windows XP (Ubuntu installed first)"
date: 2008-06-28
forum: Installation &amp; Upgrades
---

### Post by AlexBellisBrown on 2008-06-28
Does anyone know if this How-to is any good? : [http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

It seems to be, but i just dont understand step 5 (restore the GRUB bootloader), that bit is the only bit which is badly explained. Anyone have any ideas? As soon as i have installed XP and dual boot it with Linux, im going to write my own Hot-to with pictures. Fingers crossed, you guys can explain step 5 to me a little better, basically its just badly written:)

Thanks :popcorn:

---

### Post by Pumalite on 2008-06-28
This link might help:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by flytripper on 2008-06-28
looks fairly straight forward to me.... just breathe slowly... in .. out..

---

### Post by AlexBellisBrown on 2008-06-28
@ Pumalite, im sure that will come in handy, thanks. It seems pretty easy except for the end bit, restoring GRUB, but i dont get bits where it says ;

To enter the GRUB configuration mode, type in "sudo grub" and press Enter. Then type in the following commands in sequence:
- root (hd0,0)
- setup (hd0)
- quit
- exit 

Does that mean all together? Copy and Paste all at once?

---

### Post by sub2007 on 2008-06-28
You could also use the Super Grub Disk, it can be used to fix a whole bunch of boot issues including this. It's saved my skin on a couple of occasions before and so I think it's worth every user making a copy of it to keep around for an emergency, so if you have a use for it (like this) then it might be the time to make one. It's what I would use to fix this.

You boot it like a LiveCD.

Download and home page: [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
Instructions for using Super Grub Disk to fix Grub: [http://www.supergrubdisk.org/wiki/Howto_Fix_Grub](http://www.supergrubdisk.org/wiki/Howto_Fix_Grub)

---

### Post by AlexBellisBrown on 2008-06-28
Excellent idea, im making one as we speak, so let me get this right, When i install Windows, The MBR will make it totally ignore Ubuntu is there, thus booting right into XP? If i use the disk upon booting, i can restore the GRUB that easily? The only thing im worried about is that i will block Linux in! I only want Windows so that i can use my Lexmark printer, and iTunes to sync my iPod touch....

---

### Post by AlexBellisBrown on 2008-06-28
My Ubuntu live CD´s making some nasty noises inside my DVD drive... looks like im going to have to re-burn... :( Good job i decided to check everything was working ok before i started i guess...

---

### Post by housam on 2008-06-28
For recovering Grub read this [[COLOR="Red"]_simple guide_[/COLOR]]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub")

If you are going to reburn ubuntu live CD , burn it at slow speed i.e. 2X - 4X .

---

### Post by AlexBellisBrown on 2008-06-28
About the speed; Seeing as i burned it at 10x i think that was the problem, ill burn it at 2x. Does it matter if it goes on a CDRW?

---

### Post by housam on 2008-06-28
> **AlexBellisBrown said:**
> About the speed; Seeing as i burned it at 10x i think that was the problem, ill burn it at 2x. Does it matter if it goes on a CDRW?
No, it is ok to burn the cd on  CDRW.

---

### Post by AlexBellisBrown on 2008-06-28
Thanks, ill let you know how it goes, unfortunatly i downloaded it, burned it, then deleted it, ill have to download all 700mb again.... and with my slow connection... were looking at 3 hours... ah well, live and learn.:)

---

### Post by Pumalite on 2008-06-28
> **AlexBellisBrown said:**
> @ Pumalite, im sure that will come in handy, thanks. It seems pretty easy except for the end bit, restoring GRUB, but i dont get bits where it says ;

To enter the GRUB configuration mode, type in "sudo grub" and press Enter. Then type in the following commands in sequence:
- root (hd0,0)
- setup (hd0)
- quit
- exit 

Does that mean all together? Copy and Paste all at once?

One command at the time (in the Terminal)

---


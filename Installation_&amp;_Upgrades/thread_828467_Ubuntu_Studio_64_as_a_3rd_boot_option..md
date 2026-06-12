---
title: "Ubuntu Studio 64 as a 3rd boot option."
date: 2008-06-13
forum: Installation &amp; Upgrades
---

### Post by starbase1 on 2008-06-13
Hello All,
I currently have a system which started out as XP pro, I added XP64 as a second boot option, and now I want to add Ubuntu Studio 64 bit as the third option on boot. I have a separate partition all ready and formatted for it to land in, but I am not sure if I install US64 from the disk it will preserve the other 2 boot options, and I get very nervous about anything that changes boot options....

I suppose the ideal solution would be to wubi it, but I understand that wubi for US64 is not yet fully implemented.

So, if I try and install from the disk, should it leave my other options intact? And is there a nice easy way to fall back to the old setup if there are problems?

As ever, all clues for the clueless gratefully received!
Nick

PS - And what system is XP vs XP64 using to dual boot anyway?!?!

---

### Post by starbase1 on 2008-06-15
Anyone please?
Nick

---

### Post by logos34 on 2008-06-15
Well, if you are sure you don't want to use Grub, then yes, you can install studio without it overwriting the mbr which contains your windows bootloader.  Toward the end of the installion steps there's a section where it will ask you where to put grub.  Send it to a floppy or write it to the bootsector of the ubuntu root partition (hd0,**?**), or /dev/sda**?**. Then you can use windows to chainload linux.  [WinGrub]("http://users.bigpond.net.au/hermanzone/p9.html") is one way.  You could also just set it up manually (which I prefer): grab the [grub4dos zip]("http://download.gna.org/grub4dos/"), extract the **grldr** file to C: directory (XP pro), make a folder called **boot\grub** in c: and copy the ubuntu menu.lst to it (you'll need [fs-driver]("http://www.fs-driver.org/") to access linux). Then add a line to **boot.ini**:
[B]
c:\grldr="UbuntuStudio 8.04" [/B]

---

### Post by starbase1 on 2008-06-15
Thanks for the suggestions Logos34.

Does this mean that if I do the standard install, it will NOT preserver both windows boot options?

---

### Post by logos34 on 2008-06-15
what will happen is that, by default, grub will overwrite the windows bootloader on the MBR.  But it should detect the presence of one or both windows OS and give you a choice on the grub boot menu screen of linux or windows. It usually does a good job of chainloading XP, where typically you would boot to the XP pro boot.ini screen like you do now directly, then choose either XP pro or x64.  

It's up to you which way you want to go.  I don't want to encourage you to use grub if you're afraid of messing up your windows dual-boot.  I understand--I've had a similar arrangement once upon a time.

---

### Post by starbase1 on 2008-06-16
I think I understand better now, thanks for taking the time to explain. Sounds like the next step is to get th progs you mention, and read the documentation for them!

Nick

---

### Post by starbase1 on 2008-06-23
I just had another run at it, and I am now the proud owner of a triple booting system!

Thanks,
Nick

---

### Post by logos34 on 2008-06-23
hey that's great to hear

enjoy!

---


---
title: "How To: Dual-Boot Ubuntu/Windows with two SATA drives"
date: 2007-01-19
forum: Installation &amp; Upgrades
---

### Post by gislebertus on 2007-01-19
Just thought I'd pass on what worked for me, configuring a dual-boot system with Ubuntu on the primary SATA drive and Windows on the secondary SATA drive. 

As per mural's instructions in [http://ubuntuforums.org/showthread.php?t=335929](http://ubuntuforums.org/showthread.php?t=335929), just add this to the end of menu.lst in /boot/grub/menu.lst:

title      Microsoft Windows XP
root       (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
savedefault
makeactive
chainloader +1

Just open a terminal, type:

sudo gedit /boot/grub/menu.lst

and plunk it in there. Save menu.lst, and you're good to go.

---

### Post by Booradley on 2007-07-26
Hi there,

Any ideas on what to do when your XP is on a RAID volume?  I have Ubuntu on one SATA drive and then my XP is one two SATA drives that are RAID'd (RAID 0).  Ubuntu doesn't see the RAID, it sees two seperate SATA drives.

thanks

Boo

---

### Post by yarayara on 2007-07-26
I have the same issue, sort of.

except ubuntu doesnt like my 250Gb hardrive and gives me lots of trouble. When I finally succeed installing it, I will have to deal with the 2os 2sata hd issue.

i will keep a look on your thread too.

---

### Post by GerryB on 2007-08-10
Newer computers now offer the option of booting from many devices. I'm wondering, after I install another SATA drive, if I could just boot from any one of the two at the booting screen? I'd have XP on one, and Ubuntu on the other. It wouldn't be a dual boot but it would be clean, straightforward and iron clad safe. I'm not interested in sharing information between the two OS's. Does anyone have experience with this?

---

### Post by Mark Phelps on 2007-08-10
I'm presuming that you mean you want to have two independent drives, each with its own OS, and select the one to boot from in the BIOS at startup time.  

If that's true, read on ...

Yes -- it's really rather straightforward to do it.  Shutdown. Disconnect the Windows drive. Reboot and iinstall Ubuntu, let it load GRUB to the mbr of its own drive.  Shutdown.  Reconnect the Windows drive.  You now really have two systems, each on its own drive.  You will have to select in the BIOS which one to boot from.

---

### Post by groundhog on 2007-08-11
I had a heck of a time getting my system to dual boot to a WinXP installation on the secondary disk.  I think it's because the BIOS on my mobo does not recognize SATA drives, so all the 'fixes' that rely on the BIOS to select the appropriate disk did not work.  But I finally got it to work.  
Here's my adventures in dual booting: [Click Me]("http://ubuntuforums.org/showthread.php?t=521087") 
Hope this helps.
- djb

---

### Post by GerryB on 2007-08-11
> **Mark Phelps said:**
> I'm presuming that you mean you want to have two independent drives, each with its own OS, and select the one to boot from in the BIOS at startup time.  

If that's true, read on ...

Yes -- it's really rather straightforward to do it.  Shutdown. Disconnect the Windows drive. Reboot and iinstall Ubuntu, let it load GRUB to the mbr of its own drive.  Shutdown.  Reconnect the Windows drive.  You now really have two systems, each on its own drive.  You will have to select in the BIOS which one to boot from.

Thanks. That's it. With this new computer, I just need to press Del at boot up and I get a screen that let's me boot from any device connected and recognized. I read somewhere that all this master and slave configuration stuff no longer exists with SATA drives, so life is much simpler. No need to connect or disconnect drives, no need to dual boot on the same drive, no need to get into the BIOS. So, disconnect the Windows drive first..-  to avoid any confusion I guess. Thanks again.

---


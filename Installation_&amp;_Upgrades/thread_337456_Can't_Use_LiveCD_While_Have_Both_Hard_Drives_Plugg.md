---
title: "Can't Use LiveCD While Have Both Hard Drives Plugged In"
date: 2007-01-13
forum: Installation &amp; Upgrades
---

### Post by corevette on 2007-01-13
Currently I have two 80 GB hard drives. One has Windows XP on it, the other has Ubuntu Edgy.  I want to reinstall Ubuntu and when I install it, I want GRUB to recognize that I have to hard drives in my computer so I can select when I boot up the computer which ones I want.  So I put in the LiveCD for Edgy with BOTH hard drives plugged in, and the loader for the LiveCD, where the Ubuntu Logo is with the bar that shows it's loading gets stuck about 3 seconds into the loading process.  So i try unplugging one of the other hard drives, so i only have one hard drive plugged in.... and the livecd works??? why? please help

---

### Post by logos34 on 2007-01-13
are these sata or pata or a mix?  what sata channel or master/slave position is it in? Is the winxp bootloader still intact?  does the livecd install work with the ubuntu or windows disk plugged in?

---

### Post by corevette on 2007-01-13
i don't know what pata or sata is...nor do i know which is the master or slave.  the winxp bootloader is still intact.  the ubuntu livecd install works with either the ubuntu or the windows hard drive, but not plugged in at the same time.

---

### Post by logos34 on 2007-01-13
almost all hard drives are either serial ata (with the new thin cables) or parallel ata (ribbon or round ide cables...it can make a difference to linux what kind and what order they're plugged in when it comes to dual-booting on two drives...I was going to suggest using different connectors on the motherboard to see if you couldn't find some other combo that would allow both to be connected at install.  But its perfectly ok to reinstall ubuntu with the winxp disk unplugged if that's what works...you'll just have to add windows to your fstab and grub config files manually, and they will then mount automatically and be fully accessible in linux.  You'll end up with pretty much the same arrangement: windows bootloader intact on the winxp drive, grub on the linux drive.  If these are two pata drives as master/slave on the same ide channel (ide0 or ide1), the ideal arrangement would be for ubuntu to be the master drive and winxp the slave: that way you can boot into grub on the mbr of the ubuntu disk and have a choice of linux or windows while keeping the windows bootloader intact.

---

### Post by corevette on 2007-01-13
how do i make either one master/slave?  and i have parallel ata.

---

### Post by logos34 on 2007-01-13
ide cable has three connectors--one end to the motherboard, master at the other end and slave in between...if you switch them you just have to change the tiny jumpers.  [your drives are probably on same cable] Or (less likely) they could be on separate ide channels with one connected on the same cable as the dvd/cdrom.

---

### Post by corevette on 2007-01-13
whats the arrangement for the jumpers for master?

---

### Post by logos34 on 2007-01-13
depends on the drive make and model.  Sometimes it's printed on the drive label, but you might have to check the manufacturer;s website for a diagram.  There's three positions: master, slave, and cable select,

---


---
title: "No user or operating system detected to import from"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by riomx on 2007-04-21
Hey guys,

I'm a huge FreeBSD proponent that has been waiting for the perfect opportunity to try out Ubuntu.

I've always loved using FreeBSD on servers, but I've always had trouble setting up a GUI.

I was very impressed by the presentation of Ubuntu as an OS and community, and was really excited upon hearing about the migration tool, so I decided to give it a shot on the laptop I bought in December.  It's a Sony Vaio C140G.

Anyhow, everything goes well until I partition my disk and it goes on to attempting to detect user accounts or operating systems previously installed in the system.

Unfortunately, it doesn't at all.  Since my laptop is strictly for work and I was planning on using Ubuntu for less serious activity (just surfing, screwing around watching videos on my breaks, being in a Linux environment) rather than production, I can't really mess with it too much.

If Windows XP isn't detected by the installation, is it safe to assume that the dual-booting option being set up by the installation is out of the question ?

If so, or if you know a work-around, please let me know.

Thanks !

---

### Post by jiminycricket on 2007-04-21
This migration assistant is new-- past releases didn't have it, so I'd assume grub-install .  But a quick fixmbr from a recovery cd should restore the windows MBR should anything go wrong.

That's very odd that the xp is detected ...can you mount the windows partitions on the live cd or were  they mounted automatically?  Does fstab list your Windows drives?

---

### Post by riomx on 2007-04-21
> **jiminycricket said:**
> This migration assistant is new-- past releases didn't have it, so I'd assume grub-install .  But a quick fixmbr from a recovery cd should restore the windows MBR should anything go wrong.

That's very odd that the xp is detected ...can you mount the windows partitions on the live cd or were  they mounted automatically?  Does fstab list your Windows drives?

Sorry.  Been helping my gf move all day.

I don't have the installation CD due to most manufacturers' wonderful policy of not including recovery disks for new computers anymore.  I do have a Vista upgrade cd to fall back on, but I'd rather not have to use it.

And XP wasn't detected.  I didn't check to see if I could mount the windows partition, but I'll check it out.

What I do know is that the installer can detect my drive and its space, and allowed me to resize it without issue.

---

### Post by jiminycricket on 2007-04-22
There's a utility called mbrfix that can run inside a Windows installation here: [http://www.ambience.sk/fdisk-master-boot-record-windows-linux-lilo-fixmbr.php](http://www.ambience.sk/fdisk-master-boot-record-windows-linux-lilo-fixmbr.php)

It still is really weird that your install isn't detected at all though...it would be easy to add it to /boot/grub/menu.lst 

title Microsoft Windows XP
root (hd0,0) 
makeactive 
chainloader +1

make sure hd0,0 actually does point at your first partition on our first volume though if you do that.

---


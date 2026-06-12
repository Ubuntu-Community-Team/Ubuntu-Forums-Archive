---
title: "distro with a pure graphic install?"
date: 2012-06-13
forum: Installation &amp; Upgrades
---

### Post by phoenix940 on 2012-06-13
i have a HDD that i just formatted and i have no keyboard for it only a mouse. i was just wondering if there was a distro with a pure graphical installation. i have used linux (mostly ubuntu) and know the basics of how it works i just dont know if what im looking for is out there.

if not is there a way i can install ubuntu to the slave drive from the master drive? i have set up like tht because the cd/dvd drive didnt work n i couldnt get past the bios menu... plus windows 98... enough said there. that is why i want linux and would perfer something light weight like damn small linux or even an old ubuntu distro or spin off (possibly crunch bang?)

any help would be much appreciated and i thank everyone in advance for any help.

---

### Post by zombifier25 on 2012-06-14
> **phoenix940 said:**
> i have a HDD that i just formatted and i have no keyboard for it only a mouse. i was just wondering if there was a distro with a pure graphical installation. i have used linux (mostly ubuntu) and know the basics of how it works i just dont know if what im looking for is out there.
Ubuntu has a very good graphical installer. Most of the works you need to do is pretty much point-and-click. There are parts of the process that you have to use the keyboard though (entering username and password); you can always use the on screen keyboard for that.

---

### Post by efflandt on 2012-06-14
One issue with what sounds like an old computer is, even if you could connect a keyboard to make settings in CMOS setup, is the computer even capable of booting from USB?

Some computers require you to press a certain key during boot (like F12 or Esc) to boot from CD/DVD or USB regardless of BIOS boot order, probably so you do not get infected by something malicious on a removable drive or disk by unintentionally booting that.  The only virus I ever caught (in Win95 at the time) was from accidentally booting a floppy while transferring files between that and an already infected refurbished PC.

If you have another computer you could use to try to put bootable iso on a drive, you might as well do a regular installation to the drive from there.  Although, that works best if the computer you install from uses default video drivers, because I think 12.04 automatically installs nvidia drivers if the computer you are installing from has suitable nvidia.  Then you could move the drive to the other keyboardless computer.

Because grub in Ubuntu normally finds partitions by UUID, that should work even if the /dev changes.  I initially install Ubuntu on my SSD as /dev/sda in a laptop to try it there, then moved the drive to /dev/sdb in my desktop and set BIOS to boot that drive (works fine).  That is also how a regular install on a USB hard drive can boot on different computers even if it ends up as different /dev/sd#.

The login screen has an accessibility icon (round) that can bring up an on screen keyboard for login.  But once in Ubuntu, in Dash you need to go to **Universal Access** > **Typing** and turn **Typing Assistant** ON.  I also checked the box on my tablet PC for "Turn on accessibility features from the keyboard", although, not sure if that is needed or what it does.  You should end up with a square multicolored icon in upper right panel to bring up on-screen keyboard.

---

### Post by drmrgd on 2012-06-14
Can you even boot any computer without a keyboard?  I thought BIOS throws a no keyboard present error if you try to boot without one.

---


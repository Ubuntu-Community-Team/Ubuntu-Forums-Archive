---
title: "Booting from external hard drive"
date: 2011-12-08
forum: Installation &amp; Upgrades
---

### Post by Mcrann on 2011-12-08
I am new to Ubuntu and I have a computer that the hard drive crashed on. I have an external hard drive that I was able to install Ubuntu on but I can not get it to boot from the external drive. Any suggestions?

---

### Post by efflandt on 2011-12-08
Are you sure that you put grub on the mbr of the external drive?  That was a drop down list at the bottom of the partitioning screen during install if you used the "Other" method to partition the drive during install.

Even if you set USB to boot before hard drive in CMOS setup, some computers still require you to press a key in BIOS splash screen during boot (probably F12 or Esc) to boot from anything other than internal hard drive, likely as antivirus protection to avoid unintentionally booting a potentially infected floppy or CD/DVD.

The only virus I ever caught (long ago in Win95) was a boot sector virus spread by accidentally booting an infected floppy.

---

### Post by garywclem on 2011-12-08
Some computers won't boot Windows or Linux from USB.  The one I'm using now (2004 era) has a BIOS option to boot from USB, but apparently it's expecting something that emulates a floppy.  Not sure of the exact details, but this computer is living proof!

---


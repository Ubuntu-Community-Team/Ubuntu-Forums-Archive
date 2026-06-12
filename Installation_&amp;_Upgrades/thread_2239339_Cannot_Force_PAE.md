---
title: "Cannot Force PAE"
date: 2014-08-13
forum: Installation &amp; Upgrades
---

### Post by anneandypearson on 2014-08-13
I have an old IBM Thinkpad and want to upgrade from 12.04 to 14.04 but I get the message "cannot because CPU does not have PAE enabled".

I have found a thread that advises that from the boot menu (options that include install, command line, advanced and help) press F6 and go on to add "forcepae".

However my boot menu in Ubuntu is not the same. Mine is GNU Grub 1.99 and has choices for Ubuntu, Previous Linux, memory and XP (for my dual boot). F6 does not work here>.

Excuse my lack of knowledge but I do not know where to go from here.

Any advice (hopefully simple) will be greatly appreciated.

Thanks

---

### Post by plucky on 2014-08-13
> **anneandypearson said:**
> I have an old IBM Thinkpad and want to upgrade from 12.04 to 14.04 but I get the message "cannot because CPU does not have PAE enabled".

I have found a thread that advises that from the boot menu (options that include install, command line, advanced and help) press F6 and go on to add "forcepae".

However my boot menu in Ubuntu is not the same. Mine is GNU Grub 1.99 and has choices for Ubuntu, Previous Linux, memory and XP (for my dual boot). F6 does not work here>.

Excuse my lack of knowledge but I do not know where to go from here.

Any advice (hopefully simple) will be greatly appreciated.

Thanks

Open a terminal and post output for ```
cat /etc/default/grub
```

If you have this file you should be able to insert "forcepae" into the grub.cfg file.

OR

Try [Fakepae](http://ubuntuforums.org/showthread.php?t=2113826&p=12504589&viewfull=1#post12504589) 

I used this on a Pentium M to upgrade from Xubuntu 12.04 a while back, and it worked. That machine is now running a clean install of Lubuntu 14.04 i using the "forcepae" boot parameter.

I think "forcepae" only works on a clean install (I could be wrong).

Good Luck

---

### Post by anneandypearson on 2014-08-13
The output was - but I have no idea what it means or what to do now . . . 

GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

---

### Post by mörgæs on 2014-08-13
I would use the occasion to erase Ubuntu (which might be a bit too heavy for 10 year old hardware) and do a fresh install of Lubuntu 14.04.1 including forcepae:

[https://help.ubuntu.com/community/PAE](https://help.ubuntu.com/community/PAE)

Remember to choose 'something else' during partitioning to be sure that Windows is not damaged.

---

### Post by anneandypearson on 2014-08-13
OK Thanks - thought that may be the answer. Do I just create an iso image of Labuntu [COLOR=#000000]14.04.1 (no DVD reader) and load from a pen drive. How do I (and where do I) get the correct version.

Sorry to ask daft questions but I am not too technical - but I do like Ubuntu and want to keep using it.

Thanks for all your help.[/COLOR]

---

### Post by plucky on 2014-08-13
> How do I (and where do I) get the correct version.

[Ubuntu Releases](http://releases.ubuntu.com/)

Download from [Lubuntu 14.04.1](http://cdimage.ubuntu.com/lubuntu/releases/trusty/release/) the i386 Desktop iso.

Not sure howto burn an iso in Windows, but Ubuntu has a program called "Startup Disk Creator" which will make a bootable pen drive.

Good Luck

---

### Post by mörgæs on 2014-08-13
... if the computer is new enough to boot from USB. 

Else any CD writer will do. Best is to burn using the slowest speed possible.

---

### Post by sudodus on 2014-08-13
I have an IBM Thinkpad T42, and it runs well with Lubuntu and Xubuntu and forcepae of the version 14.04.1 LTS.

Will you be installing from Windows? Then I suggest Unetbootin. From Ubuntu (also the old version), you can use many tools including Unetbootin in order to make a USB boot drive. See these links (and links from them)

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it]("http://ubuntuforums.org/showthread.php?t=2230389")

---


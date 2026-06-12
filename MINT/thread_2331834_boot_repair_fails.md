---
title: "boot repair fails"
date: 2016-07-26
forum: MINT
---

### Post by klmeno on 2016-07-26
I installed mint 18 via usb alongside win xp .PC boots ti Linux no Grub menu. Boot repair gives this url:

[http://paste2.org/JHtF2UjO](http://paste2.org/JHtF2UjO)

---

### Post by howefield on 2016-07-26
Thread moved to the "*MINT*" forum.

---

### Post by klmeno on 2016-07-26
thank you ,howefield sorry for my mistake

by the way ,how do I find my post! I'm a bit of an ancient newbie to these forums,thanking you in anticipation

---

### Post by PaulW2U on 2016-07-26
> **klmeno said:**
> by the way ,how do I find my post! I'm a bit of an ancient newbie to these forums,thanking you in anticipation
If you need to find one of your posts that has been moved or you're not sure where it was posted then you can find it by going to the menu near the top of each forum page and selecting **Quick Links | Find all my posts**.

There also a **Find latest posts** link on your personal profile page.

Hope that helps. :)

---

### Post by oldfred on 2016-07-26
It does not look like you ran Boot-Repair.

Have you tried? This often finds missing systems.
sudo update-grub

If that does not work, was Windows booting? Grub only boots working Windows.
And Windows is not working if it is hibernated or if the NTFS partition needs chkdsk.

---

### Post by klmeno on 2016-07-26
Hi oldfred,I ran boot-repair a few times,because nothing seemed to happen.I did update grub.Win xp was loading fine before I installed mint 18 from usb stick.Be gentle with me please I'm an ancient newbie,Thanks

---

### Post by oldfred on 2016-07-26
In Ubuntu at terminal run this and copy & paste/post output, preferably in code tags.
You can easily add code tags with forums advanced editor and # icon.

sudo update-grub

But you Summary report shows Windows in grub menu. And if more than one operating system is found it should show grub menu automatically.
Have you tried holding shift key from BIOS until menu appears?

---

### Post by klmeno on 2016-07-26
I tried shift key after BIOS and got all excited when it said "Grub loading"........but it didn't:(.The screen has "input  out of range "floating sign for about 10 secs then the linux mint  sign.

Here are results of grub update:

```
                       Generating grub configuration file ...
 Found linux image: /boot/vmlinuz-4.4.0-31-generic
 Found initrd image: /boot/initrd.img-4.4.0-31-generic
 Found linux image: /boot/vmlinuz-4.4.0-21-generic
 Found initrd image: /boot/initrd.img-4.4.0-21-generic
 Found memtest86+ image: /boot/memtest86+.elf
 Found memtest86+ image: /boot/memtest86+.bin
 Found Microsoft Windows XP Home Edition on /dev/sda1
 done
```

   Thank you for your time and patience

Sorry the floating message is " attention input not supported"

---

### Post by oldfred on 2016-07-26
That could be video mode in grub.
Grub2 tries to use default video from system, but sometimes needs its own settings. It used to just use BIOS version and that sometimes caused issues.

sudo nano /etc/default/grub

You have this line with # which means it is commented out. remove #, if you know exact video change it that.
#GRUB_GFXMODE=640x480

Then 
sudo update-grub

And try shift from BIOS again, if it does not appear automatically.

---

### Post by klmeno on 2016-07-26
How do I save after deleting hash next toGRUB_GFXMODE=640x480   and/or do  sudo update-grub?
 This was output of sudo nano /etc/default/grub:
```
  GNU nano 2.5.3                                     File: /etc/default/grub                                                                        Modified  

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT="menuentry 'Microsoft Windows XP Home Edition (on /dev/sda1)' --class windows --class os  'osprober-chain-65D1F20B4A2D4FC3' {"
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
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
GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

^G Get Help      ^O Write Out     ^W Where Is      ^K Cut Text      ^J Justify       ^C Cur Pos       ^Y Prev Page     M-\ First Line   M-W WhereIs Next
^X Exit          ^R Read File     ^\ Replace       ^U Uncut Text    ^T To Spell      ^_ Go To Line    ^V Next Page     M-/ Last Line    M-] To Bracket
```

thank you old fred I have managed to boot into grub and win xp,well done

---

### Post by oldfred on 2016-07-26
Glad you got it working.
If graphics are not correct you may want to update setting.

---


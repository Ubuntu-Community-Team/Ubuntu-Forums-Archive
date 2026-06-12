---
title: "Secret install of Ubuntu?"
date: 2007-07-26
forum: Installation &amp; Upgrades
---

### Post by corbypete on 2007-07-26
I have a Dell D520, which I have got working ok with a LiveCD.  I want an OS I can boot secretly on a work laptop at home.

Moving from a live cd to an installation would be the next step (so I dont have to keep reconfiguring at each boot)

Basically, my laptop is a work one.  all activity in windows is monitored, so if I bring it home theres a chance all the home usage will be relayed when i get back to work.  I therefor wanted to get an isolated, unrestricted environment ready so I could either boot off a cd or usb stick.  After two weeks im giving up with windows methods and now look to ubuntu

Is it possible to install Ubuntu onto the hard drive, hiding it from windows and not making a huge change to my boot up process?  ie. can grub be non graphical or a boot cd be made? (not live cd but cd to boot ubuntu partition on my hard drive)

That way i can have xp for work, ubuntu for home use and everythings kept seperate and away from prying admin eyes.  I just want it to browse the web mainly and control my other pcs at home using VNC or Logmein.com  so my requirements are low (I have other windows pc's at home i can use for multimedia tasks etc.), but its all via wireless so I'd like that to be configured then set in stone.

What about a secret boot disc instead of the hard drive boot tracks being altered, something like that, it doesnt have a floppy drive so a cd would have to be made.

I'm not new to linux, but I'm new to the Ubuntu way of working and no-way a linux guru (I support Windows for a living) so any help appreciated, Microsoft has failed me on this occasion (in finding a usb/cd boot option)

I also have access to a USB 80gig hard drive if that's any use (ie. just boot of that if ubuntu supports? Windows didnt...)    :)

---

### Post by perce on 2007-07-26
What about an external USB disc? you can install the OS you prefer on the external disc, and keep it at home.

---

### Post by corbypete on 2007-07-26
That will work yeah?

USB external hard drive, install ubuntu onto it, boot from it at home, job done?

---

### Post by NilsE on 2007-07-26
> **corbypete said:**
> That will work yeah?

USB external hard drive, install ubuntu onto it, boot from it at home, job done?
Just make sure when you install to the external drive the internal drive is not accessible (I removed mine).  This way grub won't touch it.

Then you just need to set your USB port in the BIOS as bootable ahead of the internal drive if a device is present.  Then just plug it in and boot up and you are ready to go.  Without it plugged in the boot will be to the XP internal drive.

---

### Post by Mike_Longbow on 2007-07-26
The closest approach to that I could imagine is what a I did with my dad's desktop some days ago: as some kind of challenge, I secretly installed Ubuntu in it. This is what a I did:

Using the Live CD I just made a little ext3 partition of 5 GB at the end of the hard drive (It's 160 GB one, and it was already partitioned in two, so no one noticed it) and I installed in it
Then I just edited /boot/grub/menu.lst in order to set Windows at the start of the menu, set it hidden, and set the boot delay to 1 second. Just like this:

```
sudo gedit /boot/grub/menu.lst
```

```

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
default 4

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
[COLOR="Red"]timeout 1[/COLOR]

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
[COLOR="Red"]hiddenmenu[/COLOR]

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line) and entries protected by the
# command 'lock'
# e.g. password topsecret
# password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title Windows 95/98/NT/2000
# root (hd0,0)
# makeactive
# chainloader +1
#
# title Linux
# root (hd0,1)
# kernel /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hda3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
## alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
## lockalternative=false
# lockalternative=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
## altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
## howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
## memtest86=false
# memtest86=true

## ## End Default Options ##

[COLOR="Red"]title Microsoft Windows XP Professional
root (hd0,0)
savedefault
makeactive
chainloader +1[/COLOR]

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=086c1c09-7aa9-465c-95ed-bf726202a76d ro quiet splash acpi=off
initrd		/boot/initrd.img-2.6.20-16-generic
boot

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=086c1c09-7aa9-465c-95ed-bf726202a76d ro single
initrd		/boot/initrd.img-2.6.20-16-generic
boot

title		Ubuntu, kernel memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1

```

Now, when the computer is turned on, the grub message mixes with the bios messages and passes away so quickly that no one can notice it (I only need to press Esc when this to show the grub menu)

I've been using Ubuntu on it from time to time since then, and yet, no one has found out that it is actually installed ;)

---

### Post by dabl on 2007-07-26
Here's a way to set up a bootable Ubuntu OS on a USB thumb drive -- is that the kind of thing you're looking for?

[http://kubuntuforums.net/forums/index.php?topic=3081748.0](http://kubuntuforums.net/forums/index.php?topic=3081748.0)

:)

---

### Post by corbypete on 2007-07-26
thanks for your replies.  i dont need it to be a usb stick, i have a 2gig, but have the 80-gig usb drive that can use if easier.

Im going to try installing without the host hard drive installed, thats got to be the easiest option.  this lappy also has an easy slide option .i can remove the hd without much hassle if there is a conflict somewhere but i'll see first.

damn, i woulda got on with this tonight but ran out of CD-r's Grrrr:mad:


that and im typing this from windows, im constantly killing rebuild processes and CA monitoring tools...   the missus hates windows on this dell constantly losing wireless connectivity and crashing with no reasoning, cant wait until linux works like a microwave oven, people will drop vista like flies

---


---
title: "install on desktop abit MB with nvidia gfx goes to bla(c/n)k screen"
date: 2010-12-21
forum: Installation &amp; Upgrades
---

### Post by tunist on 2010-12-21
greetings!

i installed ubuntu 10.10 on my laptop recently (32bit) without any troubles..

today i attempted to install the 64 bit version to my desktop as a dual boot with another OS.

i made space on a SATA HDD for the linux install and booted with the Live CD in the drive...

when the PC boots, the install process shows the initial loading screen then goes to a black screen with blinking cursor and does nothing more.
following some threads i found in the forum here i played with pressing F6 and changing some options but they made no difference.

does anyone have any idea of what may be occurring?

attempting to get ubuntu to run without installing did not work either..

thanks

---

### Post by tunist on 2010-12-21
hmm.. looks like my DVD drive is no longer functioning..
so that explains that!

instead i have moved the install image to a USB key and attempted to boot from that.. 

this time i have found that the installer opens and begins the install..
but is stopping just after it registers the CPU type (intel quadcore).. the first attempt it got to listing core #1, the 2nd attempt it got to #2.. (i haven't done it four times yet to see if that's the 'issue', haha).

i used the key on another machine and it boots fine...

does anyone have any idea what the issue might be on the one that doesn't work?

its a 64bit CPU and i'm using the 64bit version of ubuntu 10.10..
i also placed the install image on the usb key using the tool from [pendrivelinux.com]("http://www.pendrivelinux.com")

thanks

---

### Post by tunist on 2010-12-21
p.s. the pc in question works fine besides the apparently now broken DVD drive.

---

### Post by dino99 on 2010-12-21
thats why i install generic-pae kernel (i386) instead of 64 bits (too many issues with lot of devices)

---

### Post by tunist on 2010-12-21
i just ran through the 32bit installer via USB key and it stops at pretty much the same point in the install process (it got up to core 3).. so it seems the issue is not version related, in that way.

---

### Post by tunist on 2010-12-21
here's a screenshot of where the installer stops:

[http://www.growforall.co.uk/images/IMG_0360.JPG]("http://www.growforall.co.uk/images/IMG_0360.JPG")

---

### Post by tunist on 2010-12-21
so having played with acpi=off and debug with the boot line in the relevant file in the isolinux folder and syslinux folder i was unable to get the install process to behave any differently at all.

i then looked at using wubi and i got it to run using 'acpi workarounds'.. however, the boot does not complete, the process stops on a black screen with flashing white cursor.

i read on one webpage that in such cases the developers may be interested to explore and find out why it is occurring.. 
anyone know who to email for that?

thanks

---


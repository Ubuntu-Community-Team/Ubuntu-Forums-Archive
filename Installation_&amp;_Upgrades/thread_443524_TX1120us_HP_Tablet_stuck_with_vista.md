---
title: "TX1120us HP Tablet stuck with vista"
date: 2007-05-14
forum: Installation &amp; Upgrades
---

### Post by petroz on 2007-05-14
--------------------------------------------------------------------------------

Hi All,

I have a new tx1120us hp tablet. I dont want to overload this post with specs, so you can find them at 
[http://h10025.www1.hp.com/ewfrf/wc/g...reg_R1002_USEN](http://h10025.www1.hp.com/ewfrf/wc/g...reg_R1002_USEN)
I have not been able to get any Ubuntu distrib to succesfully startx from any installation image. The screen goes through the color spectum to a strait black. I have also tried a few other os's like slax, solaris, gentoo and suse. So far the only success I have had was with suse and a live demo cd of looking glass on slax with the newest display drivers for my grapics card. I think that I am having a problem the display driver. I really want to use only Ubuntu. If there is any help or advice anyone can give me it would be greatly appreciated.

---

### Post by diatribex on 2007-05-14
I have the exact same notebook (search forums for tx1000).  The ACPI/IRQ seems a little buggy.   If you use the alternate ubuntu install CD, and try the installer, it should work.  As I recall, I belive I had to try some GRUB settings, however it seems hit or miss...  doscsi noapic 

I used the 32bit version, not the 64bit.   Unless there is a need for 64bit, its not worth the trouble..

Jordan

---

### Post by farbird on 2007-05-15
> **diatribex said:**
> I have the exact same notebook (search forums for tx1000).  The ACPI/IRQ seems a little buggy.   If you use the alternate ubuntu install CD, and try the installer, it should work.  As I recall, I belive I had to try some GRUB settings, however it seems hit or miss...  doscsi noapic 

I used the 32bit version, not the 64bit.   Unless there is a need for 64bit, its not worth the trouble..

Jordan

to get into the login screen [ gui ]
try this

click escape before it boots..

edit the line which have the "uuid=xxxxxx" text..

append to the same line with these codes " noapic vga=0x317"
it should get it up to the gfx login screen.


once u get in...
nano edit your /boot/grub/menu.lst file and make the line permanent..

---

### Post by farbird on 2007-05-15
to get your wifi broadcom working, try this

sudo apt-get install bcm43xx*

sudo gedit /etc/iftab

change the interface name of the wifi interface to "wlan0"
it may be eth0 or eth1 initially [ check to ensure which is the wifi one ]

sudo gedit /etc/network/interfaces
remove all lines which make references to the old "ethx" that has been replaced above to "wlan0"

now in console, do this

sudo rmmod bcm43xx
sudo modprobe bcm43xx

this should get it working...
if the rmmod doesnt work, just reboot the laptop....

if still cannot work... post reply here

---

### Post by eduardoska on 2007-05-16
i got it working with ubuntu 64 bits it's very easy
I used any live cd (ubuntu 32/64 or Kubuntu 32/64) with Boot options in the boot screen. Then typed after the F6 in boot options

```
-- doscsi nopcmcia noapic
```

That way it should start from the live cd and everything should be ok. 

To install ubuntu, i first partitioned the disc directly from windows vista (right click my pc or equivalent and then manage. Then you go to manage discs and there you can partitionate the disc) The Gparted didn't worked for me.

---


---
title: "Lirc_gpio module workaround for gutsy failed"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by Mfvane on 2007-10-20
Hi, I am new to this forum, but I have some experience in tempering with lirc, but this time either I am blind, or it is an odd bug...
I have a Pixelview MPEG2 and it worked OK with the gpio module in feisty fawn. Since I updated to gutsy,the kernel 2.6.22 no longer supported this module. So, I configured my system in a way that it wouldn't need the lirc_gpio module, as seen in one forum.
My hardware.conf ended up like this:

LIRCD_ARGS=""
LOAD_MODULES=true
DRIVER="dev/input"
DEVICE="/dev/input/by-path/pci-0000:02:06.0--event-ir"
MODULES="lirc_dev"
LIRCD_CONF="/etc/lirc/lircd.conf"
LIRCMD_CONF=""
(I also tried putting the device with /dev/input/event4 or /dev/input/irdev, none worked"

the command cat /proc/bus/input/devices recognizes my card

I: Bus=0001 Vendor=1554 Product=4011 Version=0001
N: Name="bttv IR (card=72)"
P: Phys=pci-0000:02:06.0/ir0
S: Sysfs=/class/input/input4
U: Uniq=
H: Handlers=kbd event4
B: EV=100003
B: KEY=1000000 0 0 0 0

lircd.conf is the original supplied by lirc for this card.

dmesg :lirc_dev: IR Remote Control driver registered, at major 61

Now, when I try evtest at the /dev/input/event4, it doesn't give me no outputs... as well as when at /dev/input/irdev...
irw doesn't show any of keys I press,
I know that the RC is working because dmesg shows

bttv IR (card=72): unknown key: key=0x01 raw=0x01 down=0 
when I press a key.

When trying to run lircd -n, it gives me:
lircd: WARNING: invalid code found for PixelView_PlayTV_MPEG2: ch+
lircd: lircd(devinput) ready
lircd: caught signal

And the whole thing doesn't work. If you guys have any ideas, it would be very welcome!!
Best wishes and ubuntus for everyone!
Matheus
:)

---

### Post by Mfvane on 2007-10-21
I just fiugured out that my ir-common had been edited to disable the IR-COMMON...
I recompiled it from source and now works great!
see ya

---


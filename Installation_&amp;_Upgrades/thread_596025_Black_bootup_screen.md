---
title: "Black bootup screen"
date: 2007-10-29
forum: Installation &amp; Upgrades
---

### Post by phil46 on 2007-10-29
Hi
Just installed Gutsy;

No big issue but when the pc boots or shuts down I have a black screen, no Ubuntu logo no  code lines flashing by...

The log in screen is the first thing that appears, the PC is running smooth though, I can live with it but this is being set up for  a relation... Has anybody come accross this?

---

### Post by Tranquilo on 2007-10-29
I had the same problem. I think this might be the reason:
"Blank screen with some ATI hardware
      People with ATI display adapters may get a blank screen when loading X due to the driver being unable to initialize certain hardware. Upstream is working on it, and hopefully we'll be able to release an update for 7.10 soon after the release. In the meantime, add 'Option "LVDSBiosNativeMode" "false"' to the driver section of xorg.conf. Bug #132716"

Taken from the release notes.

---

### Post by phil46 on 2007-10-29
Thanks for your answer,
Yes I have an ATI as you guessed, 

Just checking with you here, is this what you mean, in the Device section not sure if I have the syntax correct though?

Section "Device"
	Identifier	"ATI Technologies Inc RS300M AGP [Radeon Mobility 9100IGP]"
	Driver		"ati"
	BusID		"PCI:1:5:0"
	Option		"LVDSBiosNativeMode"	 "false"


Thanks

---

### Post by phil46 on 2007-10-29
HI Tranquilo

Lot of fun here!
I tried this and still had a black screen on boot up, but then I was in safe graphics mode.
IMO its an ATI driver thing.

I dont really mind, I see that some other people have had this. I mean what is a minor thing like this compared to having to use windows! 

Long live black screens!

\\:D/

---

### Post by Tranquilo on 2007-10-30
Yeah. Definately ATI problems. 
At least it is only a minor inconvenience... ;-)
Looks like you got the syntax right, but I'm no pro...
I also cut out the quiet part in the grub menu so I could see what was happening. 
Mainly cause I was having other problems after the gutsy upgrade!

---

### Post by phil46 on 2007-10-30
> I also cut out the quiet part in the grub menu so I could see what was happening.

How do you do this?

---

### Post by orange2k on 2007-10-30
> **phil46 said:**
> Hi
Just installed Gutsy;

No big issue but when the pc boots or shuts down I have a black screen, no Ubuntu logo no  code lines flashing by...

The log in screen is the first thing that appears, the PC is running smooth though, I can live with it but this is being set up for  a relation... Has anybody come accross this?

I had the same problem, but I found a solution:

sudo gedit /etc/initramfs-tools/modules
add the following

vga16fb
fbcon
vesafb

sudo gedit /etc/modprobe.d/blacklist-framebuffer
comment out the following (add prefix #) so it would look like:

# blacklist vesafb
# blacklist vga16fb

last but not least, run the following in a terminal

sudo update-initramfs -u

---

### Post by phil46 on 2007-10-30
Nice one **orange2k**  That worked sweet for me!

Now I have to move on and get the wifi working
](*,)

---

### Post by phil46 on 2007-10-30
> I also cut out the quiet part in the grub menu so I could see what was happening. 

How do I do this?

---

### Post by orange2k on 2007-10-30
> **phil46 said:**
> How do I do this?

I think this would involve editing the ** /boot/grub/menu.lst**

Somewhere it says something like: 

```
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=2cc23d50-7bc6-4331-bcc3-0657f00a8699 ro vga=791 quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet
```

Remove "splash", and instead of seeing usplash you will be booting in text-mode...

---

### Post by phil46 on 2007-11-01
Thank you this is good for me!:)

---

### Post by gnome.youbuntoo on 2008-03-02
> **orange2k said:**
> I had the same problem, but I found a solution:

sudo gedit /etc/initramfs-tools/modules
add the following

vga16fb
fbcon
vesafb

sudo gedit /etc/modprobe.d/blacklist-framebuffer
comment out the following (add prefix #) so it would look like:

# blacklist vesafb
# blacklist vga16fb

last but not least, run the following in a terminal

sudo update-initramfs -u
where did u learn this man!!!!

---


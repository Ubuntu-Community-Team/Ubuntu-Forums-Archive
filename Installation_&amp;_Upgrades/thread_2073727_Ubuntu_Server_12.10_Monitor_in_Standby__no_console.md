---
title: "Ubuntu Server 12.10 Monitor in Standby / no console available"
date: 2012-10-20
forum: Installation &amp; Upgrades
---

### Post by mrVVoo on 2012-10-20
Yesterday I installed Ubuntu Server 12.10 on my machine (Intel Atom D2700 on its D2700MUD board with integrated graphics (should be GMA3600 or GMA 3650). After finishing install and rebooting the monitor does not get a signal and goes into standby right after choosing Ubuntu in GRUB.

[LIST]
[*]Monitor in Standby
[*]SSH available
[*]System booted "correctly" (except graphics)
[/LIST]

I already searched for that issue and found many solutions, but no one is working for me.
In general I tried changing booting params in GRUB (nomodeset, vga, nosplash, etc) and nothing worked. I also tried to use DVI instead of VGA but this didn't change anything. At least I played a bit with activating uvesafb and updating initramfs. Additional i changed boot params in GRUB to use uvesafb. After that also nothing changed except i got some kernel log information (i think this is only because of i removed the quiet option). Then i installed fbset via SSH and put it into /etc/rc.local for testing purposes and finally i got a console.

So now i know that **something is wrong with framebuffer setting but i don't know what**.
Later i modified booting params to choose a specific mode for uvesafb and then the console comes up a bit earlier but there is also some output missing (i only get information about starting tomcat and this is the last thing happening).

So even if it is working somehow (which i do not prefer because 12.10 is a stable release) I'd even like to know if this is a bug which needs to be reported or how can I fix this appropriately.

What I am wondering about: Everything worked fine on 12.04 (but i need cups 1.6 which is not available for 12.04)
Also i read this topic: [http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535) but no solution was working for me.

---

### Post by mrVVoo on 2012-10-20
Now I installed a 12.04 System in parallel to compare several settings and i discovered that 12.10 uses "gma500(_gxf)" kernel module automatically to support my graphics card, which 12.04 does not use. is there a way to disable automatic loading of gma500?

---

### Post by mrVVoo on 2012-10-20
So I fixed it on my own. The problem was that after installing 12.10 Server the gma500 driver was uses but that seems to be wrong for the GMA36xx chips.

i added to /etc/modprobe.d/blacklist.conf:
```
blacklist gma500_gfx
```
ran
```
sudo update-initramfs -u
```
after that i had to modify grub, set
```
vga=xxx (795 in my case)
```
and now everything works like on 12.04.

quiete stupid issue it would be nice if it is fixed in any future version!

---

### Post by darkod on 2012-10-20
Usually for a server you would use the latest LTS release, not the latest release. In this case that would be 12.04 LTS.

The LTS has 5 years support while the normal release has 18 months.

That's why usually for servers only the LTS is used and if you upgrade you upgrade to the next LTS after it comes out.

---

### Post by mrVVoo on 2012-10-20
that might be true, but i use  this server as home server and i need cups 1.6. i set up this server some weeks ago so there was no risk to update it because i wouldn't have lost any data.

now we know that there is kind of a bug relating to GMA36xx and the gma500 driver

---

### Post by mikewhatever on 2012-10-20
Actually, gma500_gfx is the right module, it used to be called psb_gfx in 3.2 kernel and earlier, but was later renamed to gma500_gfx. Not sure why it doesn't work in 12.10 though.

---

### Post by mrVVoo on 2012-10-20
Well i do not have the logs anymore but in 12.10 lsmod & lspci -nnk explicitly names gma500 while 12.04 doesn't show any graphics driver related content in both of them.
after excluding gma500 lspci -nnk shows gma500 only as kernel module but not as kernel driver anymore while 12.04 only prints the graphic card and the subsystem.

I'd also prefer to use 12.04 but it has no CUPS 1.6 and in CUPS 1.5.3-u4 there is a missing feature. i tried to compile 1.5.3-u4 with the additional changes by myself but i got neither an error nor the missing feature was available after that.

---

### Post by mikewhatever on 2012-10-20
So, what do you get from **lspci -nnk | grep -iA3 vga**? I wonder if it uses vesa now that gma500_gfx got blacklisted. 

Here's what it looks like with 12.04 on an old Poulsbo based netbook:
```
~$ lspci -nnk | grep -iA3 vga
00:02.0 VGA compatible controller [0300]: Intel Corporation System Controller Hub (SCH Poulsbo) Graphics Controller [8086:8108] (rev 07)
	Subsystem: Dell Device [1028:02c6]
	Kernel driver in use: gma500
	Kernel modules: psb_gfx
```

---

### Post by mrVVoo on 2012-10-20
Sorry the 12.04 system is not available anymore but neither kernel driver nor kernel modules were mentioned. There were only the first two lines.

now it looks like 

	VGA compatible controller [0300]: Intel Corporation Atom Processor D2xxx/N2xxx Integrated Graphics Controller [8086:0be2] (rev 09)
	Subsystem: Intel Corporation Device [8086:2014]
	Kernel modules: gma500_gfx

---

### Post by VaelynPhi on 2013-03-12
Running Ubuntu Server 12.04.2 on a Foxconn nT-i1200-0H0WBNA ([http://www.newegg.com/Product/Product.aspx?Item=N82E16856119067](http://www.newegg.com/Product/Product.aspx?Item=N82E16856119067)) and had no monitor output; server was accessible from SSH and there were no other issues.

Had the same issue with 12.04.1 and 12.10.

Blacklisting gma500_gfx fixed this for me.

---

### Post by MAFoElffen on 2013-03-12
Please take a breath. First, if you add this to /etc/default/grub
```

GRUB_GXFPAYLOAD_LINUX=text

```
Then update grub. This will turn off kms completely and you will get a totally text terminal. 

Or specifically turn off kms and specify what to use as a setting for a port. Add this as kernel boot parameter:
```

nomodeset video=VGA:M1024x768@60m

```
with translated means turn off modeset (nomodeset, which has to be set this way for the other to work).... Use video setting (video=) for port VGA (VGA:, which you need adjust to the port you are using)... Turn on even if not connected (M, optional, I use for KM/headless startup)... use a resolution of 1024x768 (adjust as needed),... set the Vertical Refresh to 60hz (optional, adjust as needed, default if not there is 50hz), leave a small margin (m, optional)...

I seem to have to need this on all my and most of my customer's servers since Ubuntu Server v11.10. Then I set Grub res to 1024x768 by editing the line in /etc/default/grub. 
```

# Grub Resolution
GRUB_GFXMODE=1024x768x24

# Kernel param to set a port to resolution and vertical refresh.
GRUB_CMDLINE_LINUX_DEFAULT="nomodeset video=VGA:M1024x768@60m"

```
Most server boards have ATI Rage XL GPU's as graphics, that is not supported by default until you tweak it. Most will tell you server is text based, but that is a lie in practice. Console is VGA "graphics." Yes, VT's in VGA graphics mode by default. To put into text mode, you have to change that manually.

---


---
title: "No GRUB screen displayed after upgrade to Natty"
date: 2011-04-30
forum: Installation &amp; Upgrades
---

### Post by epp on 2011-04-30
I upgraded an installation to Natty this morning and when the system is booting, when the GRUB screen should appear, my monitor (Sceptre X9G-Naga III LCD 19-inch) displays "OVER RANGE" meaning it cannot display the GRUB menu (because the video may be out of range?) and it boots into Linux automatically.

This system also has Windows Vista installed on it and because of the above, I can't boot it into Windows.

Please provide instructions for fixing this issue.  Thank you.

---

### Post by kansasnoob on 2011-04-30
This sounds like a graphics issue so please boot some live Ubuntu media and post the output of this command:

```
lspci | grep VGA
```

Also did you upgrade via the update manager or using a CD?

---

### Post by epp on 2011-04-30
It was upgraded via the Update Manager.

Xubuntu does not include Startup Manager by default, a colleague suggested to install that and check the bootloader resolution.  Although on this system and on a 32-bit laptop also upgraded to Natty, it reported the default resolution was 640x480.  The actual resolution was far from this...  On the laptop, GRUB appeared, but the text was literally too small to read.

I installed this package on both, change the default bootloader resolution to 1024x768 on both, then rebooted them.  Although what I saw after this change, does not appear to be 1024x768, the text became large enough to read and on the desktop, GRUB then appeared.

There does appear to be an initial bootloader resolution problem with the version of GRUB included with Natty.

---

### Post by Hedgehog1 on 2011-04-30
Please do this to see the grub menu at boot up again:

```
gksudo gedit /etc/default/grub
```
or - in xbuntu - **sudo nano /etc/default/grub**

[COLOR="Red"]and change this line:[/COLOR]

#GRUB_GFXMODE=640x480

[COLOR="red"]to this:[/COLOR]

GRUB_GFXMODE=640x480

[COLOR="red"]Then save and exit the document.[/COLOR]


Then do:

```
sudo update-grub
```


***The Hedge***

:KS

---

### Post by MAFoElffen on 2011-04-30
> **epp said:**
> I upgraded an installation to Natty this morning and when the system is booting, when the GRUB screen should appear, my monitor (Sceptre X9G-Naga III LCD 19-inch) displays "OVER RANGE" meaning it cannot display the GRUB menu (because the video may be out of range?) and it boots into Linux automatically.

This system also has Windows Vista installed on it and because of the above, I can't boot it into Windows.

Please provide instructions for fixing this issue.  Thank you.
On "out of range" errors, please see this sticky:
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

Hope it helps.

---

### Post by MAFoElffen on 2011-04-30
> **Hedgehog1 said:**
> Please do this to see the grub menu at boot up again:

```
#GRUB_GFXMODE=640x480
[COLOR=red]to this:[/COLOR]
GRUB_GFXMODE=640x480
[COLOR=red]Then save and exit the document.[/COLOR]
Then do:
[code]sudo update-grub
```
Sometimes...

Important-- Add another parameter to that.  GFXMODE=640x480 is WIDTHxHEIGHT, when the GFXMODE parameter is actually WIDTHxHEIGTHxDEPTH... Meaning, if you leave it that, without the color depth parm, it will try each depth until it finds one that doesn't return an error code <> hoping that it hasn't locked up before that error code is returned. A "wrong" color depth will go out of range and leave a blank screen.

So, 640 by 480 resolution with 16bit color would be GFXMODE-640x480x16

---

### Post by RobertoRecordo on 2011-07-11
> **Hedgehog1 said:**
> Please do this to see the grub menu at boot up again:

<snip>
[COLOR=Red] change this line:[/COLOR]

#GRUB_GFXMODE=640x480

[COLOR=red]to this:[/COLOR]

GRUB_GFXMODE=640x480



This fixed my problem of really small text - now the grub screen look like it did in Lucid.

Thanks, I'm a noob and was lost.

---


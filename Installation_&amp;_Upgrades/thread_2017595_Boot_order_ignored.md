---
title: "Boot order ignored"
date: 2012-07-05
forum: Installation &amp; Upgrades
---

### Post by Musicmaker384 on 2012-07-05
I'm trying to install Ubuntu (or, at this point, any distro) on my old HP Pavilion a305w. I had it installed with Wubi before (that was two years ago), but now I want a true installation, and I'm running into a problem. I can't boot from the cd. There are four boot options: Removable drives, CD-ROM drive, Hard Drive, and Network Boot. CD-ROM is set to first priority, but all the computer wants to do is boot into Windows XP, which I'm trying to get rid of. I know the CD drive is plugged in because its LED is lit when I insert a CD. I know my Live CDs are burnt correctly because I've used them on other computers. On that note, I've tried all my Live CDs - Ubuntu (12.04), Zorin OS, and Linux Mint - and still nothing. I've done multiple Google searches, none of which are of any help. I've tried everything I know how, and nothing's worked.

The bios version I have is: PhoenixBIOS Core Version 4.06, revision 3.24 (10/14/2003). The OS currently installed is Microsoft Windows XP Home Edition 64-bit.

I'd really appreciate any helpful advice. I really don't know what to do.

I'm in the bios right now, and if you need any more information, I can get it quickly.

---

### Post by jmfal on 2012-07-05
At the bios/setup screen, select boot menu, from there select your DVD-CD drive, and see if that works.

---

### Post by Musicmaker384 on 2012-07-05
Yes, I forgot to mention that I already tried selecting CD-ROM from the boot menu. It only boots into Windows.

---

### Post by rukiaEnix on 2012-07-05
Could something be wrong with the CD? It could even if the LED is on.

Can you try making a boot usb?

---

### Post by QIII on 2012-07-05
Sorry to ask this, but sometimes it's the simple, frustrating face-palm things...

Did you burn the installation disks as ISO images?

---

### Post by sammiev on 2012-07-05
> **QIII said:**
> Sorry to ask this, but sometimes it's the simple, frustrating face-palm things...

Did you burn the installation disks as ISO images?

+1 seen this too many times before. Burn it as a boot able ISO. :)

---

### Post by ajgreeny on 2012-07-05
> **sammiev said:**
> +1 seen this too many times before. Burn it as a boot able ISO. :)
My original thought too, but come on folks, read the OP!

He has used the CD already on other machines, so the CD burn must be good enough to boot.

---

### Post by Musicmaker384 on 2012-07-05
> **QIII said:**
> Sorry to ask this, but sometimes it's the simple, frustrating face-palm things...

Did you burn the installation disks as ISO images?

Yes, I did. All three of them were, at one point, installed on my laptop, and I can go into a Live CD environment on any of them (on the laptop).

---

### Post by Musicmaker384 on 2012-07-05
I'll try using a USB stick. Perhaps that falls into the 'removable devices' category. I know that works, because I tried to use the Windows recovery floppies at one point. One had a corrupt .sys, so they're all useless, but that's beside the point.

EDIT: Ubuntu won't boot from a USB stick either.

If it'd be of any help, I can post photos of my bios screen (or any screen for that matter), for someone with a keen eye to figure out what the problem is.

---

### Post by Musicmaker384 on 2012-07-06
Bump, because I still need help with this.

---

### Post by rukiaEnix on 2012-07-09
Please post the photos of the error using boot from usb.

---

### Post by efflandt on 2012-07-09
One thing that is not clear is whether you are only setting boot order in BIOS, or are you pressing the hot key during BIOS splash screen to specifically select the boot device for that boot?  That hotkey is often F12, but might be something else.

With Dell computers particularly boot order in CMOS setup seems to be somewhat ignored for removable devices, unless you always boot from that device.  That may be as protection from accidentally booting something potentially malicious on CD/DVD or USB.  The only virus I ever caught (long ago) was spread by accidentally booting an infected floppy.

---


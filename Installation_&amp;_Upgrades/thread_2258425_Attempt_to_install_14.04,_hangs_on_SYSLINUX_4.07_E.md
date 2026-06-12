---
title: "Attempt to install 14.04, hangs on SYSLINUX 4.07 EDD etc"
date: 2014-12-27
forum: Installation &amp; Upgrades
---

### Post by Athena's Owl on 2014-12-27
Hello, I am trying to install Ubuntu on an Acer Aspire One 725-0826.

I have crunchbang on the machine currently but I can't seem to figure out how to update programs with it.  I thought, "This could be easier with Ubuntu."

Well, as usual I'm running into problems. I made a USB boot stick.

I see the Acer splash screen and then I see 

Syslinux 4.07 EDD 2013-07-25 Copyright (C) 1994-2013 H. Peeter Anvin et al

and it does nothing. 

I really don't know how to solve this problem. I tried reading earlier posts but I have no purple screen with a keyboard on it, so I can't press any key and then mess around with something called nomodeset(?)

I made the pen drive with Universal USB Installer, if that's useful to know.

---

### Post by MAFoElffen on 2014-12-27
did your dp an mdchecksum on the image to make sure it's all there/not corrupted?

Video = AMD Radeon HD 6290

You were on the right track with your post comments. When the Live image is booting, start hitting the <esc> key and see if you get that initial dark purple tinged panel w/ the keyboard/human icon and use the instructions you had looked up...

For yours, at the advanced install menu > <F6> > select anything (meaning nomodeset would be okay) > Press <esc>... but from there, once you see that linux boot line appear under the menu, take your cursor keys and go to the end of that and replace "nomodeset" with "radeon.modeset=0"

That would be the correct boot option for yours (with any current version of Linux) until after you install. Once installed, you are going to have to add that temp to your grub menu Linux boot line... until you get your video drivers loaded for that card.

Of course, there is still an old-school fall-back workaround on those SELinux LiveCD Images... If you can get the advance menu to appear, if at that panel, you hit <esc> a few times, it will try to probe the graphics for a known Vesa mode. If the data returned from that probe is not recognised, it will drop to a text screen, tewlling you there was a problem with graphics, asking you if you would like to continue in VGA graphics, presentation of what VGA mode to select... Then will continue in a VGA palette installer. This still works for many SELinux based installer disks as their fall-back.

---

### Post by Athena's Owl on 2014-12-27
Thank you so much for your reply.

I see *something* when I try pressing escape, but it's not purple, and it's gone in an instant. i've tried a few times but it just blinks, and then another screen blinks long enough for me to read "serial ata" and then i'm back to the obstinate page.

---

### Post by MAFoElffen on 2014-12-27
# Did you verify that it was a good downloaded image? (i didn't see that answer yet...)

---

### Post by Athena's Owl on 2014-12-27
oh! sorry. Yes, I compared the MD5sum and it was the same.

---

### Post by MAFoElffen on 2014-12-27
Have you tried to make a bootable USB with Unetbootin? Have had better luck with that, than pen linux. (just personal preference)

---

### Post by Athena's Owl on 2014-12-27
I tried, but I get the same thing only 4.03 of syslinux copyright 2010. 

I tried with the pressing escape but the screens don't stay for more than a blink.

---


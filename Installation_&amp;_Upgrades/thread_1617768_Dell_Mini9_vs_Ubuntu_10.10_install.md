---
title: "Dell Mini9 vs Ubuntu 10.10 install"
date: 2010-11-09
forum: Installation &amp; Upgrades
---

### Post by Solostian on 2010-11-09
Please have mercy on this poor noob.

Followed all the steps to install the Netbook Edition.
Boot up on Live USB worked great, install went thru without a hitch
Changed the BIOS settings to boot on the SSD HD.

Unfortunately, after th BIOS splash screen, all I get is a blinking cursor on the upper-left corner of the screen.

I suspect my SSD is starting to fail. 
Any idea on how I can fix/circumvent this?

Cheers,
Solostian

---

### Post by sikander3786 on 2010-11-10
Hi and welcome to the forums :popcorn:

Are you sure it is not a problem with Grub?

Please post the output of bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

It would help us better understand your current situation and thus help you accordingly. Please wrap the output with proper code tags # from the post menu.

Secondly, you can test your SSD by downloading the diagnostic tools from the manufacturer's website.

BTW, did you remove the USB drive before attempting to boot from the SSD? And are you sure the boot order is correct in Bios?

Rather than Grub, I feel it is a problem with the Bios boot order. Please re-check.

---

### Post by Solostian on 2010-11-12
Looks like the problem was with the MBR.
I reinstalled Windows XP (with full HD format).
Then, instead of Ubuntu Netbook, I installed Ubuntu Desktop 10.10.

That issue is since resolved.

Cheers


Note: I found out that Ext2 is a better choice for SSD HDs.

---


---
title: "Installing Hardy on a Fujitsu Siemens V5535"
date: 2008-07-25
forum: Installation &amp; Upgrades
---

### Post by The_Hop_Picker on 2008-07-25
I have had Ubuntu successfully installed on a desktop for some time but I have now obtained a Fujitsu Siemens V5535 laptop but I cannot install Ubuntu Hardy on it.  Using the desktop I have downloaded the alternate iso image, checked the md5sum and then 'written to disk'.

When trying to install I have selected 'Install Ubuntu' from the first menu (after selecting language), the kernel boots, the screen goes blank for a few seconds then I get a series of horizontal multi-coloured lines running up the screen. There is some text interspersed with the lines but I can't read it.

Can anyone help?  Should I be modifying the boot parameters?

Incidently I did try to install Gutsy on the laptop with the same result but I could install Linux Mint Celina.:confused:

---

### Post by dstew on 2008-07-25
I have seen a number of posts that say that the graphics driver that comes with Ubuntu does not operate well in this computer. There are some things you can do to try to work around it.

You can try kernel parameters. I am not sure about the alternate install CD, but for the Live CD you press F6 at the first menu. Then, I think you select the kernel line and edit it by putting a kernel parameter at the end. You can try the parameters **vesa=force** or **vga=791**. See [this post]("http://www.knoppix.net/forum/viewtopic.php?p=36777") for other vga codes. Plain 640x480, 256 colors is vga=769. Since the menu is plain vga, that might get things to work.

The other option is to see if there is a BIOS setting that makes the display act better. Sometimes, if you disable advanced display features, the Linux kernel and driver will work better.

If you can get the system installed, you can try to use a restricted driver to make the display work properly. The things I mention here are only to get the installation CD to work.

---

### Post by The_Hop_Picker on 2008-07-29
The reason I was using an 'alternate' cd was because when I tried to load 'fiesty' on my desktop sometime ago it kept freezing - so I have used an 'alternate' cd ever since.

Following your reply to my post I decided to have a go at using a 'live' cd and low and behold it worked like a charm.

To prove the point I did another succcessful re-install using the 'alternate' cd by adding 'vga=769' to the boot script as you suggested.

In both cases the resolution was limited to '800x600' but I was able to sort this by adding

Section "Monitor"
  HorizSync  28-72
  VertRefresh 43-60

to the xorg.conf file.  This resulted in '1200x768' and 1024x768' being available.

Thanks for taking the trouble to answer my post.

PS  Now let's see if I can sort out the networking bit

---


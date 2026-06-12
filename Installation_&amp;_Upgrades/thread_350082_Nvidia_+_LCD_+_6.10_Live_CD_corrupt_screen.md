---
title: "Nvidia + LCD + 6.10 Live CD corrupt screen"
date: 2007-01-31
forum: Installation &amp; Upgrades
---

### Post by Khaz on 2007-01-31
Hi;

Was looking at the Bugs list for 6.10

Apparantly there's a known bug on the Live CD release (as of today, January 31, 2007 - "ubuntu-6.10-desktop-i386.iso") regarding Safe Boot and problems that arise with all sorts of video cards.

Here are some screenshots. Screenshot 4 is after trying to boot into safe mode, booting using the "VGA" menu option at 800x600x32/640x480x16 and also using the "fix" vga=771 for "laptop display corruption". Various degrees of corruption, all complete messes and unusable.

1. Selecting safe mode
[IMG]http://kylezwarich.ca/images/linux/linux-pos-Bin.01.jpg[/IMG]

2. safe mode loads
[IMG]http://kylezwarich.ca/images/linux/linux-pos-Bin.01-2.jpg[/IMG]

3. Signal cannot be processed by monitor (out of range error); obviously corrupt output for a "safe mode"?
[IMG]http://kylezwarich.ca/images/linux/linux-pos-Bin.01-3.jpg[/IMG]

4. Attempting to run standard mode, with vga=771 added to command line, also different VGA modes result in different colors! Whee!
[IMG]http://kylezwarich.ca/images/linux/linux-pos-Bin.01-4.jpg[/IMG]

Obviously this is unacceptable seeing as I've now coastered a CD and wasted 700MB of time/bandwidth.

How can one expect to gain new users when glaring errors like this prevent Testing or even Basic install of your distribution? :( 

Of course, I attempted the only options available on the HELP included with the disc. I'm obviously not a power user but was looking forward to trying a Linux distro. Now, I'm not so sure.

Computer specs:
AMD athlon 64 3000+
ASUS a8nsli premium
Nvidia 6800 GS
1gig ram
m-audio audiophile 2496
flatron L1950S by LG

And all this after being a known bug for months. As far as 6.06 release stands, there are reports that the Safe Mode actually works. AT Least let new users KNOW that your newest release is unstable and NOT RECOMMENDED FOR NEW USERS. Thank you.

K. Zwarich

---


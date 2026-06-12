---
title: "Blank screen after bootup"
date: 2010-02-28
forum: Installation &amp; Upgrades
---

### Post by KTOmega on 2010-02-28
So, I got this old Toshiba Satellite 1800-100 laptop recently. Out of instinct, I nuked the existing XP partition to install Ubuntu 9.10 using the Alternate CD, in fear that the real CD was too much for it.

So, the installation went fine. I had to redo it only one time because of a power error. After installing, I booted into Ubuntu only to be greeted by a black screen for minutes on end after Ubuntu finished booting up. I tried some LiveCDs to see if it just wasn't my installation of Ubuntu. Out of the 4 I tested, only 2 worked: System Rescue CD and Knoppix. The Ubuntu and Parted Magic live CDs didn't work, however.

I have been dealing with this problem for 4 days with no solution so far. Here is a list of everything I've tried so far:
[LIST]
[*]Ctrl + Alt + FnX
[*]Reinstalling
[*]Diagnose X
[*]Fiddle with xorg.conf
[*]Use another distro
[*]Try to get the wireless card to work in order to use apt
[/LIST]

I have just finished trying to get the Fedora Core 12 Live CD to work with no success. And so, I gave up and resorted to posting here.

These are my specs:
[LIST]
[*]800 MHz Celeron (Coppermine)
[*]Video card: Trident Microsystems CyberBlade/i1 (rev 5d)
[*]256 MB RAM
[*]15 GB HDD
[*]11" LCD Monitor (max resolution 1024x768 )
[*]Wireless card via CardBus (don't know how to work with iwconfig with my ndiswrapper'd card)
[/LIST]

I have attached my lspci and Xorg log. My dmesg output is located [here]("http://pastebin.com/yVyUqiPx").

Thanks in advance.

(I just realized that this would fit better in the Hardware & Laptops section)

---

### Post by lloyd_b on 2010-02-28
You are well below the "recommended" amount of RAM for running Ubuntu (for 9.10, it recommends 384MB, while you only have 256MB).

Have you considered trying Xubuntu?  It uses the XFCE desktop, rather than Gnome, and supports much lower spec machines than regular Ubuntu.

Are you getting the Grub menu at startup?  If so, try booting into Recovery Mode, then choose "Normal Boot".  This will boot you into a command-line system.  From there, try running "startx" to start up the GUI, and see if gives you any error messages (I didn't see anything in your Xorg log that would indicate a problem).

Lloyd B.

---

### Post by KTOmega on 2010-03-01
Hm, I'll look into Xubuntu. I was planning on installing a lighter window system like FVWM-Crystal/IceWM if GNOME was too much for the laptop to handle anyway.

If I go into Recovery Mode via GRUB and execute "startx", it just spits out a bunch of lines to me for a split second and then the screen turns fully black. After forcing a restart, /var/log/Xorg.0.log has nothing in it.

If I remember correctly, the last line I saw on the lines it spat at me was something like "Log file: "/var/log/Xorg.0.log", ...".

---

### Post by PavelMan on 2010-03-27
I had it working. Then, after another upgrade and swapping an IDE DVD with another one (the old piece died).

Booting gives a black screen. I can do "recovery mode" and then I get the prompt. Startx immediately gives me the black screen.

Everything else seems to be working fine ;-). I can do ssh to my box, the web server is up, etc. Something is wrong with video drivers when GUI starts. Monitor just goes into a "sleep mode", as if there is no signal at all.

Do you remember how you solved your problem? Last time I had to deal with this problem was too long ago, and I do not remember how to set those default drivers, instead of nVidia's....

---


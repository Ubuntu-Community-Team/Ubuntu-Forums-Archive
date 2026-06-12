---
title: "Dell 700m"
date: 2005-11-04
forum: Installation &amp; Upgrades
---

### Post by amartin on 2005-11-04
Just recently purchased a dell 700m and wondering if others have tried Ubuntu 5.10?

Specs:
Intel® Pentium® M Processor 735 1.7GHz
Intel® PRO/Wireless 2200 B/G

Thanks.

---

### Post by audax321 on 2005-11-04
I haven't had a problem with the Pentium M for either of my Inspiron 9300 or my HP DV1000. Also, the DV1000 has a 2200 B/G which works great. I did have one problem with the connection dropping but I fixed it and you can read about that here: [http://www.ubuntuforums.org/showthread.php?t=75612](http://www.ubuntuforums.org/showthread.php?t=75612)

The solution was posted by xMetaRidley a little bit down the page.

---

### Post by Sheco on 2005-11-04
[QUOTE=audax321]I haven't had a problem with the Pentium M for either of my Inspiron 9300 or my HP DV1000. Also, the DV1000 has a 2200 B/G which works great. I did have one problem with the connection dropping but I fixed it and you can read about that here: [http://www.ubuntuforums.org/showthread.php?t=75612](http://www.ubuntuforums.org/showthread.php?t=75612)

The solution was posted by xMetaRidley a little bit down the page.[/QUOTE]

Hey, audax, I also have an Inspiron 9300, with 1GB Ram, 256MB NVidia GeForce go 6800, and I cannot resume the laptop when it goes to suspend, it suspends but when I turn it back on, it just stays black, can't switch using Control+alt+f7 or anything, the laptop is frozen, I've tried lots of things, even booting passing init=/bin/sh to the kernel and it's the same, do you, or does anybody here know if I can fix this? i've read about people beeing able to suspend their inspiron 9300. (by the way I only added 900MB of swap space, is that a problem?)

---

### Post by audax321 on 2005-11-04
Unfortunately, I've never gotten suspend to work on either of the laptops. I'd look into the Inspiron 9300 further, but I gave it to my sister when she moved like two days ago since she needed a computer. All I have is the HP with me right now, and I know it doesn't work on there... last time I tried it X kept crashing so I just turn the laptop off when I don't need it.

Take a look at this: [http://www.rtr.ca/dell_i9300/](http://www.rtr.ca/dell_i9300/)
If you scroll down past the table there are two sections called: 

# Suspend-to-RAM works!
and
# Suspend-to-Disk (aka. "software suspend") works!

They have some directions that might work out for you.

---

### Post by go2dell on 2005-11-05
I just installed Breezy on my friend's 700m and all basically went well.  Some of my experiences were:

[LIST]
[*]suspend works, but leaves the battery meter and wireless networking monitor in an unusable state on resume (didn't attempt to fix yet, as the owner doesn't understand the point of suspend);
[*]hibernate, oddly enough, works perfectly (using a 686 Ubuntu-provided kernel) but will probably never be used because the owner doesn't understand why she would ever use it;
[*]haven't tried external displays, either monitor or TV, but simply installing the "855resolution" thingy made the screen look sharper than I've ever seen it under Windows or Linux... and the installer had already detected the correct oddball resolution for xorg.conf, so only one config file to edit -- Ubuntu basically took the internal display to the quality it should really have;
[*]laptop mode, including detection of on-battery or on-ac, works beautifully, and is reasonably agressive about power savings, and seems to be fairly accurate about estimated battery runtime;
[*]"blue-function" (Fn key) combos work correctly, including sound (with a cool onscreen indicator), brightness, CD/DVD eject, and suspend (careful!);
[*]forget the SD-card reader, but AFAIK there's absolutely no support for it in Linux, period, so it's not Ubuntu's fault.
[/LIST]

I made a brave, zen-like attempt at getting the Intel wireless drivers running, and managed to successfully install them, but connection was spotty, at best.  I only had success using the very latest versions, which may simply be buggy, or it may have been my new-to-Ubuntu ignorance at fault. :rolleyes: 

Just for a lark, I decided to install using OEM mode, and I can report happiness there, as well.  If you're installing Ubuntu for others and want to give them that warm, fuzzy, "nobody's ever touched my computer but me" feeling they would have gotten with Windows, fire up OEM mode and have at it.

The 700m in question was previously running an older edition of SUSE, and my friend never seemed to be able to figure out how to do anything in it, plus it never really supported the laptop's features quite as well as I thought it should.  SUSE also had some bizarre quirks with wireless and display that I never could quite track down.  I decided to let my friend try Ubuntu mainly because it seemed much easier to use and lacked that 800-pound-gorilla-bearing-a-Swiss-army-knife approach that SUSE seems to love.  I must say I'm quite impressed at just how well Ubuntu works out of the box.

---


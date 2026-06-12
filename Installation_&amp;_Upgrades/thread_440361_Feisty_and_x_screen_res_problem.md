---
title: "Feisty and x screen res problem"
date: 2007-05-11
forum: Installation &amp; Upgrades
---

### Post by barry.rhodes@uklidian.com on 2007-05-11
This is a repeat post that I made yesterday but didn't get any responses.

I have a Dell Inspiron 8000 with Ubuntu 7.04 installed. 

lspci reports my video card as (taken verbatim from lspci)...

01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility M4 AGP

which is correct as far as I know.

But my screen is always in 800x600 or 640x 480, they are the only options I get in Gnome.

Now my xorg.conf file looks like this (just screen res bits shown) ....

Section "Device"
        Identifier      "Generic Video Card"
        Driver          "vesa"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Generic Video Card"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1600x1200" "1400x1050" "1280x1024" "1024x768" "
800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1600x1200" "1400x1050" "1280x1024" "1024x768" "
800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1600x1200" "1400x1050" "1280x1024" "1024x768" "
800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1600x1200" "1400x1050" "1280x1024" "1024x768" "
800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1600x1200" "1400x1050" "1280x1024" "1024x768" "
800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1600x1200" "1400x1050" "1280x1024" "1024x768" "
800x600" "640x480"

FYI I added all the resolutions in xconf.org higher than 800x600. I've also put this at the end ....

Section "Extensions"
        Option "Composite" "0"
EndSection

I've tried the process at 

[http://wiki.cchtml.com/index.php/Ubu...allation_Guide](http://wiki.cchtml.com/index.php/Ubu...allation_Guide)

It seemd to go well but doesn't actually change my xconf.org or give me any change in res.

I just can't work it out. Can someone help as I've now run out of options after 3 nights looking at this. The ATI M4 card is about 4 years old but surely it's still supported! I'm puzzled as to why vesa is listed in xorg.conf. 

Also if I try and use the restricted driver manager utility, the only driver listed in there is ...

Ateros Hardware Acces Layer (HAL)

which is shown as in use, though it makes no difference if I disable it - weird! Surely there should be more than 1 driver.

HEEEELP!!!!!

---

### Post by heimo on 2007-05-11
Have you tried changing vesa to ati?

---

### Post by barry.rhodes@uklidian.com on 2007-05-11
I tried changing it to fglrx and it screwed up my X and I had to go back to an old config and vesa - I'll just quickly try ati in xorg.conf .....

---

### Post by barry.rhodes@uklidian.com on 2007-05-11
Interesting, here's what happened...

I changed vesa to ati. then relogged into x (gnome) and got a much higher res password log in screen. I logged as a user to gnome and was put in 1280 mode. Problem was there was a jumping screen, I could see the layout but it was fuzzy and split screen. I hooked up my external monitor to the graphics port, did a Fn CRT/LCD (F8) to bring in crt and lcd together and I got a good 1280 screen. Used the graphics res tool in Gnome to take this to 1400 no problem. 

Then logged out and now I'm back in 800x600 with no option to get any higher - but xorg.conf still has ati instead of vesa. 

Does this make sense?

---

### Post by heimo on 2007-05-11
> **barry.rhodes@uklidian.com said:**
> Does this make sense?

I'd either run sudo dpkg-reconfigure xserver-xorg using these instructions:
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

Or try to setup HorizSync and VertRefresh according to laptop / monitor specifications:
[HOWTO: Solving resolution/refresh rate problems in Xorg]("http://www.ubuntuforums.org/showthread.php?t=83973")

---

### Post by barry.rhodes@uklidian.com on 2007-05-11
Thanks I've already tried the first one before with no success but I'll try again. The second one I've never tried and may explain why I get hi res when a crt is hooked up ( at the same time as I display on crt) I get the proper res with good stable image.

I'll try them both.

Hopefully that'll do it.

---

### Post by barry.rhodes@uklidian.com on 2007-05-11
Heimo

it works with no monitor attached at 1400 both in the login screen and after a reboot. Thanks a lot. I had to manually input the montor frequencies and that was it. So summary is, add ati to xorg,conf instead of vesa and add monitor frequencies.

Thanks a lot, now I can get on with using this system

regards

Barry

---

### Post by heimo on 2007-05-11
> **barry.rhodes@uklidian.com said:**
> Thanks a lot, now I can get on with using this system

Excellent, glad to hear you got it fixed. As father of Free Software would say: Happy Hacking!

:)

---


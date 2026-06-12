---
title: "Problem with keyboard after installation"
date: 2005-10-13
forum: Installation &amp; Upgrades
---

### Post by olivas on 2005-10-13
The install looked like everything went well.  After it rebooted
the keyboard doesn't work.  Pressing some letters does nothing.
Pressing some keys cause the wrong letter to appear.  I'm kinda
stuck here because I can't login.  Not even in safe mode.

Just for good measure I went through the installation again
and tested my keyboard ("American English") just to make sure.
Same result.

Any ideas?
Thanks,
Alex.

---

### Post by luckyaba on 2005-10-13
is it a usb/wireless keyboard?

---

### Post by olivas on 2005-10-13
Nope.  The keyboard that's integrated into the laptop.
Alex.

---

### Post by luckyaba on 2005-10-13
I'm guessing its the keyboard layout. can you uuse it in the command line?

you could try dpkg-reconfigure xserver-xorg

just pay attention to the keyboard section

---

### Post by olivas on 2005-10-13
That was my guess too.  I've been playing with it a bit
without much luck.  From a terminal I get the same behavior.
So I'm not able to run dpkg-reconfigure.  I'm pretty much
limited to what I can do with a mouse.

I'm using the live cd now since I couldn't log in before.
Again I tried the installation twice with the same results
as I'm getting from the live cd.  During the second installation
I took the time to test the keyboard during that part of
the installation, just to mak sure we were on the same page.
Everything looked good until the reboot.
Alex.

---

### Post by luckyaba on 2005-10-13
then i think you'll have to manually go in and edit the xorg.conf to use the correct layout for your keyboard. 

what kinda of laptop is it?

---

### Post by olivas on 2005-10-13
It's a Fujitsu N Series 3010.

I have used this with other flavors of linux.  FC1, FC3, gentoo
(but I have other issues with gentoo).

Any ideas on how to do that without using the keyboard?
I can't configure the networking either without the keyboard
so won't be able to scp any files into it.

---

### Post by Tomy on 2005-10-13
[quote=olivas]It's a Fujitsu N Series 3010.

I have used this with other flavors of linux.  FC1, FC3, gentoo
(but I have other issues with gentoo).

Any ideas on how to do that without using the keyboard?
I can't configure the networking either without the keyboard
so won't be able to scp any files into it.[/quote] 
You could try to copy/paste into /etc/X11/xorg.conf. Here is my keyboard section:

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "keyboard"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc104"
#       Option          "XkbLayout"     "dvorak"

From a terminal I switch from dvorak to qwerty with these commands:
$ loadkeys dvorak
$ loadkeys us

So, in theory, **loadkeys us  **in a terminal would set your keyboard to the default english qwerty layout.

Sounds pretty strange -- I doubt this will help. good luck

Tomy

ps The above stuff is from Hoary, it should be the same in Breezy.

---

### Post by olivas on 2005-10-14
I can't log in without the keyboard so editing my
xorg.conf is going to be a bit tough.  I can't switch
to any consoles so have no idea whether the keyboard
would work there.  I think I'm just going to give gentoo
another shot.  Thanks for your help.
Alex.

---

### Post by deshda on 2005-10-18
I also have a fujitsu N series with the same problem.  After installing, on the initial boot the keyboard works fine, on rebooting the keyboard no longer works.  When you push most of the keys you get no response, some of the numbers and F keys will give a response but the wrong character.  I've thought it is the keyboard layout but it's hard to tell since I can't log in to troubleshoot it.

---

### Post by artships on 2005-10-18
Happened with my USB keyboard, too, when I upgraded from Hoary.  Ended-up booting off the livecd, copying a few files to a fat32 partition, then installing breezy from disk.  Can you boot a networked computer with a livecd, then ssh into your laptop?

---

### Post by xbaez on 2005-10-20
Hello. I upgraded to Breezy at work and at my office. At my office the upgrade was done mainly with the Ubuntu & Kubuntu CDs, plus the Breezy repositories. At my house it was basically done with the CDs only, plus a own burned DVD with all the updated *.deb from /var/cache/apt/

The problem is that Breezy is running well on my laptop, but on my office, whenever I press something at the keyboard, all I see are squares

I will try to tweak the xorg.conf file, it's a standard PS2 keyboard.

Does anybody knows why does this happens?
this is the same xorg.conf file that was working with Hoary

---

### Post by xbaez on 2005-10-21
"The Shuttleworth Foundation brings risk capital to the non-profit education world. It funds innovative projects in education with an annual budget of $3m... Send us your ideas!"

I hope to find something cooler while I do some reading .. ;)
that means Canonical has founds folks
We're not some geeks using a distro-to-disappear

---

### Post by caleb9 on 2008-03-20
Check if you have num-lock on :).

---


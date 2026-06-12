---
title: "Problem with GDM on boot"
date: 2006-06-04
forum: Installation &amp; Upgrades
---

### Post by carletml on 2006-06-04
After booting, I get  a message stating that GMD is not configured properley. I am new to linux and i am at a loss of what to do.

---

### Post by skelooth on 2006-06-04
I've been using linux for over 2 years and am having the same problem and have no idea how to fix it. I made a topic about it (I'll link to it)... no one has been able to help so far... but I get the same exact problem...

---

### Post by llamakc on 2006-06-04
So you're at a commandline prompt? Login as the user you created during the install and type verbatim:

sudo dpkg-reconfigure gdm

Then type:

sudo /etc/init.d/gdm start

If it does NOT start, write back here and we'll check out your error logs and hardware. For starters are you on a laptop or using a newish ATI/NVIDIA card?

---

### Post by skelooth on 2006-06-04
that's not the problem llamakc...

[http://ubuntuforums.org/showthread.php?t=188943](http://ubuntuforums.org/showthread.php?t=188943) 

here's my topic.

It doesn't run the GDM theme, it says there is an error in the configuration file and it gives you the default login dialog. It "works" but with an error.

---

### Post by llamakc on 2006-06-04
I'll look at your thread. I was addressing the OP though.

---

### Post by skelooth on 2006-06-04
Doesn't matter who you were dressing, it's the same exact problem

---

### Post by carletml on 2006-06-04
[QUOTE=llamakc]So you're at a commandline prompt? Login as the user you created during the install and type verbatim:

sudo dpkg-reconfigure gdm

Then type:

sudo /etc/init.d/gdm start

If it does NOT start, write back here and we'll check out your error logs and hardware. For starters are you on a laptop or using a newish ATI/NVIDIA card?[/QUOTE]

I just tried that, after sudo dpkg-reconfigure gdm, the error message i was recieving blinks a few times on the screen then stops. after the second command it displays starting gnome display message but does nothing further.  I have an ATI X800XL video card.

---

### Post by llamakc on 2006-06-04
No, it is not necessarily so. That error is spit out for a variety of reasons.

---

### Post by llamakc on 2006-06-04
Is the package xorg-driver-fglrx installed?

---

### Post by carletml on 2006-06-04
[QUOTE=llamakc]Is the package xorg-driver-fglrx installed?[/QUOTE]

how do i check that?

---

### Post by llamakc on 2006-06-04
If you are using Synaptic to manage packages you run Synaptic and do a search for fglrx. If it is installed you'll see it with a green-filled box in the listing of packages (plus plenty others). THis is if you're not using a high-contrast theme btw.

Or, from the command line you can see if it is installed with:

sudo dpkg -l | grep fglrx

When I do that I get:

ken@vulva:~$ dpkg -l | grep fglrx
ii  fglrx-control                          8.25.18+2.6.15.11-1 Control panel for the ATI graphics accelerat
ii  xorg-driver-fglrx                      7.0.0-8.25.18+2.6.15.11-1 Video driver for ATI graphics accelerators

---

### Post by carletml on 2006-06-04
i get nothing when i enter that

---

### Post by llamakc on 2006-06-04
Is this a clean install of Dapper? Are you upgrading from Debian or an earlier release of Ubuntu? Are you installing over an existing, previous Linux distribution? Do you or have you used custom GDM themes you snagged off of the 'net?

You could install the package xbase-clients from the commandline:

CTRL-ALT-F1 and login with your username/password

sudo apt-get install xbase-clients

and then as that user run from the commandline:

startx

When it fails you may be able to discern more of the problem.

GDM sounds like it won't start because X isn't configured properly. If you're able to show us your /etc/X11/xorg.conf that'd be helpful.

---

### Post by carletml on 2006-06-04
this is a new install of dapper

---

### Post by llamakc on 2006-06-04
Thanks. So the problem is that X isn't starting. Now how about some specs on the hardware?

---

### Post by carletml on 2006-06-04
ATI Radeon x800 xl 256mb agp (showing as PCIe in description, not sure if that matters) with athlon 64 3500+ and asus motherboard with via chipset.

---

### Post by llamakc on 2006-06-04
IF you're comfortable with the commandline:

sudo apt-get install xorg-driver-fglrx

---

### Post by carletml on 2006-06-04
[QUOTE=llamakc]IF you're comfortable with the commandline:

sudo apt-get install xorg-driver-fglrx[/QUOTE]

just finished with that. now what?

---

### Post by carletml on 2006-06-04
it seems i have solved the proplem, with your help of course, the vga drive i was using did not suport the color depth i had set, so i changed it to 8 for now until i get the right drivers. thx for your help

---

### Post by llamakc on 2006-06-04
Well now you can reconfigure the xserver with:

sudo dpkg-reconfigure xserver-xorg and all should be well.

---

### Post by shirizaan on 2006-06-10
I'm really new to Ubuntu, and Linux in general, so forgive me if this is a poorly formed question.  I had this same problem and downloading the FireGL drivers resolved my issue.

Its not as if ATI is an uncommon card, so why wouldn't these drivers be included on the install CD?

---


---
title: "unable to install ubuntu, help needed"
date: 2007-11-12
forum: Installation &amp; Upgrades
---

### Post by LuFaXX on 2007-11-12
Hi, i am trying to install ubuntu on my HP Pavilion TX1150ea laptop but i keep coming to the same problem.

i restart with the live cd and i tell it to install, but before the cd loads me into its desktop i get a white screen, which then turns red and finally black (it looks like somebody pressing down on an LCD screen).

I have tried ubuntu 7.10 32 bit, then the 64 bit version (as i have a 64 bit processor) and then ubuntu 7.04 -- all with the same problem - all the cds were burnt at very low speeds.
(i also tried installing through wubi, but kept getting errors after i restarted)

Ubuntu works fine in VMWARE through windows.

i have read through the forums and i am stuck, with no idea what to do nex.
thanks in advance.

the spec of my laptop is:
[B]AMD Turion 64 X2 Dual Core TL-60
1.8GHz HyperTransport, 1MB Cache
2048MB RAM
160GB Hard Drive
Dual Layer DVD ReWriter MultiDrive
12.1" HD Brightview Touchscreen
128MB nVidia GeForce GO 6150 Graphics[/B]

---

### Post by kellemes on 2007-11-12
Maybe you should try the alternative disk (just tick the checkbox at the downloadpage)
You may need to configure your videocard to get it going.. so maybe you shouldn't investigate that beforehand..

---

### Post by LuFaXX on 2007-11-12
thanks :) it worked and i now have gutsy installed.

however, when i boot into ubuntu i get the loading screen with the orange bar, then it loads and gives me a white screen.

i know it may be because of my graphics card, but how can i resolve this when im unable to boot into ubuntu?

thanks

---

### Post by GepettoBR on 2007-11-12
There should be a way to fix this via the LiveCD, I think. If not, maybe someone can help you with instructions to configure your nVidia card through a command-line boot (which I don't expect to turn your screen white like the GNOME boot). Unfortunately I'm CLI-illiterate so I can't help you with that part.

---

### Post by LuFaXX on 2007-11-12
hey, the trouble with the live cd is that it wont work on this laptop, it just gives me a white screen.

if anybody could help me with the cli that would be great!

thanks

---

### Post by LuFaXX on 2007-11-12
anyone?

---

### Post by confused57 on 2007-11-13
You could try booting into Recovery mode...then try:
```
dpkg-reconfigure xserver-xorg
```

Select "No" at the first screen to autodetect, then you can probably go with the default values for everything except the video driver...try selecting "vesa" driver.  Once reconfiguration is complete, enter "reboot", without quotes, at the root prompt.  Hopefully this will give you a functioning GUI.

---

### Post by LuFaXX on 2007-11-13
hey, thanks for your advice.

however when i try and boot into recovery mode it hangs...

it displays lots of text as it boots until it gets to something like "..TIMER:..."

and just hangs there.

any ideas?

---

### Post by GepettoBR on 2007-11-13
this is really basic, but no one brought it up so there's no harm in asking: did you check the CD for errors?

---

### Post by LuFaXX on 2007-11-13
yeah i checked the cds, i burnt 4 different ones lol, a 32 bit one, a 64 bit one, then ubuntu 7.04 and then 7.10 alternate.

i checked all of them but all the live cds gave me the white screen, then alternate one let me install but ubuntu gives me the white screen as it boots into the gui, and i hear NO sound either.

i think i need some advice in configuring my graphics card in command line...?

---

### Post by GepettoBR on 2007-11-13
> **LuFaXX said:**
> yeah i checked the cds, i burnt 4 different ones lol, a 32 bit one, a 64 bit one, then ubuntu 7.04 and then 7.10 alternate.

i checked all of them but all the live cds gave me the white screen, then alternate one let me install but ubuntu gives me the white screen as it boots into the gui, and i hear NO sound either.

i think i need some advice in configuring my graphics card in command line...?

I meant using the option "check this CD for errors" instead of trying to boot - since from what you said the white screen is just after the boot. If you can't do that, check the MD5 checksum from your ISO against the one on the server to make sure the file didn't corrupt on the way.

---

### Post by LuFaXX on 2007-11-13
hey, yeah sorry thats what i did to check the cds, they were fine.
i also checked the checksum and thats fine too.

arrrrggghh! haha

---

### Post by LuFaXX on 2007-11-15
still no luck guys. i may just try a different version of linux?

hmmm?

---

### Post by benbelly on 2007-11-15
In the past, when I've had a white screen (feisty), I resolved it by downloading the latest proprietary drivers direct from nVidia or ATI (I had the problem with both kinds of cards).  The proprietary drivers provided by through the repos didn't work, for whatever reason.

  I suggest downloading the drivers from the manufacturer and installing them manually.  Watch out though - you need to keep the install package in your account because various software updates will mess up your video, and you'll need to reinstall.

---


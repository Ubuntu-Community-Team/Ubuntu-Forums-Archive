---
title: "How long until the next distro?"
date: 2008-01-23
forum: Installation &amp; Upgrades
---

### Post by Rice_slayer on 2008-01-23
About roughly how long until the next distro of Ubuntu is released? 7.10 doesn't support my 8800GT and the only way to get it working AND installed is to use this driver and it makes the fan on it go to its highest RPM, which is really noisy/hard on the card. I really hope that the new distro comes out soon, I hate just having vista...

---

### Post by Lostincyberspace on 2008-01-23
get envy search for it on google the newest version of the driver there should be all you need.

---

### Post by Rice_slayer on 2008-01-23
Does this new driver make the fan spin at high rpms? I also cant get 7.10 installed because of this setting thing, I do try the low graphic thing and it still hangs at this point where there is a command line...

---

### Post by Whiffle on 2008-01-23
[http://www.nvidia.com/object/linux_display_ia32_169.09.html](http://www.nvidia.com/object/linux_display_ia32_169.09.html)

Looks like the bug is fixed, you just need to get the driver installed.

---

### Post by Rice_slayer on 2008-01-23
Thats good to know, but how Do i install it? It doesnt get past this part with a command line... this is after I have told it to do the install in low graphics mode.

---

### Post by Whiffle on 2008-01-23
Well, if it were me doing it, I'd probably do the 10 steps to nvidia bliss

1) uninstall anything nvidia related that you already have,  
2) install the build-essential package, 
3) log out,  
4) hit ctrl+alt+F2, 
5) login to that terminal
6) do sudo /etc/init.d/gdm stop
7) then do chmod +x NVIDIAblahblah.run,
8)  then sudo sh NVIDIAblablah.run.  
9) It should install it, then you can do /etc/init.d/gdm start, and 
10) hopefully it will work.  

Keep in mind though, if you ever upgrade kernels, you'll have to do it over again.  Also, there may be some compilation dependencies  that I don't remember, you'll have to install those.  aptitude would be handy for that.  Also, I'm rather old fashioned, there may be an ubuntu approved way out there that i don't know about, so you might do some searching.

---

### Post by Rice_slayer on 2008-01-23
K thanks for the help! I'll TRY again later tonight after some gaming with a friend to see if i can get it installed again. Again thanks for the help!

---


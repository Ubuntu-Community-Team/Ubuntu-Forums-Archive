---
title: "Sony Vaio Picturebook"
date: 2008-01-14
forum: Installation &amp; Upgrades
---

### Post by chrome101 on 2008-01-14
I got my hands on a sony vaio picturebook (pcg-c1vfk) a while back from a friend who had no use for it.
It came with Win2k but he had forgotten the password.

With no cd-rom drive i've had to constantly remove the harddrive to reinstall the operating system using my toshiba. Win2k keeps failing even when I changed the original 15GB harddrive for a 60GB one. 

I have tried other distros, but I really want ubuntu on it. I dug out an old copy of ubuntu 6.06 and the install was ok until... error message on xserver. I have spent the last two weeks searching the web. I did get it to work though but was only limited to 640x480 resolution. 

Ive edited using: *sudo dpkg-reconfigure xserver-xorg*, but that hasnt worked or I end up screwing the display:confused:

There doesn't seem to be anywhere with the spec for the screen (unless i go old skool and use a ruler) or the correct drivers. All I would like is if someone could post a copy of the 'xorg.conf' file... or let me know where I could get a copy that I could edit... 

Thanks in advance

---

### Post by Pumalite on 2008-01-14
What are your specs?

---

### Post by chrome101 on 2008-01-15
Sony Vaio Model: pcg-c1vfk(gb)
8.9-inch wide-screen- graphic card/ driver unknown
memory: 111mb (+16mb for CMS)
Bios: R0213P1

Apart from that I really cannot tell you more...

---

### Post by Pumalite on 2008-01-15
You have little RAM, but you could try Feisty here:
[https://help.ubuntu.com/community/Installation/Netboot](https://help.ubuntu.com/community/Installation/Netboot)

---

### Post by chrome101 on 2008-01-15
I just mamgaed to reconfigure the xserver so I can get a 640x480 display  and checked the device manager. It reports the display device as 'ATI Rage Mobility p/m'.

I have thought about Feisty, but its the constant taking out and replacing the hdd thats becoming a bore.

Will check the link that you've provided and see if that works.

---

### Post by Pumalite on 2008-01-15
With ATI, you'll have to reconfigure your xserver at the end anyway. (maybe not; ATI Radeon 9200 SE is Ok with Feisty, but integrated graphics is another story.)

---

### Post by chrome101 on 2008-01-16
Puma, I installed feisty on the vaio. had to set the graphics, which wasnt a problem, but still getting only 640x480 resolution. I tried to use envy but that didnt work. 

The wireless worked fine... With a bit more memory and the graphics sorted this could be a nice little toy.

---

### Post by Pumalite on 2008-01-16
Good for you. Good luck!

---

### Post by chrome101 on 2008-01-16
Thanks... Using it right now:)

---


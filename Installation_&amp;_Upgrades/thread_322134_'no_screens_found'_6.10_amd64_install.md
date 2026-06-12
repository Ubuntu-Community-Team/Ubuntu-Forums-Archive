---
title: "'no screens found' 6.10 amd64 install"
date: 2006-12-20
forum: Installation &amp; Upgrades
---

### Post by sapoleon on 2006-12-20
Hi, I'm new to linux and ubuntu, well, I have used a little of suse linux, but a long time ago, and not in a very persistent mode. 
I was recently introduce to ubuntu, and wanted to try it. 
The thing is, that I made the installation of the 6.10 amd64 (took me a long time to get that to install it to the HD, i need the alternate install), and when it reboot, I get a 'no screen found' error from the xserver.
I look in the posts, but it only talks of the problem in th 6.06 version with the xserver 1.0.3_ubuntu10 version, and i checked mine, and it is the 1.1.1_ubuntu12 version. 
So, how should I do to get out of this problem?

My HW:

amd64 +3000
motherboard Asus with socket 939
video card, Asus Ati Radeon x700 256Mb
monitor Sony HS95 (19")

I'll thank any help, and, if i didn't post this in the right place, also let me know so I can move the post.

Thanks

---

### Post by dinub1 on 2006-12-20
Hi,
Does it log into text mode or PC is competely stuck? I guess if you get the X server error "no display found" you can at least log into text mde. This is generally related to ATI graphics cards. I have a similar one on my main machine and it does the same. Ubuntu has problems configuring ATI graphic card expecially newer models or/and PCI-E types. On a terminal or at the prompt try typing:
$ sudo dpkg-reconfigure xserver-xorg.

It will start a routine to try to reconfigure Xorg to recognize your video hardware. Soetimes it works soemtimes it does not. It will re write a new /etc/X11/xorg.cong file. After routine ends and reports back up copy saved try rebooting. Hope this helps. If not there is still the darn ATI cards problem under Linux.

---

### Post by dinub1 on 2006-12-20
BTW I am using the same ATI Radeon X700, 256 MB RAM card on my machine that does not load Ubuntu... too bad. same Ubuntu loads and runs perfectly on a similar machine but having an nVidia AGP card. So it seems that it is related to the video card type. ATI cards work very well under Windows XP, but are known to have problems with Linux.

---

### Post by sapoleon on 2006-12-20
hi, thanks

i have allready try the 
$ sudo dpkg-reconfigure xserver-xorg.

but without success. and in my case and now, changing the videocard, is not an $$ option .

i hope someone have another answer :)

---


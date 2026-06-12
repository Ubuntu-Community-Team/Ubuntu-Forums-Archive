---
title: "Odd.. Cant log in"
date: 2006-02-22
forum: Installation &amp; Upgrades
---

### Post by OkydOky on 2006-02-22
I've tried re-instaling it many times: Regular 32-Bit and 64-Bit version.
The install works fine. Then on 1st Login, right after I type in User / Password

The "Unbuntu" Image, in middle of screen is all messed up. It's all distorted.
And it simply sits there. Also If on log screen I click languages, it hangs there, with the new window that just poped up all distorted aswell.

Nothing Happens..

I am Running this on:
DFI Lanparty UT NF4-D 
AMD Athlon x2 4200+
1gb (2x512) Dual Channel Mushkin DDR Ram
250Gb SATA Seagate Drive (Windows partition, data partition, rest for linux)

---

### Post by Jason_25 on 2006-02-22
Nvidia video card?  If so, you'll need to ctrl-alt-F1 at the garbled screen and then login. Then 
 
```

sudo nano /etc/X11/xorg.conf

```
 and change the driver line from nv to vesa. Then ctrl-O, hit enter, then ctrl-z and reboot (or restart gdm). That should get you started. You'll want to load the nvidia driver after you've gotten into the GUI.

---

### Post by OkydOky on 2006-02-22
Yea, Nvidia Card - forgot GPU in Sys specs.. haha..
It's a Geforce 7800 GT.

This is my 1st REAL linux install, that I intend to use on a regular basis.
(Have tried a few times on my older comps (Dedian mostly) but never done much with it.)

So I may come back and ask a few newbish questions..

Thanks so far! ;)

EDIT: Here comes 1st lil' Question:
Should I Run the Regular (32Bit) or 64Bit version? -- I plan on Doing some gaming with it with Wine (Once I figure out how to use it) or Cedega. Watch DivX Movies, Music, ect.. quite a bit of Multi Tasking.

---


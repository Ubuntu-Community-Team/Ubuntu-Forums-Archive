---
title: "Upgrade error on TX2Z 10.4 to 10.10"
date: 2010-10-14
forum: Installation &amp; Upgrades
---

### Post by adrian.ccs on 2010-10-14
Hi everybody

I had Lucid Lynx 64 bit running pretty well on my HP tx2z (everything worked) I saw unity and other cool stuff of 10.10 and I decided to make a run for it. When I updated it I found the following problems.

1 first on the first boot it took me to terminal (already solved), 2 It doesn't recognize my touchscreen.
3 I get disorted menus (they go diagonally)
4  but not so important I guess i get an error at boot up of MMIO and im asked briefly to login which fades away in a few seconds.

Thanks in advance and I'm open to suggestions!!

---

### Post by sewright22 on 2010-10-21
I upgraded from 10.04 64bit and I am having similar issues. 
1. My touchscreen only works with my pen. If I touch the screen with my finger the computer freezes  about 10 seconds later.
2. I also get the MMIO region error during boot.

---

### Post by Favux on 2010-10-21
Hi sewright22,

Welcome to Ubuntu forums!

Hi also to adrian.ccs,

It depends on the N-trig firmware you have installed.  Also it looks like Ubuntu inadvertently left out code to report single finger touch in the hid-ntrig.ko if you are using older firmware.

Ayuthia is working on it.  He has patched the hid-ntrig.ko to report single finger and is working on a dkms version of it.  See his [post # 1255]("http://ubuntuforums.org/showpost.php?p=10007171&postcount=1255") on the N-trig HOW TO.  Posts going back to the previous page discuss things.

---

### Post by sewright22 on 2010-10-25
So, would I be able to just upgrade the N-trig firmware? If so, how would I do that?

---

### Post by fa225909 on 2010-11-03
Hello world !

I have the same problem of touchscreen not working in 10.10...

I also noticed compiz doesn't work well anymore 

Someone have a simple solution ? thank you everyone.

---

### Post by Favux on 2010-11-03
Hi fa225909,

If you're not able to update the firmware; to fix single finger touch see Maverick b) in the [N-trig HOW TO]("http://ubuntuforums.org/showpost.php?p=7863677&postcount=1").

---


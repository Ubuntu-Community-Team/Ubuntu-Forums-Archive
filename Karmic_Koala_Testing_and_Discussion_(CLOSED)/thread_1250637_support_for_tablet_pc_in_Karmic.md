---
title: "support for tablet pc in Karmic?"
date: 2009-08-26
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by R3fr4cti0n on 2009-08-26
will there be any i still cant get this damn computer running properly ?

---

### Post by coldReactive on 2009-08-26
> **R3fr4cti0n said:**
> will there be any i still cant get this damn computer running properly ?

What model and manufacturer is it?

---

### Post by R3fr4cti0n on 2009-08-26
hp touchsmart tx2, ive followed the instructions to get this **** to work on jaunty like 10x but the touch makes the cursor go to the top left corner and no auto magic rotation. i love ubuntu but i bought this pc for its features

---

### Post by R3fr4cti0n on 2009-08-26
bump

---

### Post by overdrank on 2009-08-26
Moved to Karmic Koala Testing and Discussion

---

### Post by vishalrao on 2009-08-27
You can help out, see [lpbug]317094[/lpbug]

---

### Post by leech on 2009-08-27
I have the same touch tablet, and while I had Jaunty on it and working somewhat, I wanted to see if I could get the multitouch working and that requires 2.6.30 at least.  So I installed Debian Sid on it.  Touch screen, and rotation works (though I don't have the button that is supposed to do rotation working).

But there are other things that don't work yet, like the multitouch itself.  Not to mention it is rather cool in Windows 7 that things like firefox work out of the box with it.  I can touch the screen and have it scroll up/down, zoom in and out, etc.  Would absolutely LOVE to not run Windows on it at all, and since it's not really for gaming, I could probably do so if I could get all the multitouch stuff working (after all, that's why I bought it!)

Oddly I see requests for the next version of openSUSE to support tablet PCs better as well.

But I think this thread is titled incorrectly.  Tablet PC and Touch Screen are two different things entirely.  The HP Touchsmart TX2 happens to be both.

I'm hoping with Karmic Koala using 2.6.31 kernel, most of the touch screen stuff will work without too much messing around.

But if you have been running Win7 on the TX2, you'll probably be aware that the n-trig drivers stink right now.  Not to mention that when you have a problem, then you re-install the firmware, it changes what pci path it uses, so you have to reconfigure xorg.conf.

Anyhow, just some thoughts.  I have been thinking of installing Karmic again on my Touchsmart, but I have been waiting for an FGLRX driver that works with 2.6.31.

---

### Post by Ayuthia on 2009-08-27
The only real difference between Karmic and Jaunty is that the hid-ntrig.c file exists in the kernel so the device is recognized.  However, it is missing one patch for that file so we will most likely need to make a patched hid-ntrig.ko file instead of creating an entire kernel.

The linuxwacom code also does not have the N-Trig patch so that will need to be done.  If you use the most recent version of the linuxwacom code, there are some additional steps that will need to be done to make it compile.

Overall, I think the configuration for Karmic might be easier than Jaunty.

---

### Post by zoomy942 on 2009-08-27
um - my tablet PC works great.  100%

---

### Post by _dF on 2009-10-14
I'm trying to get hp tx2-1250 works on OpenSUSE 11.1. The base kernel is 2.6.27 : it do not work for touch. So I've installed a 2.6.31 kernel from HEAD OpenSuSE repository : everything is working, except the TPCButton ...
So I've tried to compile the hid-ntrig.ko, BUT this kernel has buitin hid-ntrig in the kernel : no way to change it without recompiling the whole kernel.
Is there any way to get all work with the existing hid-ntrig builtin in the kernel ? (2.6.31)

---

### Post by R3fr4cti0n on 2009-10-15
talk to favux. he's the king

---

### Post by Ayuthia on 2009-10-15
> **_dF said:**
> I'm trying to get hp tx2-1250 works on OpenSUSE 11.1. The base kernel is 2.6.27 : it do not work for touch. So I've installed a 2.6.31 kernel from HEAD OpenSuSE repository : everything is working, except the TPCButton ...
So I've tried to compile the hid-ntrig.ko, BUT this kernel has buitin hid-ntrig in the kernel : no way to change it without recompiling the whole kernel.
Is there any way to get all work with the existing hid-ntrig builtin in the kernel ? (2.6.31)

As far as I know, there is no other way.  The hid-ntrig source is the code that reports the button.

By the way, I saw your post in the from the linux-input mailing list about the three buttons.  So far, only the middle button reports on mine (the fancy "m" button for the Touchsmart media).  The other two buttons have not been found yet.  I have the tx2-1025dx.

---

### Post by _dF on 2009-10-23
Thanks, Ayuthia. Since my first post, I've configured everything and wrote an Howto for OpenSuSe ( [http://en.opensuse.org/SDB:Howto_install_OpenSuSE_on_HP_tx2-xxxx_laptops](http://en.opensuse.org/SDB:Howto_install_OpenSuSE_on_HP_tx2-xxxx_laptops) )  which could help under Ubuntu too. I've also wrote bug reports to get hid-ntrig.c integrated in opensuse kernels.

We still need also a proper integration of "1b96" in linuxwacom : we certainly needs to participate to the linuxwacom project to get it integrated. Don't forget that the owner of linuxwacom project on sourceforge is employed by wacom : perhaps that's the reason why the patche isn't still integrated ? 

I also wrote to the author of the hid_ntrig.c, and therefore I was probably the first to run Linux with the last linuxwacom and therefore with a perfect touch on a tx2 (previous linuxwacom didn't worked so well). As you can have seen, it's still too tricky for newbies, just by the lack of two small changes in the kernel (proper hid-ntrig.c) and in linuxwacom (Vendor/product 1b96:0001). That are very small changes.

Every community effort to get this 2 small changes integrated in new kernels and in linuxwacom would help greatly.

If you are aware enough of bug reporting, patches, and open-source projects, please help by all the ways.

And for developers : please notice that the last linuxwacom-dev release began to integrate multitouch support with the new BTN_TRIPLE_TAP events and the "Gesture" Option for xorg.conf : now, the hid-ntrig.c should be extended to take advantage of this very new linuxwacom feature.

---

### Post by flipper9 on 2009-10-23
If I install one of those touch-screen kits from ebay onto my Asus Eee PC 1000h, will I get those multi-touch and touch-screen features in Karmic?

---


---
title: "4870 + Ubuntu = one blind mess...."
date: 2008-10-05
forum: Installation &amp; Upgrades
---

### Post by kDDs on 2008-10-05
I decided to give ubuntu another whirl on my main desktop PC today, which has the newest ATI 4870 card in. Great, I thought, I can even play a few games!

But no. When trying to boot from the live CD it would flicker, monitors say no signal etc. So I installed from the "alternate" CD. But now, when I try and fire it up, it doesn't work, same problem as before. I know the ATI drivers are a piece of SHITE but honestly, were they tested at all?

Anyway, I can get to recovery mode, although I'm not 100% sure if I have any kind of internet, so any suggestions will have to take that into account. I do have a 1gb memory stick handy though.

I've searched around loads, but haven't found anything specific to this.... I also heard that ATI 4xxx series weren't supported (after I installed, of course...), but do they not work AT ALL? 

I've tried using the commands "startx" from the safe mode, but, of course, that flickers out, I can end it with "killx" aswell.

Also, I'm a bit of a n00b, so please be patient.

---

### Post by kDDs on 2008-10-07
No one else EVER had this problem? =/

---

### Post by Neo_The_User on 2008-10-07
OK first off, ATI owns with Linux. Its a very strange problem. I'd never use any other GPU for Ubuntu.  When you boot up from the LiveCD (normal desktop) wait 60 - 120 seconds. Don't expect it to detect your display in a second. I had the same problem. If you still have problems, try using a different monitor. After you install ubuntu with the different screen, go to the ati driver website and download the drivers. Don't install them or anything. Plug in the other monitor after its downloaded. if it cant detect it, restart your computer. I'll give you detailed instructions on updating the graphics accelerator along with the driver installation afterwards.

If you just type in sh (driver here) into the Terminal, you won't get the most out of your card because the old out of date accelerators will still be in use. Anyway, I hope this helps.

---

### Post by kDDs on 2008-10-08
Ok, it does, kind of.

I've downloaded the ATI drivers, and put them on a memory stick, so, is it possible to navigate to the memory stick and then run the xxx.run file? If so, how would I naviagte to it through safe mode?

---

### Post by kDDs on 2008-10-08
Fixed it!

Here's how!

Installed ex2ifs, so I could read the ubuntu partition in windowz.
Downloaded the ATI driver, and placed it in the ubuntu partition/ root/ folder.
Went into safe mode, and ran the command:

> 
sh driver.run

(I called it driver to make it simple)

Went through a few configurations, and that was it! It's now working 100% 

Soo... if anyone else gets this prob, then this is the easiest solution!

---

### Post by Jeanpaul145 on 2008-10-13
> **kDDs said:**
> Fixed it!

Here's how!

Installed ex2ifs, so I could read the ubuntu partition in windowz.
Downloaded the ATI driver, and placed it in the ubuntu partition/ root/ folder.
Went into safe mode, and ran the command:



(I called it driver to make it simple)

Went through a few configurations, and that was it! It's now working 100% 

Soo... if anyone else gets this prob, then this is the easiest solution!

That's one way to get the driver to your Ext3 partition :)

Here's another: you don't actually have to copy it from windwos.
If you're in recovery mode, you actually can mount an usb disk (assuming Ubuntu doesn't do it for you in recovery mode), and here's how:

```

sudo mount /dev/sdb1 /media/usbdisk

```

This assumes that the partition of your usb disk is seen as */dev/sdb1* and that you have a directory in */media* calles *usbdisk*. At least this method has always worked for me.

To unmount, just do

```

sudo umount /media/usbdisk

```

Yes, this says umount, not unmount ;)

Sidenote: the *sudo* isn't needed if you're already root. I just put it there for good measure.

---

### Post by showcaser on 2008-10-14
I know you solved your problem but am just curious. You mentioned 'monitors', are you running a dual monitor setup? Did you try booting the Live CD with one of the monitors unplugged (not just off but the DVI or VGA unplugged).

First time I installed Ubuntu (edgy) I pulled my hair out over this. Now it's a little better. Hardy or Intrepid LiveCD (and fresh install) results in one monitor going crazy but the other one is fine. I'm running an nvidia card though.

---

### Post by kDDs on 2008-10-28
Nah, it was a single monitor. I tried it on my 22" (1680x1050) and 15" (1024x768.) and neither worked. =/

Hopefully issues like this are fixed in ibex, but oh well, I sold the dan card now anyway :D

---


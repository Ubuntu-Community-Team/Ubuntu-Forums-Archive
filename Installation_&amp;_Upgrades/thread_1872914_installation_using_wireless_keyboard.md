---
title: "installation using wireless keyboard"
date: 2011-10-31
forum: Installation &amp; Upgrades
---

### Post by waynewoodman on 2011-10-31
I attempted to install Ubuntu on my windows pc. I use a wireless combo keyboard & mouse. I could not install because the keyboard was not recognized.
I have a Logitech MK710 set that works flawlessly on windows. However, when attempting to install I get as far as needing the keyboard and that's it.
I would like to try Ubuntu again but?

---

### Post by Paddy Landau on 2011-10-31
When you install Ubuntu, it will probably download the required drivers (ensure you are connected to the Internet when you install).

However, that does not solve your problem in the meantime.

Go to your computer's BIOS and enable the "legacy" mode for USB. That way, the BIOS will enable to the wireless keyboard before it even gets to Windows or Ubuntu. Hmm... if the legacy mode is disabled, you will be unable to get to your BIOS unless you borrow a wired keyboard!

If the legacy mode is already enabled, then sorry, I don't know what is going on.

---

### Post by waynewoodman on 2011-10-31
Hi Paddy,
I was using a cd to install? But I will check on the legacy mode.
Thanks.

---

### Post by Paddy Landau on 2011-11-01
> **waynewoodman said:**
> I was using a cd to install? But I will check on the legacy mode.
Legacy mode for USB simply means that the BIOS will intercept and translate the incoming data. (Your wireless keyboard & mouse are connected to the computer via USB, yes?)

Without legacy USB mode, the BIOS ignores the devices, and so they will work only once your OS has started up.

---

### Post by waynewoodman on 2011-11-02
Hi,
 
Yes the Legacy mode is enabled but it still does not recognize the keyboard or mouse. I guess I will have to pick up a wired set to try it?
Wayne

---

### Post by Paddy Landau on 2011-11-02
I'm sorry, Wayne, it seems so. I do not understand why your Ubuntu does not see your mouse and keyboard.

---

### Post by awsome4 on 2012-03-25
Hi
Mine is the same problem. I downloaded the Ubantu 11.10 to a DVD [Varified after the download], &
put in my computer that has bluetooth wireless keyboard & mouse. [I wanted to try from a DVD not to install on my computer]
 
It takes me to the Ubantu screen that has the Language to choose and to if want to run from the CD or install. I am unable to to get my keyboard or mouse recognised on the screen. My computer remain connected to broadband internetwhile I attempt to do the above. [Broadband speed is about 6mb/sec]
 
However I am able to install my XP MCE, Vista and Win 7 of all flavours on the same computer with the wireless keyboard & Mouse.
 
Does any-body know of a solution?
Regards

---

### Post by Mark Phelps on 2012-03-26
Bluetooth and Wireless, while they accomplish similar functions, are not the same thing.

Wireless keyboards and mice connect to the host PC using USB devices, which in nearly all cases, results in them being seen even when an OS is not yet running.

Bluetooth uses very different drivers; however, if is enabled in your BIOS, your keyboard and mouse SHOULD be seen.

Since they are not, you will probably have to resort to using wired keyboard and mouse to get Ubuntu installed.  After that, when you then activate the mouse and keyboard, Ubuntu should see them and download and install the proper drivers.

---


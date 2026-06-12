---
title: "Intel 82945G/GZ cant go over 800x600"
date: 2009-10-03
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by shadysamir on 2009-10-03
From both the live CD boot and after upgrade, Karmic Koala Beta does not offer a resolution above 800x600. I have an integrated Intel 82945G/GZ display and an acer AL1916W LCD which is detected as "unknown".

---

### Post by dentaku65 on 2009-10-03
> **shadysamir said:**
> From both the live CD boot and after upgrade, Karmic Koala Beta does not offer a resolution above 800x600. I have an integrated Intel 82945G/GZ display and an acer AL1916W LCD which is detected as "unknown".

Try to boot with nomodeset option in grub.

1) At the grub menu choose e (edit) in the kernel line that you want to boot
2) Move at the splash option, and write nomedeset after splash option
3) ctrl-x to boot

---

### Post by VMC on 2009-10-03
Sounds like Ubuntu selected the "vesa" driver. In lue of nomodeset I use the older [Intel-2.4.1]("https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4") driver and it works great.

---

### Post by shadysamir on 2009-10-03
> **dentaku65 said:**
> Try to boot with nomodeset option in grub.

1) At the grub menu choose e (edit) in the kernel line that you want to boot
2) Move at the splash option, and write nomedeset after splash option
3) ctrl-x to boot

nomodeset did not solve the problem. same result

---

### Post by shadysamir on 2009-10-03
> **VMC said:**
> Sounds like Ubuntu selected the "vesa" driver. In lue of nomodeset I use the older [Intel-2.4.1]("https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4") driver and it works great.


Wouldn't I end up losing the new driver's performance boost this way?

---

### Post by zevans on 2009-10-03
> **shadysamir said:**
> Wouldn't I end up losing the new driver's performance boost this way?

Yes, there's no need to go back to 2.4.1, that's overkill. 

Could be worth a formal bug report to launchpad, I think the Intel team have the impression Intel now works out of the box with Karmic... so if you have a repeatable problem they'll want to know.

---

### Post by dentaku65 on 2009-10-03
> **shadysamir said:**
> nomodeset did not solve the problem. same result

Try to install xorg-edgers driver
[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

On the same repo install ppa-purge too, in case you have to remove the xorg-edgers package
```
sudo ppa-purge xorg-edgers
```
to switch back to the official Karmic.

I have an intel and I use them.

---

### Post by shadysamir on 2009-10-04
> **dentaku65 said:**
> Try to install xorg-edgers driver

I will try that when I go back home and tell you. Thanks

---

### Post by shadysamir on 2009-10-04
> **zevans said:**
> 
Could be worth a formal bug report to launchpad, I think the Intel team have the impression Intel now works out of the box with Karmic... so if you have a repeatable problem they'll want to know.

I tried to "report a problem" from the installation with no luck. Any idea how I can report the bug directly on the website?

---

### Post by shadysamir on 2009-10-05
> **dentaku65 said:**
> Try to install xorg-edgers driver

This did not work out either! Still Monitor unknown and only 640x480 and 800x600 are the two choices there

I also found a new problem that I wasnt aware of. I set display to turn off after a set amount of time in power management. The computer never wakes up from that. I have to manually reset.

---

### Post by zevans on 2009-10-07
From the sticky thread in this forum:

"To report a bug in the default desktop applications, use the "Help > Report a Problem" menu item. Where this is not applicable, use the "ubuntu-bug" command line bug reporting tool. You can invoke it by pressing Alt+F2 to open the "Run Application" window, or starting a terminal emulator, and typing

ubuntu-bug package_name

and pressing "Enter", where package_name is the name of the package you want to report a bug in.

If you have trouble finding the right package to report the bug in, take a look at the Bugs/FindRightPackage page on the wiki. If that doesn't help, feel free to start a thread to ask for assistance."

Your package name is probably xserver-xorg-video-intel because I would guess it is not reading screen capabilities correctly.

Just to check: Can you post the contents of your /etc/X11/xorg.conf here? THere may be something in there from your previous release which is preventing the new automatic stuff from working.

---

### Post by VMC on 2009-10-07
What fixed Intel video i865 for me was installing **both** kernel-12 AND intel-2.9.0 driver. It now works perfectly!
Edit: I see no [reference]("http://lists.freedesktop.org/archives/xorg/2009-September/047439.html") to i945 though. Still kernel-12 may fix you problem.

---

### Post by zevans on 2009-10-08
> **VMC said:**
> What fixed Intel video i865 for me was installing **both** kernel-12 AND intel-2.9.0 driver. It now works perfectly!
Edit: I see no [reference]("http://lists.freedesktop.org/archives/xorg/2009-September/047439.html") to i945 though. Still kernel-12 may fix you problem.

There's probably no mention in your link because i945 problems were largely fixed in 2.6.99.some driver and 2.6.29 kernel. In other words, you missed out on the fix for the last few months because you went down to 2.4 instead of up to unreleased 2.6, but that's life on the cutting edge huh?

---

### Post by VMC on 2009-10-08
> **zevans said:**
> There's probably no mention in your link because i945 problems were largely fixed in 2.6.99.some driver and 2.6.29 kernel. In other words, you missed out on the fix for the last few months because you went down to 2.4 instead of up to unreleased 2.6, but that's life on the cutting edge huh?

Actually after each and every intel driver update I tried them out only to have them fail. So I went back to 2.4.1 and then a new driver would come along and I would try that as well. Nothing work until the aforementioned combination of kernel-12, intel-2.9.0.

---

### Post by frustphil on 2009-10-10
I hope this will be fixed before the release. I am pushing aside ubuntu for now after 2yrs of use. This is the only time my screen resolution is messed up. I don't want to go back to Jaunty either...

---


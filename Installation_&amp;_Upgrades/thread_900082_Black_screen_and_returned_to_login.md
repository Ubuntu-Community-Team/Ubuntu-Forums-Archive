---
title: "Black screen and returned to login"
date: 2008-08-25
forum: Installation &amp; Upgrades
---

### Post by IGLAW on 2008-08-25
I downloaded and burned the installer and set up Ubuntu in Windows XP and when I tried to log in the screen blacked out then flickered with a little green before returning me to the login prompt. So then I tried installing it outside of Windows on a partition, same thing. So *then* I saved all my crap on my external hard drive, formatted my computer, and installed it on its own. Same ******* thing.

In the boot demo I can get a little farther; the account automatically logs in after 10 seconds and everything's peachy but when I try to open the folder on the desktop the black screen goes up again and I'm back at the login screen.

Anybody know what my problem is?

---

### Post by maddog39 on 2008-08-25
Could you provide some more information such as the kind of hardware you're running and such? Also did you check the disk for defects to see if anything you installed may have been corrupted during the burn process. Im betting that its either that or a video issue.

---

### Post by IGLAW on 2008-08-25
It's probably not a burn problem because I not only burned it twice, I deleted it the first time so the second was a clean download completely separate from the first.

As for my hardware... is there a web gadget that can check that for me? I'm not incredibly hardware savvy so I'd be more comfortable letting the computer tell you.

---

### Post by finlost on 2008-08-25
Go to a Terminal

> sudo lshw -html > hardware.html

This will create a html document in your personal folder, named hardware.html.

---

### Post by IGLAW on 2008-08-25
> **finlost said:**
> Go to a Terminal



This will create a html document in your personal folder, named hardware.html.

Sorry, what do I do with that?

---

### Post by finlost on 2008-08-25
After running the terminal command, check your personal folder for a document called *hardware.html*.  Double click it.  It will open in your web browser giving you your hardware specs.

---

### Post by IGLAW on 2008-08-25
[http://www.xfire.com/profile/#game_rig](http://www.xfire.com/profile/#game_rig)

There, I used Xfire to get my specs.

I'll actually be getting a Sapphire Radeon HD 3650 on Monday, if you think the video card's the problem.

---

### Post by IGLAW on 2008-08-25
> **finlost said:**
> After running the terminal command, check your personal folder for a document called *hardware.html*.  Double click it.  It will open in your web browser giving you your hardware specs.

I meant what do I do with the "sudo lshw -html > hardware.html" line. I'm not sure what you meant by terminal.

Anyway I got the specs already.

---

### Post by IGLAW on 2008-08-25
Nobody? Aww...

---

### Post by finlost on 2008-08-25
To get to a terminal screen do: Applications - Accessories - Terminal

---

### Post by IGLAW on 2008-08-25
> **finlost said:**
> To get to a terminal screen do: Applications - Accessories - Terminal

Uh... there's definitely no "terminal" in accessories. This is XP MCE I'm running here, incidentally.

Anyway I got my hardware specs up there, four posts ago. Any idea at all?

---


---
title: "Live CD Having No Effect"
date: 2008-03-30
forum: Installation &amp; Upgrades
---

### Post by arcelios on 2008-03-30
I downloaded the latest Ubuntu Linux distrobution (7.04), and burned the .iso onto a CD. I popped that CD into my old Dell running Windows 98. I then restarted the computer, and Windows came up, as if nothing happened. When I popped it in the first time, it gave me a window with some open source software in it (Firefox, etc.), as well as some information about Ubuntu. I've tried rebooting, but it just doesn't load Ubuntu. Any ideas? I heard something about my BIOS settings maybe being wrong? Any way to fix this?

Thanksl :)

Arcelios

---

### Post by Pumalite on 2008-03-30
If you burn your iso as 'image', it should be bootable I hope you followed this guide:
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)
Make sure to access your BIOS ('Del'?) and set CD as 1st in the boot order.

---

### Post by arcelios on 2008-03-30
I did follow that guide, and I'm very certain that I did it correctly. How do I access the BIOS, and make the CD 1st in the boot order? 

Thanks :)

Arcelios

---

### Post by Pumalite on 2008-03-30
BIOS is accessed when you first boot.. Use Del or Tab, etc. Consult your motherboard Manual.

---

### Post by prshah on 2008-03-30
> **arcelios said:**
> 
 I then restarted the computer, and Windows came up, as if nothing happened. 

Looks like your comp is set to boot from hard drive first.

Immediately after powering up your computer, keep tapping (don't keep pressed, keep tapping one after the other) "Del" then "F2" then "F10", then repeat ; these are typical keys to enter the BIOS setup.

From there, look around for something called "Boot order" and change it to boot from CDROM first.

For EXACT instructions, it would be useful if you can snap a couple of pics of your comp BIOS setup screen with a digital camera, from which I or someone else can tell you which options to choose; just the opening screen of the BIOS setup is enough.

---

### Post by JamesGrimlee on 2008-03-30
Depending on your Dell, you may be able to hit F12 when it is booting up. It should tell you at the first screen in the upper right hand corner. If that isn't there, you'll need to change your BIOS settings. Generally, getting in to do that will require you to press a key(delete or F2 commonly) as it's booting. Different BIOS have different menu layouts, but you should be able to find a booting section in there. From there, just make sure the CD drive is listed before the hard drives. Save and reboot.

Hope that helps.

---

### Post by arcelios on 2008-03-30
Ok, I got something. I restarted, and hit "F2". I got a black screen with some white text on it. Not really a menu, just a lot of weird DOS stuff. Whenever I try to put some kind of input into it, the computer just beeps. It eventually times out and windows continues to start up.

---

### Post by arcelios on 2008-03-30
Great. Now I get the Blue Screen of Death :confused:

---


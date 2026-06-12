---
title: "Operating system not found"
date: 2014-01-25
forum: Installation &amp; Upgrades
---

### Post by kjandersonjr on 2014-01-25
I am trying to fix my Dell Studio 1737 laptop that came with Vista Home Premium. Because it will no longer boot past the Microsoft Corporation load screen, I want to see if I can recover my files using ubuntu. I tried to boot up ubuntu 32-bit and 64-bit multiple times from a flash drive after successfully changing the boot order with no success. The same error message comes up with Operating system not found. Am I better off trying to repair using a Vista installation disc or is there a way I can use ubuntu to access my files before totally wiping my PC?

---

### Post by fantab on 2014-01-25
How did you burn the ubuntu.iso to DVD/USB? Sounds to me like a 'burn' issue. Re-burn if needed.
Also do a [MD5Sum Check]("https://help.ubuntu.com/community/HowToMD5SUM") on the downloaded .iso to determine its integrity. If the test fails re-download ubuntu.

Your processor is 64bit so use 64bit Ubuntu only.

If you can repair and get Vista back, then why not give it a try.

---

### Post by Bucky Ball on 2014-01-26
Welcome. As fantab has said, what did you burn it with?

Try Unetbootin. Works for me.

The general answer though is, yes, it is entirely possible to boot from a Ubuntu USB dongle and backup your files before killing Vista (which sounds like it is on its last breath anyhow so might be the merciful thing to do). ;)

---

### Post by kjandersonjr on 2014-01-26
Unetbootin worked great guys, thanks! However, now that I am just running ubuntu without installing I can't select any of my old files that I see on my hard drive. Is there a setting I need to change to make this happen?

---

### Post by kjandersonjr on 2014-01-26
Nevermind, upon second reboot the files are now accessible.

---


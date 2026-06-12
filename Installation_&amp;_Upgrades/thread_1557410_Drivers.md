---
title: "Drivers"
date: 2010-08-20
forum: Installation &amp; Upgrades
---

### Post by Baxterton on 2010-08-20
Hello, I need some help with installing some drivers or rather getting them. I need a driver for my Asus M4N68T-M Motherboard, it came with a disc that installs the drivers, but Ubuntu won't execute the disc.

Is there anyway that I could get them over the Internet or would it be possible to rip the disc to a flash drive and load them that way?

---

### Post by bukwirm on 2010-08-20
Your disc probably only has Windows drivers, which are pretty useless in Linux.

Does your motherboard work? Linux includes drivers for most motherboard components.

EDIT: Looks like there's at least [one person]("http://georgia.ubuntuforums.org/showthread.php?t=1552317") who got it to work:

---

### Post by tommcd on 2010-08-20
According to this:
[http://www.superwarehouse.com/ASUS_M4N68T-M_Motherboard/M4N68T-M/ps/1572263](http://www.superwarehouse.com/ASUS_M4N68T-M_Motherboard/M4N68T-M/ps/1572263)
Your motherboard uses the NVIDIA GeForce 7025 / nForce 630a chipset, which should work fine in Ubuntu.
Were you able to install Ubuntu ok?
Is this a wubi (inside Windows) install? Or is this a real Ubuntu install to a dedicated partition on your hard drive?
I am assuming you are using Ubuntu 10.04, which is the current version. Is that correct?

If you need the drivers for your integrated graphics on your motherboard, see this:
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
Write back if you need more help.

---

### Post by Baxterton on 2010-08-20
I actually ripped it to my usb and Ubuntu allowed them to execute, I couldn't get all of the divers tho, like the EPU driver.

---

### Post by tommcd on 2010-08-20
> **Baxterton said:**
> I actually ripped it to my usb and Ubuntu allowed them to execute, I couldn't get all of the divers tho, like the EPU driver.
I don't know what that means.
What, exactly, did you "rip"? And what is EPU?
You did not answer any of my questions. Please read my last post again and answer *all* of the questions I asked. You need to make some sort of effort here to try to solve your problems. You need to be more verbose with your answers.

---

### Post by Baxterton on 2010-08-21
uhm ok, I installed Ubuntu then tried to install the drivers, I didn't partition because why would I need to? "ripped" meaning I took the file from the disc and moved them to my usb, then from there I was able to get Ubuntu to execute them, idk what EPU is I don't think it matters though. 

I literally solved my problem minutes after posting, I just didn't edit to say so, thats my bad.

---


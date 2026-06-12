---
title: "Kbuntu 9.10 Dual boot no grub visible"
date: 2009-11-14
forum: Installation &amp; Upgrades
---

### Post by CheresZabor on 2009-11-14
hey guys,
i just upgraded my comp and am trying to install kubuntu 9.10 and win7. Now the win7 install went fine and works however the i can not get kubuntu to work, its on the second partition and there does not seem to be any sign on grub installation so every time i boot the computer defaults to win7.

any suggestions on how to fix that? 

Thank 

PS; just to clarify im running this of a single hard drive

---

### Post by darkod on 2009-11-14
Did you install first win7 or kubuntu?

---

### Post by CheresZabor on 2009-11-14
i installed win7 and then kubuntu

---

### Post by darkod on 2009-11-14
In that case grub should have been installed on the MBR of the hard drive, unless you chose different in Advanced options of the last screen when installing just before hitting Install.

I can only find the link for Ubuntu right now, not Kubuntu, but the procedure is the same. You should be able to figure it out:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

Look at Reinstalling from Live CD. In case you don't know, live CD is called when you boot with the kubuntu CD and you select the option Try Kubuntu. In that situation kubuntu is running from the CD not from your hdd.

See if the above can help, the instructions are not too complex.

---

### Post by CheresZabor on 2009-11-14
Ok, i've tried that approach as well it doesn't seem to help, i also reinstalled kubuntu again and no luck, there was a message that grub was being installed but after when i rebooted there was no sign of grub or anything

---


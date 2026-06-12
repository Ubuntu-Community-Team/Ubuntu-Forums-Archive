---
title: "Keyboard doesnt work after upgrade to 20.04"
date: 2021-02-22
forum: Installation &amp; Upgrades
---

### Post by hhef on 2021-02-22
Hi All,

I just upgraded to ubuntu" 20.04.2 LTS (Focal Fossa)" from 18.04 LTS, and I now have a very strange issue. My computer is set up to dual boot Windows 10 and Linux. After the upgrade, the keyboard on my laptop (A Lenovo V330-15IKB), no longer works in many cases. In particular, the keyboard _only_ works on the login screen. Even stranger, the keyboard no longer works on my Windows partition. My touchpad still works fine. I have tried running ```
sudo apt-get install xserver-xorg-input-all
``` (which did not change anything after a reboot) and I have checked that the settings "Bounce Keys" and "Slow Keys" are off.

The fact the keyboard works for logging into ubuntu makes me think its not a hardware problem, and the fact that Windows is messed up makes me think maybe(?) its a problem with grub. However, I have no idea how to debug this, and was hoping someone might have some ideas.

Also, how confident should I be that a clean install would fix the issue?

Thanks in advance,
Henry
(Please let me know if there is any addition data that would be helpful!)

---

### Post by CelticWarrior on 2021-02-23
Does it work in UEFI? If so, does it work in Windows if booted directly?

---

### Post by hhef on 2021-02-23
Hi @CelticWarrior,
Thanks for the suggestion! I tried it and the keyboard on the laptop neither works in UEFI, nor does it work when I change the boot order so it goes directly into Windows. The laptop keyboard still works for on the log in page of ubuntu, and it also works if I press f5 and drop into a shell on the log in page. Im thinking I might have corrupted something low level in the keyboard drivers or something. Im not sure how to test that theory though

---

### Post by CelticWarrior on 2021-02-23
Try disabling Fast Boot (UEFI) and also make sure, if applicable, Legacy USB support IS enabled.

---

### Post by hhef on 2021-02-23
Thanks again! I couldnt find a Fast Boot option inside the UEFI menu's, but I have disabled "fast startup" in my Windows OS. I have also enables Legacy USB. Niether of these seem to have had any effect. Do you think a factory reset of the computer will work? Im ok starting again from scratch.

---

### Post by mastablasta on 2021-02-24
you can try a live session (or windows system rescue disk), but based on your description, the issue starts at UEFI, when neither OS is loaded. also if it doesn't work in UEFI, how do you make any changes there?

also make sure you don't have some option turned on in both OS where it disables keyboard when external USB keyboard is plugged in. maybe some external device is then messing up with this setting. for example laptop would think you have external USB keyboard plugged in but you actually have a mouse or something.

also does the Fn key work when in OS?

---


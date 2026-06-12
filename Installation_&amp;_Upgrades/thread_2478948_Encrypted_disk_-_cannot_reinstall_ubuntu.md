---
title: "Encrypted disk - cannot reinstall ubuntu"
date: 2022-09-09
forum: Installation &amp; Upgrades
---

### Post by bemojedk on 2022-09-09
Hi all. I hope someone can help me.

I've installed Ubuntu on a Lenovo laptop and enabled full disk encryption and now forgot the password (don't ask).
I want to fully reinstall Ubuntu and don't care about data within the current installation.

I have a Ubuntu Live USB installer pen drive that I'm trying to boot from. But it seems the computer won't let me. Instead of booting from the USB, it goes into trying to start the OS and asks me to unlock the disk "nvmeOn1p3_crypt".

Of course I GOT the boot menu up and selected the USB as boot device. I also tried setting the boot order in the BIOS so that the USB was on top. Still it would not boot into it and again just ask for the password for the encrypted disk. I tried 3 different boot USBs now - even a Windows one just for the sake of trying something else. Still boots into disk.

Can it really be that I can't boot from anything else than the installed OS? Do I have to buy a new SSD?

Thanks for your help :)

I made a video that shows what the screen shows and also quickly paging through the current BIOS settings: [https://www.youtube.com/watch?v=Bb6iJoWNDa4](https://www.youtube.com/watch?v=Bb6iJoWNDa4)

---

### Post by TheFu on 2022-09-09
> **bemojedk said:**
>  Can it really be that I can't boot from anything else than the installed OS? Do I have to buy a new SSD?

I'd guess that the BIOS was set to boot from the internal storage first.  Go into the BIOS and change the boot order to allow booting from non-internal drives first.  There might be a key you can press before the system attempts to boot that will pull up a boot device menu.  I've never used Lenovo stuff, but on an Asus and Dell, I think it is F10 or F10 or DEL.  At boot, just start pressing DEL, DEL, DEL, DEL, DEL, DEL, DEL, DEL, DEL, DEL, DEL, DEL, DEL, DEL, DEL, DEL, DEL, DEL, DEL, DEL, DEL, DEL, DEL, DEL, DEL, DEL, DEL, DEL, DEL, DEL, DEL, DEL, DEL, DEL, DEL, DEL, DEL, DEL, DEL, DEL, DEL, DEL, DEL, DEL, DEL, DEL, DEL, DEL, DEL, DEL, DEL, DEL, DEL, DEL, DEL, DEL, DEL, DEL, DEL, DEL ... you get the idea.

until the menu shows up.
If it goes into the grub or encryption unlock screen, try a different key. I suppose you could look up the correct key, but since there are only 3-5 real choices, I just press them until 1 works.

---

### Post by tea for one on 2022-09-09
F12 is the dedicated key for Lenovo boot menu.
Also, if you have a recent laptop, there should be a Novo pinhole/button.
[https://support.lenovo.com/gb/en/solutions/ht062552-introduction-to-novo-button-ideapad](https://support.lenovo.com/gb/en/solutions/ht062552-introduction-to-novo-button-ideapad)

---

### Post by TheFu on 2022-09-09
> **tea for one said:**
> F12 is the dedicated key for Lenovo boot menu.

What?  It isn't F10 or F10? <RBG>  Sorry, I meant for the second F10 to be F12. It is a common button for many systems.  ;)

---

### Post by bemojedk on 2022-09-10
No no, I GOT the boot menu up and selected the USB as boot device. I also tried setting the boot order in the BIOS so that the USB was on top. STILL it would not boot into it and again just ask for the password for the encrypted disk. I tried 3 different boot USBs now. Same result.

---

### Post by bemojedk on 2022-09-10
I got it working. I changed a setting in the BIOS that set something about optimizing for OS defaults or something. Disabled that, then it would boot from USB.

---


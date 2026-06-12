---
title: "Boot off CD failed"
date: 2007-12-01
forum: Installation &amp; Upgrades
---

### Post by Mindflux0 on 2007-12-01
I downloaded 64bit Ubuntu and burned it to cd and tried to load it up  (off the cd) on my laptop (hp 6xxx) to see how it feels. It pulled up the loading screen, seemed to be fine, the screen went black and then just never came back. Then I tried to use it on my desktop and it froze on the loading screen (maybe because it's OCed? runs error free in windows though).
My laptop was shipped with vista and is unusable even with dualcore amd@1.7ghz and 2gigs of ram so I figured Linux would be a good way to go, free and all I'm doing with the laptop is text/internet maybe some old games that should have linux support (CS, NWN, etc).
So is this going to be a huge hassle to get working? Is it something to do with booting off the cd? I don't really want to wipe the drive and install linux if I'm not sure it's going to work which was why I was doing this in the first place.......so, suggestions?

---

### Post by Pumalite on 2007-12-01
Make sure you burn as image and not as data.
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)
With Vista you have to allocate space for Ubuntu with Vista partitioner.
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)

---

### Post by Mindflux0 on 2007-12-01
Ok, like I said, it starts running as I boot off the cd, it goes to the load screen and then goes blank.  I'm not trying to dual boot, I'm trying to load linux to see if it will function.

---

### Post by Pumalite on 2007-12-01
If it's not a bad burn, it's your hardware, and that means Alternate CD, which is only for installation.

---

### Post by MrFSL on 2007-12-01
It probably has to do with the graphics. What type of graphics card is in the computer? I wager a guess and say it has ATI graphics. Am I right?

It might be possible to get it working through a boot time option. Let us know what you have for graphics.

---

### Post by Pumalite on 2007-12-01
If you want to try boot parameters; here is a tutorial and a collection to try:

[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)
[https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html](https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html)
noapic nolapic acpi=off pci=noacpi pnpbios=off vga=0x317

If nothing works; go with the Alternate CD.

---

### Post by Mindflux0 on 2007-12-02
using onboard geforce go 6150.

---

### Post by Pumalite on 2007-12-02
On board graphics>Many times>Alternate CD.

---

### Post by Mosphet on 2007-12-02
Try:

At the install options screen, choose the 'additional options' (F6 I think), remove 'quiet splash' from the end of the boot parameters, press enter.

I had the same symptoms you describe and this method fixed the problem for me.

good luck

---

### Post by MrFSL on 2007-12-02
> **Mosphet said:**
> Try:

At the install options screen, choose the 'additional options' (F6 I think), remove 'quiet splash' from the end of the boot parameters, press enter.

I had the same symptoms you describe and this method fixed the problem for me.

good luck

Yup! I agree give this a shot.

> If you want to try boot parameters; here is a tutorial and a collection to try:

[http://grumpymole.blogspot.com/2007/...arameters.html](http://grumpymole.blogspot.com/2007/...arameters.html)
[https://help.ubuntu.com/7.04/install...oot-parms.html](https://help.ubuntu.com/7.04/install...oot-parms.html)
noapic nolapic acpi=off pci=noacpi pnpbios=off vga=0x317

If nothing works; go with the Alternate CD. 

Again yes! I think that it is a graphics issue. The CD wants to run a nice looking graphical boot screen which can cause crashes on certain configurations because it is trying to load graphics at such an early stage of loading the O/S. 

For starters remove quiet and splash as already recommended. Next you can use this chart:
[**SOURCE**]("http://techpatterns.com/forums/about342.html")


..coupled with the "vga" option. For instance vga=791. This way you can try a few to get it working.

---

### Post by Mindflux0 on 2007-12-04
if you're refering to where it says "Ubuntu" and has a windows-like loading animation, it does that and *then* dies. I tried removing that and it didn't work.

---

### Post by Mindflux0 on 2007-12-04
I ran with noacpi nolapci and it loaded. Thanks!

---

### Post by Pumalite on 2007-12-04
You are welcome. Good luck.

---

### Post by Efaill on 2007-12-04
This thread just helped me to :KS

Was having the very same problem, select install from the start screen and nada. Using the alt cd with the text install and away it went. Most excellent\\:D/

---

### Post by Neostart on 2007-12-04
> **Pumalite said:**
> You are welcome. Good luck.

Sorry, but this doesn't helped me. Its unfair.

I deleted quiet splash, added noacpi nolacpi and I see listings of loading the core, Realtek, CDdrive, Disc, and ... stops.

---

### Post by Pumalite on 2007-12-04
Start a new thread with your specs and details of your problems.

---


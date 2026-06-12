---
title: "unable to load xserver with nvidia card"
date: 2010-02-14
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by giorsat on 2010-02-14
Hi. I tried lucid daily image 32bit and installed in 3 different pc. the one with intel videocard is workin flawlessly while the 2 other with an nvidia video card (both have recent cards btw) at reboot I get a dark gdm login. no way to go to console either. any idea how to fix this?

---

### Post by dino99 on 2010-02-14
what driver is used ?
On my owns, i have "sevenmachine ppa" package on nvidia system.

then activated it via: system --> admin --> select driver (or liked)

---

### Post by SevenMachines on 2010-02-14
dino99: you should probably move to [alberto milone's ppa]("https://launchpad.net/%7Ealbertomilone/+archive/proprietary-video-improvements")

it has the 195 driver and alberto is the person who works on the repository packages, meaning that the packaging is much better than mine :)

---

### Post by giorsat on 2010-02-14
sorry. I mean that the xserver goes dark at first boot after installing. I cannot access my home because the screen goes dark . strange thing is that while booting instead of the ubuntu log I get three progress bar: one blue, one white and one light blue. what is wrong?

---

### Post by AlanR8 on 2010-02-14
If I understand you correctly, you are getting as far as the log on screen but when you press enter to log on things lock up solid.

I have the same problem on my Lucid Alpha 2 daily release build from last Thursday on my Sony Vaio VGN FZ21S and Nvidia 8600M.

I found a workaround, not elegant but quick and dirty! When the screen locks up I kill the X session using Alt+SysRq+k. The session ends and the screen goes black and I get lots of random colour blocks followed by a new log on screen that works.

Give it a go and let us know if it works for you.

---

### Post by SevenMachines on 2010-02-14
this sounds like plymouth to me, you might want to either uninstall it or disable it in /usr/default/grub (remove the splash entry) and run update-grub. you might also want to remove the quiet option so you an see whats happening during the boot

---

### Post by tad1073 on 2010-02-14
I experiences the triple "fedora progress bars" about 2 weeks ago myself, I was able to see the login screen but the keyboard and mouse would freeze, figured out it was plymouth, removed and the problem was solved for the moment.

---

### Post by giorsat on 2010-02-15
ok. How can I edit grub at first reboot?  grub 2 is so different from grub 1 and it seems that hitting the E letter doesn't do anything

---

### Post by dino99 on 2010-02-15
keep in mind that if you have both grub1 and grub2, os-prober brings settings found into menu.lst(ie grub1) instead of picking settings from /etc/default/grub.

So, remove /purge grub1 ](*,)

---

### Post by VMC on 2010-02-15
Removing Plymouth in a way is like "sticking your head in the sand". It ignores the problem. We need to hammer some bug reports to Launchpad.

If you remove splash and right after the last two messages:
```
Begin:Running /scripts/init-bottom
fsck ...
```
and it freezes that very well could be Plymouth. But they need to know this.

Another thing is if I power-cycle(the only way out) and re-boot, it may boot up with no apparent errors.

 Some times it takes 5 power-cycles but it will boot?!

 This is not good for the file system. On each power-cycle fsck has to recover file structure.

---


---
title: "Ctrl Alt f2?"
date: 2010-02-04
forum: Installation &amp; Upgrades
---

### Post by FreyGrimrod on 2010-02-04
Ok... so I upgraded to Karmic amd64 and continue to have nothing but problems... so many changes so little reason I see for them other than to turn Ubuntu into OSX if I wanted OSX I would have installed it...

Had poked around a few google searches didn't seem to find anyone else having this problem...

Any ideas why ctrl alt f2 won't give me a prompt? In fact any run layer but 7 only gives me a blank screen....


This is getting ridiculous may be time to give up on ubuntu....

---

### Post by FreyGrimrod on 2010-02-04
So I enabled ctrl alt backspace and even that just reboots X and logging in as xterm is X term how does one kill X and actually get a prompt under karmic is the real question here?

Oh also sudo /etc/init.d/gdm stop and/or sudo service gdm stop just leaves me hanging also...


And I'm pretty sure this is all because I had three crazy screens the third one just died trying to move back to two. So I had xinerama enabled under the nvidia driver trying to reinstall the nvidia driver as xinerama meant no randr and all sorts of other issues that is the likely cause of this... even trying to edit my xorg gui style with nvidias settings no luck...

---

### Post by FreyGrimrod on 2010-02-04
And grub root shell can't sh nvidia driver package for some reason...


So manual nano of my xorg.conf did get xinerama disabled but that third screen is still incorrectly detected hrm...

Will have to play more later...

Running Dual 6600LE's second one is now not in use

---

### Post by FreyGrimrod on 2010-02-04
Ok got it... after getting xinerama disabled via nano sudo nvidia-settings started actually functioning properly managed to disable the non existent monitor...

Anyone who reads this feel free to look over the ramblings of a crazy person Mods feel free to delete it...

---


---
title: "upgrade 11 fails all I can do is login then nothing"
date: 2011-05-02
forum: Installation &amp; Upgrades
---

### Post by ssfbfun on 2011-05-02
I upgraded to 11.04 on a system that works just great under 10.10.
 clean install from the iso downloaded from ubuntu.
 installs fine but ...I get nothing just the login screen that works then  nothing...no unity shell..nothing.  things POP on and off the screen.. but  total failure to get a desktop..
 had to reinstall 10.10 which worked just fine.
 
 Ubuntu has problems with this 11.04 release..
 
 anybody have any ideos..can not be my video since the login screen worsk jut fine.

---

### Post by dpwilson on 2011-05-02
I wouldnt say it cant be your video just because you can log in. I logged in just fine, but nothing else was normal after that.  Turned out in my case to be that nvidia drivers arent workign with unity at this time.  At least thats what I read and after removing them and using the default, all is well.

---

### Post by dino99 on 2011-05-02
boot in recovery mode (second line from grub menu, which you get if you hold "shift" key down at bios end process) and select "repair packages"

then check driver activation (system admin additional drivers) and perform some commands into a terminal:

sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

---

### Post by elliotcroft on 2011-05-02
Is unity listed in the desktop environment selection list?
If not:
Press Ctrl + Alt + F2 and use 'sudo apt-get install Ubuntu-desktop' then restart.
Does the problem still persist?

---

### Post by ssfbfun on 2011-05-02
Yes I have an nvidia FX 3000 dual DVI AGP card but I just install v11.04 and get the login screen. aAfter logging in the Unity desktop goes awry and I get folder icons popping on the monitor for 1/2 second then disappear.

I never had  a chance to install any nvidia drivers.

I give up and I will wait (8) weeks until UBUNTU gets thousands of complaints and finally fixes the damn thing.

how can they release this garbage.

my box works with any distro no problem except 11.04.......... it has generic common parts that need well known drivers.

---

### Post by Michael108 on 2011-05-02
Hi Dino99, 

Can you specify what this means?: check driver activation (system admin additional drivers) ?

I got to repair packages and did the sudo commands but nothing changed & I still have a display that does nothing but have a mouse that moves. I have an Nvidia video card and everything was working in 10.10 until I upgraded today.

thanks!
Michael

---


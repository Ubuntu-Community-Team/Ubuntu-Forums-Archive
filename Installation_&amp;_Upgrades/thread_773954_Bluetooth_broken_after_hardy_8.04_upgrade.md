---
title: "Bluetooth broken after hardy 8.04 upgrade"
date: 2008-04-29
forum: Installation &amp; Upgrades
---

### Post by sfenton on 2008-04-29
I'm not sure why, but on my IBM T60 after I upgraded to Hardy, by bluetooth doesn't work any longer. I tried both my mobile, and my Apple wireless mouse and bluetooth doesn't see them. 

It's not that I cannot pair. When I look at Bluetooth preferences, there are no bluetooth devices there. 

I did a bluetooth search with my mobile, and I could see another device, but my laptop would not see it. 

hcitool scan doesn't find anything. 

syslog doesn't show anything unusual. 

It worked well with 7.10

Any ideas from the community? 

Cheers

---

### Post by adjua on 2008-04-29
Same problem with me on the IBM r60e - tried to boot under previous kernel version, no changes

---

### Post by balagosa on 2008-04-29
sfenton...might i ask you how you did/install the bluetooth on 7.10?

having probs here.

my distro...Xubuntu 7.10

---

### Post by sfenton on 2008-04-29
I believe that it just worked. I do remember that I had to in 7.04 monkey with the configurations. I'm not on the thinkpad right now. I'll reply when I'm on there and look at the configuration. 

It is interesting that there is another thinkpad that doesn't work as well. 

I did have the wrong kernel in there after the upgrade, but updated the grub and everything else works.

---

### Post by sfenton on 2008-04-30
I was poking around the thinkwiki site and saw that bluetooth might not be turned on, so I tried it. 

It worked. I pressed Fn F5 and the darn thing came to life. 

before I pressed the keys, lsusb didn't show a broadcom bluetooth adapter. After sure enough it was there. 

I guess during the upgrade bluetooth got turned off.

---

### Post by adjua on 2008-05-02
Didn't work for me. Went through [http://ubuntuforums.org/archive/index.php/t-593016.html](http://ubuntuforums.org/archive/index.php/t-593016.html), turned module on, still hcitool dev shows no device

Update: Switched the hardware-wireless switch (NOT Fn-F5, the other one) on, then it worked. I wonder if Gutsy simply ignored this switch as I swear, i never touched it, and never knew where it was ...

---


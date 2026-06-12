---
title: "Grub2 error: no such device: HELP!!!!!"
date: 2010-05-12
forum: Installation &amp; Upgrades
---

### Post by asuastrophysics on 2010-05-12
Hey guys,

I reformatted and completely reinstalled ubuntu 9.10 on my computer. However, I still can't boot anything. I get the following grub error;
```
Verifying DMI Pool Data....
error: no such device: 7e22c0f7-5852-4cb8-ac0d-b293feff3103
grub rescue> _
```

I tried reinstalling grub2, but I still get the same message. Can anybody please help me???? I'm desperate. I haven't been able to use my computer for 2 weeks and I'm about to literally throw the whole thing away. No OS can boot now.  :(

---

### Post by asuastrophysics on 2010-05-12
bump

---

### Post by Keith1212 on 2010-05-12
I had this problem. I jusy used a live cd and disabled the UUID check and it booted fine.

so boot from a live cd and use this below.

> **drs305 said:**
> If you can't access your system, from the Grub 2 menu: Press ENTER after each line; # are just clarifying comments - do not type them.
```
c  # enter command line mode
set root=(hd0,1)  # to set sda1 as root
linux /vmlinuz root=/dev/sda1 ro
initrd /initrd.img
boot
```

Once into the system, open /etc/default/grub:
```
sudo gedit /etc/default/grub
```

You can try disabling the UUID function to see if that solves things for you (uncomment it):


Update Grub2:
```
sudo update-grub
```
If this works for you send drs305 a pm thanking him hes a real nice guy and very helpful.

Check here for more help. 
[http://ubuntuforums.org/showthread.php?t=1337254](http://ubuntuforums.org/showthread.php?t=1337254)

Good Luck!

---

### Post by asuastrophysics on 2010-05-13
SOLVED!!!!!!!!!!!!

I popped in a disc I made years ago called "Super Grub Bootloader" and just selected random different options in the menu. After that, it only booted the hard disk with windows vista on it. So, I simply yanked the SATA cable out of the motherboard for that hard drive. Voila, booting ubuntu. Then I just did:
```
sudo update-grub
```
Then, only Ubuntu would boot. I re-inserted the SATA cable and ran "sudo update-grub" again. All fixed. 2 weeks of debilitating anger and frustration solved by some random cd that performed commands I have no idea what. :confused: whatever, it works.

If you get "ata4: SATA link down", Error 11, or some other grub issue, just google "super grub bootloader" and download it and burn it to a disc. Slam it into your crappy, malfunctioning, and totally useless computer (which was made useless by stupid linux) and just press random options till it works.:guitar:

---


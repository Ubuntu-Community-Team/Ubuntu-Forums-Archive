---
title: "Ubuntu 64bit installer won't Boot"
date: 2011-08-14
forum: Installation &amp; Upgrades
---

### Post by Mr Puffin on 2011-08-14
so i am trying to install 64bit ubuntu on an HP Laptop that was given to me 
i know the laptop is 64bit capable as i have win7 x64 on it

HP Pavilion DV6208nr laptop

AMD turion 64 mobile
nvidia geforce 6150 go
3gb Ram

now the actual issue is not install failed but when i boot the install media it has weird black and white lines across the screen

to trouble shoot 
i have re-downloaded the iso 2 times
and downloaded the alternate installer once (which installs but on first boot is just a black screen)
tried installing via usb and 2 separate discs (brand new)

what would cause the issue?
and should i maybe try an older one like 10.04 LTS?


i know 32 bit worked before but i would prefer to have a 64bit OS

[IMG]http://i.imgur.com/AWLdA.jpg[/IMG]

---

### Post by varunendra on 2011-08-15
Welcome to the forums Mr Puffin!

This seems to be a typical graphics problem. Try these:

If it is installed-

[LIST]
[*]press 'shift' key while booting to bring up advance grub menu
[*]select 'recovery' mode
[*]select failsafeX in the recovery menu
[*]if the above fails to boot normally, retry with 'dpkg' in the recovery menu.
[/LIST]
If using live cd to install-

[LIST]
[*]press any key while booting from cd to bring up advance menu
[*]press F6 pop-up boot options menu
[*]select 'nomodeset' (by highlighting it and pressing 'spacebar') and press 'Enter' to boot
[*]if it fails, select acpi=off, noapic and nomodeset next time to see if you get normal graphics.
[/LIST]
Once you succeed to get normal (or safe mode) graphics in the setup, you may need to manually install correct driver for your graphics.

**PS:** Trying 10.04.3 LTS is not a bad idea as it is the most stable long-term-supported version at the moment.

---

### Post by oldos2er on 2011-08-15
Did you check the integrity of the ISOs you downloaded? [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---


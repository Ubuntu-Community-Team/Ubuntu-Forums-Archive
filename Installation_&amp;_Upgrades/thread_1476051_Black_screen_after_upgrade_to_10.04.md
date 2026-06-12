---
title: "Black screen after upgrade to 10.04"
date: 2010-05-07
forum: Installation &amp; Upgrades
---

### Post by hfgfdhrtjtyjtykjtjd on 2010-05-07
I just upgraded to 10.04 on my laptop and after install, clean-up and reboot the screen goes absolutely black. The initial bios stuff is still there and the GRUB loader text. Then darkness without any response.

There is one way to start up and getting screen (which I'm using now). If hitting ESC in grub loader, selecting recovery-mode, selecting re-configure monitor, selecting start up in graphics-safe mode (this session only). Then it'll work. Other combinations, such as re-configuration and normal reboot or just graphics safe-mode does not work.

The only real error message I have obtained is the following:
(EE) intel(0): ch701x not detected, got 29, from DVOI2C_E Slave 234
Given as pop-up dialogue when going into recovery-mode.

My laptop is a Compaq Pressaro M2000. I can provide more details on graphics, but I'm not so fluent in linux, so I don't know what terminal commands to enter to get the right debugging information.

Thanks in advance.

---

### Post by Catharsis on 2010-05-07
I'm pretty sure that laptop has an Intel 855GM card. You can check by putting this in a terminal:
```
lspci | grep VGA
```

If you get "Intel Corporation 82852/855GM Integrated Graphics Device", then take a look here:
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

The first workaround should fix it.

---

### Post by hfgfdhrtjtyjtykjtjd on 2010-05-07
'lspci | grep VGA' gives:
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)

so you're right. I'm on my way out now, but I'll test first thing in the morning and write back if it worked. Thank you so much!

---

### Post by ne3e on 2010-05-07
Here is my 2 cents worth.
I have an old laptop.
I held down the shift key to bring up the GRUB menu.
I selected recovery mode.
I picked failsafe X.
My old laptop booted into a low graphics mode, which looks just fine.
I went to /etc/X11 and found a file xorg.conf.failsafe.
I then copied this file to xorg.conf and my old laptop booted up in graphics mode just fine.
Good luck to you all!


John

---

### Post by hfgfdhrtjtyjtykjtjd on 2010-05-08
Thank you Catharsis.
The 'Workaround A: Re-enable KMS' did the trick.
Just wrote:
echo options i915 modeset=1 | sudo tee /etc/modprobe.d/i915-kms.conf
sudo update-initramfs -u
and rebooted.
Thanks a lot

---

### Post by okkie on 2010-05-31
I have intel pentium 4 x86 machine with radeon 9200 pro card.
After upgrade to 10.04 Ubuntu kernel 2.6.32-22 gives me a black screen same as many others.My knowledge is inadequate to rectify the problem.Please give me a step by step workaround to paste into terminal to get 10.04 working .
Thanks.

---

### Post by davidmohammed on 2010-05-31
suggest create a new thread - the above was for intel graphics.

---


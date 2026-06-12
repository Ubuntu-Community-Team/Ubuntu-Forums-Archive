---
title: "Upgraded 9.10 to 10.04: Grub display Issue"
date: 2010-05-02
forum: Installation &amp; Upgrades
---

### Post by bootbat on 2010-05-02
Friends,

Upgrade went fine and I am loving it. Boot time is a definite improvement and the interface looks really good. Also, getting Thunderbird Notification integration was something I was looking for a long time now. Overall, I am very pleased with the improvements. I have an issue though in getting the GRUB display. 

Upon boot-up, the display shows "Out of Range 74.8KHz-60Hz". After the defined 10 seconds it boots using the default entry under GRUB and gets me to the Ubuntu login screen. So, the GRUB is fine and defaults to Ubuntu as set. My issue is that I cannot boot to Windows now as I do not see any option there. Here's what sudo grub-update shows:

```
Generating grub.cfg ...
Found Debian background: ubuntuhhok5.png
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found linux image: /boot/vmlinuz-2.6.31-21-generic
Found initrd image: /boot/initrd.img-2.6.31-21-generic
Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
Found Microsoft Windows XP Professional on /dev/sda1
done
```

Also I just noticed that my Firefox does not come-up after clicking. I reinstalled it through Synaptic but still does not launch. 

Need some help to sort these out. Any assistance will be appreciated.

---

### Post by bootbat on 2010-05-02
Looks like I was able to fix the firefox issue using the fix for  Bug #538796. Uninstalled libmoon (and moonlight-plugin-core and moonlight-plugin-mozilla as they depend on it) and firefox works fine again.

---

### Post by bootbat on 2010-05-02
I tried changing the GRUB 2 display resolution also but that did not make any difference. Any assistance/pointers to sort this out is appreciated.

---

### Post by dino99 on 2010-05-02
startup manager into system menu

---

### Post by bootbat on 2010-05-02
Hi dino99,

```

startup manager into system menu
```

I am not sure if I understood you correctly. Do you need me to post something here?

---

### Post by bootbat on 2010-05-02
I have now resolved it by using the startup Manager to configure GRUB to use 1024x768 for both the bootloader menu resolution and the test resolution. All seems to be working fine now.Thanks to dino99 for the pointers.

---


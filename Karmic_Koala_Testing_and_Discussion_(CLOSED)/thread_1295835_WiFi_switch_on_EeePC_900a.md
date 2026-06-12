---
title: "WiFi switch on EeePC 900a"
date: 2009-10-20
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Sven6210 on 2009-10-20
I have a small issue with my Ubuntu 9.10 Beta. Actually all function keys ('FN' +) work quite well out of the box. No problem with sound volume, background light etc.

Even the function key to toggle the Wifi off works out of the box. I press it once and the wireless is deactivated. But I can not reactivate it by pressing the function key once more. In order to get Wifi to work again I have to restart the computer.

Does anybody know the reason for this? Is there a script I can use to get Wifi working again without restarting Ubuntu? With the original Xandros that was not an issue but in Ubuntu it never worked for me. With Ubuntu 9.04 I was even not able to switch Wifi off. Now I can switch it off but have trouble restarting it again.



UPDATE 15th November 2009:

I found the solution for reactivating wireless when switching it on and off with the hot key

You have to pass the following parameters to the kernel command line:
pciehp.pciehp_force=1 pciehp.pciehp_poll=1

1. sudo gedit /etc/default/grub

2. edit the line with GRUB_CMDLINE_LINUX_DEFAULT:

GRUB_CMDLINE_LINUX_DEFAULT=&#8221;pciehp.pciehp_force=1 pciehp.pciehp_poll=1 quiet splash&#8221;

3. sudo update-grub2

Restart the system. Now you can toggle WiFi and you get reconnected when you switch it on again.

---

### Post by blackened on 2009-10-20
Not entirely relevant to your issue, but you can probably restart the wireless adapter using ifconfig (make sure you reference the appropriate interface {the bolded part}):

```
sudo ifconfig **wlan0** up
```

---


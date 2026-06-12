---
title: "Ubuntu 9.10 intall failure"
date: 2010-02-07
forum: Installation &amp; Upgrades
---

### Post by parminides on 2010-02-07
Yesterday I upgraded my HP Touchpad from Ubuntu 8.x to 9.10 using the update manager. Everything seemed to go well, but there were 2 kernels listed in the grub menu.

If I chose the more recent one, the computer would only boot up in safe graphics mode. If I chose the older kernel, the graphics would be fine, but there was no sound!

I decided to backup files and do a fresh install from read/write dvd created with ubuntu-9.10-desktop-amd64.iso. (I used this same dvd without any problems to install Ubuntu 9.10 on my laptop a few days earlier.)

In hindsight, what I did next was stupid, but it's the method that worked flawlessly with my laptop.

I booted to Windows Vista and deleted the ubuntu and bootup partitions. My reasoning for deleting the bootup partition was that it would be recreated by the Ubuntu installation (this was the stupid part).

Then I rebooted with the dvd to start the fresh installation. It didn't got very far, hanging at the point where it endlessly repeats the following message:

```

[drm:intelfb_restore] *ERROR* Failed to restore crtc configuration: -22

```

The only way to stop these messages was to power down the computer.

I've Googled this error message, and it typically appears during bootup of an already installed system. So there are various suggestions for how to deal with it in configuration files.

None of those suggestions will work for me because I've cleaned Ubuntu and the grub menu completely from the system. I'm dead in the water right now. Any ideas?

---

### Post by parminides on 2010-02-07
Update: I tried to install Ubuntu 9.10 from a bootable flash drive and encountered the same error. I was able to install Ubuntu 8.04.4 from a bootable flash drive created from ubuntu-8.04.4-desktop-amd64.iso. Very strange.

So I'm not dead in the water anymore, but I still would like to know how I can get Ubuntu 9.10 on my Touchsmart desktop.

---


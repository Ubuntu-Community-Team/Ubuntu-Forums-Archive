---
title: "Asus A7T Woes -- Beeping"
date: 2008-03-27
forum: Installation &amp; Upgrades
---

### Post by grooveman on 2008-03-27
Hello.

I am trying to install Ubuntu Gusty Gibbon on my Asus A7T laptop.

I am having two major issues.  I will post one here, and the other in another thread.

The problem I am having here is that probably 3/4 of the time I boot my system to Ubuntu (I have Vista installed on the system as well), I get the god-awful loud beep that lasts for about 60 seconds.  It happens immediately after grub hands the system off to the kernel.  

It only happens on Ubuntu -- and NEVER on vista.  It likewise does not happen when I boot to an Elive or a Knoppix linux CD.

During the beeping, and for about 60 seconds after, I get a blank, black screen.  I know that things are happening, because I see the HD led flickering, but it isn't coming to the screen (Pretty sure you are supposed to get a Framebuffer image of the Ubuntu Logo with the pulsating progress bar under it).

After a bit, the screen lights up with the GDM login screen, and everything seems to work from that point on (except sound, but that will be another post).

I haven't seen any other posts like this, and I have never seen this behavior before.

The only error output I get at boot time is:

```
[    0.684000] PCI: Cannot allocate resource region 7 of bridge 0000:00:04.0
[    0.684000] PCI: Cannot allocate resource region 5 of device 0000:04:00.0

```

Anyone know hot to fix this?

Thank you.

G

---

### Post by Irony on 2008-03-27
Perhaps a vga setting problem?

```
Screen   640x480     800x600     1024x768     1280x1024     1600x1200
Colors    --------------------------- -------------------------------------------
 256     | 769         771          773            775              796
 32,768 | 784         787           790           793              797
 65,536 | 785         788           791           794              798
 16.8M  | 786        789           792           795              799 
```

Thus you might add the setting to your menu.lst boot file;

```
/boot/vmlinuz-2.6.22-14-generic root=/dev/hda1 ro splash vga=791
```

---


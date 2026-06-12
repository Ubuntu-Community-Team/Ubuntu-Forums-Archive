---
title: "Another Grub2 Problem"
date: 2009-08-14
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by bennachie on 2009-08-14
I run a triple-boot configuration on a single disk, with Linux Mint 7 as my production system. I've been trying to get Grub2 to recognise Mint in the boot menu (it does pick up the XP partition). When I run update-grub2, I get the following response:

john@eeePC-1000H:~$ sudo update-grub2
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-5-generic
Found initrd image: /boot/initrd.img-2.6.31-5-generic
Found memtest86+ image: /memtest86+.bin
Found Microsoft Windows XP Home Edition on /dev/sda1
Found Windows NT/2000/XP on /dev/sda2
Found Linux Mint 7 Gloria - Main Edition (7) on /dev/sda9
done

That all looks fine, but Gloria is still MIA from the boot menu.

Any advice? Yes, I know I can just install anything using legacy Grub in the partitions I'm using for 9.10, and restore my access to Gloria, but I would like to help test Karmic.

---

### Post by phenest on 2009-08-14
You say a triple boot, but I'm sure I can see 4 there.

---

### Post by bennachie on 2009-08-14
Well, I guess that's right - but the other one is just the Windows recovery partition. I notice that I'm not the only one who has experienced problems with the last system identified in the grub-update process dropping out - you do have to wonder whether Grub2 is really ready for prime time.

---

### Post by bennachie on 2009-08-15
I've replaced 9.10 with Mandriva (with the best boot menu management in the business) to get under way again, but I would still like to participate in testing 9.10. I'd therefore appreciate advice as to how Grub2 can be persuaded to add every OS that it recognises to the boot menu.

---

### Post by xebian on 2009-08-15
> **bennachie said:**
> I run a triple-boot configuration on a single disk, with Linux Mint 7 as my production system. I've been trying to get Grub2 to recognise Mint in the boot menu (it does pick up the XP partition). When I run update-grub2, I get the following response:

john@eeePC-1000H:~$ sudo update-grub2
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-5-generic
Found initrd image: /boot/initrd.img-2.6.31-5-generic
Found memtest86+ image: /memtest86+.bin
Found Microsoft Windows XP Home Edition on /dev/sda1
Found Windows NT/2000/XP on /dev/sda2
Found Linux Mint 7 Gloria - Main Edition (7) on /dev/sda9
done

That all looks fine, but Gloria is still MIA from the boot menu.

Any advice? Yes, I know I can just install anything using legacy Grub in the partitions I'm using for 9.10, and restore my access to Gloria, but I would like to help test Karmic.

Well "Found Linux Mint 7 Gloria .." doesn't mean anything but just telling you it found something.  There must be some error messages somewhere why it's not in the final /boot/grub/grub.cfg.

---

### Post by phenest on 2009-08-15
> **xebian said:**
> Well "Found Linux Mint 7 Gloria .." doesn't mean anything but just telling you it found something.  There must be some error messages somewhere why it's not in the final /boot/grub/grub.cfg.

I've just being looking at 30_os_prober. It probes for all OS's and the devices their on. For each device, it probes for kernels, etc to make the menuentry. I guess linux_boot_prober is having trouble with Mint, and therefore didn't add an entry.

---

### Post by bennachie on 2009-08-15
I do reccall that, on one occasion, there was a fleeting pop-up saying that os-prober had crashed but that I was barred from lodging a bug report for some reason; the message vanished before I could record its actual content. You must indeed have put your finger on the underlying problem.

If Grub2 can't recognise existing Grub-based Linux installations (bearing in mind that many major distros have yet to make the decision to move to Grub2) then Ubuntu's well-earned reputation for robustness and inter-operability is going to take a bit of a hit.

I don't think there should be anything unusual about Mint, which is very much an Ubuntu derivative (and all the better for that).

---

### Post by plun on 2009-08-15
Os-prober got an update today
[https://lists.ubuntu.com/archives/karmic-changes/2009-August/006231.html](https://lists.ubuntu.com/archives/karmic-changes/2009-August/006231.html)


If it doesn't work, file a bug !!!! This forum doesn't solve it !

```
ubuntu-bug os-prober
```

---


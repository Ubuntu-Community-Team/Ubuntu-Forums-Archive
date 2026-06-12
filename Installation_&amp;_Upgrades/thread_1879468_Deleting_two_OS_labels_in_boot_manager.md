---
title: "Deleting two OS labels in boot manager"
date: 2011-11-11
forum: Installation &amp; Upgrades
---

### Post by cheerPuncH on 2011-11-11
Hi!

On my laptop I have dually installed Windows7 and Ubuntu 10.04. In the boot manager of my laptop (where it lists the OS you can choose) the following is listed.

```
Ubuntu, with Linux 2.6.32-35-generic
Ubuntu, with Linux 2.6.32-35-generic (recovery mode)
Ubuntu, with Linux 2.6.32-35-generic
Ubuntu, with Linux 2.6.32-35-generic (recovery mode)
Ubuntu, with Linux 2.6.32-35-generic
Ubuntu, with Linux 2.6.32-35-generic (recovery mode)
Windows Vista
Windows 7
```.

Now I'm not exactly sure why Vista is there, but it probably has something to do with Win7. If you're keen, you probably noticed that Ubuntu is listed 3 times. I believe this is attributed to my installing mistake where I left the USB in the laptop for, well, 3 restarts. I wanted to know if there was a way if i could get rid of the extra two listed in the boot manager. I thought maybe somewhere under system, administration.... I can't seem to find a way to do it. Maybe you do!

Any feedback would be helpful.

Thanks in Advance!

---

### Post by darkod on 2011-11-11
Without more data we don't know what is what, but if you suspect there are entries that don't exist the first command to run is to update the grub.cfg file (to rediscover the OSs on the disk):

sudo update-grub

See if that removes something from the list.

---

### Post by drs305 on 2011-11-11
I don't use Windows but I believe W7 incorporates it's boot files into the existing Vista folder to some degree and that is what Grub 2 is detecting.

Probably the easiest way to hide an OS or other entry you don't want to see is to install and use Grub Customizer. It was designed after the introduction of Grub 2 and does a variety of Grub 2 tweaking very well. 

You can learn more about it by clicking the 'Customizer' link in my signature line.

Also, if you remove the USB before running the update-grub command it may remove those extra entries (if you don't need the USB inserted to boot).

---

### Post by cheerPuncH on 2011-11-11
Okay so I tried it. I got this in response. I rebooted the computer and they are all still there. I worried that if I delete one, it might do some damage. I just installed Ubuntu (this is a new computer) so it wouldn't hurt too much to uninstall it and re-install it.

<code>jeri@jeri-laptop:~$ sudo update-grub
[sudo] password for jeri: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-35-generic
Found initrd image: /boot/initrd.img-2.6.32-35-generic
Found linux image: /boot/vmlinuz-2.6.32-34-generic
Found initrd image: /boot/initrd.img-2.6.32-34-generic
Found linux image: /boot/vmlinuz-2.6.32-33-generic
Found initrd image: /boot/initrd.img-2.6.32-33-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
Found Windows Vista (loader) on /dev/sda4
done
jeri@jeri-laptop:~$ </code>

---

### Post by darkod on 2011-11-11
Your second post is not the same as your first one. :)

2.6.32-35 is not the same as 2.6.32-34. As you update kernel by kernel, ubuntu does not automatically remove them. That's why you have -33, -34 and -35 while they are all 10.04 I believe.

The Win7 loader is your win7 and the vista loader is your recovery partition. The windows recovery partitions have boot files on them which are located by the grub search and entered as separate boot entry.

PS. Do not boot that entry on /dev/sda4 unless you want your computer deleted. I am not sure if you boot it from grub menu it will ask you for confirmation before starting the factory default recovery. It depends how it's set up.
But if you ever want your computer as it was when you bought it, you can run it and it should recover it to the original state.

---

### Post by cheerPuncH on 2011-11-11
drs305. I just unchecked the second two Ubuntu's in Grub. I'm going to give it a reboot and see what I get.

---

### Post by cheerPuncH on 2011-11-11
Worked like a charm. Thanks!

---


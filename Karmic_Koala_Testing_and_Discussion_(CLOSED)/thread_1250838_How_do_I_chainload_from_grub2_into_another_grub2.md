---
title: "How do I chainload from grub2 into another grub2?"
date: 2009-08-27
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by todak on 2009-08-27
I have two hard drives on my system. The first one has Ubuntu 9.04 with grub2. The second has Kubuntu 9.10 A4 with grub2. Whenever a kernel update is installed in Kubuntu, it will auto-update its grub to boot with the newest kernel; I wish to be able to restart and go to a menu entry from the grub2 on the MBR of the first drive that will load the newest kernel with whatever distro I am running on my second drive (yes, I know about kexec-tools and how to use that, but that is not my point). As it is now, I have to load Ubuntu 9.04, then run update-grub to get it to recognize the new kernel on Kubuntu 9.10, then reboot and select the newest kernel in Kubuntu 9.10. Not a very elegant solution! What is the proper file to edit in grub2 on my first (Ubuntu 9.04) drive? In grub legacy, I just gave the second drive a title of "whatever" and then told it root was (hd1,0) and then chainload +1. That was it. No matter what distro I ran on the second drive, I would select the "whatever" entry in my grub menu and it would load with the newest kernel on the second drive by default. Is there a way to chainload similarly using grub2?

---

### Post by dino99 on 2009-08-27
Like you, i have 3 hdd with grub2 on each & several distro.
Now with last upgrades, everything is smootly reconized as os-prober is used.

---

### Post by ssam on 2009-08-27
but with out chainloading when one of the other OS updates is kernel the ubuntu's grub on the MBR won't know about it.

chainloading is the only sane way to do a multiboot linux system.

---

### Post by StephenDavison on 2009-08-31
> **todak said:**
> .
.
.
What is the proper file to edit in grub2 on my first (Ubuntu 9.04) drive? In grub legacy, I just gave the second drive a title of "whatever" and then told it root was (hd1,0) and then chainload +1. That was it. No matter what distro I ran on the second drive, I would select the "whatever" entry in my grub menu and it would load with the newest kernel on the second drive by default. Is there a way to chainload similarly using grub2?

The chainload entry should go in  /etc/grub.d/40_custom.  You may also want to consider putting any 'other os' entries in there too, and then chmod -x /etc/grub.d/30_os-prober to disable it.  That way you'll avoid your MBR grub2 from including entries for Kubuntu 9.10 kernels on the second hard drive.

My setup is Ubuntu 9.04 on /dev/sda1 with Grub2 installed to the MBR, Windows XP installed on /dev/sda2, and finally Ubuntu 9.10 alpha-4 installed in /dev/sda3 with it's own Grub2.  My /etc/grub.d/40_custom contains the menu entries below.  I also disabled 30_os-prober, and commented out recovery mode (single user) menu entry generating code from 10_linux.  

menuentry "Microsoft Windows XP" {
    set root=(hd0,2)
    chainloader +1
}
menuentry "Chainload Ubuntu 9.10 on /dev/sda3" {
    set root=(hd0,3)
    chainloader +1
}

---

### Post by todak on 2009-08-31
> **StephenDavison said:**
> The chainload entry should go in  **/etc/grub.d/40_custom**.  You may also want to consider putting any 'other os' entries in there too, and then chmod -x /etc/grub.d/30_os-prober to disable it.  That way you'll avoid your MBR grub2 from including entries for Kubuntu 9.10 kernels on the second hard drive.

My setup is Ubuntu 9.04 on /dev/sda1 with Grub2 installed to the MBR, Windows XP installed on /dev/sda2, and finally Ubuntu 9.10 alpha-4 installed in /dev/sda3 with it's own Grub2.  My /etc/grub.d/40_custom contains the menu entries below.  I also disabled 30_os-prober, and commented out recovery mode (single user) menu entry generating code from 10_linux.  

menuentry "Microsoft Windows XP" {
    set root=(hd0,2)
    chainloader +1
}
menuentry "Chainload Ubuntu 9.10 on /dev/sda3" {
    set root=(hd0,3)
    chainloader +1
}

AHA! 

```
menuentry "Chainload Ubuntu 9.10 on /dev/sda3" {
    set root=(hd0,3)
    chainloader +1
}
``` was just the command I was looking for (customised for my own layout, of course)! Many thanks. :KS

---

### Post by philinux on 2009-09-01
I think I might need this very soon. Cheers

---

### Post by rplantz on 2009-09-19
> **todak said:**
> AHA! 

```
menuentry "Chainload Ubuntu 9.10 on /dev/sda3" {
    set root=(hd0,3)
    chainloader +1
}
``` was just the command I was looking for (customised for my own layout, of course)! Many thanks. :KS

If I may add a little to this, I am chain loading OpenSolaris from Ubuntu 9.10. My Ubuntu is on one disk, OpenSolaris on another. With grub legacy my /boot/grub/menu.lst had the entry:
```

title           OpenSolaris
root            (hd1,0)
makeactive
chainloader     +1

```

With grub2 this becomes
```

menuentry "OpenSolaris" {
   set root=(hd1,1)
   chainloader +1
}

```
in /etc/grub.d/40_custom.

Two things to note about this:
1. Partitions are now numbered from 1 instead of 0.
2. "root" is now a variable, not a command.

Then I did
```

$ sudo cp -p /boot/grub/grub.cfg /boot/grub/grub.cfg_back
[s]$ sudo grub-mkconfig -o /boot/grub/grub.cfg[/s]
$ sudo update-grub

```
update-grub [s]grub-mkconfig[/s] will write over /boot/grub/grub/cfg, adding in the new entry in 40_custom. It's a good idea to back up the old copy first since this is a critical file.

---

### Post by todak on 2009-09-19
> **rplantz said:**
> If I may add a little to this, I am chain loading OpenSolaris from Ubuntu 9.10. My Ubuntu is on one disk, OpenSolaris on another. With grub legacy my /boot/grub/menu.lst had the entry:
```

title           OpenSolaris
root            (hd1,0)
makeactive
chainloader     +1

```

With grub2 this becomes
```

menuentry "OpenSolaris" {
   set root=(hd1,1)
   chainloader +1
}

```
in /etc/grub.d/40_custom.

Two things to note about this:
1. Partitions are now numbered from 1 instead of 0.
2. "root" is now a variable, not a command.

Then I did
```

$ sudo cp -p /boot/grub/grub.cfg /boot/grub/grub.cfg_back
$ sudo grub-mkconfig -o /boot/grub/grub.cfg

```
grub-mkconfig will write over /boot/grub/grub/cfg, adding in the new entry in 40_custom. It's a good idea to back up the old copy first since this is a critical file.

In my case I load grub onto the MBR, rather than the root partition of my (2nd) drive during the install. In this instance it contains Kubuntu Karmic. I use my main drive as my stable, everyday drive. The second drive is used for testing different distros. Therefore the grub2 menu of my Ubuntu (1st) drive shows ```
menuentry "Kubuntu, OpenSuse, OpenSolaris, Who knows?" {
   set root=**(hd1)**
   chainloader +1
```
and it works like a charm. Notice the root is **(hd1)**, not **(hd1,1)** as would be the case for grub being installed on the root partition. In this case, the **set root=** is where grub2 resides on the second drive, not necessarily the location of the root partition itself. I just started using grub2 and am still learning! :)

---

### Post by rplantz on 2009-09-20
> **todak said:**
> I just started using grub2 and am still learning! :)

Aren't we all?

I have edited my post to show that the proper way to implement changes in the /boot/grub/grub.cfg file is
```

$ sudo update-grub

```

Another change I made was in the /etc/default/grub file. I changed 
```

GRUB_DEFAULT=0

```
to
```

GRUB_DEFAULT=saved

```
Then I ran sudo update-grub. Now a reboot will default to the same OS entry as the last one I was running. You could also specify the number of an OS entry here (starting from 0).

---


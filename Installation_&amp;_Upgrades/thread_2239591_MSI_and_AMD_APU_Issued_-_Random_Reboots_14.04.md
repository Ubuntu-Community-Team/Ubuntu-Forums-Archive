---
title: "MSI and AMD APU Issued - Random Reboots 14.04"
date: 2014-08-14
forum: Installation &amp; Upgrades
---

### Post by tarmac515 on 2014-08-14
[FONT=arial]Ok, so I appear to be having issues with random reboots after changing a hard drive to an SSD. I am convinced that this is due to this bug:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1309578](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1309578)
I did manage to get 14.04 working ok before I swapped the hard drive by amending the graphics drivers but this does not appear to be doing the trick this time.

So as a few others are having issued with MSI boards and AMD APU chips I followed this advice:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1309578](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1309578)

Reading through this I kept the mouse moving throughout the install and it did the trick despite being a little bizarre. So I have installed 14.04.1 successfully I then continued to followed some advice on the post to:

"[COLOR=#333333]from the terminal type; gedit /etc/default/grub The file will open in the editor.
edit this line ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash 
```'[/COLOR]
[COLOR=#333333]to look like this; ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash noapic"
```[/COLOR]
[COLOR=#333333]then I ran - ```
sudo update-grub
```

But this still results in random reboots?

Anything I can change in grub or should i do:
```
apt-get install linux-image-generic-lts-saucy
```

Any help would be great![/COLOR]

[COLOR=#000000]
System spec:[/COLOR]
[COLOR=#000000]AMD A6-6400K APU dual core cpu[/COLOR]
[COLOR=#000000]64bit Ubuntu 14.04
[/COLOR]MSI M'board - A88XM-E35 (FM2)
[COLOR=#000000]Memory 4GB Corsair Value[/COLOR]
[COLOR=#000000]PNY SSD120GB[/COLOR][/FONT]

---

### Post by tarmac515 on 2014-08-16
[FONT=arial]So have been trying a few things

I replaced "noapic" with "acpi=off" which resulted in the pc rebooting everytime i shut it down and would not boot without recovery.

edited grub again to "noapic", then went to additonal drivers and changed to [COLOR=#333333]fglrx-updates graphics driver, which still resulted in reboots.[/COLOR]

tried to install lubuntu 14.04.1 as I read this worked OK, but was it just rebooted as soon as the desktop appeared[/FONT]

so then reinstalled ubuntu 14.04.1 again - went ok,

then tried to upgrade the kernel to 3.16.1 running these commands from here:[http://www.yourownlinux.com/2014/08/how-to-install-linux-kernel-3-16-1-in-linux.html](http://www.yourownlinux.com/2014/08/how-to-install-linux-kernel-3-16-1-in-linux.html)
but the final package was not available or wrong so I could not complete the upgrade. 

i'm guessing upgrading the kernel is going to be the easist way to solve?
Any ideas when 3.16 will be provided as an ubuntu update?

thanks,

code from: [http://www.yourownlinux.com/2014/08/how-to-install-linux-kernel-3-16-1-in-linux.html](http://www.yourownlinux.com/2014/08/how-to-install-linux-kernel-3-16-1-in-linux.html)

$ wget [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.16.1-utopic/linux-headers-3.16.1-031601_3.16.1-031601.201408140014_all.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.16.1-utopic/linux-headers-3.16.1-031601_3.16.1-031601.201408140014_all.deb)

$ wget [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.16.1-utopic/linux-headers-3.16.1-031601-generic_3.16.1-031601.201408140014_i386.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.16.1-utopic/linux-headers-3.16.1-031601-generic_3.16.1-031601.201408140014_i386.deb)

$ wget [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.16.1-utopic/linux-image-3.16.1-031601-generic_3.16.1-031601.201408140014_i386.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.16.1-utopic/linux-image-3.16.1-031601-generic_3.16.1-031601.201408140014_i386.deb)


$ sudo dpkg -i linux-headers-3.16.1*.deb linux-image-3.16.1*.deb 

(i'm assuming I can leave the * as a wildcard or do i need to specify?)

sudo reboot

---


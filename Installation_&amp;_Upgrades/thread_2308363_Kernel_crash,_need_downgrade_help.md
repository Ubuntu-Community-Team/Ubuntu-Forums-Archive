---
title: "Kernel crash, need downgrade help"
date: 2016-01-02
forum: Installation &amp; Upgrades
---

### Post by Steve_Horvath on 2016-01-02
I accepted the upgrade to **3.19.0-42** kernel upgrade packages through **Ubuntu Software cente**r.  Now server crashes in a few hours to perhaps a day max.  Would like to safely downgrade back to **3.19.0-41**.  I am scared to death that I will brick the server if I just uninstall the packages. I get a package dependency broken message when I mark them for complete removal.  Whats the right way to downgrade a kernel through Software Center? Will all the pointers, headers, dependencies, etc get reverted correctly if I uninstall a kernel version?(  FYI..I dont ever overclock and have run  memtest86 for days without failure on this hardware).  Any help is highly appreciated!

recent upgrade
[ATTACH=CONFIG]266508[/ATTACH]

previous upgrade
[ATTACH=CONFIG]266509[/ATTACH]

system: ASROCK Q1900-ITX motherboard with integrated CPU, PANRAM 16GB. no cards.
psensors/smart data stored every minute via cron job shows: CPU temp, HDDTEMP, voltages, etc all normal and below 40C at time of crash.
Crash seems more likely if desktop left open or locked (runlevel 5), but have not confirmed this yet...

---

### Post by oldos2er on 2016-01-02
What kernels do you have installed? ```
dpkg --list  | grep linux-image
```

---

### Post by Steve_Horvath on 2016-01-02
```
$ sudo dpkg --list | grep linux-image
ii  linux-image-3.19.0-25-generic                         3.19.0-25.26~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-30-generic                         3.19.0-30.34~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-32-generic                         3.19.0-32.37~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-37-generic                         3.19.0-37.42~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-39-generic                         3.19.0-39.44~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-41-generic                         3.19.0-41.46~14.04.2                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-42-generic                         3.19.0-42.48~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-25-generic                   3.19.0-25.26~14.04.1                                amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-30-generic                   3.19.0-30.34~14.04.1                                amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-32-generic                   3.19.0-32.37~14.04.1                                amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-37-generic                   3.19.0-37.42~14.04.1                                amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-39-generic                   3.19.0-39.44~14.04.1                                amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-41-generic                   3.19.0-41.46~14.04.2                                amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-42-generic                   3.19.0-42.48~14.04.1                                amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-generic-lts-vivid                         3.19.0.42.27                                        amd64        Generic Linux kernel image
```

---

### Post by oldos2er on 2016-01-02
You don't need "sudo" for that command. Since  linux-image-3.19.0-41-generic is still installed you should be able to reboot and choose it from the grub menu.

---

### Post by Steve_Horvath on 2016-01-02
thanks oldos2er !
Back booted the older kernel from Grub.  Works fine.  Cool that you can do that. I am going to let it ride for a few days.  If it doesn't crash,  seems like I should be able to set it permanently from grub.conf.

---

### Post by coldraven on 2016-01-03
I followed the advice in the first link to stay on an older kernel:
[http://ubuntuforums.org/showthread.php?t=2300290&p=13399995#post13399995](http://ubuntuforums.org/showthread.php?t=2300290&p=13399995#post13399995)

---

### Post by oldos2er on 2016-01-03
> **Steve_Horvath said:**
>   Works fine. 

Great! Could you please mark the thread as 'Solved' under Thread Tools at the top of the page? Thanks.

---

### Post by Steve_Horvath on 2016-01-03
Still running on the old kernel...I'll close this thread.  Thanks all for the help.

---

### Post by Steve_Horvath on 2016-01-03
for anyone else following this thread....
  **to boot into the grub menu**:  hold down the **"left shift key"** at the magic moment between BIOS finishing and the Ubuntu splash screen.  Might take a few tries or different timing.  From the GRUB menu, select "advanced options" and select a different kernel previously installed.  Once fully booted, type "uname -r" in a terminal to confirm the kernel version currently running.

---


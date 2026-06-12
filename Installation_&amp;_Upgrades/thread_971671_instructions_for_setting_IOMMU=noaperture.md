---
title: "instructions for setting IOMMU=noaperture"
date: 2008-11-05
forum: Installation &amp; Upgrades
---

### Post by fballem on 2008-11-05
Running 8.10 AMD64 with 4Gig RAM with an nvidia 8600 with 512meg video RAM. At startup, I'm getting a warning about setting IOMMU in BIOS, but I've also read that there is a configuration in the boot menu that will eliminate this warning. I am able to boot, but ubuntu does appear to be running slower in 64-bit mode than it did in 32-bit mode.

I am a relative newbie to linux and would very much appreciate specific instructions on how to correct the warning. In addition, what is the impact if I don't correct this.

Thanks,

---

### Post by fballem on 2008-11-06
Found it here: [http://ubuntuforums.org/showthread.php?t=911768&highlight=noaperture](http://ubuntuforums.org/showthread.php?t=911768&highlight=noaperture)

In a terminal:

```
sudo gedit /boot/grub/menu.lst
```

Once there, locate the line that starts with 'kernel' and add 'iommu=noaperture' to the end of the line.

Save the file, and then close gedit and the terminal.

Restart the computer.

---

### Post by fballem on 2008-11-06
Rats, the message still shows up!

Any other ideas would be much appreciated.

---

### Post by ubersolid on 2008-11-28
> **fballem said:**
> Found it here: [http://ubuntuforums.org/showthread.php?t=911768&highlight=noaperture](http://ubuntuforums.org/showthread.php?t=911768&highlight=noaperture)

In a terminal:

```
sudo gedit /boot/grub/menu.lst
```

Once there, locate the line that starts with 'kernel' and add 'iommu=noaperture' to the end of the line.

Save the file, and then close gedit and the terminal.

Restart the computer.

Thanks, it worked for me! :)

---

### Post by donsimon on 2008-12-04
I am having that same error message but can't follow the instructions to fix it because after the message I get the Ubunto loading screen and then my monitors go blank.

AMD64 bit
4G Ram
Nvidia video card

---

### Post by Izek on 2008-12-13
I think it's due to the lack of showing an example of how to add it correctly, I don't know how to add it correctly to the list.

```
title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		e1af5d58-4452-45a4-96ce-20445ec59834
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=e1af5d58-4452-45a4-96ce-20445ec59834 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		e1af5d58-4452-45a4-96ce-20445ec59834
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=e1af5d58-4452-45a4-96ce-20445ec59834 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		e1af5d58-4452-45a4-96ce-20445ec59834
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=e1af5d58-4452-45a4-96ce-20445ec59834 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		e1af5d58-4452-45a4-96ce-20445ec59834
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=e1af5d58-4452-45a4-96ce-20445ec59834 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		e1af5d58-4452-45a4-96ce-20445ec59834
kernel		/boot/memtest86+.bin
quiet
```

where and HOW do I add it? That message is a little annoying.

---

### Post by linux4me on 2008-12-13
I was getting the same error. Here is what you need to do. First, open Terminal by going Applications->Accessories->Terminal. Then enter the command:
```
sudo gedit /boot/grub/menu.lst
```
That will open the file menu.lst in Gedit for you to edit. 

Look for the section that looks like this:
> 
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

Add the "iommu=noaperture" so it looks like this:
> ## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash iommu=noaperture
Save your changes and exit Gedit. Now run the command:
```
sudo update-grub
```
If you want, you can then look in menu.lst again and you will find that the last command updated the kernel lines so that noaperture is appended in the appropriate places.

Reboot and the error should be history.

---

### Post by Izek on 2008-12-13
Thanks linux4me, it's gone now. ;)

---

### Post by mount_evans on 2009-02-08
I used iommu=noaperture when I installed 8.10 64-bit on my AMD 64 with 4GB of RAM.  I have since reverted to the 32-bit version of the operating system, since I don't think I will be doing any of the things for which 64 bits offers any benefit.  I have not put the statement in my menu.lst yet; should I just forget that the whole issue ever existed?  Or do I need to do something funny to utilize 4GB under the 32 bit operating system?

---

### Post by jschodde on 2010-01-05
This worked for me by editing /etc/default/grub (since I'm on Karmic with Grub2).

Before:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

After
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash iommu=noaperture"

I no longer get the error messages.

---

### Post by moz_21 on 2010-02-17
> **jschodde said:**
> This worked for me by editing /etc/default/grub (since I'm on Karmic with Grub2).

Before:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

After
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash iommu=noaperture"

I no longer get the error messages.

Thanks, this worked perfectly for me and fixed my comp from being unable to suspend!

---


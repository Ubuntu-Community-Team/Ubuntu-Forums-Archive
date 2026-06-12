---
title: "Start up error after upgrading to 8.10"
date: 2008-11-02
forum: Installation &amp; Upgrades
---

### Post by juny20 on 2008-11-02
Hello everyone! I was upgrading to Ubuntu 8.10 from 8.04. I did something wrong:I left the computer unattended for a few hours. When I came back, the screen was blank. I know all the components had downloaded and the installation was in progress when I left.

I am getting the following error right after boot up:

Starting up...
[    0.000000] ACPI: BIOS age (1999) fails cutoff (2000), acpi=force is required to enable ACPI
[    0.884544] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

Does anyone know what this could be? I was ready to re-install using the Kubuntu CD as I recently wiped out Windows out of my wife's laptop and is now running Kubuntu perfectly fine. My laptop is an old IBM Thinkpad, 600X with a Pentium III 600 MHZ, 512 Ram, and a 10 gig hard drive. Ubuntu 8.04 was running perfectly fine, flawlessly. I was also thinking about a minimal installation. Thanks in advance for any help you could provide.

---

### Post by taurus on 2008-11-02
Can you boot with the old kernel from 8.04?  Then, post your /boot/grub/menu.lst (without the lines that have # in front since those lines are comment) here.

Applications -> Accessories -> Terminal
```
sudo cat /boot/grub/menu.lst
```

---

### Post by juny20 on 2008-11-02
Actually, I can not fully boot into anything. I get the error message right after it says that grub is starting. I can not boot into 8.04 or 8.10.

---

### Post by juny20 on 2008-11-03
I wonder if I had to tweak the bios because of the error code? Also, if I start my laptop using the Kubuntu 8.10 live cd, can I extract information from the laptop that can tell me what the problem might be? If I need the Ubuntu live cd, I can download it as well.

---

### Post by taurus on 2008-11-03
If you can boot your machine from a LiveCD, then you can mount the partition where /boot is located, and look at /boot/grub/menu.lst to see if there is any typo in it, preventing the system to boot.

Assuming that the partition where /boot is located is /dev/sda1, do something like these from the LiveCD.

Applications -> Accessories -> Terminal
```
sudo mkdir /mnt/ubuntu
sudo mount -t ext3 /dev/sda1 /mnt/ubuntu
sudo cat /mnt/ubuntu/boot/grub/menu.lst
```

---

### Post by Scott.Mercer on 2008-11-03
Starting up...
[    0.000000] ACPI: BIOS age (1999) fails cutoff (2000), acpi=force is required to enable ACPI

I get the same error trying to boot using parrells

but if I boot into the disk error is not there

dont know what problem is hope this helps

---

### Post by juny20 on 2008-11-03
Ok, this is what I get when following this

sudo mkdir /mnt/ubuntu
sudo mount -t ext3 /dev/sda1 /mnt/ubuntu
sudo cat /mnt/ubuntu/boot/grub/men

Is there anything I should change/edit? I get the following:

title           Ubuntu 8.10, kernel 2.6.27-7-generic
root            (hd0,0)                             
kernel          /boot/vmlinuz-2.6.27-7-generic root=UUID=4669d126-78c5-40bd-8054-462ca69b8364 ro quiet splash                                                   
quiet                                                                           

title           Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root            (hd0,0)                                             
kernel          /boot/vmlinuz-2.6.27-7-generic root=UUID=4669d126-78c5-40bd-8054-462ca69b8364 ro single                                                         

title           Ubuntu 8.10, kernel 2.6.24-21-generic
root            (hd0,0)                              
kernel          /boot/vmlinuz-2.6.24-21-generic root=UUID=4669d126-78c5-40bd-8054-462ca69b8364 ro quiet splash                                                  
initrd          /boot/initrd.img-2.6.24-21-generic                              
quiet                                                                           

title           Ubuntu 8.10, kernel 2.6.24-21-generic (recovery mode)
root            (hd0,0)                                              
kernel          /boot/vmlinuz-2.6.24-21-generic root=UUID=4669d126-78c5-40bd-8054-462ca69b8364 ro single                                                        
initrd          /boot/initrd.img-2.6.24-21-generic                              

title           Ubuntu 8.10, kernel 2.6.24-19-generic
root            (hd0,0)                              
kernel          /boot/vmlinuz-2.6.24-19-generic root=UUID=4669d126-78c5-40bd-8054-462ca69b8364 ro quiet splash                                                  
initrd          /boot/initrd.img-2.6.24-19-generic                              
quiet                                                                           

title           Ubuntu 8.10, kernel 2.6.24-19-generic (recovery mode)
root            (hd0,0)                                              
kernel          /boot/vmlinuz-2.6.24-19-generic root=UUID=4669d126-78c5-40bd-8054-462ca69b8364 ro single                                                        
initrd          /boot/initrd.img-2.6.24-19-generic                              

title           Ubuntu 8.10, kernel 2.6.24-18-generic
root            (hd0,0)                              
kernel          /boot/vmlinuz-2.6.24-18-generic root=UUID=4669d126-78c5-40bd-8054-462ca69b8364 ro quiet splash                                                  
initrd          /boot/initrd.img-2.6.24-18-generic                              
quiet                                                                           

title           Ubuntu 8.10, kernel 2.6.24-18-generic (recovery mode)
root            (hd0,0)                                              
kernel          /boot/vmlinuz-2.6.24-18-generic root=UUID=4669d126-78c5-40bd-8054-462ca69b8364 ro single                                                        
initrd          /boot/initrd.img-2.6.24-18-generic                              

title           Ubuntu 8.10, kernel 2.6.24-17-generic
root            (hd0,0)                              
kernel          /boot/vmlinuz-2.6.24-17-generic root=UUID=4669d126-78c5-40bd-8054-462ca69b8364 ro quiet splash                                                  
initrd          /boot/initrd.img-2.6.24-17-generic                              
quiet                                                                           

title           Ubuntu 8.10, kernel 2.6.24-17-generic (recovery mode)
root            (hd0,0)                                              
kernel          /boot/vmlinuz-2.6.24-17-generic root=UUID=4669d126-78c5-40bd-8054-462ca69b8364 ro single
initrd          /boot/initrd.img-2.6.24-17-generic

title           Ubuntu 8.10, kernel 2.6.24-16-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-16-generic root=UUID=4669d126-78c5-40bd-8054-462ca69b8364 ro quiet splash
initrd          /boot/initrd.img-2.6.24-16-generic
quiet

title           Ubuntu 8.10, kernel 2.6.24-16-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-16-generic root=UUID=4669d126-78c5-40bd-8054-462ca69b8364 ro single
initrd          /boot/initrd.img-2.6.24-16-generic

title           Ubuntu 8.10, kernel 2.6.22-14-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=4669d126-78c5-40bd-8054-462ca69b8364 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 8.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=4669d126-78c5-40bd-8054-462ca69b8364 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 8.10, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
ubuntu@ubuntu:~$

---

### Post by taurus on 2008-11-03
Interesting that you don't have a "initrd" for 2.6.27-7-generic kernel.  Edit /mnt/ubuntu/boot/grub/menu.lst

```
gksudo gedit /mnt/ubuntu/boot/grub/menu.lst
```
and add this line 

```
initrd /boot/initrd.img2.6.27-7-generic
```
after the kernel entry and before the quiet.  It should look something like this for the first title.

```

title Ubuntu 8.10, kernel 2.6.27-7-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=4669d126-78c5-40bd8054-462ca69b8364 ro quiet splash
**initrd /boot/initrd.img2.6.27-7-generic**
quiet

```
Save it and reboot.  Now, see if you can boot Ubuntu from your harddrive.

---

### Post by juny20 on 2008-11-09
Unfortunately, I am still having problems. After reading many posts here, it seems that 8.10 had some bugs. As for me, it seems that the problems are cause by kernel 2.6.27-7-generic somehow, although I lack the skills to properly determine this. However, my Kubuntu laptop started having problems after a kernel update to this version as well! The problems are similar to the ones on my Ubuntu laptop. 

The funny thing is that I can start the laptop only using the 2.6.24-21-generic (recovery mode) kernel. I can only start the system using XFCE and not Gnome and I get an error message that HAL can not start? I can not connect to the internet, which limits my options of updating and upgrading the system. So, the saga continues for me. I am thinking about installing 8.04 back in the system as that was working flawlessly for me.

---


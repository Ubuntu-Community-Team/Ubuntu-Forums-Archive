---
title: "Updated and Grub : &quot;Load Kernel first&quot;"
date: 2010-03-25
forum: Installation &amp; Upgrades
---

### Post by LakatosI on 2010-03-25
So I have been using Ubuntu for the past couple of months using Wubi, mainly because my parent's are afraid that I'll screw something up on the computer if I partition the hard drive and stuff like that :P

And Today I installed the latest updates for 9.10, asked me to restart the computer, and now whenever I try to boot using the latest kernel BRUB keeps telling me to "Load kernel first". The funny thing is that I can boot with the older kernel fine, But I would really like to get the lates updates, which I can't using the older kernel. Can anyone help me out here?

---

### Post by tom4everitt on 2010-03-25
The boot entries are all in the file: /boot/grub/grub.cfg. In every boot entry there is a line: linux <name-of-a-kernel>

When that command fails, you get the "load kernel first"-error. 


Try running: 

sudo update-grub

it will regenerate the /boot/grub/grub.cfg file. (You can do that booting from an older kernel.)

---

### Post by LakatosI on 2010-03-25
Unfortunately this didn't solve my problem. I checked out the grub.cfg file, and The entries are absolutely the same for the new and the old kernel. 
```


### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
    insmod ntfs
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set e27c86fe7c86cd2b
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-20-generic root=/dev/sda5 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.31-20-generic
}

menuentry "Ubuntu, Linux 2.6.31-14-generic" {
    insmod ntfs
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set e27c86fe7c86cd2b
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda5 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.31-14-generic
}


```


What could be the problem?

---

### Post by tom4everitt on 2010-03-25
Strange. If you want you can check whether there actually is a kernel named vmlinuz-2.6.31-20-generic in /boot. 


One option would be to try reinstalling the kernel:
sudo apt-get remove --purge linux-image-2.6.31-20-generic       #To remove it
sudo apt-get install linux-image-2.6.31-20-generic              #To install it again.


If it still doesn't work you can try to install the second latest kernel:
sudo apt-get install linux-image-2.6.31-19-generic


Or just screw it and install the lucid beta instead :P

---

### Post by LakatosI on 2010-03-26
I already checked, vmlinuz-2.6.31-20-generic is already there :P

I guess I'll try reinstalling it, or installing the latest kernel.

And what's hat lucid beta?

---

### Post by tom4everitt on 2010-03-26
Lucid (or 10.04) is the Ubuntu version that will be released the 29th of April. So its not entirely done yet, but at least I am never patient enough to wait for something to be done to try it :P

Its available at [www.ubuntu.com](www.ubuntu.com) if you're interested.

---

### Post by alexandrosM on 2010-04-02
I am using wubi/ubuntu 9.10 and had the same problem. Booting with an older kernel and marking the newest kernel for reinstallation did the trick.

---

### Post by CaKiwi on 2010-04-03
I'm having this problem too. How do I mark the kernel for reinstallation?

---

### Post by CaKiwi on 2010-04-03
I went into synaptic and I think I accidently installed linux-2.6.31-20-generic-pae nstead of linux-2.6.31-20-generic. Now linux-2.6.31-20-generic-pae is the first entry in the grub menu and it boots sucessfully, What is pae and should I reinstall linux-2.6.31-20-generic? I have an AMD Athlon X2 with a 32 bit install if that is important

---

### Post by CaKiwi on 2010-04-03
I found that pae stands for physical address extension allowing the addressing of more than 4gb of memory on a 32bit system. I deleted linux-2.6.31-20-generic-pae and installed linux-2.6.31-20-generic and it is booting fine.

---


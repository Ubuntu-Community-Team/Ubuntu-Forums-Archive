---
title: "Booting Grub without UUID possible?"
date: 2008-08-22
forum: Installation &amp; Upgrades
---

### Post by Rallg on 2008-08-22
No problems, just a question. I have dual-boot Ubuntu 8.04 i386 and Vista, but this should apply to anything:

My system is configured so that Grub is not on the MBR. Instead, I have Grub4DOS on a USB stick. It seems that Grub4DOS does not care about UUID. If I copy out the Grub menu.lst from my Ubuntu partition, transfer it to the USB (changing hd0 to hd1), I can eliminate all references to UUID, and the boot works.

So, If I have Ubuntu on the third partition of several different computers, the same USB boot will work for all of them, even though different UUIDs are involved.

It is also possible to install Grub to USB from within Ubuntu. But this would not be Grub4DOS, it would be Linux Grub. I've tried it and it works, BUT it seems that the UUID is necessary. If I have several computers, I would need to put separate entries for each on menu.lst, and if I lose a UUID, the only way to recover is to use the live CD to learn the UUID for each device.

Here is my question: Can Linux Grub (the kind used by Ubuntu) boot using a menu.lst WITHOUT any UUID? If so, what is the trick?

---

### Post by Neo_The_User on 2009-03-09
Yes you can. A compiled kernel from /usr/src and not installed as a .deb package.

Like this

```

cd /usr/src
sudo wget (kernel source)
sudo tar zxf or sudo tar xjf (kernel source)
cd (kernel source)
sudo make menuconfig or sudo make xconfig
sudo make clean && sudo make && sudo make modules_install
sudo cp arch/x86/boot/bzImage /boot/vmlinuz-custom
sudo nano /boot/grub/menu.lst

```

Most important part is here:

Title Custom Kernel
root (hd0,0) or whatever is yours
kernel /boot/vmlinuz-custom root=/dev/sda1 ro (replace sda1 with your linux partition)

Hit Control+O to write out (i think or Control+W i forget) then reboot into your custom kernel.

Building the kernel like this is how you WOULD normally go about to do it the "Ubuntu Way" and WITH UUID.

```

make-kpkg clean
fakeroot --initrd --revision=custom kernel_image kernel_headers kernel_source
sudo dpkg -i your_kernel_image
sudo dpkg -i your headers
sudo dpkg -i kernel source
sudo update-grub

```

This thread is a bit old but I just wanted to help since you helped me out so much.

---

### Post by maybeway36 on 2009-03-11
I'd think you could just change the "uuid xxxxxxxxxxxxx" to "root (hdx,x)" and be done with it.

---

### Post by Neo_The_User on 2009-03-11
> **maybeway36 said:**
> I'd think you could just change the "uuid xxxxxxxxxxxxx" to "root (hdx,x)" and be done with it.

You don't put root (hdx,x) on the kernel line. Has to be identified with /dev/sdx and it cannot be unpacked as a deb package.

---


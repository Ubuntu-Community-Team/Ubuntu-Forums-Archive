---
title: "Problem in Configure grub boot loader"
date: 2013-09-15
forum: Installation &amp; Upgrades
---

### Post by mavik1 on 2013-09-15
Hi,

I have patched the kernel with rt patch and compiled properly.
linux-3.10.4.tar.xz
patch-3.10.4-rt1.patch.bz2

Now, i am facing problem in configuring using grub.
i added new entry in grub.cfg

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "RTLinux (RealTime Kernel)"{
    ecordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root (hd0, msdos7)
    kernel /boot/rtzImage ro root = /dev/hda3
    
}
### END /etc/grub.d/40_custom ###

When i select RTLinux in grub it's giving error.
Is this menuentry is correct?
Can any one, help me out here.

Thanx.

---

### Post by carl4926 on 2013-09-15
Are you sure /dev is hda not sda

---

### Post by danjohansen on 2013-09-15
as carl4926 says, make sure that your bootpartition is called hda. Most drives these days are SATA drives and are therefore named sda instead.

---

### Post by mavik1 on 2013-09-15
thanx, for replay.

no effect after change to sda7.

Here i copied 
cp arch/i386/boot/bzImage     /boot/rtzImage


here is existing linux kernel entry

menuentry 'Ubuntu, with Linux 3.5.0-39-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set=root 915d7ae6-d6d2-49f6-9268-53807a97a9c7
    linux    /boot/vmlinuz-3.5.0-39-generic root=UUID=915d7ae6-d6d2-49f6-9268-53807a97a9c7 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.5.0-39-generic
}

how to write for new Kernel?

---

### Post by carl4926 on 2013-09-15
Just wondering why you need a custom entry
If update grub (and the kernel is already built to the system) it will get picked up

---

### Post by mavik1 on 2013-09-15
Existing kernel is not real time kernel

i took fresh copy of linux kernel and realtime patched.
 linux-3.10.4.tar.xz
patch-3.10.4-rt1.patch.bz2

i want to work on this new kernel.

---

### Post by oldfred on 2013-09-15
Is initrd not required? Do not know real time systems.

Also looks like you have a space after the root? Or is just how you typed it here?

---

### Post by grahammechanical on 2013-09-15
Just a couple of points that may help you.

hdo = first hard disk msdos7 = partition 7 What we would call sda7. Also you should rename 40-custom to something like 15-custom then update-grub will put it into the menu after the Ubuntu menu entry and before the memtest entries. And the script must be executable. That is important.

You also need to run

```
sudo update-grub
```
```
sudo grub install /dev/sda
```

You may already know these things. I am just passing on things I learned from my failures. You can also copy the existing menu parameters and then modify them. So, you can use this and change the bits that I have underlined.

> menuentry '_Ubuntu, with Linux 3.5.0-39-generic_' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set=root 915d7ae6-d6d2-49f6-9268-53807a97a9c7
    linux    /boot/_vmlinuz-3.5.0-39-generic_ root=UUID=915d7ae6-d6d2-49f6-9268-53807a97a9c7 ro   quiet splash $vt_handoff
    initrd    /boot/_initrd.img-3.5.0-39-generic_
}

You can replace vmlinuz-3.5.0-generic with your modified kernel. This modified kernel must of course be in /boot/ with all the other kernels. When experiments do not work out the way we plan it is sometimes good to review the steps we need to take. Even the obvious steps.

Regards.

---

### Post by deadflowr on 2013-09-15
You could probably give us the output of 
```
ls /boot
```

And I'm not sure the ro flag should be before the root=/boot line.

---

### Post by Quackers on 2013-09-15
Just for your information in your first post in your output of/etc/grub.d/40_custom there is a r missing from the start of recordfail

---

### Post by mavik1 on 2013-09-16
> **deadflowr said:**
> You could probably give us the output of 
```
ls /boot
```

And I'm not sure the ro flag should be before the root=/boot line.

marvik@marvik-Vostro-1015:~$ ls /boot
abi-3.5.0-23-generic         memtest86+.bin
abi-3.5.0-39-generic         memtest86+_multiboot.bin
config-3.5.0-23-generic      rtzImage
config-3.5.0-39-generic      System.map-3.5.0-23-generic
grub                         System.map-3.5.0-39-generic
initrd.img-3.5.0-23-generic  vmlinuz-3.5.0-23-generic
initrd.img-3.5.0-39-generic  vmlinuz-3.5.0-39-generic

---

### Post by mavik1 on 2013-09-16
deadflower,

marvik@marvik-Vostro-1015:~$ ls /boot -l
total 52692
-rw-r--r-- 1 root root   856743 Jan 25  2013 abi-3.5.0-23-generic
-rw-r--r-- 1 root root   861474 Aug 14 21:20 abi-3.5.0-39-generic
-rw-r--r-- 1 root root   154436 Jan 25  2013 config-3.5.0-23-generic
-rw-r--r-- 1 root root   154713 Aug 14 21:20 config-3.5.0-39-generic
drwxr-xr-x 3 root root     8192 Sep 15 21:47 grub
-rw-r--r-- 1 root root 15361194 Sep  6 03:34 initrd.img-3.5.0-23-generic
-rw-r--r-- 1 root root 15529435 Sep  6 03:39 initrd.img-3.5.0-39-generic
-rw-r--r-- 1 root root   176764 Nov 27  2011 memtest86+.bin
-rw-r--r-- 1 root root   178944 Nov 27  2011 memtest86+_multiboot.bin
-rw-r--r-- 1 root root  5219648 Sep 11 17:10 rtzImage
-rw------- 1 root root  2421090 Jan 25  2013 System.map-3.5.0-23-generic
-rw------- 1 root root  2420797 Aug 14 21:20 System.map-3.5.0-39-generic
-rw-r--r-- 1 root root  5237968 Feb 14  2013 vmlinuz-3.5.0-23-generic
-rw------- 1 root root  5233168 Aug 14 21:20 vmlinuz-3.5.0-39-generic

---

### Post by deadflowr on 2013-09-16
Something tells me it didn't install right.
Which of the various compile and installation methods did you use?
since you seem to be, as oldfred pointed out, missing the crucial initrd file.

---

### Post by mavik1 on 2013-09-19
thanx for response,

removed everything and 
here i again installed ubuntu-12.04.3-desktop-i386 

followed steps to install rtlinux

1) linux-3.10.4.tar.xz
    patch-3.10.4-rt1.patch.bz2
   compressed in /usr/src

 2) /usr/src/linux-3.10.4
     and applyed the patch.
     patch -p1 </usr/src/patch/patch-3.10.4-rt1.patch 

3) Configuring the Kernel
    cd /usr/src/linux-3.10.4
    cp /boot/config-3.8.0.29-generic .config
    make menuconfig CC=/usr/bin/gcc-4.6.3 CXX=/usr/bin/g++-4.6.3

4) configuration
    Selected the default options

5) Compiling the kernel
    apt-get install kernel-package fakeroot
    make-kpkg clean
    fakeroot make-kpkg --initrd --app\end-to-version=-rtai \kernel_image kernel\_headers
after complie
    cd /usr/src
    dpkg -i *.deb

Grub

root@marvik-Vostro-1015:~# sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.10.4-rtai-rt1
Found initrd image: /boot/initrd.img-3.10.4-rtai-rt1
Found linux image: /boot/vmlinuz-3.8.0-29-generic
Found initrd image: /boot/initrd.img-3.8.0-29-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done

next how do i have to 
configure and complie RTLinux?

thanx.

---

### Post by deadflowr on 2013-09-19
I don't understand your question, because it seems you've already configured and compiled the rt patch as per the listing of your update-grub shows.

---

### Post by mavik1 on 2013-09-20
i mean how  to start and run RTLinux apps?
how to test weather RTLinux is working.

---

### Post by su:bhatta on 2013-09-20
You can install grub with

```

sudo update-grub
sudo grub-install /dev/sda
```

Then at the boot screen choose the RTLinux option, that will load Ubuntu using the RTLinux kernel.If you are unsure which entry has the RT kernel use 'e' & see what kernel it is showing.

Once OS loads check your kernel version with 

```
uname -r
```

Then try out whatever apps you want that uses the RT kernel.

It should be fine.

Also, if everything is fine, you can delete the generic kernel using Synaptic Package Manager, 
just search for 'linux-image' and it should list both -3.10.4-rtai-rt1 & 3.8.0-29-generic

Mark 3.8.0-29-generic for complete removal, and then do (NOTE IMPORTANT: Please ensure you remove the generic kernel when you are booted to the RT Kernel)

```
sudo update-grub
```

---

### Post by deadflowr on 2013-09-20
It would seem that actually getting the rt kernel to work would be a separate issue than getting it to boot.
I'd suggest starting a new thread in the development and programming sub-forum for that
[http://ubuntuforums.org/forumdisplay.php?f=310](http://ubuntuforums.org/forumdisplay.php?f=310)

As you'd probably get better help there, as it would seem to be a highly specialized function, beyond something general users would know.
I'm a general user enough to be able to admit I have no idea what the rt kernel is suppose to do.

But posting in dev/programming, some one there might have better knowledge.

---

### Post by mavik1 on 2013-09-21
thanx [**[COLOR=#000000]bhattabhishek[/COLOR]**]("http://ubuntuforums.org/member.php?u=1819052") 

i did not understood to delete the generic kernel.
if it is not removed, does it cause problem in dev RT apps?

---

### Post by su:bhatta on 2013-09-21
Hi mavik1,
 firstly,  Did you get the Rt kernel working for you & are your RT applications running better with it?

There is no problem if the generic kernel stays, you just have to choose the RT kernel from the bootloader every time you startup, in case the RT kernel is not the default choice in  the bootloader screen.

The generic kernel uses nearly 100 odd MB space, that is all, which you might want to free up.

Also, I use UbuntuStudio(Official Ubuntu flavor), which is optimized for most audio,video,3D rendering processing apps and UbuntuStudio comes with a lowlatency kernel instead of RT kernel. What kind of applications are you using? 

You can give UbuntuStudio a go and find out if it suits you better and out-of-the-box, then you don't have to build your own RT patches from scratch.

You can get Ubuntu Studio from here : [http://ubuntustudio.org/download/](http://ubuntustudio.org/download/)
Also, if you are experimenting a little and do not mind Bugs and reporting them then you can download the latest Ubuntu Studio 13.10 Beta from here : [www.ubuntustudio.org]("http://www.ubuntustudio.org"), just follow the links.

---

### Post by mavik1 on 2013-09-21
thanx [**[COLOR=#000000]bhattabhishek[/COLOR]**]("http://ubuntuforums.org/member.php?u=1819052"),


To work on ARM based development i installed RTLinux.
I could not find header files like rtl_time and so on, where from i have download?
i patched patch-3.10.4-rt1.patch.bz2 is this correct RT patch?
how to test weather RTLinux is working or not?
Any qucik start guide on RT Linux dev?

thanx

---

### Post by su:bhatta on 2013-09-22
Sorry mavik1, way out of my domain...

Got a few links : [http://www.arm.com/community/software-enablement/linux.php](http://www.arm.com/community/software-enablement/linux.php) & [http://www.linux.com/news/featured-blogs/200-libby-clark/710319-intro-to-real-time-linux-for-embedded-developers](http://www.linux.com/news/featured-blogs/200-libby-clark/710319-intro-to-real-time-linux-for-embedded-developers)

Surely you will find a way to get things working. Also, I suggest if there is any arm community boards do explore them as those will be a guide for you.

Best of luck,

---


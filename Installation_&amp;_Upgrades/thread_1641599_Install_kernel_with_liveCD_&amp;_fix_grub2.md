---
title: "Install kernel with liveCD &amp; fix grub2"
date: 2010-12-09
forum: Installation &amp; Upgrades
---

### Post by afrodeity on 2010-12-09
I seem to be in a sticky situation.

I ran a script called ubuclean and it removed all my kernels. Now I boot up right into the memory test.

I am trying to find an easy way to reinstall my kernel using the LiveCD and possibly update or fix grub2

From what I can gather this means mounting my file system and chrooting?

I can mount /dev/sda1 /mnt

and 

mount --bind /dev/pts /mnt/dev/pts
mount --bind /proc /mnt/proc
mount --bind /sys /mnt/sys

But not sure if this is right and what is the easiest way of reinstalling the kernel?

Apititude doesn't show any available kernels?

---

### Post by drs305 on 2010-12-09
You are on the right track about chrooting.

You can go to the link in my signature line for "G2-Chroot" for the commands. Since you will be installing a kernel, make sure the LiveCd you are using is the same as your installed OS. If it's not, before you chroot you will need to change your /etc/apt/sources.list "main" repository to the version you are trying to install the kernel to.

Once chrooted, just run:```

sudo apt-get update
sudo apt-get install linux-image
sudo update-grub
```

---

### Post by afrodeity on 2010-12-09
Thanks, it installs the kernels but update-grub is having a problem:

```
cannot find a device for / (is dev mounted?)
```

Not sure how to get dev mounted properly

If i try to 

```
mount --bind /dev /mnt/dev 
```

It says mount point /mnt/dev does not exist. What am i doing wrong?

---

### Post by afrodeity on 2010-12-09
Ok, I followed your tutorial, it was quite intimidating, but this is the part I needed to follow

```

sudo mkdir /mnt/temp 
sudo mount /dev/sdXY /mnt/temp  # Example: sudo mount /dev/sda5 /mnt/temp
### Run the next two commands only if you have a separate /boot partition
sudo mkdir /mnt/temp/boot
sudo mount /dev/sdXZ /mnt/temp/boot  # Example: sudo mount /dev/sda6 /mnt/temp/boot  (sda6 is the /boot partition)
###
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/temp$i;  done
sudo cp /etc/resolv.conf /mnt/temp/etc/resolv.conf  # May be required to connect to the Internet.
sudo chroot /mnt/temp
```

Will reboot and see

UPDATE: Works like a charm, but not exactly like mounting OSX is it?

---

### Post by Insperatus on 2011-02-26
> **drs305 said:**
> You are on the right track about chrooting.

You can go to the link in my signature line for "G2-Chroot" for the commands. Since you will be installing a kernel, make sure the LiveCd you are using is the same as your installed OS. If it's not, before you chroot you will need to change your /etc/apt/sources.list "main" repository to the version you are trying to install the kernel to.

Once chrooted, just run:```

sudo apt-get update
sudo apt-get install linux-image
sudo update-grub
```

I deleted my kernel only to realize what I had done after rebooting.  Using your tips I reinstalled my kernel with a live cd (natty alpha 2 of all things!)

I used gparted to identify which partition I have unbuntu installed on (could have done it from the CLI I know) and then:

```
sudo mkdir /mnt/temp 
sudo mount /dev/sdXY /mnt/temp  # Example: sudo mount /dev/sda5 /mnt/temp
```

```
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/temp$i;  done
sudo cp /etc/resolv.conf /mnt/temp/etc/resolv.conf  # May be required to connect to the Internet.
sudo chroot /mnt/temp
```

```
sudo apt-get update
sudo apt-get install linux-image
sudo update-grub
```

  
This is what worked for me.  Thank you SO much! I love the fact that I could fix this from the CLI without having to reinstall like a noob.  GNU/LINUX is AWESOME!

---

### Post by yrohinkumar on 2012-04-28
Thanks a million chrooting works great! :)

---

### Post by tedrogers on 2013-02-22
> **Insperatus said:**
> I deleted my kernel only to realize what I had done after rebooting.  Using your tips I reinstalled my kernel with a live cd (natty alpha 2 of all things!)

I used gparted to identify which partition I have unbuntu installed on (could have done it from the CLI I know) and then:

```
sudo mkdir /mnt/temp 
sudo mount /dev/sdXY /mnt/temp  # Example: sudo mount /dev/sda5 /mnt/temp
```

```
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/temp$i;  done
sudo cp /etc/resolv.conf /mnt/temp/etc/resolv.conf  # May be required to connect to the Internet.
sudo chroot /mnt/temp
```

```
sudo apt-get update
sudo apt-get install linux-image
sudo update-grub
```

  
This is what worked for me.  Thank you SO much! I love the fact that I could fix this from the CLI without having to reinstall like a noob.  GNU/LINUX is AWESOME!

I did exactly the same thing, as part of my periodic spring-cleaning, but like an idiot I deleted the kernel I was running at the time, rebooted and my ubuntu was gone from grub2! :confused:

At first I thought it was Grub 2 that was messed up, so went about fixing that. It was only later that I realised that I had borked it by removing my kernels.

Thank you so much for this chroot trick. I didn't understand much of it, but I knew my root partition was /sda3...which was enough for me to use along with pasting the code you provided in order.

My next and last resort was to reinstall like a noob...thanks for saving me the hassle. ):P

---


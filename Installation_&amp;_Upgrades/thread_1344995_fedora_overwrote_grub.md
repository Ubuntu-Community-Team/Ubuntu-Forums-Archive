---
title: "fedora overwrote grub"
date: 2009-12-03
forum: Installation &amp; Upgrades
---

### Post by GamesForLinux on 2009-12-03
When I installed Ubuntu 9.10, it was a fresh install, but with a separate partition for the home directory from Ubuntu 8.10 and a partition for Fedora 10. It added Fedora to the list of choices to boot from, but it didn't work. No big problem, because there wasn't anything important there, and I was planning on installing Fedora 12.

Fedora 12 installed, but overwrote grub with no choice to boot to Ubuntu. Editing the menu.lst file this is what I came up with:
```
title Fedora (2.6.31.5-127.fc12.x86_64)
	root (hd0,1)
	kernel /boot/vmlinuz-2.6.31.5-127.fc12.x86_64 ro root=UUID=02eee3ae-0422-4758-8ee5-14a0252d6d6b noiswmd LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYBOARDTYPE=pc KEYTABLE=us rhgb quiet
	initrd /boot/initramfs-2.6.31.5-127.fc12.x86_64.img
title Ubuntu-3-root-sda3
	root (hd0,3)
	kernel /boot/vmlinuz-2.6.31-15-generic ro root=/dev/sda3
	initrd /boot/initrd.img-2.6.31-15-generic
```
This gets the computer to try to boot Ubuntu, but it just drops to a busybox terminal, and I'm lost as to what else to do the menu.lst

To make sure some things are clear - the title (Ubuntu-3-root-sda3) has some unneccesary stuff in it that just refers to stuff I was playing with, so that I could add a bunch of different things and successivly boot each one and see the differences. 
Second, my hard drive is partitioned as follows:
Partition 1: 2GiB of swap for Ubuntu
Partition 2: 18GiB of Fedora
Partition 3: 116GiB of /home for Ubuntu
Partition 4: 13GiB of / for Ubuntu

I'd really appreciate any mistakes pointed out in my custom menu.lst. Thanks for any help I can get!

---

### Post by darkod on 2009-12-03
I don't know to create custom entry for 9.10 but the beauty of the new grub2 coming with 9.10 is that it detects other OSs automatically. Unless you have a good reason, I would reinstall grub2 again. You seem to know that your 9.10 is on /dev/sda4 so the command would be (boot with ubuntu cd and select Try Ubuntu, then open terminal):
sudo mount /dev/sda4 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

Job done. I guess it will detect Fedora 12 and all the rest.

---

### Post by coffeecat on 2009-12-03
> **GamesForLinux said:**
>  I'd really appreciate any mistakes pointed out in my custom menu.lst. Thanks for any help I can get!

Here's one:

> **GamesForLinux said:**
> ```
title Ubuntu-3-root-sda3
    root (hd0,3)
    kernel /boot/vmlinuz-2.6.31-15-generic ro root=/dev/sda3
    initrd /boot/initrd.img-2.6.31-15-generic
```

Fedora 12 uses legacy grub, so sda3 will be (hd0,2). Edit your root line and you should be able to boot into Ubuntu.

It's confusing, isn't it? That (hd0,3) would be correct in grub 2.

**Edit:** just noticed your partition list. If you mean that your Ubuntu root partition is on sda4, then (hd0,3) is correct, but 'root=/dev/sda3' in the kernel line doesn't match, so change that to 'root=/dev/sda4'.

---

### Post by GamesForLinux on 2009-12-03
Thanks Darko! That restored my old configuration perfectly!
Unfortunately, it still only shows Fedora 10 when it boots, and it still doesn't work. I added the Fedora 12 lines to /etc/grub.d/40_custom but that doesn't add anything to the boot list.

coffeecat: You're right, sda3 would be (hd0,2). But, sda3 is the /home, and the root partition is sda4, which would be (hd0,3). Besides, I already tried with (hd0,2) :)

---

### Post by coffeecat on 2009-12-03
> **GamesForLinux said:**
> 
coffeecat: You're right, sda3 would be (hd0,2). But, sda3 is the /home, and the root partition is sda4, which would be (hd0,3). Besides, I already tried with (hd0,2) :)

Yes - look at my edit. It was your kernel line that was wrong. Anyway, it's hypothetical now if you've got it going with grub2. Much better! Enjoy! :)

---

### Post by oldfred on 2009-12-03
I copied this from someone who said they got Fedora working with this ( you will have to adjust versions, partitions & UUIDs:

menuentry "Fedora 2.6.31.5 on sda7" {
    recordfail=1
    if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set a2cb340e-b3df-44e3-a602-52d0cb1201c5
    linux /boot/vmlinuz-2.6.31.5-127.fc12.x86_64 root=UUID=a2cb340e-b3df-44e3-a602-52d0cb1201c5 ro         quiet splash
    initrd /boot/initramfs-2.6.31.5-127.fc12.x86_64.img
}

---

### Post by darkod on 2009-12-03
> **GamesForLinux said:**
> Thanks Darko! That restored my old configuration perfectly!
Unfortunately, it still only shows Fedora 10 when it boots, and it still doesn't work. I added the Fedora 12 lines to /etc/grub.d/40_custom but that doesn't add anything to the boot list.

coffeecat: You're right, sda3 would be (hd0,2). But, sda3 is the /home, and the root partition is sda4, which would be (hd0,3). Besides, I already tried with (hd0,2) :)

Did you run
sudo update-grub

after editing 40_custom? Grub2 needs you to run that after any config setting change.

And why would it show Fedora 10 that you don't have any more? Can that be the entry for 12?

---

### Post by GamesForLinux on 2009-12-03
sudo update-grub worked! It added Fedora 12 and removed of Fedora 10. Now the dual boot works perfectly! Thanks!!

And, coffeecat, sorry, I see that now. That would probably have fixed it. Thanks.

---


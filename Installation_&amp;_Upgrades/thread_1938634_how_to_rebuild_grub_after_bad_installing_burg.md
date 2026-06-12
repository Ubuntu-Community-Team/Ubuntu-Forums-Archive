---
title: "how to rebuild grub after bad installing burg??"
date: 2012-03-10
forum: Installation &amp; Upgrades
---

### Post by hamidhqs on 2012-03-10
i've just installed burg with following commands but after restarting system, it shows only a command screen with " grub: "  prompt and i cant log in my system. i have ubuntu11.10 and windows 7 installed on my system.

```
sudo add-apt-repository ppa:n-muench/burg
sudo apt-get update
sudo apt-get install burg burg-themes

```
the next command:
```
# burg-install /dev/sda --no-floppy
```i just entered to continue....:( 
what should i do now to have my grub again and come back to ubuntu??
tnx

---

### Post by darkod on 2012-03-10
If you never removed grub2 or its files, first try simple reinstalling the part on the MBR. Lets assume your root partition is /dev/sda5 (use the correct one in the first command). You only need to run from live mode:

```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

If that doesn't work, the next option is to enter the hdd installation with chroot, purge burg completely and reinstall grub2 completely.

---

### Post by hamidhqs on 2012-03-10
how should i know if i removed grub2?? when i was in ubuntu i just used those codes to install burg.offcourse just now i know i didn't chose which device to install burg in!!! i mean the window asked me to chose "dev/sda" i just entered and continue....
in "grub>" prompt don't know what to do....
may you plz guide me a lil simpler.
tnx

---

### Post by darkod on 2012-03-10
Try the mentioned two commands first. Restart and see if it worked.

If not, thee is a more complicated approach for complete reinstall.

---

### Post by hamidhqs on 2012-03-10
i did those commands and the shell returned 
Installation finished . No error reported

but when i restart, the burg page is changed to grub page and there is no OS i can chose!!
but  "grub>" prompt.

my partitions are safe in linve cd when i use command " fdisk -l "..
what should i do now??
tnx for your help

---

### Post by darkod on 2012-03-10
OK, then it looks like the grub files (or some of them) are gone during the burg install. To enter your hdd installation with chroot, boot live mode again and do:
```
sudo mount /dev/sda5 /mnt
sudo mount --bind /proc /mnt/proc
sudo mount --bind /dev /mnt/dev
sudo mount --bind /sys /mnt/sys
sudo chroot /mnt
```

Now you are inside the installation as root. Remove grub, burg, and reinstall grub:
```
apt-get remove --purge burg burg-themes grub-pc grub-common
apt-get install grub-pc
grub-mkconfig
update-grub
grub-install /dev/sda
```

That should reinstall it and recreate new config files. Exit the chroot, unmount all:
```
exit
sudo umount /mnt/sys
sudo umount /mnt/dev
sudo umount /mnt/proc
sudo umount /mnt
```

Restart and check if it worked.

---

### Post by hamidhqs on 2012-03-10
when i type
sudo mount --bind /sys /mnt/sys
it alarms: 
mount: mount point /mnt/sys does not exist

im using ubuntu 11.4 live cd. doesn't it make any problem?

---

### Post by darkod on 2012-03-10
Hmm, and the three commands before that one execute without errors?

---

### Post by hamidhqs on 2012-03-11
ye.. they execute without errors!!! now the burg page has been chanegd to grub page( yet with "grub>" prompt) but the main problem exist yet.

sth else: because i have the boot partition,i used those commands like this: "/mnt/boot" instead of solitary "/mnt". 
this that i use ubuntu 11.4 live cd to fix ubuntu 11.10 grub, does matter??

and now what should i do just now??
tnx

---

### Post by darkod on 2012-03-11
Of course it matters if you have separate /boot man. Give us the info in advance.

With this new info, maybe the short version (the two commands from post #2) might work. Just add a third command in between the two in post #2 it is:

```
sudo mount /dev/sd? /mnt/boot
```

Use the correct partition number instead of the ? for your boot partition. But you still have to mount root since it is the main system partition.

Also, in the chroot procedure after mounting root at /mnt you also need to mount boot at /mnt/boot as a second command. After that you can continue.

As for using the 11.04 cd to restore 11.10 grub2, in the latest ubuntu releases it says you need to use a cd of the same version if using the short procedure. If you use the longer chroot procedure it doesn't matter.

Just DO NOT forget that you always need to mount boot at /mnt/boot after mounting root at /mnt when you have separate /boot partition.

---

### Post by hamidhqs on 2012-03-11
thank you man!! it's true now!!!! mer30
the only thing left now is that in grub page i have 3 ubuntu 11.10 and their recovery modes. i think it's bcz i've installed grub times!!! how i can remove two of them? not only those lines in grub page but also their files in system file...?
thanks in advance:)

---


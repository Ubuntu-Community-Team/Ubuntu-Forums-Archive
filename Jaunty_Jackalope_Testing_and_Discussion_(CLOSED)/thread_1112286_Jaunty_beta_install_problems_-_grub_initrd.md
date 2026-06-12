---
title: "Jaunty beta install problems - grub initrd"
date: 2009-03-31
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by bpalmer4 on 2009-03-31
When I had completed the Jaunty (x86-64) beta install process (on my Gigabyte EX38-DS5, E8600 box) I was greeted with grub error 15 - file not found.

I went through the complete install process again, with the same result. For some inexplicable reason, the Jaunty beta live-CD did not install the grub boot loader, nor did it create the initrd. I had to do it manually.

If there are others with this problem - (roughly from memory) these are the steps I went through (be warned, they are not for a newbie).

(1) Boot up the live-CD to use Ubuntu.

(2) Fire up the terminal program.

(3) Mount your Jaunty root drive (for me it was /dev/sda2)

     sudo mount -t ext3 /dev/sda2 /mnt

(4) Give yourself access to /dev and /proc once we change root (chroot)

     sudo mount --bind /dev /mnt/dev
     sudo mount --bind /proc /mnt/proc

(5) Now let's give ourselves a root shell based on /mnt as /

     sudo chroot /mnt

(6) Have a look in /boot - for me the grub directory was missing as was the initrd image

     ls -l /boot

(7) Make the /boot/grub directory

     mkdir /boot/grub

[8] Create a menu.lst file in /boot/grub

     update-grub

(9) Unfortunately, this created a poor /boot/grub/menu.lst file. Which I had to edit. In my case, the root file system was wrong - I replaced (hd0,0) with (hd0.1) - which maps to /dev/sda2 in my case. It also did not have the address of the initrd file (which I had to put in). Use your favourite editor to change the relevant bit of the menu.lst file to look like the following (use the right hd address for your situation).

     title		Ubuntu jaunty (development branch), kernel 2.6.28-11-generic
     root		(hd0,1)
     kernel		/boot/vmlinuz-2.6.28-11-generic root=/dev/sda2 ro quiet splash
     initrd		/boot/initrd.img-2.6.28-11-generic

(10) Next I installed grub

     grub-install

(11) Then I created the initrd file

     update-initramfs -c

(12) At this point you should be able to boot properly. But before you do, check that the initrd image file in /boot matches the entry in /boot/grub/menu.lst.

(13) Once I had rebooted, I discovered that synaptic was not working properly; so I did the following from a terminal

     sudo apt-get update
     sudo apt-get dist-upgrade

Now all seems fine.

---

### Post by markbuntu on 2009-03-31
I had the same problem with the live cd. There is a pile of bug reports at launchpad about this. You might have gotten a crash report if you could get to a desktop.

What happens during the install is that migration assitant can crash ubiquity and so grub is not installed at all. If you select manual partitioning you get no option to turn migration assistant off so if you have a few different distros this will happen to you.

I have 6 distros on my machine, some of them are broken/abandoned. There is no way migrations assistant would work successfully but it was also absolutely necessary to use manual partitioning soo...

To get around this is fairly easy but not very apparent. Run the live cd and then open a terminal and type ubiqity --no-migration-assistant. The installer will run as usual and skip migration assistant and install grub properly.

This happened to me with Alpha5 and Alpha6 and is apparently a regression since there are old bug reports about this happening with Hardy. I have not tried Beta and probably won't but it looks like it is still not fixed. Maybe you should comment on that at one of these.

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/234835](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/234835)

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/329614](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/329614)

---


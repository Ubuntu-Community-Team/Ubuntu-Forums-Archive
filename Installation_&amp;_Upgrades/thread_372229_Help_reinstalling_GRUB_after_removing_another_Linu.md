---
title: "Help reinstalling GRUB after removing another Linux installation"
date: 2007-02-27
forum: Installation &amp; Upgrades
---

### Post by shellhrs on 2007-02-27
I triple boot with W2K, Fluxbuntu, and Dreamlinux (installed in that order). Since my harddisk is very limited in size (6 GB), I decided to remove Dreamlinux to make space for another Linux flavor.

The problem is that Dreamlinux installed GRUB replacing Fluxbuntu's. Now, if I am to remove Dreamlinux, it would certainly cause booting error, because GRUB wouldn't be able to find /boot/grub/menu.lst file in Dreamlinux root partition. I've checked Fluxbuntu's root partition, and its /boot/grub/menu.lst file still exist. (I would like to use this file.)

So, I guess the only solution was to reinstall GRUB (in MBR, as before). I've searched around, and there are to suggestions out there. The first:

> 1. Boot your computer up with Ubunto CD
2. Go through all the process until you reech "[!!!] Disk Partition"
3. Select Manual Partition
4. Mount your appropriate linux partions

/
/boot
swap
.....

5. DO NOT FORMAT THEM.
6. Finish the manual partition
7. Say "Yes" when it asks you to save the changes
8. It will give you errors saying that "the system couldn't install ....." after that
9. Ignore them, keep select "continue" until you get back to the Ubuntu installation menu
10. Jump to "Install Grub ...."
11. Once it is finished, just restart your computer

The other is:

> 1. Pop in the Live CD, boot from it until you reach the desktop.
2. Open a terminal window or switch to a tty.
3. Type "grub"
4. Type "root (hd0,6)", or whatever your harddisk + boot partition numbers are (my /boot is at /dev/sda7, which translates to hd0,6 for grub).
5. Type "setup (hd0)", ot whatever your harddisk nr is.
6. Quit grub by typing "quit".
7. Reboot.

Now, I maybe wrong, but the first method mention that I should restart the computer after it finished. Is it after the program finished installing GRUB, or after it finished installing all the Ubuntu installation files? Will I be able to use Fluxbuntu LiveCD instead?

If I use the second method, I can find out my boot partition from the /boot/grub/menu.lst entry for Fluxbuntu, right? So step number 4 shouldn't be a problem.

Is there any other way to restore GRUB while maintaining the use of my Fluxbuntu /boot/grub/menu.lst file?

---

### Post by mikewhatever on 2007-02-28
The fist method does not reinstall Ubuntu.
> It will give you errors saying that "the system couldn't install ....." after that
9. Ignore them, keep select "continue" until you get back to the Ubuntu installation menu

At the end of the process, you'll actually be asked to reboot, so that's easy.
Another method to reinstall GRUB is with Super Grub CD, but really, how many do you need?

---

### Post by shellhrs on 2007-03-01
I tried the first method, but the only LiveCD I have at the moment was Fluxbuntu and Dreamlinux. Both don't have grub command. Maybe they do, but when I tried the command in terminal (I even tried using tty), the error message appeared saying command not found.

I ended up trying the second method. It worked perfectly. And it is much faster compared to booting the LiveCD.

If anyone interested, this is how I did it. First, I list the partition using fdisk. I noted the location of the Fluxbuntu partition. This is really necessary to avoid any error later. Just a note: you have to use "sudo fdisk -l" if  you want to get any result. Then, just follow the steps in my first post. Oh yeah, you have to "sudo grub" too.

By the way, I still have all the partitions intact before I run those steps. I booted to Fluxbuntu using Dreamlinux's grub, and then use Eterm to perform the steps. Then I rebooted. After making sure that grub used the /boot/grub/menu.lst file in Fluxbuntu's root partition, not Dreamlinux's, I deleted Dreamlinux partition using GParted LiveCD. -- I need to say this because threads I read usually advised using either of those two methods from LiveCD.

---

### Post by mikewhatever on 2007-03-01
Thanks for the follow up.

---


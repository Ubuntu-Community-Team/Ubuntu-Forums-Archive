---
title: "Removed old kernel - Shows no kernel in boot menu"
date: 2011-02-15
forum: Installation &amp; Upgrades
---

### Post by bipin.nag on 2011-02-15
I was using ubuntu 10.04 (dual boot with win 7) and i had several kernel versions installed from updates (6 to be exact). I decided to remove last 4 versions from synaptic manager. But on restarting ubuntu does **NOT** boot - **doesn't show any kernel or kernel rescue option from boot menu**, just an option for win 7 loader. 

On advance menu it shows grub command line :(:sad::sad:
I have no experience of using grub command line and all my data is locked within ubuntu disk, I cannot access it from Windows 7.

PLEASE HELP ME :x
I won't try anything smart with kernel ever again

[IMG]file:///C:/Users/bipin/AppData/Local/Temp/moz-screenshot.png[/IMG]

---

### Post by PaulReaver on 2011-02-15
I know for a fact it is possible to restore this :)

you'll need to boot into a ubuntu live cd 
"chroot" into your hard disk and install a kernel.  then reinstall grub on the hard disk....

---

### Post by PaulReaver on 2011-02-15
boot into an ubuntu live cd.

important double check where your ubuntu / partition is  (IT WON'T BE SDA1 IF YOU INSTALLED WINDOWS FIRST)  change * for partition number.... 'disk utility' is useful for this..... system/administration/disk utility... NTFS partitions will be windows

sudo mkdir /mnt/temp 
sudo mount /dev/sda* /mnt/temp
sudo chroot /mnt/temp

sudo apt-get update
sudo apt-get install linux
sudo update-grub

exit

sudo shutdown -r now.


and i think this should maybe just about fix your ubuntu install....not 100% sure though.....

---

### Post by bipin.nag on 2011-02-16
Thanks for replying
I did manage to boot,I followed your instructions and reinstalled the kernel version
But there is slight problem in that
On update-grub there is no new kernel entry in the grub.cfg file
Is it normal ? because it was blank (except for win 7 loader entry) before reinstalling the kernel on live session which I suppose is causing the problem.

I had to manually enter the kernel menu entry to my original wubi installation by mounting its root.disk and changing grub.cfg 
 
For now it boots from wubi but again updating grub does not show any new kernel entry in grub.cfg
grub updating generates grub.cfg without any kernel entries
:frown: I have to check my grub.cfg for entries every time before restart or it wont boot.

---

### Post by bipin.nag on 2011-02-21
Can anyone help me out : The problem still remains

update-grub command does not detect my kernel 
i had to modify 40_custom file in /etc/grub.d to add the kernel entry into boot menu so that i can boot

but this is just makeshift : if i update my kernel and delete the previous one it will show the error again

---

### Post by coffeecat on 2011-02-21
> **bipin.nag said:**
> update-grub command does not detect my kernel

Do you mean that update-grub run in the chroot environment does not detect your kernel?
 
> **bipin.nag said:**
>  i had to modify 40_custom file in /etc/grub.d to add the kernel entry into boot menu so that i can boot

but this is just makeshift : if i update my kernel and delete the previous one it will show the error again

Not quite. **If** you have a working entry in 40_custom and **if** that entry appears in your grub menu and **if** you can boot into Ubuntu with it, then boot into Ubuntu and run 'sudo update-grub'. If you do, grub should pick up your kernel and parse 40_custom as well so that you'll get two entries for your kernel. If the automatically added one works, then simply remove 40_custom and run sudo update-grub again.

The reason that update-grub in the chroot environment didn't detect the new kernel is that there were a few extra mount commands needed for that to happen. When doing a chroot it's usual to mount the host  /dev/, /dev/pts, /sys/ and /proc/ into the chroot environment. Offhand I can't remember which you need for update-grub to work properly, but it was the absence of one or more that caused update-grub to fail.

---

### Post by bipin.nag on 2011-02-24
kernel installation in chroot environement worked fine --that's not the problem
i was able to boot into my wubi using the entry i had created in 40_custom --its alright 

my problem is --after booting into original partition grub update does not detect the new kernel ,no new entries are added in to the grub.cfg file on updating
that is the reason i had to modify grub.cfg , 40_custom --to show my new kernel into the menu

i am not sure why it is not detecting anything but it happened after i deleted/reinstalled  kernel
also it takes too much time to boot (around 30 secs)

---

### Post by Habeouscorpus on 2011-02-24
Never mind.

---

### Post by bipin.nag on 2011-02-24
Any help would be appreciated .

---


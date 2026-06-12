---
title: "Disable framebuffer from Grub Meno or Launch ubuntu comand line"
date: 2010-03-14
forum: Installation &amp; Upgrades
---

### Post by popolvar on 2010-03-14
Hello all,

let us start with the problem. After making and update my Karmic Koala and trying to set up lamp through tasksell, i have rebooted my notebook. Then the ubuntu logo was displayied and i get an

"Ubuntu is eunnung in low graphics mode"
(EE) open /dev/fe0: No such file or dierctory

i have done some googling and figured that it has most likely to do with ubuntu tryin to using frame buffer wrongly. I have tried to follow some advices posted at 

[https://wiki.ubuntu.com/FrameBuffer#Setting%20different%20framebuffer%20resolutions%20in%20GRUB]("https://wiki.ubuntu.com/FrameBuffer#Setting%20different%20framebuffer%20resolutions%20in%20GRUB")

like this


[LIST]
[*]"vga=normal", or "nofb", disables the framebuffer
[*]if "nofb" does not help, try "nomodeset" to disable kernel mode setting
[*]"vga=ask" will able you to set a value at each boot good for testing out the various modes.
[/LIST]
non of them worked. Than i thought i run grub2 (in fact it is 1.97~beta4), so i tried to run this

[http://crunchbanglinux.org/wiki/howto/adjust_grub2_framebuffer](http://crunchbanglinux.org/wiki/howto/adjust_grub2_framebuffer)

to set at least the right resolution to the frame buffer. However i put there a wrong resolution (my mistake obviously). The problem is that now all the screen turns black (after i select the system in Grub menu) and i can't see the command line, so i am helpless.

So now i get to GRUB menu, i can edit the line by hitting 'e' and i get 

recordfail=1
if [ -n ${have_grubenv} ]; then save_env recordfail; fi
set quiet=1insmod ext2
set root=(hd0,5)
search --no-floppy --fs-uuid --set c763a81d-d00b-4880-9111-9c305affc67b
linux   /boot/vmlinuz-2.6.31-20-generic root=UUID=c763a81d-d00b-4880-9111-9c305affc67b ro   quiet splash
initrd  /boot/initrd.img-2.6.31-20-generic

so this is right now everything i can edit, and i would need either to set/remove the framebuffer or get back the commandline somehow so i can do the trick through /etc/default/grub.

Any ideas? Pleas hope i am quite desperate

i have tried to put into the kernel/linux line

'nomodeset'
'nofb'
'i915.modeset=0' at various places
remove 'quiet'
put the 'nosplash' 'nomodeset'
put there 'single'

use Ctrl-Alt_F1 and Ctrl-Alt-Esc to get the console (However i run vista as a dual boot so i have pressed the key after selecting the system)
recovery more also yields a black screen

Nothing has worked so far.

Pleassse help

popolvar

---

### Post by popolvar on 2010-03-15
ok i was able to fix the problem with the wrong resolution, that is i can use console again

i have booted from life CD, and followed the instructions from [https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

$ sudo fdisk -l 

[LIST]
[*]Now, you need to remember which device listed is your linux distribution, for reference, /dev/sda1 will be used. Now we need to mount the filesystem to /mnt 
[/LIST]
$ sudo mount /dev/sda1 /mnt 

[LIST]
[*]If you have /boot on a separate partition, that need's to be mounted aswell.  For reference, /dev/sda2 will be used. 
[/LIST]
$ sudo mount /dev/sda2 /mnt/boot *Make sure you don't mix these up, pay attention to the output of FDISK* 

[LIST]
[*]Now mount the rest of your devices 
[/LIST]
$ sudo mount --bind /dev /mnt/dev 

[LIST]
[*]Now chroot into your system 
[/LIST]
$ sudo chroot /mnt 
You should be chroot'd into your system as root, you can now run commands as root, without the need for sudo. 

[LIST]
[*]Now you need to edit the **/etc/default/grub** file to fit your system 
[/LIST]
$ nano /etc/default/grub 

[LIST]
[*]When that is done you need to run **update-grub** to create the configuration file. 
[/LIST]
$ update-grub 

[LIST]
[*]To install GRUB 2 to the MBR, next you need to run **grub-install /dev/sda** 
[/LIST]

$ sudo umount /mnt/dev 

[LIST]
[*]Now you can unmount the root system. (But if you have a separate boot partition which you mounted earlier, you have to unmount this first, or you will get a "device busy" error message.) 
[/LIST]
$ sudo umount /mnt 

[LIST]
[*]And you should be free to restart your system right into GRUB 2 and then into your system installation.  
[/LIST]
If you had alternate OS entries, update-grub might say "Cannot find list of partitions!". Ignore it and continue - once you can boot into your linux installation, do so and then rerun update-grub and grub-install /dev/sda as root.

i still have the low graphics problem with missing /dev/fb0 but i will post it separately.

---


---
title: "An odd boot screen"
date: 2006-10-31
forum: Installation &amp; Upgrades
---

### Post by SB42 on 2006-10-31
So, I recently upgraded from Dapper to Edgy, and I think I have fixed most things that were broken.  But I am left with an odd boot screen.  I have attached an image of it.  I tried reinstalling usplash, and the default usplash boot screen.  I also tried switching it with usplash-switcher, program I found referenced in another post.  

Any information is useful, since all attempts to change it have failed.

I think I might just have to break down and do a fresh install.

Thanks in advance

---

### Post by ciscosurfer on 2006-10-31
This is the usplash I got after upgrading from Dapper to Edgy.  Subsequent updates fixed this.  Try issuing from a terminal```
sudo aptitude update && sudo aptitude dist-upgrade
```All one line..you can just copy and paste.

---

### Post by SB42 on 2006-11-01
Thanks for the suggestion, but no luck.

---

### Post by ciscosurfer on 2006-11-01
Have you tried changing your usplash via update-alternatives?  You can see which ones you have installed by issuing```
sudo update-alternatives --config usplash-artwork.so
```If you have multiple usplash's installed (and configured under alternatives) you can choose which one you'd like running.  Just follow the prompts.  After you select one, it will say something like the following:
[B]
Using `/usr/lib/usplash/usplash-theme-youselected.so' to provide `usplash-artwork.so'.[/B]  

Once that has been written to the screen, in order to use it, you need to reconfigure your linux-`uname -r` by issuing the following:```
sudo dpkg-reconfigure linux-image-$(uname -r)
```You can copy and paste if you like.  The output will look something like this:

[B]Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.17-10-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.17-10.33 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.17-10.33 was configured last, according to dpkg)
Running postinst hook /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Testing for an existing GRUB menu.list file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.17-10-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

[/B]You'll need to modify your /boot/grub/menu.lst file after that has completed:
Add vga= to your kernel line in your GRUB menu.lst file.  Load it up by running```
sudo gedit /boot/grub/menu.lst
```Go to your boot kernel and add one of the following to the end of the line (you can also add to a section above to keep it there permanently -- every time you update your kernel, update-grub will overwrite anything you've modified between the area that says AUTOMAGICALLY ADDED......to do this, you should add the vga= line here:

[B]## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash vga=791
[/B]
DON'T REMOVE THE POUND SIGNS...the double's stand for comments, the single pound means "read this in".  Otherwise, add it to your kernel line shown below.

FYI:
vga = 785 (for standard vga)
vga = 788 (for 800x600)
vga = 791 (for 1024x768) *
vga = 794 (for 1280x1024)

===
From your /boot/grub/menu.lst file:

...

[SIZE=-1]title Ubuntu, kernel 2.6.15-23-386
root (hd0,0)
kernel /boot/vmlinuz-2.6.15-23-386 root=/dev/hda1 ro quiet splash **vga=791**
initrd /boot/initrd.img-2.6.15-23-386
[/SIZE]
[SIZE=-1]...[/SIZE]


You can also look at [this thread]("http://ubuntuforums.org/showthread.php?t=180924"), it discusses an alternative usplash, allows you to download it, and explains how it changes/effects your alternatives.

You can also [download it at the UDSF]("http://doc.gwos.org/index.php/Serengeti_Usplash_for_Dapper") (a different, more current usplash alternative)

Let me know if I can help on any of this or if you'd like me to upload the files necessary for you to download.

---

### Post by seatea on 2006-11-01
You might look at this bug report, [HTML]https://launchpad.net/distros/ubuntu/+source/usplash/+bug/60621[/HTML], and try the part that includes:

```
sudo gedit /etc/usplash.conf
```

> # Usplash configuration file
xres=1024
yres=768

save and close

```
sudo update-initramfs -u
```, then restart. I don't know that much about grub, but you may need to remove the quiet reference in your grub configuration if you  want to see text.

---

### Post by SB42 on 2006-11-01
Thanks for all the help, but I ended up just doing a new install.  Luckily I had /home on its own partition, so it was easy to backup everything.  

Now to reinstall all of my favorite programs.

---


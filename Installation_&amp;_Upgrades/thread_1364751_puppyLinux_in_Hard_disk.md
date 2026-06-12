---
title: "puppyLinux in Hard disk"
date: 2009-12-26
forum: Installation &amp; Upgrades
---

### Post by chuina on 2009-12-26
Hi, 
I'm using Karmic and RHEL5.
Using Karmic's grub for booting.

I've downloaded PuppyLinux-4.3.1.iso.
I read this linux install in a flash drive.

But since i have enough space left. So, i wish to install it in 
hard disk, with current Karmic's grub using.

(I've only one hard disk)

So, what is the steps ?

Thanks.

---

### Post by phillw on 2009-12-26
You'll need to make some room for puppylinux. Use your LiveCD to boot into and then use that to make some room.

Following these instructions will pop puppy linux on --> [http://www.puppylinux.com/hard-puppy.htm](http://www.puppylinux.com/hard-puppy.htm)

I've never used it. If it borks your ubuntu Grub, then re-set your grub following this link

[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

> [SIZE=5][COLOR=red]How to restore the Ubuntu grub bootloader (9.10 and beyond)[/COLOR][/SIZE]

Since Ubuntu 9.10 uses Grub 2, the above method will not work. However, it can still be done and this is how:
 First you need to find out what your drives are called. You can do this by going to a terminal and typing:  	Code:
 	sudo fdisk -l 
 You will get something like this:


[IMG]http://talsemgeest.doesntexist.com/blog/wp-content/uploads/2009/09/SVR8XIL.JPG[/IMG]

From that you need to find the device name of your Ubuntu drive, something like “/dev/sda5&#8243;.
 So, still in the terminal, type:
 	Code:
 	sudo mkdir /media/sda5
sudo mount /dev/sda5 /media/sda5 
And then, to reinstall the grub:  	Code:
 	sudo grub-install --root-directory=/media/sda5 /dev/sda 
Push enter and you’re done! Of course you need to replace “/dev/sda5&#8243; and “/dev/sda” with what you found in the fdisk output.


Do make a note which your Ubuntu install is on - as the fdisk will find two areas of linux.
your puppylinux should see your existing /swap area & use it. But, as I say - I've never used it.

Hope that gets you running.

Regards,

Phill.

---

### Post by chuina on 2009-12-26
Thanks Phillw :KS,
I'll try and let you know the result.

---


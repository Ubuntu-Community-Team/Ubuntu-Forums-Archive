---
title: "can't boot Ubuntu after upgrade"
date: 2010-10-01
forum: Installation &amp; Upgrades
---

### Post by jimjing on 2010-10-01
I have a ubuntu 10.04 LTS and a Windows 7 installed on my laptop with wubi. everything worked well until i upgraded my ubuntu today (oct 1st).
After upgrade, i restarted ubuntu and chose ubuntu from the OS list. Right after that, my laptop restarted. No error showed. I have tried several times, same thing happened everytime.
Could anyone help me?
Thanks
I will wait online for reply.

Jim

---

### Post by sikander3786 on 2010-10-01
Can you still boot into Windows 7?

Can you see the Grub menu? What if you select the older kernel (if there) or the recovery mode?

---

### Post by jimjing on 2010-10-01
> **sikander3786 said:**
> Can you still boot into Windows 7?

Can you see the Grub menu? What if you select the older kernel (if there) or the recovery mode?
yes, i can still boot into my windows 7
no i can't see the grub menu. right after i chose ubuntu from OS list, the laptop will restart

Jim

---

### Post by bcbc on 2010-10-01
Are you referring to the 10.10 upgrade?

---

### Post by jimjing on 2010-10-01
> **bcbc said:**
> Are you referring to the 10.10 upgrade?
I don't think so. I remember it just some upgrades to the packages, not to ubuntu system.

---

### Post by bcbc on 2010-10-01
Do you have an ubuntu CD you can boot from i.e. a live CD, or perhaps a USB.

---

### Post by freddybob on 2010-10-01
Same thing has happened to my daughter's laptop.

Ubuntu 10.04 (64 bit) installed dual boot with Windows 7 using Wubi.

She installed updates (not an upgrade to 10.10) on Sep 30.

She now cannot boot Ubuntu, machine restarts whenever she tries.

Windows 7 still works.

---

### Post by bcbc on 2010-10-01
> **freddybob said:**
> Same thing has happened to my daughter's laptop.

Ubuntu 10.04 (64 bit) installed dual boot with Windows 7 using Wubi.

She installed updates (not an upgrade to 10.10) on Sep 30.

She now cannot boot Ubuntu, machine restarts whenever she tries.

Windows 7 still works.

First, you can back up the root.disk (that contains the entire ubuntu install and in the worst case, you can recover data from it). Back it up outside the \ubuntu directory (as this gets deleted if you uninstall/reinstall wubi). Usually it's found in c:\ubuntu\disks\root.disk  or change the drive letter as appropriate.

Then you can run the [bootinfoscript]("http://bootinfoscript.sourceforge.net") and post the results. It's not strictly required but it helps if you want explicit instructions. 

These are some fixes you could try in order of how much effort is required:
1. if you are getting error messages about loadfont, try this solution first: [http://ubuntuforums.org/showpost.php?p=9640093&postcount=30](http://ubuntuforums.org/showpost.php?p=9640093&postcount=30)

If that doesn't work,
2. boot from a live cd and chroot into the wubi, run "update-grub" (in this example I am assuming the ubuntu folder is on /dev/sda2 - so change if nec.):
EDIT: <commands cut> (you can't run update-grub in a chroot for wubi installs)

If that doesn't work,
3. Make sure you copied that root.disk somewhere outside c:\ubuntu.
Uninstall and reinstall wubi.
Copy over the new root.disk using the backup.

---

### Post by freddybob on 2010-10-02
> **bcbc said:**
> Then you can run the [bootinfoscript]("http://bootinfoscript.sourceforge.net") and post the results. It's not strictly required but it helps if you want explicit instructions.

thanks, here's the result of bootinfoscript

---

### Post by bcbc on 2010-10-02
> **freddybob said:**
> thanks, here's the result of bootinfoscript

I had a similar problem with a maverick install that I tried to fix last night. There is something in grub.cfg that is causing the grub to reboot the computer. I got around it by booting from a live CD and editing my grub.cfg. It's not a fix, it's a temporary workaround (as grub.cfg will be regenerated eventually automatically and manual changes will be lost).

This is what I suggest.
Boot from a live CD, mount the wubi install and edit grub.
```
sudo mkdir /media/win
sudo mount /dev/sda5 /media/win
sudo mount -o loop /media/win/ubuntu/disks/root.disk /mnt
sudo cp /mnt/boot/grub/grub.cfg /mnt/boot/grub/grub.cfg.copy
gksudo gedit /mnt/boot/grub/grub.cfg
```

Just remove everything from grub.cfg but leave the following:
```
menuentry "Ubuntu, Linux 2.6.32-25-generic" {
	insmod ntfs
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set b8c201cacedda917
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-25-generic root=/dev/sda5 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.32-25-generic
}

```
Reboot and it should work.

If you install a new kernel, or uninstall an old one, or run sudo update-grub then grub.cfg will be regenerated and your changes will be lost. Maybe by then there;ll be some fix for this.

---

### Post by freddybob on 2010-10-02
thanks for your help, I'm getting an error when I try that

```
ubuntu@ubuntu:~$ sudo mkdir /media/win
ubuntu@ubuntu:~$ sudo mount /media/win /dev/sda5
mount: /media/win is not a block device

```

---

### Post by jimjing on 2010-10-02
> **bcbc said:**
> I had a similar problem with a maverick install that I tried to fix last night. There is something in grub.cfg that is causing the grub to reboot the computer. I got around it by booting from a live CD and editing my grub.cfg. It's not a fix, it's a temporary workaround (as grub.cfg will be regenerated eventually automatically and manual changes will be lost).

This is what I suggest.
Boot from a live CD, mount the wubi install and edit grub.
```
sudo mkdir /media/win
sudo mount /media/win /dev/sda5
sudo mount -o loop /media/win/ubuntu/disks/root.disk /mnt
sudo cp /mnt/boot/grub/grub.cfg /mnt/boot/grub/grub.cfg.copy
gksudo gedit /mnt/boot/grub/grub.cfg
```

Just remove everything from grub.cfg but leave the following:
```
menuentry "Ubuntu, Linux 2.6.32-25-generic" {
	insmod ntfs
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set b8c201cacedda917
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-25-generic root=/dev/sda5 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.32-25-generic
}

```
Reboot and it should work.

If you install a new kernel, or uninstall an old one, or run sudo update-grub then grub.cfg will be regenerated and your changes will be lost. Maybe by then there;ll be some fix for this.
Thanks for all your help.
I finally decided to install ubuntu on a partition of my HD instead of using wubi, since this is not the first time that wubi has a problem.
I used ext2explore to get what i want from the old ubuntu and finally had everything back to work. hopefully no more problem like this from now on.
Thanks for your help anyway

Jim

---

### Post by freddybob on 2010-10-02
ah I got it, should have been...

```
sudo mount /dev/sda5 /media/win

```

thank you bcbc

---

### Post by bcbc on 2010-10-02
> **jimjing said:**
> Thanks for all your help.
I finally decided to install ubuntu on a partition of my HD instead of using wubi, since this is not the first time that wubi has a problem.
I used ext2explore to get what i want from the old ubuntu and finally had everything back to work. hopefully no more problem like this from now on.
Thanks for your help anyway

Jim

You're welcome. Sorry it didn't work out, but you'll be happier with a regular install. Wubi + grub2 has been a bit flaky lately.

> **freddybob said:**
> ah I got it, should have been...

```
sudo mount /dev/sda5 /media/win

```

thank you bcbc
Yeah sorry about that - I got mixed up :)

PS if you go the regular install route I wrote a [howto]("http://ubuntuforums.org/showthread.php?t=1519354") to migrate a wubi to partition. Saves a bunch of time reconfiguring everything.

---

### Post by freddybob on 2010-10-02
> PS if you go the regular install route I wrote a howto to migrate a wubi to partition. Saves a bunch of time reconfiguring everything.

That's good to know, I probably will once 10.10 is released.

Thanks again.

---

### Post by Ephrem on 2010-10-28
Thanks a lot. Works fine.

---


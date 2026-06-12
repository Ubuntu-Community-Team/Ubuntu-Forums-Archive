---
title: "Triple boot: XP, Ubuntu, Ubuntu (and GRUB)"
date: 2010-01-06
forum: Installation &amp; Upgrades
---

### Post by drdf on 2010-01-06
I'm starting from scratch on a laptop, and would like to have two Ubuntu 9.10 installations, and one XP.  I've tried to do this a few times with no success (though I've had lots of success with the XP and Ubuntu dual boot combo).

Mostly I'm hoping that someone here could outline the preferred approach to doing this.

Currently I'm partitioning like:
ntfs     25 GB (Primary) Windows XP
ntfs     80 GB (Primary) shared data
Extended
   ext3  35 GB Ubuntu
   ext3  10 GB Ubuntu
   swap   6 GB

I install XP, then the first Ubuntu from the 9.10 LiveCD (to the 35 GB partition) and everything works fine.  But when I install the second Ubuntu, the system fails at the GRUB load.  I think I'm missing something basic here, but I've looked around for this info without success.
Thanks for any help...

---

### Post by presence1960 on 2010-01-06
> **drdf said:**
> I'm starting from scratch on a laptop, and would like to have two Ubuntu 9.10 installations, and one XP.  I've tried to do this a few times with no success (though I've had lots of success with the XP and Ubuntu dual boot combo).

Mostly I'm hoping that someone here could outline the preferred approach to doing this.

Currently I'm partitioning like:
ntfs     25 GB (Primary) Windows XP
ntfs     80 GB (Primary) shared data
Extended
   ext3  35 GB Ubuntu
   ext3  10 GB Ubuntu
   swap   6 GB

I install XP, then the first Ubuntu from the 9.10 LiveCD (to the 35 GB partition) and everything works fine.  But when I install the second Ubuntu, the system fails at the GRUB load.  I think I'm missing something basic here, but I've looked around for this info without success.
Thanks for any help...

When you install the second Ubuntu put GRUB on the 10 GB partition by clicking the advanced button on the Ready to install window (see attached pic). You will choose where to put it there. Assuming your partitions you listed are in partition table order you will choose /dev/sda6
**_But verify what sdXY designation is the 10 GB partition._** You want the second Ubuntu to have GRUB installed to the first sector of it's partition.

The above is assuming you have only one hard disk as you made no mention of multiple HDDs

---

### Post by kansasnoob on 2010-01-06
> **presence1960 said:**
> When you install the second Ubuntu put GRUB on the 10 GB partition by clicking the advanced button on the Ready to install window (see attached pic). You will choose where to put it there. Assuming your partitions you listed are in partition table order you will choose /dev/sda6
**_But verify what sdXY designation is the 10 GB partition._** You want the second Ubuntu to have GRUB installed to the first sector of it's partition.

The above is assuming you have only one hard disk as you made no mention of multiple HDDs

I generally choose to install no bootloader at all if the existing OS has grub2, then after install I just boot into the existing *buntu and run "sudo update-grub" and grub2 finds the new OS and adds it to the menu.

Not so good with suse or fedora though, grub2 doesn't like to find them :(

---

### Post by drdf on 2010-01-07
Thank you both (presense1960 and kansasnoob) for your help, and I hope I'm almost there...

I now get "error: invalid signature" when I select a Windows boot from grub.  Oddly, though, the Windows boot worked up until I installed the second Ubuntu partition.  Here I kept grub in the 35 GB Ubuntu 1 (following kansasnoob's suggestion) since I want that to be my main Ubuntu partition.

In more detail, here's my sequence when Windows broke:
1) partition disk as described above (a single disk, btw)
2) load a saved Windows partition (using Acronis True Image)
3) install Ubuntu #1
4) verify that I can boot into Windows and Ubuntu 1.
5) install Ubuntu 2
6) "sudo grup-update" in Ubuntu 1
7) verify that I can boot into Ubuntu 1 and 2 and both work fine
8) get updates for both, and get a few errors in Ubuntu 2 about grub but can still boot into both.
9) final verification of boot into Windows fails with "error: invalid signature" (much to my sadness and dismay -- though the two Ubuntu partitions still boot just fine, and I've run "update-grub" in hopes that that might find it correctly again).

---

### Post by kansasnoob on 2010-01-07
In order that we can get a better look please post the output of the Boot Info Script as described here:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

And also the output of:

```
sudo parted /dev/sda print
```

Did you resize Windows with Gparted prior to installing Ubuntu #2? That's a no-no with Win 7 and Vista.

Never mind that last blurb, I see this is XP not Vista or 7.

Have you tried booting with both Ubuntu's grub?

---

### Post by drdf on 2010-01-07
I've attached the outputs of the two commands.

A couple of notes that might be helpful:
1) I used gparted to pre-partition and size everything and then never partitioned or resized after this or during the installs.
2) BootInfoScript lists sda2 as Vista/7, but I just formatted it in gparted as ntfs and haven't touched it since.
3) I think I only have grub installed on Ubuntu 1, and not Ubuntu 2, as I thought that's what you meant by "I generally choose to install no bootloader at all if the existing OS has grub2", i.e. since Ubuntu 1 already has grub installed, I used the Advanced tab (re presence1960's post) to not install grub when installing Ubuntu 2.

---

### Post by oldfred on 2010-01-07
Try running 
sudo update-grub

Your windows is missing two lines compared to mine. I do not think the set root is optional but the search maybe optional:

menuentry "Windows XP Media Center Edition (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set d0782de7782dccd2
    drivemap -s (hd0) ${root}
    chainloader +1
}

If the update-grub does not work. Copy the entry into 40_custom make sure it is correct and run the update again.

---

### Post by drdf on 2010-01-07
Thanks oldfred, as you suggest, "set root" was the issue.  

What I now have works but it's a bit ugly...

I needed to edited /usr/lib/grub/grub-mkconfig_lib and remove the following lines

  # If there's a filesystem UUID that GRUB is capable of identifying, use it;
  # otherwise set root as per value in device.map.
  echo "set root=`${grub_probe} --device ${device} --target=drive`"
  if fs_uuid="`${grub_probe} --device ${device} --target=fs_uuid 2> /dev/null`" ; then
    echo "search --no-floppy --fs-uuid --set ${fs_uuid}"
  fi

If the "set root" line is there, my second Ubuntu partition doesn't boot (I've called this Ubuntu 2), but Windows will, and visa versa.  So currently what works is to not have it there and add the changes to 40_custom that oldfred suggested, so my 40_custom looks like this:

menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	drivemap -s (hd0) ${root}
	chainloader +1
}

Furthermore, I've removed the lines in grub-mkconfig_lib between if and fi due the a bug in grub ([https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/403408](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/403408)).

So this all works, and I'm extremely grateful from everyone's help that got me to this point, but my current solution seems a bit less than ideal, so I'm open to trying suggestions.  Thanks, again to all, as I now have a working system.

---

### Post by kansasnoob on 2010-01-07
It seems odd to me that you're having problems, I multi-boot too:

```
lance@lance-desktop:~$ sudo update-grub
[sudo] password for lance: 
Generating grub.cfg ...
Found Debian background: moreblue-orbit-grub.png
Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found Microsoft Windows XP Home Edition on /dev/sda1
Found Ubuntu 8.04.3 LTS (8.04) on /dev/sda13
Found Ubuntu lucid (development branch) (10.04) on /dev/sda3
Found Ubuntu 9.04 (9.04) on /dev/sda5
Found Linux Mint 7 Gloria - Main Edition (7) on /dev/sda7
done

```

---

### Post by drdf on 2010-01-07
kansasnoob... I'm not quite sure what to say to this other than the general point that working with computers would be much easier if "works on my system" implied it will work on all others.

My guess is that there's something in the grub-mkconfig_lib file, or some other config file, that is accounting for the details of your system but not mine.  For example why do I run into the bug at [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/403408](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/403408) and you don't?  This is particularly interesting since the offending line for me (with the "set root" command) is the line immediately previous to the ones that cause this known bug.  Or maybe that isn't the problem and there's a bug somewhere else, I'm much too much a noob to know.

I'm still open to trying more robust fixes if anyone has suggestions, but I guess I won't hold my breath.

---


---
title: "Booting from external HD"
date: 2011-12-05
forum: Installation &amp; Upgrades
---

### Post by scradock on 2011-12-05
I have been using Ubuntu for some years, and recently got a large (2TB) external HD so I could go crazy with lots of different installs - my laptop is old and small (hp pavilion zv6000, about 2004/5 vintage) and three or four OSs were about all it could fit on a 93GB HD. It all worked fine, grub finds installs in an ext4 extended partition and they boot up if the machine hasn't been turned off. I have to start up an install on the laptop's HD first, before the external HD becomes available.

Now the laptop is dying, and I am taking over a newer machine - more RAM, more HD space, more oomph all round. But when I plug the external HD with all my extra Ubuntu installs on it, they get mounted OK, and grub finds them, but won't boot them even if I do a Restart rather than a cold boot.

I set the BIOS to enable booting from external devices, so I could install my first Ubuntu from a USB stick, but then put the external device option to 3rd, after the DVD/CD drive and the internal HD. I left the Network Boot disabled.

The error message says that the partition (correct UUID) is not found, and follows that with a line saying that the drive hd1 does not report its C/H/S numbers.

What do I need to do to boot from the external HD? The machine I'm now working with is a Sony Vaio VGN-FW235J.

---

### Post by oldtimer7777 on 2011-12-05
Are you trying to boot from an external hard drive that you cloned your older system onto?  You need to install Ubuntu onto the external hdd first before you move your older system onto the external. You have the right idea, but the order of operation is wrong. 

> **scradock said:**
> I have been using Ubuntu for some years, and recently got a large (2TB) external HD so I could go crazy with lots of different installs - my laptop is old and small (hp pavilion zv6000, about 2004/5 vintage) and three or four OSs were about all it could fit on a 93GB HD. It all worked fine, grub finds installs in an ext4 extended partition and they boot up if the machine hasn't been turned off. I have to start up an install on the laptop's HD first, before the external HD becomes available.

Now the laptop is dying, and I am taking over a newer machine - more RAM, more HD space, more oomph all round. But when I plug the external HD with all my extra Ubuntu installs on it, they get mounted OK, and grub finds them, but won't boot them even if I do a Restart rather than a cold boot.

I set the BIOS to enable booting from external devices, so I could install my first Ubuntu from a USB stick, but then put the external device option to 3rd, after the DVD/CD drive and the internal HD. I left the Network Boot disabled.

The error message says that the partition (correct UUID) is not found, and follows that with a line saying that the drive hd1 does not report its C/H/S numbers.

What do I need to do to boot from the external HD? The machine I'm now working with is a Sony Vaio VGN-FW235J.

---

### Post by scradock on 2011-12-05
Nope - I have a Ubuntu install on the new laptop, with grub installed on /dev/sda. If I plug in the external HD with a bundle of installs grub finds them when I run update-grub, and builds grub.cfg with the correct UUIDs and so on. 

From the point of view of the external HD the setup is exactly the same as it has been with the old laptop; but the new laptop is refusing to "find" the bootable partitions on the external HD, whereas the old laptop finds them just fine, so long as it hasn't been turned right off since the external HD was last mounted. 

Different machines, different BIOSes; maybe there's a switch somewhere in the BIOS setup I don't know about....

---

### Post by oldfred on 2011-12-05
Some have issues with BIOS settings, some have not had enough power thru USB port and needed external power for a larger drive to work. Some have found grub just does not work from a large / (root) partition on some system (I still think it is BIOS but that is not known for sure). Smaller / partitions at the front of the drive like the old 137GB limit on 6 or 7 year or older systems. It may be some legacy IDE setting or something or part of the USB & BIOS not working correctly.

---

### Post by fantab on 2011-12-06
> **scradock said:**
> Nope - I have a Ubuntu install on the new laptop, with grub installed on /dev/sda. If I plug in the external HD with a bundle of installs grub finds them when I run update-grub, and builds grub.cfg with the correct UUIDs and so on. 

From the point of view of the external HD the setup is exactly the same as it has been with the old laptop; but the new laptop is refusing to "find" the bootable partitions on the external HD, whereas the old laptop finds them just fine, so long as it hasn't been turned right off since the external HD was last mounted. 

Different machines, different BIOSes; maybe there's a switch somewhere in the BIOS setup I don't know about....

Check the Partition Table of your HDD on Laptop and on the ExHDD.
Are you sure your new laptop does **not** use EEFI instead of BIOS?

If I may suggest an alternative to what you are doing to boot your ExHDD then I will suggest that you install GRUB on ExHDD also and let it use its own GRUB when it is Plugged in. IMO this has more benefits and less issues.

---

### Post by darkod on 2011-12-06
Also make sure you don't have a separate /boot partition on the old laptop. In that case the old laptop would boot just fine, but the new can't find the boot files because they are not on the ext HDD. Depends how you got it set up.
I agree with the idea having the grub on the ext HDD if you have installations there. It's the best way.

---

### Post by scradock on 2011-12-06
> **darkod said:**
> Also make sure you don't have a separate /boot partition on the old laptop. In that case the old laptop would boot just fine, but the new can't find the boot files because they are not on the ext HDD. Depends how you got it set up.
I agree with the idea having the grub on the ext HDD if you have installations there. It's the best way.
Thanks for the suggestions.

So I would have to run "grub-install /dev/sdb" from linux running on the internal HD? Or from a liveCD non-installed linux? I can't get into the installs on the external HD yet, unless I do a chroot, which I haven't had time to try yet.

I don't want to mess around too much with the internal HD or the MBR, because I need to be sure that the machine will boot from the internal HD if the external one isn't there...

---

### Post by darkod on 2011-12-06
EDIT: Not Correct, WRONG. If you want to use grub-install /dev/sdb you have to be into one of the OSs on the ext HDD. If you are into the int HDD and just run that command, the grub2 from the ext HDD will depend on your root partition on the int HDD which you don't want. But other method should work, look below.

But I wonder if chroot is necessary. Usually you need chroot for really messed up installs. If your installs on the ext HDD are fine, and all grub files correct, you could do it from live CD or even from your ubuntu on the int HDD. You only need to tell the install command that you are referring to another installation and not the one currently loaded.

For example, if the main ubuntu install that you want to use its grub on sdb is /dev/sdb5 (the root partition), something like this should work either from live CD or the int HDD ubuntu:

sudo mount /dev/sdb5 /mnt
sudo grub-install --root-directory=/mnt /dev/sdb

With specifying to use /mnt (where you earlier mounted sdb5) you tell it not to consider the loaded system as root partition, but instead your parameter.

---

### Post by scradock on 2011-12-06
> **darkod said:**
> EDIT: Not Correct, WRONG. If you want to use grub-install /dev/sdb you have to be into one of the OSs on the ext HDD. If you are into the int HDD and just run that command, the grub2 from the ext HDD will depend on your root partition on the int HDD which you don't want. But other method should work, look below.

But I wonder if chroot is necessary. Usually you need chroot for really messed up installs. If your installs on the ext HDD are fine, and all grub files correct, you could do it from live CD or even from your ubuntu on the int HDD. You only need to tell the install command that you are referring to another installation and not the one currently loaded.

For example, if the main ubuntu install that you want to use its grub on sdb is /dev/sdb5 (the root partition), something like this should work either from live CD or the int HDD ubuntu:

sudo mount /dev/sdb5 /mnt
sudo grub-install --root-directory=/mnt /dev/sdb

With specifying to use /mnt (where you earlier mounted sdb5) you tell it not to consider the loaded system as root partition, but instead your parameter.

Thanks again. I'm still not sure what happens if I try that and the external HD isn't recognized early enough in the booting process. How do I recover the ability to boot from the internal HD?

---

### Post by darkod on 2011-12-07
That's the point. You are never touching the bootloader on /dev/sda. Right now your computer boots with the ext hdd unplugged, yes?

The command I wrote earlier to install a bootloader on /dev/sdb does not touch /dev/sda at all. You just need to make sure in the first command (the mount) to specify the root partition of the OS on the ext hdd that you consider to be your "main" OS.

---

### Post by scradock on 2011-12-07
> **darkod said:**
> That's the point. You are never touching the bootloader on /dev/sda. Right now your computer boots with the ext hdd unplugged, yes?

The command I wrote earlier to install a bootloader on /dev/sdb does not touch /dev/sda at all. You just need to make sure in the first command (the mount) to specify the root partition of the OS on the ext hdd that you consider to be your "main" OS.

Thanks. I tried that, but even if I set the machine to boot from the external disk it fails to find the partition and dumps me to grub-rescue. If I leave it booting from the internal HD it gives me the grub menu with all the entries, including those on the external HD, but they fail to boot.

---

### Post by darkod on 2011-12-07
Boot rescue usually means the root partition is not present. Maybe we should have done this from start, but it's time to run the boot info script to see what is where.
Have your ext HDD connected too, boot the ubuntu on the int HDD (you have one there right?) or simply boot the cd into live mode and follow the link in my signature to run the script. Post the result as explained there.

---

### Post by scradock on 2011-12-07
I just ran boot_script - here are the results, if it helps. I'm stumped, even after checking through it....

---

### Post by darkod on 2011-12-07
Wow... you have all the OSs in the world... :)
Unfortunately this latest version of the script seems to be confused detecting at which partition # grub from the MBR is looking at. And in your case that would be excellent information.
Lets break down the problem:
Without the ext HDD can you boot your computer? Yes or no? Do all OSs in the boot list boot fine?

We will deal with the ext HDD later, first lets clarify the int HDD.

---

### Post by scradock on 2011-12-07
> **darkod said:**
> Wow... you have all the OSs in the world... :)
Unfortunately this latest version of the script seems to be confused detecting at which partition # grub from the MBR is looking at. And in your case that would be excellent information.
Lets break down the problem:
Without the ext HDD can you boot your computer? Yes or no? Do all OSs in the boot list boot fine?

We will deal with the ext HDD later, first lets clarify the int HDD.
Well, the Vista and the Mint installs boot fine, with or without the external HD connected. The second Ubuntu install doesn't boot, but that's a problem with the Precise alpha liveCD I used.

The error message at the end of Boot_script says that I need "unlzma" to see the partition info; Synaptic says that I have liblzma3 or something installed, so I don't know why that isn't working. I could try installing lzma itself, I suppose....

I do notice in the BIOS setup there is no listing of the hard-drives, just the "Internal HD", "DVD/CD drive" and "External device" categories. In my old laptop, with a different BIOS, I can hit Enter and expand the categories to list specific drives and choose which one is booting first.

---

### Post by darkod on 2011-12-08
OK. So that means the bootloader on the int HDD does not depend on any files from the ext HDD (otherwise it wouldn't boot anything without the ext HDD connected). That's what you want I guess. To boot fine without the ext HDD.

Now, from all those OSs on the ext HDD, which one do you consider your "main"? I guess you would like the bootloader on the ext HDD to be from this main OS.

---

### Post by scradock on 2011-12-08
> **darkod said:**
> OK. So that means the bootloader on the int HDD does not depend on any files from the ext HDD (otherwise it wouldn't boot anything without the ext HDD connected). That's what you want I guess. To boot fine without the ext HDD.

Now, from all those OSs on the ext HDD, which one do you consider your "main"? I guess you would like the bootloader on the ext HDD to be from this main OS.

The various installs on sdb are all in working order, so any of them would do. I can boot any of them on my old machine, and set up grub in /dev/sdb, then see what happens when the external HD is plugged into the new machine.

But I'm pretty sure I know what will happen - nothing useful - the drive is not getting recognized at boot time. If I watch the boot messages I see the second drive being set up, but only AFTER the linux image has been loaded from the internal HD.

---

### Post by oldfred on 2011-12-08
Do you have a one time boot key (f12 on my system) that lets you choose what to boot without changing BIOS. What options does that give?

---

### Post by scradock on 2011-12-09
> **oldfred said:**
> Do you have a one time boot key (f12 on my system) that lets you choose what to boot without changing BIOS. What options does that give?

No, that option is not offered during pre-boot, and F12 doesn't do anything except switch to the grub menu very fast. In fact , there are no options offered during pre-boot - I had to Google to discover that BIOS setup needed F2.

---

### Post by oldfred on 2011-12-09
I can understand old system not having a USB boot option. Is new system so new that it is UEFI not BIOS? Most very new systems have a mixed BIOS/UEFI that hides that it can be either or the vendor calls it BIOS when it is UEFI or vice-versa.

---

### Post by scradock on 2011-12-09
> **oldfred said:**
> I can understand old system not having a USB boot option. Is new system so new that it is UEFI not BIOS? Most very new systems have a mixed BIOS/UEFI that hides that it can be either or the vendor calls it BIOS when it is UEFI or vice-versa.

The BIOS offers three boot options: Internal Optical Drive, Internal HD, External Device. The only thing that can be changed is the order they're tried in. I can put External Device first and boot from a USB stick. But if the external drive is plugged in (USB) it doesn't get recognized - I get "error - partition does not exist". 

I'll try doing an install from CD directly onto the external HD and tell the installer to put grub onto the sdb drive.

---

### Post by scradock on 2011-12-11
Well, that didn't get me anywhere.

I have been trying command-line stuff from the grub> prompt.

ls lists the external drive as (hd1), and some of the partitions, but when I try "ls (hd1,10)" it says it cannot recognize the filesystem.

I can enter "set root=(hd1,10)" without an error, but trying then to enter "linux /vmlinuz root=/dev/sdb10 ro" gives me the error "hd1 cannot get C/H/S values." Tab autocompletion while typing in this line does not generate any helpful possibilities.

This suggests that the error is in the BIOS, which apparently does not correctly access the external drive.

In the BIOS setup routine, under Boot Order, I can see the external drive, if it is plugged in, but setting it to the first position in the list and trying to boot from HD simply gives me the grub menu from the internal drive.

I have installed grub2 in the MBR of the external drive (by booting into one of its installs using my older laptop); I have removed the "boot" flag from the NTFS partition and put a "boot" flag on one of the Ubuntu partitions, all to no avail.

Any bright ideas, anyone?

---

### Post by scradock on 2011-12-11
And some more, this time from the grub-rescue> prompt, which i got to by setting the External Device to boot first.....

"set prefix=(hd1,10)/boot/grub"
"set root=(hd1,10)"

are accepted without error. But if I try
"linux /vmlinuz root=/dev/sdb10 ro"

I get the error "Unknown command 'linux'"

Trying "insmod linux"
gets me the error
"unknown filesystem"

On the other hand, entering "insmod normal"
gets me the error
"no such partition"

while issuing the command "normal"
\gets me the error
Unknown command 'normal'

Similarly, setting prefix and root to point to (hd1,msdos5) lead to the same error messages.

---

### Post by oldfred on 2011-12-11
Boot flag is used by Windows to know which primary partition is the bootable one. Grub does not use boot flag.

You show the kernel files in sdb10, but it has no core.img which indicates grub was not fully installed to that partition. Have you tried booting any of the others?

Sometimes this will let you boot:

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
[http://www.supergrubdisk.org/wiki/Main_Page](http://www.supergrubdisk.org/wiki/Main_Page)

Otherwise the manual boot procedures you are trying should work if grub starts to load.

Adjust drive, partition to your install:
sh:grub>ls
#If on (hd1,1) or sdb1
sh:grub>ls (hd1,1)/
#Should show the links vmlinuz & initrd.img
sh:grub>linux (hd1,1)/vmlinuz root=/dev/sdb1
sh:grub>initrd (hd1,1)/initrd.img
sh:grub>boot

---

### Post by scradock on 2011-12-12
> **oldfred said:**
> Boot flag is used by Windows to know which primary partition is the bootable one. Grub does not use boot flag.

You show the kernel files in sdb10, but it has no core.img which indicates grub was not fully installed to that partition. Have you tried booting any of the others?



Thanks, Oldfred. I'm afraid I have tried others. Don't know why the sdb10 entry doesn't show core.img, but it boots fine on my older machine.

I've gone to town on this one; it seemed possible that the BIOS might be failing to read beyond 137GB or something, so I tried making a /boot partition at the beginning of the external disk. No joy.

I tried making a new partition at the start of the disk and installing Ubuntu in it, telling grub to install itself in the MBR of the external disk. Won't boot, from either machine.

Then I ran update-grub from an existing install on the internal disk, and the new install wouldn't boot from the grub menu on the internal disk. Do the same on the older machine, the new install boots fine.

The BIOS on the newer machine has a very limited setup routine; no switches for enabling stuff and so on - only External Device and Network under the Boot tab. I tried updating the BIOS from the Sony website, but it didn't add anything in the ay of capabilities, or solve the problem.

It seems to me that the newer machine (Sony Vaio VGN-FW235J) is lacking some USB-handling modules at a very low level, so the BIOS doesn't get to directly address the USB drive. Yet, strangely, it boots from a simple USB stick.

Once the linux kernel is loaded, the USB drive is mounted OK, but by then its too late.

Can anyone direct me to a description of how to start up with a linux kernel on the internal drive and switch to an install on the external drive later? I haven't gotten much into chrooting yet, so it would be beyond me unaided...

---

### Post by oldfred on 2011-12-12
I find it difficult to believe a system will boot a flash drive but not a USB drive?? Most flash drives look like USB drives anyway.

But many have reported that this works for old systems that will not boot from a USB port directly.

Boot USB or PCMCIA (new)
[http://www.plop.at/en/home.html](http://www.plop.at/en/home.html)

---

### Post by scradock on 2011-12-13
> **oldfred said:**
> I find it difficult to believe a system will boot a flash drive but not a USB drive?? Most flash drives look like USB drives anyway.

But many have reported that this works for old systems that will not boot from a USB port directly.

Boot USB or PCMCIA (new)
[http://www.plop.at/en/home.html](http://www.plop.at/en/home.html)

Thanks - it looks as if it might help, but it's too complicated to do in a hurry! Might try it in a few days, when I have more time.

---

### Post by scradock on 2011-12-14
> **oldfred said:**
> I find it difficult to believe a system will boot a flash drive but not a USB drive?? Most flash drives look like USB drives anyway.



I did wonder about that myself. One significant difference is that the flash drive uses syslinux to boot, rather than grub. There were some cryptic notes in the PLOP documentation about using syslinux and grub, but I haven't really penetrated them yet.

Anyway, I backed off, thought it all through and did everything again, just to be sure. I can now boot either machine from installs on its own internal HD, and boot either machine from a bootable flash drive, by setting the boot order appropriately. BUT if I try to boot THE SAME installs from the external drive, one machine boots them fine (including the one with no core.img in /boot/grub (!)), the other machine pretends it doesn't know what I'm talking about, and goes back to booting from the top of the grub menu on the internal HD.

I have re-run update-grub and made sure the installs on the external drive are listed properly, on both machines. One machine allows them to boot, under the control of grub on the INTERNAL HD, the other doesn't. 

I haven't been able to get either machine to accept booting from grub in the MBR of the EXTERNAL HD. Even on the older machine, where I can explicitly set the External HD as the preferred boot drive, the grub menu from the "install-grub /dev/sdb" command never appears; instead I get the grub menu from the internal HD.

Any more ideas? I'll try PLOP, but I can't help feeling that something is just out of reach, if only I knew where to find it...

---

### Post by oldfred on 2011-12-14
If you can boot into the external, then try the full uninstall and reinstall of grub2 and be sure to install grub2's boot loader to sdb.


You can skip  the chroot if you can boot into your install.
drs305 chroot to purge & reinstall grub2
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

Sometimes this works, but it does not uninstall grub to make a totally clean reinstall.
#to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

---

### Post by scradock on 2011-12-15
> **oldfred said:**
> If you can boot into the external, then try the full uninstall and reinstall of grub2 and be sure to install grub2's boot loader to sdb.


You can skip  the chroot if you can boot into your install.
drs305 chroot to purge & reinstall grub2
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)



Thanks - that was helpful... I hadn't realized that Natty uses a different Grub2 from Maverick - I have a slew of Maverick, Natty, Oneiric and Precise installs, so I've probably been using more than one Grub2 version. Might account for some errors.

But my main problem is precisely that I can't boot into the installs on the external drive from the newer machine (Sony Vaio), though I can from the older machine (HP Pavilion). Actually, that's my ONLY problem. If I could get to the external drive installs from the Sony I would be happy!

I'll see if I can get into one using chroot, now I have the directions, and do a grub2 reinstall from there.

---

### Post by scradock on 2011-12-15
> **oldfred said:**
> If you can boot into the external, then try the full uninstall and reinstall of grub2 and be sure to install grub2's boot loader to sdb.


You can skip  the chroot if you can boot into your install.
drs305 chroot to purge & reinstall grub2
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

Sometimes this works, but it does not uninstall grub to make a totally clean reinstall.
#to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

Well, that was fun!

I tried the reconfigure, which didn't help. So I tried the chroot route. 

I chrooted into one of the installs on the external HD OK, but running update-grub and grub-install /dev/sdb left me still unable to boot from grub in the external HD. Purging and re-installing grub2, and letting the grub files be written to BOTH sda and sdb left me unable to boot from either drive - both gave "file not found" errors. I had to boot from the LiveCD (actually a USB flash drive!) and chroot from there into one of the installs on the internal drive to re-install a working grub2 on /dev/sda.

Now I'm back where I started, and more and more convinced it's a disability of the Sony to access USB devices before the kernel is loaded, which means it won't ever boot from the external drive unless I can get PLOP working.

---

### Post by oldfred on 2011-12-15
I think the newest grub 1.99 does require you to use the same version liveCD/USB to run the 'simple' updates. 
Chroot should work from any Linux as then you are working from inside the install.
I have seen many reports of plop working, but have not used it, nor know how easy it is to configure.

---

### Post by scradock on 2011-12-16
> **oldfred said:**
> 
I have seen many reports of plop working, but have not used it, nor know how easy it is to configure.

Well, that fixed it!  I downloaded PLOP, extracted the binary and copied it to the /boot folder of the "grub master" install on the internal HD. Then I created a boot stanza for it and inserted it into grub.cfg - I'll put it in with /etc/grub.d/40_custom later. Choosing the PLOP entry from the Grub2 menu gives me a PLOP menu. Choosing USB from that takes me to the Grub2 menu based on the MBR of the EXTERNAL HD, from which I can choose any of the installs (of course I made sure to run "update-grub", and had already done "grub-install /dev/sdb" from the chroot).

Booting from the /dev/sda Grub2 menu is not affected UNLESS I choose PLOP from it.

Thanks for the suggestions, and for sticking with it!

---

### Post by oldfred on 2011-12-16
Glad that worked.:)

---


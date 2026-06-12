---
title: "Have no hope already! UEFI system."
date: 2011-05-31
forum: Installation &amp; Upgrades
---

### Post by Avidanborisov on 2011-05-31
Hey everyone!
I just can't install ubuntu 11.04 or 10.10 or 10.04.
I have tried everything but either I get busybox, or the installer crashes. I have reported this bugs but I don't see them fixed:
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/779824](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/779824)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/777222](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/777222)

What's weird though, is that when first time I tried to install 11.04 beta 1 on live-usb, it worked!
But now, I have tried all the betas and the final versions and they all seem to not work. 10.10 can't even boot!
I think the problem is ubuntu just doesn't know how to deal with UEFI systems. The first time I installed, I was able to fix all Grub-efi stuff with the help of this thread I opened:
[http://ubuntuforums.org/showthread.php?t=1719851](http://ubuntuforums.org/showthread.php?t=1719851)
but in the end of it I described that one update screwed everything, and I just don't know what to do already.
I also tried the alternate installer. I goes pretty well except that in the end it says it fails to install grub bootloader.

I would really appreciate help!

---

### Post by oldfred on 2011-05-31
I think your issue is more with grub2's efi than the bugs you posted.

Have you seen this and what version are you using?
[https://launchpad.net/ubuntu/+source/grub2/1.99~rc1-13ubuntu3](https://launchpad.net/ubuntu/+source/grub2/1.99~rc1-13ubuntu3)

“grub2” 1.99~rc1-13ubuntu3 source package in Ubuntu

   1. Ubuntu
   2. “grub2” package
   3. 1.99~rc1-13ubuntu3

Changelog

grub2 (1.99~rc1-13ubuntu3) natty; urgency=low

  * Cherry-pick from upstream:
    - Fix grub-install on amd64 EFI systems.
 -- Colin Watson <email address hidden>   Thu, 21 Apr 2011 12:16:55 +0100

See posts 33 & 36 on #grub IRC. Since your seem to have bleeding edge system perhaps CJWatson will be on line and able to help. Your problem seems unique enough it may intrigue them.

[http://ubuntuforums.org/showthread.php?t=1771095&page=4](http://ubuntuforums.org/showthread.php?t=1771095&page=4)

---

### Post by Avidanborisov on 2011-05-31
> **oldfred said:**
> I think your issue is more with grub2's efi than the bugs you posted.

Have you seen this and what version are you using?
[https://launchpad.net/ubuntu/+source/grub2/1.99~rc1-13ubuntu3](https://launchpad.net/ubuntu/+source/grub2/1.99~rc1-13ubuntu3)

“grub2” 1.99~rc1-13ubuntu3 source package in Ubuntu

   1. Ubuntu
   2. “grub2” package
   3. 1.99~rc1-13ubuntu3

Changelog

grub2 (1.99~rc1-13ubuntu3) natty; urgency=low

  * Cherry-pick from upstream:
    - Fix grub-install on amd64 EFI systems.
 -- Colin Watson <email address hidden>   Thu, 21 Apr 2011 12:16:55 +0100

See posts 33 & 36 on #grub IRC. Since your seem to have bleeding edge system perhaps CJWatson will be on line and able to help. Your problem seems unique enough it may intrigue them.

[http://ubuntuforums.org/showthread.php?t=1771095&page=4](http://ubuntuforums.org/showthread.php?t=1771095&page=4)

Could also be a bug in grub2-efi but grub does seem to work from the live-usb and live-cd, however except for 11.04 final live-cd and alternate installer, on all the other versions I get BusyBox.
On 11.04 live-cd the installer crashes, or just stuck.
On the alternate installer, the installation is fine, however grub2 fails to install.
I think this should be a very high importance bugs, becuase UEFI systems are really going to be very popular soon, only GIGABYTE is left.
And, I didn't understand what to do with those links you sent.

---

### Post by oldfred on 2011-05-31
I was suggesting to use the IRC for immediate help. But that depends on who may be available when you are on that.

I had posted a grub bug once, but they already had a fix (I should have looked) but Colin Watson replied within a day or two on my bug post since they already had a fix.

I think Colin is very busy right now since they have a major issue with all distributions throwing a 404 error on update. I see his name on the ones working on the bug, which I think they have fixed, but I am sure he is busy.

---

### Post by srs5694 on 2011-05-31
I've just reviewed the earlier thread you referenced. (Anybody else who does the same, everything relevant to *this* thread is on page 6 and later.) I offered advice in that thread that was helpful; but I've since gained more experience with UEFI that leads me to make different recommendations now....

My current suggestions are:


[LIST]
[*]Since you say you got Ubuntu installed *except* for GRUB when using the alternate installer, stick with that. Of course, an OS without a boot loader isn't much use, but getting a boot loader installed in UEFI is a matter of copying files, editing configuration files, and getting the firmware to load the correct files. This is actually easier than doing the equivalent on a BIOS-based computer, although the understanding of UEFI is still lacking and the tools are still cruder.
[*]Make sure that your EFI System Partition (ESP) is *at least* 100 MiB in size. The Ubuntu installer tends to create a ridiculously small ESP -- 16 MiB in one of my tests, 32 MiB in another. The method I'm about to suggest will require that you have enough space on the ESP to hold your kernel and initial RAM disk (about 19 MiB), and more will be necessary if you want to boot from a selection of kernels.
[*]GRUB 2 currently supports UEFI, but very poorly, IMHO. It works for me on most systems but tends to be very delicate; the slightest configuration problem causes the boot to fail. Worse, a problem on one system is a requirement on another, so you've got to tweak by hand and then fight the automatic update features to keep your tweaks in place. On one of my systems, GRUB fails completely about 3/4 of the time but mysteriously works about 1/4 of the time.
[*]On my one true UEFI hardware system, [ELILO]("http://elilo.sourceforge.net/cgi-bin/blosxom") works much better than GRUB. I recommend you use it (see below for more details). OTOH, ELILO also seems sensitive to system-specific things; I've been unable to get it to work in a VirtualBox environment. Since you've got a real UEFI on a motherboard, though, I'm betting that my UEFI-on-a-motherboard experience is more relevant. (I've got an Intel DG43NB board.)
[*]ELILO boots Linux, but AFAIK can't chainload another UEFI boot loader. Thus, you'll need to rely on your BIOS or another boot loader to select between Linux and Windows, if you're dual-booting with Windows. [rEFIt]("http://refit.sourceforge.net") should do this job acceptably, although I can't make any promises since my installations don't yet dual-boot with Windows.
[/LIST]
It's possible that your failure this time around has to do with specifying the ESP in the installer. If you don't tell the installer where the ESP is, it won't be able to install GRUB 2. The Ubuntu installer uses an odd name for the ESP ("EFI boot partition" or something like that, IIRC). You've just got to flag it in that way, not specify a mount point. (It'll automatically be mounted at /boot/efi if you do it right.)

Assuming you still can't get the Ubuntu installer to install GRUB, you can follow my advice below. This involves installing Ubuntu with the alternate installer and then installing both rEFIt and ELILO to the ESP of your hard disk. I can provide a procedure for doing this, but it's off the top of my head and is therefore untested. You might run into problems. My suggestion is:


[list=1]
[*]Partition the disk, ensuring that the ESP is at least 100 MiB.
[*]Install Windows, if desired.
[*]Install Ubuntu via the alternate installer. At this point, I expect the computer will boot Windows but not Linux.
[*]Load the Ubuntu desktop installer into "live CD" mode.
[*]Mount your Linux root partition somewhere convenient, like /mnt.
[*]If you've got a separate /boot partition, mount it at /mnt/boot.
[*]Mount your ESP (probably /dev/sda1) at /mnt/boot/efi.
[*]If you've got other system partitions, such as /var or /usr, mount them at appropriate locations under /mnt. Don't bother with /home, if it's a separate partition; you won't need to write anything to it.
[*]Download the Ubuntu [elilo]("http://packages.ubuntu.com/natty/admin/elilo"), [refit,]("http://packages.ubuntu.com/natty/admin/refit") [efibootmgr,](http://packages.ubuntu.com/natty/efibootmgr) and [gptsync]("http://packages.ubuntu.com/natty/gptsync") packages. (The last two are dependencies for ELILO and rEFIt, respectively.)
[*]Install these four packages in your installed system by typing "sudo dpkg -i --root=/mnt elilo{version}.deb refit{version}.deb efibootmgr{version}.deb gptsync{version}.deb", where "{version}" is the complete version information for each package, so that you specify the three files you've downloaded. The "--root=/mnt" option tells dpkg to install to the version of Ubuntu located at /mnt, so it's critical your already-installed Ubuntu be available there. If dpkg says that refit and/or elilo conflict with grub-efi, you'll need to uninstall it with "sudo dpkg --root=/mnt -P grub-efi grub-efi-amd64" (and maybe other GRUB-related package names, too).
[*]Type "sudo mkdir /mnt/boot/efi/EFI/refit". This creates a directory on the ESP where rEFIt will live.
[*]Type "cd /mnt/usr/lib/refit/refit"
[*]Type "sudo cp -r * /mnt/boot/efi/EFI/refit". This installs the rEFIt files to the ESP, except for one....
[*]Type "sudo cp ../x64/refit.efi /mnt/boot/efi/EFI/refit". This installs the final rEFIt file.
[*]Type "sudo mkdir /mnt/boot/efi/EFI/elilo". This creates ELILO's home on the ESP.
[*]Type "sudo cp /mnt/lib/elilo/elilo.efi /mnt/boot/efi/EFI/elilo/". This copies ELILO to its home on the ESP.
[*]Type "sudo cp /mnt/boot/vmlinuz-* /mnt/boot/initrd.img-* /mnt/boot/efi/EFI/elilo/". This copies the Linux kernel and initial RAM disk to the ESP.
[*]Create an ELILO configuration file (see below) and store it as /mnt/boot/efi/EFI/elilo/elilo.conf.
[*]Type "sudo efibootmgr -c -l \\EFI\\elilo\\elilo.efi -L ELILO". This adds ELILO to the list of boot loaders maintained by your firmware. Note the double backslashes; EFI uses backslashes as directory separators, and you've got to double them up in the Linux shell. (If you get a "no command 'efibootmgr' found" error, you can either install efibootmgr in the live CD environment or run it by specifying its path in /mnt.)
[*]Type "sudo efibootmgr -c -l \\EFI\\refit\\refit.efi -L rEFIt". This adds rEFIt to the list of boot loaders.
[/list]


At this point you should be able to reboot and use your EFI's boot selector to pick either rEFIt or ELILO. You can either use the same method to select between ELILO and Windows on a regular basis or pick rEFIt as your default boot loader and use it to do that job. (If you use the firmware's boot selector, there's really no reason to install rEFIt.) Unfortunately, I can't tell you precisely how to select the boot loader in your firmware since that detail varies a lot from one UEFI implementation to another. You *might* be able to force the issue by creating a UEFI boot script in the root directory of the ESP. It would have just one line that references the boot loader you want to use:

```

fs0:\EFI\refit\refit.efi

```

As to the ELILO configuration file, here's a sample:

```

prompt
timeout=50
default=linux
#chooser=textmenu

image=vmlinuz-2.6.38-8-generic
        label=linux
        initrd=initrd.img-2.6.38-8-generic
        read-only
        root=/dev/sda4
        append="reboot=a,w"

```

You'll probably be able to use one that's nearly identical; just change your "root=" line to point to your root partition (or specify it via its UUID or LABEL). The "append=" line is necessary on some (but not all) systems to keep the computer from hanging when you reboot.

Be sure to back up the elilo.conf file somewhere; the Ubuntu elilo package includes a script called "elilo" that will overwrite this file, and that script might be called when you upgrade your kernel. Unfortunately, the script overwrites the configuration file with a buggy one. (As Homer Simpson would say, "d'oh!")

On most of my tests, rEFIt has some minor video glitches -- some text-mode error messages get printed over the GUI OS selector. If you have this problem, you can avoid it by reconfiguring it to run in text mode. (There's a configuration file that gets copied to the ESP; edit it and uncomment the "textonly" line.)

I know this is a mess. IMHO, Ubuntu's UEFI support is early alpha-quality at best. I'm sure it'll improve a lot in the future, since most Sandy Bridge boards and a lot of new AMD boards use UEFI.

---

### Post by Avidanborisov on 2011-06-01
> **srs5694 said:**
> I've just reviewed the earlier thread you referenced. (Anybody else who does the same, everything relevant to *this* thread is on page 6 and later.) I offered advice in that thread that was helpful; but I've since gained more experience with UEFI that leads me to make different recommendations now....

My current suggestions are:


[LIST]
[*]Since you say you got Ubuntu installed *except* for GRUB when using the alternate installer, stick with that. Of course, an OS without a boot loader isn't much use, but getting a boot loader installed in UEFI is a matter of copying files, editing configuration files, and getting the firmware to load the correct files. This is actually easier than doing the equivalent on a BIOS-based computer, although the understanding of UEFI is still lacking and the tools are still cruder.
[*]Make sure that your EFI System Partition (ESP) is *at least* 100 MiB in size. The Ubuntu installer tends to create a ridiculously small ESP -- 16 MiB in one of my tests, 32 MiB in another. The method I'm about to suggest will require that you have enough space on the ESP to hold your kernel and initial RAM disk (about 19 MiB), and more will be necessary if you want to boot from a selection of kernels.
[*]GRUB 2 currently supports UEFI, but very poorly, IMHO. It works for me on most systems but tends to be very delicate; the slightest configuration problem causes the boot to fail. Worse, a problem on one system is a requirement on another, so you've got to tweak by hand and then fight the automatic update features to keep your tweaks in place. On one of my systems, GRUB fails completely about 3/4 of the time but mysteriously works about 1/4 of the time.
[*]On my one true UEFI hardware system, [ELILO]("http://elilo.sourceforge.net/cgi-bin/blosxom") works much better than GRUB. I recommend you use it (see below for more details). OTOH, ELILO also seems sensitive to system-specific things; I've been unable to get it to work in a VirtualBox environment. Since you've got a real UEFI on a motherboard, though, I'm betting that my UEFI-on-a-motherboard experience is more relevant. (I've got an Intel DG43NB board.)
[*]ELILO boots Linux, but AFAIK can't chainload another UEFI boot loader. Thus, you'll need to rely on your BIOS or another boot loader to select between Linux and Windows, if you're dual-booting with Windows. [rEFIt]("http://refit.sourceforge.net") should do this job acceptably, although I can't make any promises since my installations don't yet dual-boot with Windows.
[/LIST]
It's possible that your failure this time around has to do with specifying the ESP in the installer. If you don't tell the installer where the ESP is, it won't be able to install GRUB 2. The Ubuntu installer uses an odd name for the ESP ("EFI boot partition" or something like that, IIRC). You've just got to flag it in that way, not specify a mount point. (It'll automatically be mounted at /boot/efi if you do it right.)

Assuming you still can't get the Ubuntu installer to install GRUB, you can follow my advice below. This involves installing Ubuntu with the alternate installer and then installing both rEFIt and ELILO to the ESP of your hard disk. I can provide a procedure for doing this, but it's off the top of my head and is therefore untested. You might run into problems. My suggestion is:


[list=1]
[*]Partition the disk, ensuring that the ESP is at least 100 MiB.
[*]Install Windows, if desired.
[*]Install Ubuntu via the alternate installer. At this point, I expect the computer will boot Windows but not Linux.
[*]Load the Ubuntu desktop installer into "live CD" mode.
[*]Mount your Linux root partition somewhere convenient, like /mnt.
[*]If you've got a separate /boot partition, mount it at /mnt/boot.
[*]Mount your ESP (probably /dev/sda1) at /mnt/boot/efi.
[*]If you've got other system partitions, such as /var or /usr, mount them at appropriate locations under /mnt. Don't bother with /home, if it's a separate partition; you won't need to write anything to it.
[*]Download the Ubuntu [elilo]("http://packages.ubuntu.com/natty/admin/elilo"), [refit,]("http://packages.ubuntu.com/natty/admin/refit") [efibootmgr,](http://packages.ubuntu.com/natty/efibootmgr) and [gptsync]("http://packages.ubuntu.com/natty/gptsync") packages. (The last two are dependencies for ELILO and rEFIt, respectively.)
[*]Install these four packages in your installed system by typing "sudo dpkg -i --root=/mnt elilo{version}.deb refit{version}.deb efibootmgr{version}.deb gptsync{version}.deb", where "{version}" is the complete version information for each package, so that you specify the three files you've downloaded. The "--root=/mnt" option tells dpkg to install to the version of Ubuntu located at /mnt, so it's critical your already-installed Ubuntu be available there. If dpkg says that refit and/or elilo conflict with grub-efi, you'll need to uninstall it with "sudo dpkg --root=/mnt -P grub-efi grub-efi-amd64" (and maybe other GRUB-related package names, too).
[*]Type "sudo mkdir /mnt/boot/efi/EFI/refit". This creates a directory on the ESP where rEFIt will live.
[*]Type "cd /mnt/usr/lib/refit/refit"
[*]Type "sudo cp -r * /mnt/boot/efi/EFI/refit". This installs the rEFIt files to the ESP, except for one....
[*]Type "sudo cp ../x64/refit.efi /mnt/boot/efi/EFI/refit". This installs the final rEFIt file.
[*]Type "sudo mkdir /mnt/boot/efi/EFI/elilo". This creates ELILO's home on the ESP.
[*]Type "sudo cp /mnt/lib/elilo/elilo.efi /mnt/boot/efi/EFI/elilo/". This copies ELILO to its home on the ESP.
[*]Type "sudo cp /mnt/boot/vmlinuz-* /mnt/boot/initrd.img-* /mnt/boot/efi/EFI/elilo/". This copies the Linux kernel and initial RAM disk to the ESP.
[*]Create an ELILO configuration file (see below) and store it as /mnt/boot/efi/EFI/elilo/elilo.conf.
[*]Type "sudo efibootmgr -c -l \\EFI\\elilo\\elilo.efi -L ELILO". This adds ELILO to the list of boot loaders maintained by your firmware. Note the double backslashes; EFI uses backslashes as directory separators, and you've got to double them up in the Linux shell. (If you get a "no command 'efibootmgr' found" error, you can either install efibootmgr in the live CD environment or run it by specifying its path in /mnt.)
[*]Type "sudo efibootmgr -c -l \\EFI\\refit\\refit.efi -L rEFIt". This adds rEFIt to the list of boot loaders.
[/list]


At this point you should be able to reboot and use your EFI's boot selector to pick either rEFIt or ELILO. You can either use the same method to select between ELILO and Windows on a regular basis or pick rEFIt as your default boot loader and use it to do that job. (If you use the firmware's boot selector, there's really no reason to install rEFIt.) Unfortunately, I can't tell you precisely how to select the boot loader in your firmware since that detail varies a lot from one UEFI implementation to another. You *might* be able to force the issue by creating a UEFI boot script in the root directory of the ESP. It would have just one line that references the boot loader you want to use:

```

fs0:\EFI\refit\refit.efi

```

As to the ELILO configuration file, here's a sample:

```

prompt
timeout=50
default=linux
#chooser=textmenu

image=vmlinuz-2.6.38-8-generic
        label=linux
        initrd=initrd.img-2.6.38-8-generic
        read-only
        root=/dev/sda4
        append="reboot=a,w"

```

You'll probably be able to use one that's nearly identical; just change your "root=" line to point to your root partition (or specify it via its UUID or LABEL). The "append=" line is necessary on some (but not all) systems to keep the computer from hanging when you reboot.

Be sure to back up the elilo.conf file somewhere; the Ubuntu elilo package includes a script called "elilo" that will overwrite this file, and that script might be called when you upgrade your kernel. Unfortunately, the script overwrites the configuration file with a buggy one. (As Homer Simpson would say, "d'oh!")

On most of my tests, rEFIt has some minor video glitches -- some text-mode error messages get printed over the GUI OS selector. If you have this problem, you can avoid it by reconfiguring it to run in text mode. (There's a configuration file that gets copied to the ESP; edit it and uncomment the "textonly" line.)

I know this is a mess. IMHO, Ubuntu's UEFI support is early alpha-quality at best. I'm sure it'll improve a lot in the future, since most Sandy Bridge boards and a lot of new AMD boards use UEFI.

Thanks for the really helpful comment!
One question:
If this at the end works, Will I be able to clean this temporary messy method and return to regular GRUB2?
Again, thank you very much!

---

### Post by srs5694 on 2011-06-01
> **Avidanborisov said:**
> One question:
If this at the end works, Will I be able to clean this temporary messy method and return to regular GRUB2?

Yes, but if you want to use GRUB 2, you should install *it* manually, rather than ELILO (and perhaps rEFIt). See [here](https://help.ubuntu.com/community/UEFIBooting) for the version with the gory details; or you could hope that Ubuntu's automated installation method would work better when you trigger it manually (vs. from the installer).

Much of the point of the procedure I posted is to *avoid* GRUB 2, which IMHO is at alpha-quality level (at best) on EFI/UEFI systems. ELILO is at beta-quality, IMHO, which is a vast improvement.

I'd also like to emphasize that the procedure I posted is required *once*. With everything installed, it boots the system with minimal fuss. If you need to update the kernel, you'll have to manually add an entry to your elilo.conf file in the ESP, but that's easy enough to do. Thus, once it's installed, it's not a "messy" boot loader; the only "mess" is during installation.

---

### Post by Avidanborisov on 2011-06-01
> **srs5694 said:**
> Yes, but if you want to use GRUB 2, you should install *it* manually, rather than ELILO (and perhaps rEFIt). See [here](https://help.ubuntu.com/community/UEFIBooting) for the version with the gory details; or you could hope that Ubuntu's automated installation method would work better when you trigger it manually (vs. from the installer).

Much of the point of the procedure I posted is to *avoid* GRUB 2, which IMHO is at alpha-quality level (at best) on EFI/UEFI systems. ELILO is at beta-quality, IMHO, which is a vast improvement.

I'd also like to emphasize that the procedure I posted is required *once*. With everything installed, it boots the system with minimal fuss. If you need to update the kernel, you'll have to manually add an entry to your elilo.conf file in the ESP, but that's easy enough to do. Thus, once it's installed, it's not a "messy" boot loader; the only "mess" is during installation.

Actually, on the previous time i have installed ubuntu, compiling grub2-efi from source worked very well, the problem was definitely with ubuntu repos as they updated/downgraded/removed what was necessary. So, from your experience doing the same with lilo won't cause all this problems as with grub?

---

### Post by srs5694 on 2011-06-01
Half-baked software updates are always a threat; I can't promise that Ubuntu won't release an ELILO update that will cause problems. You can always install ELILO from [its Sourceforge page](http://sourceforge.net/projects/elilo/files/elilo/) instead of from the Ubuntu repositories if you're concerned about that. (This is actually how I've got one of my systems booting, but I've tested it both ways.) If you do so, you'd need to tweak my instructions in a couple of places -- you'd download and unpack the ELILO package from Sourceforge (it comes precompiled, but you could compile it yourself if you wanted to) and copy elilo.efi from a different location. Otherwise, the procedure would be the same.

---

### Post by Hedgehog1 on 2011-06-02
srs5694,

Just a quick thank you on your detailed descriptions about these issues.  Not only will it help the OP; it is a great learning experience for the rest of us, too.

***The Hedge***

:KS

---

### Post by Avidanborisov on 2011-06-09
@srs5694 OK, finally I had free time to try your suggestion.
I have followed your instructions (however I didn't install rEFIt). It went pretty smooth, altough I found one liitle mistake. In here:
```
sudo cp /mnt/lib/elilo/elilo.efi /mnt/boot/efi/EFI/elilo/
```
It should have been:
```
sudo cp /mnt/usr/lib/elilo/elilo.efi /mnt/boot/efi/EFI/elilo/
```
Anyway, I had no errors but when I rebooted and selected ELILO in the UEFI, it couldn't load anything and looped itself forever. Here is a video:
[http://www.youtube.com/watch?v=AXTxkjqwCqo](http://www.youtube.com/watch?v=AXTxkjqwCqo)
(btw, I heard that 11.10 alpha 1 came out so I have tried it. The bugs still exist).

---

### Post by srs5694 on 2011-06-09
I suggest you review the ELILO configuration. Make sure you've specified the correct values for:


[list]
[*]The Linux kernel (on the image= line). Note that this file *must exist* on your EFI System Partition. If you don't specify a directory for it, it must exist in the same directory as the other ELILO files.
[*]The initial RAM disk (on the initrd= line). As with the kernel, this file must exist on your EFI System Partition.
[*]The "root=" line must point to *your* Linux root partition. It's /dev/sda4 in my example, but I have no idea what it is for you.
[*]The "append=" line contains kernel arguments. I specified "reboot=a,w" there because that helps avoid a reboot problem on one of my systems; but it's conceivable this option is causing problems for you, or you might need some other option in its place.
[/list]


Another option is to go back to GRUB. You could try installing GRUB to the ESP, as described [here.](https://help.ubuntu.com/community/UEFIBooting) Perhaps it will work better for you, once you get it installed. (As I understand it, your current situation is that GRUB didn't install from the Ubuntu installer.)

One more thing: 11.04 alpha 1 is an *old* version of 11.04, not a *new* one. It's pre-release, in fact; that's what "alpha" means.

---

### Post by Avidanborisov on 2011-06-09
> I suggest you review the ELILO configuration. Make sure you've specified the correct values for:


[list]
[*]The Linux kernel (on the image= line). Note that this file *must exist* on your EFI System Partition. If you don't specify a directory for it, it must exist in the same directory as the other ELILO files.
[*]The initial RAM disk (on the initrd= line). As with the kernel, this file must exist on your EFI System Partition.
[*]The "root=" line must point to *your* Linux root partition. It's /dev/sda4 in my example, but I have no idea what it is for you.
[*]The "append=" line contains kernel arguments. I specified "reboot=a,w" there because that helps avoid a reboot problem on one of my systems; but it's conceivable this option is causing problems for you, or you might need some other option in its place.
[/list]

Well all the files are in the same folder as elilo.efi in my ESP. My system is also under /dev/sda4. What am I missing?
the path is:
```
ESP/EFI/elilo
```
the files in this folder are:
```
elilo.efi
vmlinuz-2.6.38-7-generic
vmlinuz-2.6.38-8-generic
initrd.img-2.6.38-7-generic
initrd.img-2.6.38-8-generic
elilo.conf
```
the contents of elilo.conf:

```
prompt
timeout=50
default=linux
#chooser=textmenu

image=vmlinuz-2.6.38-8-generic
        label=linux
        initrd=initrd.img-2.6.38-8-generic
        read-only
        root=/dev/sda4
        append="reboot=a,w"

```

> Another option is to go back to GRUB. You could try installing GRUB to the ESP, as described here. Perhaps it will work better for you, once you get it installed. (As I understand it, your current situation is that GRUB didn't install from the Ubuntu installer.)

Actually I have read this and tried this before but the firmware just couldn't load grub or I got grub rescue.

> One more thing: 11.04 alpha 1 is an old version of 11.04, not a new one. It's pre-release, in fact; that's what "alpha" means.
Sorry, I have meant 11.10 alpha, I'll change this.

---

### Post by srs5694 on 2011-06-09
Your elilo.conf looks right to me; however, you may need to play with kernel options (on the "append=" line). Start by removing what's there now ("reboot=a,w"); it may not be necessary, and could conceivably be causing problems. It's conceivable that you'd need to add something else, but the only suggestions I've got are:


[list]
[*]"noefi", which ironically is required on some EFI systems. (This disables EFI runtime services, which AFAIK creates very minor limitations; you might never notice the limitations.)
[*]"add_efi_memmap", which affects how the kernel determines what memory is available.
[/list]


You could also check your grub.cfg file to see what it's using. On one of my installations, aside from the root= (which uses a UUID rather than a raw device file) and "ro" (equivalent to elilo.conf's "read-only" line), there's just "quiet splash vt.handoff=7", none of which I'd expect to make booting more reliable. The first two can make debugging harder, since they're what create the pretty (but useless) boot images.

Another option would be to try the slightly older kernel (2.6.38-7 rather than 2.6.38-8) that you've also got installed. I recommend creating a second elilo.conf entry for the new kernel; cut-and-paste the existing entry (starting at image=) and then edit it to change the image=, label=, and initrd= lines. When you reboot, you can hit the Tab key to see the kernels. Type the name (that you entered on the label= line) to boot that kernel.

---

### Post by Avidanborisov on 2011-06-29
> **srs5694 said:**
> Your elilo.conf looks right to me; however, you may need to play with kernel options (on the "append=" line). Start by removing what's there now ("reboot=a,w"); it may not be necessary, and could conceivably be causing problems. It's conceivable that you'd need to add something else, but the only suggestions I've got are:


[list]
[*]"noefi", which ironically is required on some EFI systems. (This disables EFI runtime services, which AFAIK creates very minor limitations; you might never notice the limitations.)
[*]"add_efi_memmap", which affects how the kernel determines what memory is available.
[/list]


You could also check your grub.cfg file to see what it's using. On one of my installations, aside from the root= (which uses a UUID rather than a raw device file) and "ro" (equivalent to elilo.conf's "read-only" line), there's just "quiet splash vt.handoff=7", none of which I'd expect to make booting more reliable. The first two can make debugging harder, since they're what create the pretty (but useless) boot images.

Another option would be to try the slightly older kernel (2.6.38-7 rather than 2.6.38-8) that you've also got installed. I recommend creating a second elilo.conf entry for the new kernel; cut-and-paste the existing entry (starting at image=) and then edit it to change the image=, label=, and initrd= lines. When you reboot, you can hit the Tab key to see the kernels. Type the name (that you entered on the label= line) to boot that kernel.

Hi there!
Its been some time and I read a lot about UEFI and UEFI boot loaders for linux. Anyway, ELILO didn't work but I succeed to compile and install grub2-efi. So based on [skodabenz's script]("https://raw.github.com/skodabenz/My_Shell_Scripts/master/grub2/grub2_uefi.sh") I wrote a script that will automatically compile and install grub2 for UEFI systems. the script will also check for required dependencies, and will produce a package that can be easily uninstalled.
You can get the script by the following commands:
```
wget http://my-shell-scripts.googlecode.com/files/compile_grub2_uefi.sh
chmod +x compile_grub2_uefi.sh
./compile_grub2_uefi.sh
```
if you want some more info run this:
```
./compile_grub2_uefi.sh -h
```
Of course, any suggestions or bugs found are more then welcome to be reported.

By the way Debian has already packaged grub-efi 1.99 which works great. If anyone is interested you can get the packages here:
[http://ftp.us.debian.org/debian/pool/main/g/grub2/grub-efi_1.99-8_amd64.deb](http://ftp.us.debian.org/debian/pool/main/g/grub2/grub-efi_1.99-8_amd64.deb)
[http://ftp.us.debian.org/debian/pool/main/g/grub2/grub-common_1.99-8_amd64.deb](http://ftp.us.debian.org/debian/pool/main/g/grub2/grub-common_1.99-8_amd64.deb)
[http://ftp.us.debian.org/debian/pool/main/g/grub2/grub-efi-amd64_1.99-8_amd64.deb](http://ftp.us.debian.org/debian/pool/main/g/grub2/grub-efi-amd64_1.99-8_amd64.deb) (64bit)
[http://ftp.us.debian.org/debian/pool/main/g/grub2/grub-efi-ia32_1.99-8_i386.deb](http://ftp.us.debian.org/debian/pool/main/g/grub2/grub-efi-ia32_1.99-8_i386.deb) (32bit)

Place them all in the same directory and open the terminal in the directory and run this:
```
sudo dpkg -i *
```
after the packages are finished installing you need to install grub to the ESP by this command:
```
sudo grub-install --boot-directory="/boot/efi/efi" --bootloader-id="grub" --no-floppy --recheck --debug
```
The only problem in the debian packages are that update-grub file will generate grub.cfg in /boot/grub instead of in the ESP (/boot/efi/efi/grub)
So open update-grub file:
```
gksu gedit /usr/sbin/update-grub
```
and change this line:
```
exec grub-mkconfig -o /boot/grub/grub.cfg "$@"
```
into:
```
exec grub-mkconfig --output /boot/efi/efi/grub/grub.cfg
```
save, and then run:
```
sudo update-grub
```
and in the end:
```
sudo efibootmgr --create --gpt --disk /dev/sda --part 1 --write-signature --label "GRUB2" --loader \\EFI\\grub\\grub.efi
```

also, just for compatibility with some other programs and scripts, symlink between the grub folder in the ESP and /boot/grub.
```
sudo ln -s /boot/efi/efi/grub /boot/grub
```

---

### Post by the-ridikulus-rat on 2011-06-29
> **Avidanborisov said:**
> 
Hi there!
Its been some time and I read a lot about UEFI and UEFI boot loaders for linux. Anyway, ELILO didn't work but I succeed to compile and install grub2-efi. So based on [skodabenz's script]("https://raw.github.com/skodabenz/My_Shell_Scripts/master/grub2/grub2_uefi.sh") I wrote a script that will automatically compile and install grub2 for UEFI systems. the script will also check for required dependencies, and will produce a package that can be easily uninstalled.
You can get the script by the following commands:
```
wget http://my-shell-scripts.googlecode.com/files/compile_grub2_uefi.sh
chmod +x compile_grub2_uefi.sh
./compile_grub2_uefi.sh
```
if you want some more info run this:
```
./compile_grub2_uefi.sh -h
```
Of course, any suggestions or bugs found are more then welcome to be reported.


Wow. That looks like a debianized version of my script (and interactive too). Anyway you might want to checkin some of the changes i made to the grub2_uefi.sh script (like prefix,bin,sbin dir vars etc.). If there are any distro-neutral changes in your script wrt mine, I would try to incorporate into my script. However I like to keep my script distro neutral as far as possible and non-interactive (except for sudo password prompt).

Few comments

1. Line 270 - dos2unix * will not work. Yoou need xman_dos2unix script to recursively change the line-ending in all files within sub-dirs. Also dos2unix --d2u should be used. Otherwise any unix line endings will be converted bnack to dos ones.

2. Line 300 - Although file names might me similar between grub-legacy and grub2, there are no usable "common" files among them.

3. Lines 345 and 346 - you are not actually runnning efibootmgr.sh, you make it executable and then delete it.

```

chmod +x efibootmgr.sh
rm efibootmgr.sh

```

Also creating efibootmgr.sh is unnecesssary IMO when you can run the commands directly.

4. Lines 364 and 365  - dangerous if someone boots using both grub2-bios and grub2-uefi. Grub2 bios files will be deleted. Use some other symlink path instead of /boot/grub.

5. Line 112 - typo mistakes.

---

### Post by Avidanborisov on 2011-06-30
> **skodabenz said:**
> Wow. That looks like a debianized version of my script (and interactive too). Anyway you might want to checkin some of the changes i made to the grub2_uefi.sh script (like prefix,bin,sbin dir vars etc.). If there are any distro-neutral changes in your script wrt mine, I would try to incorporate into my script. However I like to keep my script distro neutral as far as possible and non-interactive (except for sudo password prompt).

Few comments

1. Line 270 - dos2unix * will not work. Yoou need xman_dos2unix script to recursively change the line-ending in all files within sub-dirs. Also dos2unix --d2u should be used. Otherwise any unix line endings will be converted bnack to dos ones.

2. Line 300 - Although file names might me similar between grub-legacy and grub2, there are no usable "common" files among them.

3. Lines 345 and 346 - you are not actually runnning efibootmgr.sh, you make it executable and then delete it.

```

chmod +x efibootmgr.sh
rm efibootmgr.sh

```

Also creating efibootmgr.sh is unnecesssary IMO when you can run the commands directly.

4. Lines 364 and 365  - dangerous if someone boots using both grub2-bios and grub2-uefi. Grub2 bios files will be deleted. Use some other symlink path instead of /boot/grub.

5. Line 112 - typo mistakes.

Fixed, I have updated the script.
as about dos2unix, I am not sure if your xman_dos2unix supposed to do what I get from it. When I run it it will loop something like this, lots of times.
```
dos2unix 5.1.1 (2010-08-18)
Usage: dos2unix [-fhkLlqV] [-c convmode] [-o file ...] [-n infile outfile ...]
 -c --convmode    conversion mode
   convmode       ascii, 7bit, iso, mac, default to ascii
 -f --force       force conversion of all files
 -h --help        give this help
 -k --keepdate    keep output file date
 -L --license     display software license
 -l --newline     add additional newline
 -n --newfile     write to new file
   infile         original file in new file mode
   outfile        output file in new file mode
 -o --oldfile     write to old file
   file ...       files to convert in old file mode
 -q --quiet       quiet mode, suppress all warnings
                  always on in stdio mode
 -V --version     display version number

```
Also the reason that I am executing efibootmgr in a different script is because bash will always add one character brackets before and after EFI\grub\grub.efi . For example this line in bash as in your script:
```
sudo efibootmgr --create --gpt --disk "${EFISYS_PARENT_DEVICE}" --part [CODE]"${EFISYS_PART_NUM}" --write-signature --label "${GRUB2_UEFI_NAME}" --loader "\\EFI\\${GRUB2_UEFI_NAME}\\${GRUB2_UEFI_NAME}.efi"
```
Will actually output to:
```
sudo efibootmgr --create --gpt --disk /dev/sda --part 1 --write-signature --label grub --loader [COLOR="Red"]'[/COLOR]\EFI\grub\grub.efi[COLOR="red"]'[/COLOR]
```
While in sh it works great, the output will be:
```
sudo efibootmgr --create --gpt --disk /dev/sda --part 1 --write-signature --label grub --loader \EFI\grub\grub.efi
```

The main reason for symlinking is just for compatibility with all those GUI's and scripts for modifying grub. And why should someone use both GRUB UEFI and GRUB BIOS?

---

### Post by YesWeCan on 2011-06-30
A question to the learned:
I am not familiar with UEFI. But I presume you can make the bios boot any GPT partition. So why doesn't Ubuntu just create a tiny boot partition in which it only installs Grub's boot code + core.img to the PBR area, just like it would normally do to the MBR area of an MBR system? Then booting would be a cynch, wouldn't it?

This can be done manually, of course. It involves using the normal grub-install to the Ubuntu partition (for the sole purpose of configuring the files correctly). Then using dd to copy the boot code and the core.img to the special boot partition's PBR areas. I can provide details if you wish to implement this.

---

### Post by Avidanborisov on 2011-06-30
Also, @skodabenz - Why doesn't your script generate /etc/default/grub?
And, it although is has nothing with this thread, I saw you posting on onther forum that linux can mount msftres partitions (Microsoft Reserved Partition). I am asking this because I have this annoying partition which I can't to with anything, and Windows fails to boot without it.

---

### Post by Avidanborisov on 2011-06-30
> **YesWeCan said:**
> A question to the learned:
I am not familiar with UEFI. But I presume you can make the bios boot any GPT partition. So why doesn't Ubuntu just create a tiny boot partition in which it only installs Grub's boot code + core.img to the PBR area, just like it would normally do to the MBR area of an MBR system? Then booting would be a cynch, wouldn't it?

This can be done manually, of course. It involves using the normal grub-install to the Ubuntu partition (for the sole purpose of configuring the files correctly). Then using dd to copy the boot code and the core.img to the special boot partition's PBR areas. I can provide details if you wish to implement this.

UEFI is meant to be a modern replacement for the traditional BIOS. You can read more about it and linux here:
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

I didn't really understand what you meant, so:

1. Most of the modern UEFI systems come with GPT instead of MBR.
2. GRUB needs to be installed to the ESP (EFI SYSTEM PARTITION). The ESP has to be the first partition in the drive, with file system of a FAT variant, and it has to be larger then 100 MiB. Ubuntu mounts the ESP by default in /boot/efi .
3. After you install grub in the ESP, you need to make a boot enrty for it using efibootmgr, or you could launch it with the [UEFI shell]("https://help.ubuntu.com/community/UEFIBooting#UEFI Shell")

---

### Post by YesWeCan on 2011-06-30
Thanks, I'll read up. My suggestion is based on the conjecture (on my part) that your EFI mobo has the ability to boot a partition that has boot code in its PBR. If it cannot do this then that's different.

---

### Post by the-ridikulus-rat on 2011-06-30
> **Avidanborisov said:**
> Fixed, I have updated the script.
as about dos2unix, I am not sure if your xman_dos2unix supposed to do what I get from it. When I run it it will loop something like this, lots of times.
```
dos2unix 5.1.1 (2010-08-18)
Usage: dos2unix [-fhkLlqV] [-c convmode] [-o file ...] [-n infile outfile ...]
 -c --convmode    conversion mode
   convmode       ascii, 7bit, iso, mac, default to ascii
 -f --force       force conversion of all files
 -h --help        give this help
 -k --keepdate    keep output file date
 -L --license     display software license
 -l --newline     add additional newline
 -n --newfile     write to new file
   infile         original file in new file mode
   outfile        output file in new file mode
 -o --oldfile     write to old file
   file ...       files to convert in old file mode
 -q --quiet       quiet mode, suppress all warnings
                  always on in stdio mode
 -V --version     display version number

```


I have

```

keshav_pr@my-comp ~ % dos2unix -V
hd2u 1.0.3
keshav_pr@my-comp ~ % dos2unix --help
usage:
	dos2unix [--verbose|-v] [--test|-t] [--force|-f] \
		[--<x>2<y>|--auto|-<Z>] \
		[<file name> [...]]
where:
	--auto, -A	output will be set based upon auto-detection
			of source format
	--d2u, -U	perform DOS -> UNIX conversion
	--m2u, -T	perform MAC -> UNIX conversion
	--u2d, -D	perform UNIX -> DOS conversion
	--u2m, -M	perform UNIX -> MAC conversion
	--d2m, -O	perform DOS -> MAC conversion
	--m2d, -C	perform MAC -> DOS conversion

	--force		suppress internal conversion type corrections
			based on autodetected input format
	--skipbin, -b	skip binary files
	--test, -t	don't write any conversion results; useful with
			--verbose to just report on source type
	--verbose, -v	print extra information on stderr
	--version, -V	print version information on stderr

- when no options are given then input format will be automatically detected
  and converted as follows:
	DOS -> UNIX
	MAC -> UNIX
	UNIX -> DOS
- same as above applies if --auto option is used
- when no file is given, then stdin is used as input and stdout as output
- binary files will be skipped automatically if option --skipbin
  (or -b) is used
- stray '\r' characters (without a following '\n') in files in DOS format are
  reported but only conversion 'DOS -> Unix' affects them (they are skipped)
- stray '\n' characters in files in MAC format are not detected for now

```

I guess Archlinux uses a more updated version of dos2unix. I don't have separate dos2unix and unix2dos files, instead they have been incorporated into a single dos2unix file with --d2u and --u2d (for unix2dos) options.

> 
Also the reason that I am executing efibootmgr in a different script is because bash will always add one character brackets before and after EFI\grub\grub.efi . For example this line in bash as in your script:
```
sudo efibootmgr --create --gpt --disk "${EFISYS_PARENT_DEVICE}" --part "${EFISYS_PART_NUM}" --write-signature --label "${GRUB2_UEFI_NAME}" --loader "\\EFI\\${GRUB2_UEFI_NAME}\\${GRUB2_UEFI_NAME}.efi"
```
Will actually output to:
```
sudo efibootmgr --create --gpt --disk /dev/sda --part 1 --write-signature --label grub --loader [COLOR="Red"]'[/COLOR]\EFI\grub\grub.efi[COLOR="red"]'[/COLOR]
```
While in sh it works great, the output will be:
```
sudo efibootmgr --create --gpt --disk /dev/sda --part 1 --write-signature --label grub --loader \EFI\grub\grub.efi
```

The quotes in "\\EFI\\${GRUB2_UEFI_NAME}\\${GRUB2_UEFI_NAME}.efi" take care of any spaces in the GRUB2_UEFI_NAME env var (ie. the path. But you can remove " " quotes if you want.

> 
The main reason for symlinking is just for compatibility with all those GUI's and scripts for modifying grub. And why should someone use both GRUB UEFI and GRUB BIOS?


I know many people who use both grub2-bios and grub2-uefi just to test it out till grub2-uefi (or the uefi firmware in their system) becomes stable.

Also which one is more updated? [https://gist.github.com/1047884](https://gist.github.com/1047884) or [http://my-shell-scripts.googlecode.com/files/compile_grub2_uefi.sh](http://my-shell-scripts.googlecode.com/files/compile_grub2_uefi.sh) .

---

### Post by the-ridikulus-rat on 2011-06-30
> **Avidanborisov said:**
> 
Also, @skodabenz - Why doesn't your script generate /etc/default/grub?


My script has - lines 247

```

[ -e "${WD}/grub.default" ] && sudo cp --verbose "${WD}/grub.default" "${GRUB2_UEFI_SYSCONF_DIR}/default/grub" || true

```

line 265

```

[ -e "${WD}/grub.cfg" ] && sudo cp --verbose "${WD}/grub.cfg" "${GRUB2_UEFI_SYSTEM_PART_DIR}/${GRUB2_UEFI_MENU_CONFIG}.cfg" || true

```

It does not try to do more than what is necessary. If you have a grub.default file in ${WD}, it will copy it to ${GRUB2_UEFI_SYSCONF_DIR}/default/grub . It WILL NOT generate a grub.default file nor will it generate a grub.cfg by default (line 254 commented out)

line 254

```

# sudo "${GRUB2_UEFI_SBIN_DIR}/${GRUB2_UEFI_NAME}-mkconfig" --output="${GRUB2_UEFI_SYSTEM_PART_DIR}/${GRUB2_UEFI_MENU_CONFIG}.cfg" || true

```

I don't think it is a problem for a user to manually run the grub-mkconfig command if required.

I use a grub.cfg that cannot be generated by grub-mkconfig

```

insmod part_gpt
insmod fat
insmod ext2

set _root_part_uuid="XXXXXXXXXXXXXXX"
set _root_fs_uuid="XXXXXXXXXXXXXXX"

set _boot_part_uuid="XXXXXXXXXXXXXXX"
set _boot_fs_uuid="XXXXXXXXXXXXXXX"

search --fs-uuid --no-floppy --set=_arch64_boot ${_boot_fs_uuid}
# search --fs-uuid --no-floppy --set=_arch64_root ${_root_fs_uuid}

insmod efi_gop
insmod font

if loadfont ${prefix}/unicode.pf2
then
	insmod gfxterm
	set gfxmode=auto
	set gfxpayload=keep
	terminal_output gfxterm
	
	# set color_normal=light-blue/black
	# set color_highlight=light-cyan/blue
	
	# insmod png
	# insmod jpeg
	# insmod gfxmenu
	
	# background_image (${_arch64_boot})/images/archlinux.png
fi

set timeout=5
set default=2

set _kernel_flags="radeon.modeset=1 add_efi_memmap"
set _systemd="init=/bin/systemd"
set _rootfstype="ext4"

# menuentry "Arch Linux Stock Kernel" --users "keshav,user" {

menuentry "Arch Linux Stock Kernel" {
set root=(${_arch64_boot})
linux /vmlinuz26 root=/dev/disk/by-partuuid/${_root_part_uuid} ro rootfstype=${_rootfstype} ${_kernel_flags} pcie_aspm=force ${_systemd}
initrd /initramfs26.img
}

menuentry "Arch Linux Stock Kernel Fallback" {
set root=(${_arch64_boot})
linux /vmlinuz26 root=/dev/disk/by-partuuid/${_root_part_uuid} ro rootfstype=${_rootfstype} ${_kernel_flags} pcie_aspm=force ${_systemd}
initrd /initramfs26-fallback.img
}

menuentry "Arch Linux Mainline Kernel" {
set root=(${_arch64_boot})
linux /vmlinuz26-mainline root=/dev/disk/by-partuuid/${_root_part_uuid} ro rootfstype=${_rootfstype} ${_kernel_flags} pcie_aspm=force ${_systemd}
initrd /initramfs26-mainline.img
}

menuentry "Arch Linux Mainline Kernel Fallback" {
set root=(${_arch64_boot})
linux /vmlinuz26-mainline root=/dev/disk/by-partuuid/${_root_part_uuid} ro rootfstype=${_rootfstype} ${_kernel_flags} pcie_aspm=force ${_systemd}
initrd /initramfs26-mainline-fallback.img
}

menuentry "Windows 7 x86_64 Professional UEFI" {
search --file --no-floppy --set=root /efi/Microsoft/Boot/bootmgfw.efi
chainloader (${root})/efi/Microsoft/Boot/bootmgfw.efi
}

```

> 
And, it although is has nothing with this thread, I saw you posting on onther forum that linux can mount msftres partitions (Microsoft Reserved Partition). I am asking this because I have this annoying partition which I can't to with anything, and Windows fails to boot without it.


Microsoft reserved Partition as the name says is a Reserved Partition for FUTURE USE by Windows OS to compensate for the lack of 32 KiB space following the MBR region in GPT partitioning wherein the said space has been taken up by GPT Primary Header and Primary Partition Table. One use of that partition is converting Basic Data Partitions to Windows Dynamic paritions (Windows equivalent of Linux LVM). I have deleted that partition in my system to prevent accidental conversion of my partition to dynamic ones by Windows. As such it is not needed for normal booting of Windows in UEFI-GPT setup.

And about my script, I started writing it in Fedora and continued it Archlinux, so I would like to keep it cross-distro and make it do just the bare-minimum needed to get grub2-uefi compiled and setup to boot. I will be making changes to it from time-to-time (even to grub2_bios.sh script) but I won't be incorporating automatic generation of /etc/default/grub and such stuff (this kind of stuff is highly specific to Debian/Ubuntu systems).

---

### Post by the-ridikulus-rat on 2011-06-30
Ok. I am confused. There are atleast three different implementations of dos2unix.

[http://waterlan.home.xs4all.nl/dos2unix.html](http://waterlan.home.xs4all.nl/dos2unix.html)
[http://www.thefreecountry.com/tofrodos/index.shtml](http://www.thefreecountry.com/tofrodos/index.shtml)
[http://hany.sk/~hany/software/hd2u/](http://hany.sk/~hany/software/hd2u/)

Archlinux uses the 3rd one which ironically does not seem to be updated in years. I don't know which one ubuntu uses or most other distros use (either one of the first two).

---

### Post by the-ridikulus-rat on 2011-06-30
I have updated the [https://raw.github.com/skodabenz/My_Shell_Scripts/master/xmanutility/xman_dos2unix.sh](https://raw.github.com/skodabenz/My_Shell_Scripts/master/xmanutility/xman_dos2unix.sh) script to use [http://waterlan.home.xs4all.nl/dos2unix.html](http://waterlan.home.xs4all.nl/dos2unix.html) dos2unix command. I suppose thats the one mostly widely used (in many linux distros). The xman script uses some recent options like "-ascii --safe --skip-symlink" so you might have to update your version.

My dos2unix is now -

```

keshav_pr@my-comp ~ % dos2unix -V
dos2unix 5.3 (2011-04-26)
With native language support.
LOCALEDIR: /usr/share/locale

```

```

keshav_pr@my-comp ~ % dos2unix -h
dos2unix 5.3 (2011-04-26)
Usage: dos2unix [options] [file ...] [-n infile outfile ...]
 -ascii                convert only line breaks (default)
 -iso                  conversion between DOS and ISO-8859-1 character set
   -1252               Use Windows code page 1252 (Western European)
   -437                Use DOS code page 437 (US) (default)
   -850                Use DOS code page 850 (Western European)
   -860                Use DOS code page 860 (Portuguese)
   -863                Use DOS code page 863 (French Canadian)
   -865                Use DOS code page 865 (Nordic)
 -7                    Convert 8 bit characters to 7 bit space
 -c, --convmode        conversion mode
   convmode            ascii, 7bit, iso, mac, default to ascii
 -f, --force           force conversion of binary files
 -h, --help            give this help
 -k, --keepdate        keep output file date
 -L, --license         display software license
 -l, --newline         add additional newline
 -n, --newfile         write to new file
   infile              original file in new file mode
   outfile             output file in new file mode
 -o, --oldfile         write to old file
   file ...            files to convert in old file mode
 -q, --quiet           quiet mode, suppress all warnings
                       always on in stdio mode
 -s, --safe            skip binary files (default)
 -F, --follow-symlink  follow symbolic links and convert the targets
 -R, --replace-symlink replace symbolic links with converted files
                       (original target files remain unchanged)
 -S, --skip-symlink    keep symbolic links and targets unchanged (default)
 -V, --version         display version number

```

I think this solves the dos2unix problem. This is mostly for those who checkout the grub2 bzr repo in Winodws and then try to compile it in linux. In that case autogen.sh script will not run due to CRLF (dos) line endings in the script due to initial checkout in Windows. It will give errors like

```

./autogen.sh: line 2: $'\r': command not found

```

Hope this helps.

---

### Post by srs5694 on 2011-06-30
> **YesWeCan said:**
> A question to the learned:
I am not familiar with UEFI. But I presume you can make the bios boot any GPT partition. So why doesn't Ubuntu just create a tiny boot partition in which it only installs Grub's boot code + core.img to the PBR area, just like it would normally do to the MBR area of an MBR system? Then booting would be a cynch, wouldn't it?

If you're talking about UEFI booting, as your first sentence suggests, the reason is that UEFI booting doesn't work that way. In UEFI, all boot operations are based on *files*, not code tucked away in MBRs, PBRs, partitions that don't have filesystems, or unallocated parts of the disk. At least, that's the way it normally works; I suppose you could always write a boot loader that relies on one of these things, but the only reason I can think of to do such a thing would be to enable older BIOS-based OSes to boot on a UEFI-based computer -- something like the opposite of UEFI DUET, which implements UEFI for BIOS-based computers. (In fact, most UEFI-based x86 and x86-64 systems implement a BIOS compatibility mode, so you can end up with a mish-mash of BIOS and UEFI booting.)

If you're talking about BIOS booting on GPT, then that's close to what GRUB does on such systems; the core.img code goes in the BIOS Boot Partition and is loaded by an MBR-resident boot loader.

[quote=Avidanborisov]2. GRUB needs to be installed to the ESP (EFI SYSTEM PARTITION). The ESP  has to be the first partition in the drive, with file system of a FAT  variant, and it has to be larger then 100 MiB. Ubuntu mounts the ESP by  default in /boot/efi .[/quote]

These "requirements" are certainly the conventional layout of a GPT disk, but most of them aren't actually requirements in the GPT spec. Specifically:


[list]
[*]You can boot with something other than GRUB, so GRUB doesn't need to be installed to the ESP; but of course the context is about GRUB, so in that context this isn't really incorrect, and I realize you probably didn't intend to say that GRUB was a requirement for UEFI booting. I only mention this so that somebody reading your post out of context isn't misled into thinking that GRUB is required on all UEFI-based systems. In fact, it's not even required to boot Linux, since ELILO can do that job, too.
[*]The ESP does *not* need to be the first partition on the disk. According to the UEFI spec (version 2.3 errata B), p. 476: "UEFI does not impose a restriction on the number or location of System Partitions that can exist on a system. System Partitions are discovered when required by UEFI firmware...." That said, Microsoft says, in its [GPT FAQ,](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx#X-201104111922504) that it supports just one ESP per disk and that it "should be first on the disk." This, however, is *Microsoft's* requirement. Since Microsoft is not in charge of the UEFI spec, this should be considered Microsoft's limitation, not a UEFI requirement. (Ironically, the Windows installer will create a second ESP if it doesn't like the one that's present on the disk, so Microsoft violates its own requirement under certain conditions!)
[*]The ESP's filesystem is supposed to be not just FAT, but FAT32, as per the UEFI spec (as above), p. 472: "EFI encompasses the use of FAT32 for a system partition..." In practice, (U)EFI implementations support as ESPs whatever filesystems they support at all, which means any version of FAT or, for Macintoshes, HFS+. Unfortunately, Ubuntu creates a FAT16 ESP. This wouldn't be so bad except that Microsoft is a stickler for this particular detail; the Windows 7 installer won't use a FAT16 ESP, and instead creates a new FAT32 ESP. (Windows Vista is supposed to be more flexible on this score.)
[*]I'm not aware of any statement in the UEFI spec concerning the size of an ESP. Microsoft's FAQ says that the ESP should be "approximately 100MBs," whereas Apple, in its [Tech Note 2166,](http://developer.apple.com/library/mac/#technotes/tn2166/_index.html) says the ESP should be "200 MB." I haven't studied the issue in detail, but Ubuntu's installer seems to vary the size of its ESP with the disk size, and they're often skimpy by these standards -- I've seen Ubuntu-created ESPs as small as 32 MiB. Personally, I recommend creating an ESP in the 100-200 MiB range, or possibly larger if you expect to boot several kernels with ELILO. The reason is that ELILO relies on the firmware to load the kernel and initial RAM disk, so these things are normally stored on the ESP when using ELILO. A kernel and initial RAM disk can total close to 20 MB, so a few of them can fill a 100 MiB ESP pretty quickly if you're booting more than one Linux distribution.
[/list]

---

### Post by YesWeCan on 2011-07-01
> **srs5694 said:**
> If you're talking about UEFI booting, as your first sentence suggests, the reason is that UEFI booting doesn't work that way. In UEFI, all boot operations are based on *files*, not code tucked away in MBRs, PBRs, partitions that don't have filesystems, or unallocated parts of the disk. At least, that's the way it normally works; I suppose you could always write a boot loader that relies on one of these things, but the only reason I can think of to do such a thing would be to enable older BIOS-based OSes to boot on a UEFI-based computer -- something like the opposite of UEFI DUET, which implements UEFI for BIOS-based computers. (In fact, most UEFI-based x86 and x86-64 systems implement a BIOS compatibility mode, so you can end up with a mish-mash of BIOS and UEFI booting.)

If you're talking about BIOS booting on GPT, then that's close to what GRUB does on such systems; the core.img code goes in the BIOS Boot Partition and is loaded by an MBR-resident boot loader.
This is where I am coming from. It seems to me that the advantage of UEFI (I gather UEFI has superseded EFI)is that it supports GPT and that it supports a more sophisticated booting system - whole boot files can be executed rather than a tiny MBR boot code. Is that right?
It also seems to me that it would be highly convenient if the UEFI system also supported booting from PBR or MBR code, preferably the latter as one doesn't really want to mess with the "protective MBR code" in a GPT disk. In this way, an OS or loader that doesn't support UEFI and is installed on a GPT disk can still be directly booted via PBR boot code.
In this way, Windows could be directly booted on a GPT disk. Grub could be directly booted. And I must assume a disk in the system that has MBR PT rather than GPT could be directly booted.

My question is, is an UEFI mobo flexible enough to be able to boot using either the UEFI boot files in the ESP of a GPT disk or boot the PBR code of a partition on a GPT disk or boot the MBR code of a disk that uses MBR PT?

I assumed UEFI would cater for all of these options.

IOW if one wanted to install Ubuntu to a GPT disk and boot using Grub2, one could simply set up a partition for Grub's boot code and have the UEFI system boot the PBR directly. So a special UEFI-Grub boot file would not be necessary (although such a thing would be simpler to set up once it works).

[edit]
Another thought. Are the .efi files in the ESP just executable binaries? IOW could Grub's core.img (which is the position-independent pre-loader for Grub) be modified (to remove its own boot sector) and given a .efi suffix and put in the ESP? In principle?

---

### Post by Avidanborisov on 2011-07-01
> **YesWeCan said:**
> Thanks, I'll read up. My suggestion is based on the conjecture (on my part) that your EFI mobo has the ability to boot a partition that has boot code in its PBR. If it cannot do this then that's different.

Well, it should, but at least for me nothing else than UEFI-GPT works.


> i have

```

keshav_pr@my-comp ~ % dos2unix -v
hd2u 1.0.3
keshav_pr@my-comp ~ % dos2unix --help
usage:
	Dos2unix [--verbose|-v] [--test|-t] [--force|-f] \
		[--<x>2<y>|--auto|-<z>] \
		[<file name> [...]]
where:
	--auto, -a	output will be set based upon auto-detection
			of source format
	--d2u, -u	perform dos -> unix conversion
	--m2u, -t	perform mac -> unix conversion
	--u2d, -d	perform unix -> dos conversion
	--u2m, -m	perform unix -> mac conversion
	--d2m, -o	perform dos -> mac conversion
	--m2d, -c	perform mac -> dos conversion

	--force		suppress internal conversion type corrections
			based on autodetected input format
	--skipbin, -b	skip binary files
	--test, -t	don't write any conversion results; useful with
			--verbose to just report on source type
	--verbose, -v	print extra information on stderr
	--version, -v	print version information on stderr

- when no options are given then input format will be automatically detected
  and converted as follows:
	Dos -> unix
	mac -> unix
	unix -> dos
- same as above applies if --auto option is used
- when no file is given, then stdin is used as input and stdout as output
- binary files will be skipped automatically if option --skipbin
  (or -b) is used
- stray '\r' characters (without a following '\n') in files in dos format are
  reported but only conversion 'dos -> unix' affects them (they are skipped)
- stray '\n' characters in files in mac format are not detected for now

```

i guess archlinux uses a more updated version of dos2unix. I don't have separate dos2unix and unix2dos files, instead they have been incorporated into a single dos2unix file with --d2u and --u2d (for unix2dos) options.

This is what I get when i execute this:

```
avidan@avibuntu:~$ dos2unix --help
dos2unix 5.1.1 (2010-08-18)
Usage: dos2unix [-fhkLlqV] [-c convmode] [-o file ...] [-n infile outfile ...]
 -c --convmode    conversion mode
   convmode       ascii, 7bit, iso, mac, default to ascii
 -f --force       force conversion of all files
 -h --help        give this help
 -k --keepdate    keep output file date
 -L --license     display software license
 -l --newline     add additional newline
 -n --newfile     write to new file
   infile         original file in new file mode
   outfile        output file in new file mode
 -o --oldfile     write to old file
   file ...       files to convert in old file mode
 -q --quiet       quiet mode, suppress all warnings
                  always on in stdio mode
 -V --version     display version number
```

Also, the description of this package is:

This package contains utilities dos2unix, unix2dos, mac2unix,
unix2mac to convert the line endings of text files between UNIX (LF),
DOS (CRLF) and Mac (CR) formats.

Text files under Windows and DOS typically have two ASCII characters
at the end of each line: CR (carriage return) followed by LF (line
feed). Older Macs used just CR, while UNIX uses just LF. While most
modern editors can read all these formats, there may still be a need
to convert files between them.

**This is the classic utility developed in 1989.**

> the quotes in "\\efi\\${grub2_uefi_name}\\${grub2_uefi_name}.efi" take care of any spaces in the grub2_uefi_name env var (ie. The path. But you can remove " " quotes if you want.

The problem is in bash. When I execute this in bash (with quotes):

```
sudo efibootmgr --create --gpt --disk "${EFISYS_PARENT_DEVICE}" --part "${EFISYS_PART_NUM}" --write-signature --label "${GRUB2_UEFI_NAME}" --loader "\\EFI\\${GRUB2_UEFI_NAME}\\${GRUB2_UEFI_NAME}.efi"
```

bash will execute it as this (with one character brackets which will not produce any errors but will fail to boot, at least for me.):

```
sudo efibootmgr --create --gpt --disk /dev/sda --part 1 --write-signature --label grub --loader [COLOR="Red"]'[/COLOR]\EFI\grub\grub.efi[COLOR="red"]'[/COLOR]
```

When I execute this in bash (without quotes):

```
sudo efibootmgr --create --gpt --disk "${EFISYS_PARENT_DEVICE}" --part "${EFISYS_PART_NUM}" --write-signature --label "${GRUB2_UEFI_NAME}" --loader \\EFI\\${GRUB2_UEFI_NAME}\\${GRUB2_UEFI_NAME}.efi
```

I will still get this:

```
sudo efibootmgr --create --gpt --disk /dev/sda --part 1 --write-signature --label grub --loader [COLOR="red"]'[/COLOR]\EFI\grub\grub.efi[COLOR="red"]'[/COLOR]
```

which will not work.

I tried many variations, and the only one that works for me as a script is this, under sh and not bash:

```
sudo efibootmgr --create --gpt --disk ${EFISYS_PARENT_DEVICE} --part ${EFISYS_PART_NUM} --write-signature --label ${GRUB2_UEFI_NAME} --loader \\\\EFI\\\\${GRUB2_UEFI_NAME}\\\\${GRUB2_UEFI_NAME}.efi
```

which will output to:

```
sudo efibootmgr --create --gpt --disk /dev/sda --part 1 --write-signature --label grub --loader \\EFI\\grub\\grub.efi
```

and will work successfuly.


> i know many people who use both grub2-bios and grub2-uefi just to test it out till grub2-uefi (or the uefi firmware in their system) becomes stable.


Also which one is more updated? [https://gist.github.com/1047884](https://gist.github.com/1047884) or [http://my-shell-scripts.googlecode.com/files/compile_grub2_uefi.sh](http://my-shell-scripts.googlecode.com/files/compile_grub2_uefi.sh) .

OK, I have updated it and warned that it is not recommended for people with both GRUB BIOS and GRUB UEFI to symlink between the ESP and /boot/grub.
The updated script is always in google code.

> my script has - lines 247

```

[ -e "${wd}/grub.default" ] && sudo cp --verbose "${wd}/grub.default" "${grub2_uefi_sysconf_dir}/default/grub" || true

```

line 265

```

[ -e "${wd}/grub.cfg" ] && sudo cp --verbose "${wd}/grub.cfg" "${grub2_uefi_system_part_dir}/${grub2_uefi_menu_config}.cfg" || true

```

it does not try to do more than what is necessary. If you have a grub.default file in ${wd}, it will copy it to ${grub2_uefi_sysconf_dir}/default/grub . It will not generate a grub.default file nor will it generate a grub.cfg by default (line 254 commented out)


> ```

# sudo "${grub2_uefi_sbin_dir}/${grub2_uefi_name}-mkconfig" --output="${grub2_uefi_system_part_dir}/${grub2_uefi_menu_config}.cfg" || true

```

i don't think it is a problem for a user to manually run the grub-mkconfig command if required.

> I use a grub.cfg that cannot be generated by grub-mkconfig

```

insmod part_gpt
insmod fat
insmod ext2

set _root_part_uuid="xxxxxxxxxxxxxxx"
set _root_fs_uuid="xxxxxxxxxxxxxxx"

set _boot_part_uuid="xxxxxxxxxxxxxxx"
set _boot_fs_uuid="xxxxxxxxxxxxxxx"

search --fs-uuid --no-floppy --set=_arch64_boot ${_boot_fs_uuid}
# search --fs-uuid --no-floppy --set=_arch64_root ${_root_fs_uuid}

insmod efi_gop
insmod font

if loadfont ${prefix}/unicode.pf2
then
	insmod gfxterm
	set gfxmode=auto
	set gfxpayload=keep
	terminal_output gfxterm
	
	# set color_normal=light-blue/black
	# set color_highlight=light-cyan/blue
	
	# insmod png
	# insmod jpeg
	# insmod gfxmenu
	
	# background_image (${_arch64_boot})/images/archlinux.png
fi

set timeout=5
set default=2

set _kernel_flags="radeon.modeset=1 add_efi_memmap"
set _systemd="init=/bin/systemd"
set _rootfstype="ext4"

# menuentry "arch linux stock kernel" --users "keshav,user" {

menuentry "arch linux stock kernel" {
set root=(${_arch64_boot})
linux /vmlinuz26 root=/dev/disk/by-partuuid/${_root_part_uuid} ro rootfstype=${_rootfstype} ${_kernel_flags} pcie_aspm=force ${_systemd}
initrd /initramfs26.img
}

menuentry "arch linux stock kernel fallback" {
set root=(${_arch64_boot})
linux /vmlinuz26 root=/dev/disk/by-partuuid/${_root_part_uuid} ro rootfstype=${_rootfstype} ${_kernel_flags} pcie_aspm=force ${_systemd}
initrd /initramfs26-fallback.img
}

menuentry "arch linux mainline kernel" {
set root=(${_arch64_boot})
linux /vmlinuz26-mainline root=/dev/disk/by-partuuid/${_root_part_uuid} ro rootfstype=${_rootfstype} ${_kernel_flags} pcie_aspm=force ${_systemd}
initrd /initramfs26-mainline.img
}

menuentry "arch linux mainline kernel fallback" {
set root=(${_arch64_boot})
linux /vmlinuz26-mainline root=/dev/disk/by-partuuid/${_root_part_uuid} ro rootfstype=${_rootfstype} ${_kernel_flags} pcie_aspm=force ${_systemd}
initrd /initramfs26-mainline-fallback.img
}

menuentry "windows 7 x86_64 professional uefi" {
search --file --no-floppy --set=root /efi/microsoft/boot/bootmgfw.efi
chainloader (${root})/efi/microsoft/boot/bootmgfw.efi
}

```


I totally understand that, however I tried my script to be as much as more compatible with grub as it is by default in ubuntu which means that the configuration as stored in /etc/default/grub and you update grub.cfg by update-grub command.

> microsoft reserved partition as the name says is a reserved partition for future use by windows os to compensate for the lack of 32 kib space following the mbr region in gpt partitioning wherein the said space has been taken up by gpt primary header and primary partition table. One use of that partition is converting basic data partitions to windows dynamic paritions (windows equivalent of linux lvm). I have deleted that partition in my system to prevent accidental conversion of my partition to dynamic ones by windows. As such it is not needed for normal booting of windows in uefi-gpt setup.

When I tried to delete that partition, windows could not boot, in the middle of the boot proccess I would get a quick BSOD and the system will move to the next boot entry. but do you have any idea how to actually mount/access/do something like move or resizing to that partition?

> And about my script, i started writing it in fedora and continued it archlinux, so i would like to keep it cross-distro and make it do just the bare-minimum needed to get grub2-uefi compiled and setup to boot. I will be making changes to it from time-to-time (even to grub2_bios.sh script) but i won't be incorporating automatic generation of /etc/default/grub and such stuff (this kind of stuff is highly specific to debian/ubuntu systems).

Again, totally understand that. I know my modification of your script isn't cross-distro, and I didn't tried it to be, I modified your script to be as easy as possible to use and as much as closer to regular grub as it should appear in ubuntu/debian .

> **skodabenz said:**
> ok. I am confused. There are atleast three different implementations of dos2unix.

[http://waterlan.home.xs4all.nl/dos2unix.html](http://waterlan.home.xs4all.nl/dos2unix.html)
[http://www.thefreecountry.com/tofrodos/index.shtml](http://www.thefreecountry.com/tofrodos/index.shtml)
[http://hany.sk/~hany/software/hd2u/](http://hany.sk/~hany/software/hd2u/)

archlinux uses the 3rd one which ironically does not seem to be updated in years. I don't know which one ubuntu uses or most other distros use (either one of the first two).

Ubuntu apperas to be using a one that was developed in 1989..

> These "requirements" are certainly the conventional layout of a GPT disk, but most of them aren't actually requirements in the GPT spec. Specifically:


[list]
[*]You can boot with something other than GRUB, so GRUB doesn't need to be installed to the ESP; but of course the context is about GRUB, so in that context this isn't really incorrect, and I realize you probably didn't intend to say that GRUB was a requirement for UEFI booting. I only mention this so that somebody reading your post out of context isn't misled into thinking that GRUB is required on all UEFI-based systems. In fact, it's not even required to boot Linux, since ELILO can do that job, too.
[*]The ESP does *not* need to be the first partition on the disk. According to the UEFI spec (version 2.3 errata B), p. 476: "UEFI does not impose a restriction on the number or location of System Partitions that can exist on a system. System Partitions are discovered when required by UEFI firmware...." That said, Microsoft says, in its [GPT FAQ,](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx#X-201104111922504) that it supports just one ESP per disk and that it "should be first on the disk." This, however, is *Microsoft's* requirement. Since Microsoft is not in charge of the UEFI spec, this should be considered Microsoft's limitation, not a UEFI requirement. (Ironically, the Windows installer will create a second ESP if it doesn't like the one that's present on the disk, so Microsoft violates its own requirement under certain conditions!)
[*]The ESP's filesystem is supposed to be not just FAT, but FAT32, as per the UEFI spec (as above), p. 472: "EFI encompasses the use of FAT32 for a system partition..." In practice, (U)EFI implementations support as ESPs whatever filesystems they support at all, which means any version of FAT or, for Macintoshes, HFS+. Unfortunately, Ubuntu creates a FAT16 ESP. This wouldn't be so bad except that Microsoft is a stickler for this particular detail; the Windows 7 installer won't use a FAT16 ESP, and instead creates a new FAT32 ESP. (Windows Vista is supposed to be more flexible on this score.)
[*]I'm not aware of any statement in the UEFI spec concerning the size of an ESP. Microsoft's FAQ says that the ESP should be "approximately 100MBs," whereas Apple, in its [Tech Note 2166,](http://developer.apple.com/library/mac/#technotes/tn2166/_index.html) says the ESP should be "200 MB." I haven't studied the issue in detail, but Ubuntu's installer seems to vary the size of its ESP with the disk size, and they're often skimpy by these standards -- I've seen Ubuntu-created ESPs as small as 32 MiB. Personally, I recommend creating an ESP in the 100-200 MiB range, or possibly larger if you expect to boot several kernels with ELILO. The reason is that ELILO relies on the firmware to load the kernel and initial RAM disk, so these things are normally stored on the ESP when using ELILO. A kernel and initial RAM disk can total close to 20 MB, so a few of them can fill a 100 MiB ESP pretty quickly if you're booting more than one Linux distribution.
[/list]

1. Of course GRUB must not exist on every UEFI system, not even linux as you said, I just mentioned that a bootloader such as grub should exist in the ESP.

2. Thanks for the info, I didn't knew that. Anyway, will I be correct when I will say that it is RECOMMENDED that the ESP will be the first partition? I think this is just at least for me, more convenient.
3. Actually, both Windows 7 and Ubuntu created for me an ESP with FAT16 filesystem which works great for windows too.
4. I just mentioned that because I used to have an ESP with 100 MiB which filled up very quickly, so I had to resize it.

> This is where I am coming from. It seems to me that the advantage of UEFI (I gather UEFI has superseded EFI)is that it supports GPT and that it supports a more sophisticated booting system - whole boot files can be executed rather than a tiny MBR boot code. Is that right?

Pretty much. UEFI is meant to be a modern and smarter replacement for the traditional BIOS-MBR.

> It also seems to me that it would be highly convenient if the UEFI system also supported booting from PBR or MBR code, preferably the latter as one doesn't really want to mess with the "protective MBR code" in a GPT disk. In this way, an OS or loader that doesn't support UEFI and is installed on a GPT disk can still be directly booted via PBR boot code.
In this way, Windows could be directly booted on a GPT disk. Grub could be directly booted. And I must assume a disk in the system that has MBR PT rather than GPT could be directly booted.

Actually it does should support that. In my mobo I have the option to boot in UEFI mode hard drive or removable media, but I don't whether it is me doing something wrong or something is wrong with the firmware, but when i tried to boot ubuntu installer without UEFI mode and installed ubuntu as regularly, I was stuck with a black screen.

> My question is, is an UEFI mobo flexible enough to be able to boot using either the UEFI boot files in the ESP of a GPT disk or boot the PBR code of a partition on a GPT disk or boot the MBR code of a disk that uses MBR PT?

I assumed UEFI would cater for all of these options.

Again, it does, or at least should. but actually now I prefer to use UEFI instead of traditional BIOS-MBR compability mode, well, because  UEFI is actually a lot of easier and convenient to set up. I think it is just matter of time until the support for UEFI will be much better.

> IOW if one wanted to install Ubuntu to a GPT disk and boot using Grub2, one could simply set up a partition for Grub's boot code and have the UEFI system boot the PBR directly. So a special UEFI-Grub boot file would not be necessary (although such a thing would be simpler to set up once it works).

Correct.

> 
[edit]
Another thought. Are the .efi files in the ESP just executable binaries? IOW could Grub's core.img (which is the position-independent pre-loader for Grub) be modified (to remove its own boot sector) and given a .efi suffix and put in the ESP? In principle?


The .efi files are executable binaries for the UEFI firnware so I don't think renaming core.img to core.efi can be done.

---

### Post by srs5694 on 2011-07-01
> **YesWeCan said:**
> This is where I am coming from. It seems to me that the advantage of UEFI (I gather UEFI has superseded EFI)is that it supports GPT and that it supports a more sophisticated booting system - whole boot files can be executed rather than a tiny MBR boot code. Is that right?

That's part of it; but there are other factors that contribute to the push toward UEFI. Some of them aren't directly relevant to end users, though. They include:


[list]
[*]UEFI is written in C, which makes porting and maintaining it easier than porting and maintaining the BIOS, which is written in 16-bit assembly code. (At least, that's the claim; the firmware industry has a lot of existing code and expertise in 16-bit assembly code, so switching to C isn't all roses for them.)
[*]UEFI runs using the platform's native bit width -- 64-bit for x86-64 systems. (My suspicion is that Intel is pushing UEFI for this reason, since it would let them drop support for the antiquated 16-bit modes from their CPUs in a few years. This is only a suspicion, though.)
[*]UEFI is more easily extensible than BIOS. You can add drivers for video cards, filesystems, etc. In some cases this can obviate the need to put firmware on the hardware in question.
[/list]


These are just off the top of my head; I'm sure there are others that I'm forgetting.

> It also seems to me that it would be highly convenient if the UEFI system also supported booting from PBR or MBR code, preferably the latter as one doesn't really want to mess with the "protective MBR code" in a GPT disk. In this way, an OS or loader that doesn't support UEFI and is installed on a GPT disk can still be directly booted via PBR boot code.

It doesn't work like that. The OS has to support the partitioning system, and perhaps the firmware, in order to operate normally. If you were to try this with DOS, OS/2, BeOS, Windows XP, or some other legacy OS, it wouldn't work, since the OS wouldn't be able to read the GPT partitions. (Note that reading the partition table is *not* a function of the BIOS -- it's the OS that reads and interprets the partition table, *not* the BIOS!) Some OSes also rely on BIOS calls early in their boot process (or even after they've booted), and when booting in UEFI mode, those wouldn't be present.

This suggestion is pointless for something like Windows Vista or 7 64-bit, since these OSes support UEFI boot directly. Booting them in UEFI mode via PBR code would be like buying a new sports car and using it to tow an 18th-century wagon.

> My question is, is an UEFI mobo flexible enough to be able to boot using either the UEFI boot files in the ESP of a GPT disk or boot the PBR code of a partition on a GPT disk or boot the MBR code of a disk that uses MBR PT?

Most or all current (U)EFI implementations for x86 and x86-64 provide a BIOS compatibility mode. This enables them to boot using either UEFI or BIOS boot mechanisms. I know that it's possible for a boot loader to switch dynamically between them on a Mac, but I'm not sure if that's possible with the UEFI implementations on the latest crop of commodity PCs. Such boards typically have an option you can set in the firmware relating to which boot mode is used. Note that the BIOS compatibility mode, when activated, essentially takes over the firmware side of the PC; the computer becomes a regular BIOS-based computer as far as the boot loader and OS are concerned.

It should also be noted that UEFI isn't restricted to x86 and x86-64 systems. IIRC, UEFI was developed first for Itanium systems, and I think it's used on one or two other platforms, too. On such systems, there's no point in implementing BIOS compatibility or booting from MBR or PBR, since OS support for such methods is nonexistent.

> IOW if one wanted to install Ubuntu to a GPT disk and boot using Grub2, one could simply set up a partition for Grub's boot code and have the UEFI system boot the PBR directly. So a special UEFI-Grub boot file would not be necessary (although such a thing would be simpler to set up once it works).

You could boot in BIOS mode in this way, and as a practical matter, that's the easiest way to get Ubuntu up and running on the current crop of UEFI-based computers. This says more about the poor state of Ubuntu's UEFI support than it does about UEFI's method of booting, though; Ubuntu's UEFI installation and booting methods just leave a lot to be desired, in my experience. Once you've got it set up properly, though, booting in UEFI mode works fine, and once the Ubuntu developers work the bugs out of their UEFI installation code, it should become slightly easier to install and maintain a system to boot in UEFI mode than in BIOS mode.

> Another thought. Are the .efi files in the ESP just executable binaries? IOW could Grub's core.img (which is the position-independent pre-loader for Grub) be modified (to remove its own boot sector) and given a .efi suffix and put in the ESP? In principle?

I'm not sure if *all* .efi files are executable binaries, but many of them are. Looked at *very* broadly, the grub.efi file (or whatever name it's given on any given installation) is what you suggest. There are many details that differ, though. Most importantly, the core.img file is (I think) 16-bit x86 code, whereas grub.efi is 64-bit x86-64 (on most UEFI systems) or 32-bit x86 (on some early Intel-based Macs) code. There are also file format differences, differences in the firmware calls the code uses, and other differences, as well. In other words, you can't hack together a grub.efi file by taking a binary core.img file and doing a few dd operations on it; you need to build it from the GRUB source code.

Broadly speaking, I recommend that you stop thinking in BIOS terms when considering UEFI booting. The two are very different systems, and there's no point in trying to cram BIOS-style booting into a UEFI framework. A BIOS compatibility layer is a partial exception to this rule -- but such a framework *replaces* the UEFI system, at least on a boot-by-boot basis.

> **Avidanborisov]will I be correct when I will say that it is RECOMMENDED that the ESP will be the first partition?[/quote]

Phrasing the question in the passive voice omits the critical detail of who is doing the recommending, which makes it impossible to give a simple answer to the question as stated. If you fill in that information, the answer depends on that detail. If it's the UEFI Forum (who are in charge of the spec), then the answer seems to be "no," at least based on the spec itself. If it's Microsoft, then the answer is "yes," based on their EFI FAQ.

As a practical matter, it's beneficial to keep the ESP out of the way of other partitions, which means putting it first or last on the disk said:**
> Actually, both Windows 7 and Ubuntu created for me an ESP with FAT16 filesystem which works great for windows too.

I'm skeptical of this claim. If you installed Windows first, then Ubuntu 11.04 has the terrible habit of creating a new filesystem on the ESP, so if you didn't check the partition's status between installing Windows and Ubuntu, you'd find that it would have a FAT16 ESP, despite the fact that Windows created it as a FAT32 partition.

I've done several Windows 7 installations. They've all created FAT32 ESPs, and every time I've tried installing Windows 7 to a system with an existing FAT16 ESP, the Windows installer has refused to accept it, which has ultimately derailed the installation. I've seen similar reports from others. I'm told that Windows Vista is more forgiving on this score, but I don't have a 64-bit version of that OS with which to test.

[quote=Avidanborisov][quote=YesWeCan]IOW if one wanted to install Ubuntu to a GPT disk and boot using Grub2, one could simply set up a partition for Grub's boot code and have the UEFI system boot the PBR directly. So a special UEFI-Grub boot file would not be necessary (although such a thing would be simpler to set up once it works).[/quote]
Correct.[/quote]

Not quite; see my response above.

The BIOS compatibility mode in current x86 and x86-64 UEFI firmware is a handy stopgap; it helps with legacy OSes with no or poor UEFI support. It makes it easy for users to lose sight of what's happening, though. When BIOS compatibility mode is active, the computer acts just like a BIOS-based computer, and it boots via the MBR (and perhaps PBRs); and when BIOS compatibility mode is *not* active, the computer acts like a UEFI-based computer and boots via .efi files in the ESP. It's sort of like a dual-boot on the firmware level -- you choose which firmware to use (BIOS or UEFI), not just which OS to use. Although you *could* write a boot loader that merges the two in one way or another, I can't think of an advantage to doing so. Note that just redirecting the boot process isn't enough -- you'd need suitable boot loader code for the mode (BIOS or UEFI) being used. That is, if you're in BIOS mode, a boot loader can't just load an .efi file and execute it directly, since the .efi file is a 32- or 64-bit EFI executable; and if you're in UEFI mode, a boot loader can't run a standard BIOS MBR or PBR boot loader, since those are in 16-bit mode. You could do this by switching modes (BIOS vs. UEFI), of course, but that will have implications at the OS level. Windows 7, for instance, ties its partition table requirements for the boot disk to the firmware type.

---

### Post by Avidanborisov on 2011-07-01
> I'm skeptical of this claim. If you installed Windows first, then Ubuntu 11.04 has the terrible habit of creating a new filesystem on the ESP, so if you didn't check the partition's status between installing Windows and Ubuntu, you'd find that it would have a FAT16 ESP, despite the fact that Windows created it as a FAT32 partition.

I've done several Windows 7 installations. They've all created FAT32 ESPs, and every time I've tried installing Windows 7 to a system with an existing FAT16 ESP, the Windows installer has refused to accept it, which has ultimately derailed the installation. I've seen similar reports from others. I'm told that Windows Vista is more forgiving on this score, but I don't have a 64-bit version of that OS with which to test.


Maybe that is something unique in Windows 7 Enterprise, because I formatted the disk many times and I checked before I installed ubuntu and the filesystem of the ESP was always FAT16, and till now Windows boots fine in FAT16.

> Not quite; see my response above.

The BIOS compatibility mode in current x86 and x86-64 UEFI firmware is a handy stopgap; it helps with legacy OSes with no or poor UEFI support. It makes it easy for users to lose sight of what's happening, though. When BIOS compatibility mode is active, the computer acts just like a BIOS-based computer, and it boots via the MBR (and perhaps PBRs); and when BIOS compatibility mode is *not* active, the computer acts like a UEFI-based computer and boots via .efi files in the ESP. It's sort of like a dual-boot on the firmware level -- you choose which firmware to use (BIOS or UEFI), not just which OS to use. Although you *could* write a boot loader that merges the two in one way or another, I can't think of an advantage to doing so. Note that just redirecting the boot process isn't enough -- you'd need suitable boot loader code for the mode (BIOS or UEFI) being used. That is, if you're in BIOS mode, a boot loader can't just load an .efi file and execute it directly, since the .efi file is a 32- or 64-bit EFI executable; and if you're in UEFI mode, a boot loader can't run a standard BIOS MBR or PBR boot loader, since those are in 16-bit mode. You could do this by switching modes (BIOS vs. UEFI), of course, but that will have implications at the OS level. Windows 7, for instance, ties its partition table requirements for the boot disk to the firmware type.


I also mentioned that BIOS compatibility mode never worked for me in installations of Windows & Ubuntu, so I support what you say, but in theory, or at least the UEFI specification says that BIOS compatibility can be done.

---

### Post by srs5694 on 2011-07-01
> **Avidanborisov said:**
> Maybe that is something unique in Windows 7 Enterprise, because I formatted the disk many times and I checked before I installed ubuntu and the filesystem of the ESP was always FAT16, and till now Windows boots fine in FAT16.

It's certainly possible that it varies from one variety of Windows to another. It's also conceivable that the installer just has problems with certain sub-types of FAT16. I ran into problems with FAT16 partitions created with Linux's mkdosfs, but maybe a FAT16 partition created using a Windows tool would work better. It might even vary with the UEFI implementation, although the UEFI itself had no problems with the FAT16 ESPs that gave Windows fits in my tests. Note also that this is a problem with the Windows 7 *installer*. Once installed, you can change the ESP from FAT32 to FAT16 or vice-versa and it'll be fine.

> I also mentioned that BIOS compatibility mode never worked for me in installations of Windows & Ubuntu, so I support what you say, but in theory, or at least the UEFI specification says that BIOS compatibility can be done.

I'm not saying that a UEFI's BIOS compatibility mode is useless or doesn't work; my point is that a computer booted using that mode acts just like a BIOS computer, not like a UEFI computer. Although at least some boot loaders can switch from UEFI mode to BIOS mode (rEFIt does it on Macs), for the most part the two modes should be considered entirely separate. In particular, there's nothing to be gained from putting EFI boot code in an MBR or PBR; and if you switch to BIOS mode and use regular BIOS-style MBR or PBR code, your computer will boot just like a BIOS computer, with all the limitations that entails (like Windows requiring MBR partitions rather than GPT).

---

### Post by YesWeCan on 2011-07-01
Thanks Avidanborisov & srs5694 for you informative replies.

I guess I thought the new mobo firmware would be highly flexible so you could boot a MBR, boot a PBR or boot a .efi file on a per partition/disk basis as you wished. It sounds a little more like the old and new systems are not integrated.

I am interested in the nature of the .efi files. I wonder whether there is an online programmer's guide?

[sigh]UEFI is written in C?  You must be kidding. Gawd, why bother? C is such an old-fashioned, miserable excuse for a programming language. [/sigh] :|

---

### Post by srs5694 on 2011-07-02
> **YesWeCan said:**
> I guess I thought the new mobo firmware would be highly flexible so you could boot a MBR, boot a PBR or boot a .efi file on a per partition/disk basis as you wished. It sounds a little more like the old and new systems are not integrated.

I'm not sure how easy it is to switch modes on UEFI-based PCs. On Macs, it can be done in rEFIt; however, once you've chosen the path, you can't pick and choose which aspects of UEFI and which aspects of BIOS you want to use. The OS will see the computer as one or the other, not a mish-mash of both, both during the boot process and once booted.

> I am interested in the nature of the .efi files. I wonder whether there is an online programmer's guide?

See [http://www.uefi.org/home/](http://www.uefi.org/home/). There's lots of documentation there.

> [sigh]UEFI is written in C?  You must be kidding. Gawd, why bother? C is such an old-fashioned, miserable excuse for a programming language. [/sigh] :|

You are full of opinions, aren't you? Are you aware that Linux, and most major Linux programs, are written in C? I can understand and respect if you personally don't like C, but please realize that's a *personal opinion*. Not everybody shares it.

---


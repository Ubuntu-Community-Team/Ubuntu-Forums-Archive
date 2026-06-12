---
title: "Lubunto 5.4.0.97 upgrade crashe with EFI error"
date: 2022-01-31
forum: Installation &amp; Upgrades
---

### Post by jet-bundle on 2022-01-31
I have a Dell XPS 13 which has been running Lubuntu 20.04 since the summer of 2020; I use REFInd instead of GRUB. Recently I've been using 5.4.0.96.,

I've just upgraded to 5.4.0.97, and upon rebooting I get the following error:

```
EFI stub: ERROR: failed to read file
Trying to load files to higher address
EFI stub: ERROR: failed to read file
```

Rebooting 5.4.0.97 with minimal options gives the same error. I can, though, boot into 5.4.0.96 without any problem.

I'd be grateful for any advice on resolving this.

---

### Post by oldfred on 2022-01-31
I use rEFInd for emergency boot and it has worked well for that.

Boot-Repair will probably offer to reinstall grub. Do not run any automatic fix.
But report may help debug issue.

Please copy & paste the pastebin link to the Bootinfo summary report ( do not post report), do not run the auto fix till reviewed.Lets see details, use ppa version with your USB installer (2nd option) or any working install,  not Boot-Repair ISO
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by jet-bundle on 2022-02-01
Thanks.
[https://paste.ubuntu.com/p/WfmV98ZKVm/](https://paste.ubuntu.com/p/WfmV98ZKVm/)

---

### Post by oldfred on 2022-02-01
You are showing UEFI Secure Boot enabled.
I did not think rEFInd worked with secure boot on.

If you updated UEFI (or Windows did or fwupd did) then that may have reset some UEFI settings to defaults.
Check all the UEFI settings you had to change to install Ubuntu.

Line 237 shows disabled.
Was that your Ubuntu boot entry?

You are showing 7 kernels?
System normally keeps only two (or three before third is deleted).
Are you not updating & deleting?

---

### Post by jet-bundle on 2022-02-01
> You are showing UEFI Secure Boot enabled.
I did not think rEFInd worked with secure boot on.

In fact secure boot isn't enabled, despite the report. I disabled it when replacing Ubuntu with Lubuntu (see below). At present the setup screen (F2) shows "Secure Boot > Secure Boot Enable", and when I do boot there's a message "Booting in insecure mode" before entering rEFInd. 

> If you updated UEFI (or Windows did or fwupd did) then that may have reset some UEFI settings to defaults.
Check all the UEFI settings you had to change to install Ubuntu.

Line 237 shows disabled.
Was that your Ubuntu boot entry?

I purchased the machine from Dell with Ubuntu 16.04 preinstalled. I replaced that with Lubuntu 16.04, disabling secure boot at that stage. I upgraded to Lubuntu 18.04 when it became available. I installed 20.04 alongside 18.04 when it became available, and I've attached my notes from that procedure.

> You are showing 7 kernels?
System normally keeps only two (or three before third is deleted).
Are you not updating & deleting?

I let the system updater (Apply Full Upgrade) handle deleting old versions. I don't know why it has kept so many.

I hope that helps.

---

### Post by oldfred on 2022-02-01
The new install should have overwritten this in your ESP with the partition UUID of the new install, but still has UUID of old install.

```
=================== nvme0n1p1/efi/ubuntu/grub.cfg (filtered) ===================

search.fs_uuid 16effec9-5de0-4d55-bbae-9103d8b5ae7f root 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg
```

Ubuntu & rEFInd entry in UEFI use partUUID or GUID to know which ESP to boot from.
Or your nvme0n1p1.
Then in nvme0n1p1 grub/ubuntu uses the grub.cfg to find the install with the rest of grub and uses a configfile type entry to load the full grub in your install. With multiple installs you can only boot one Ubuntu, but then grub menu should let you boot all other installs. You want your preferred install to be the one in the ESP's grub.cfg. You can update by booting into your newer install and reinstalling grub. Or manually edit the grub with the different UUID & partition info.

Have not checked rEFInd lately and not sure which boot stanza it is loading.

Since SSD I suggest adding noatime to mount of partitions in fstab.
This is my entry, I do not have a /home to show, but similar in changing to noatime.
```
[FONT=monospace][COLOR=#000000]# / was on /dev/nvme0n1p3 during installation [/COLOR]
UUID=54029c4f-0cbe-413e-80ce-78a4995b0551 /               ext4    noatime,errors=remount-ro 0       1
[/FONT]
```

---

### Post by jet-bundle on 2022-02-01
I haven't made any changes yet, but thought that the following might be worth mentioning.

If I use rEFInd to boot into GRUB, rather than into one of the Lubuntu installations, I see that the GRUB list of options doesn't include the new 5.4.0.97 at all; the default is 5.4.0.96, whereas the rEFInd default is 5.4.0.97 and this crashes. In fact the reason for installing rEFInd was to match the setup on another machine, and I could happily live without it. If I uninstalled it and used GRUB instead, presumably the next automatic upgrade would be to 5.4.0.98?

---

### Post by oldfred on 2022-02-01
I do not understand why grub would not show .97.
With every kernel update, it should run several processes including an update to grub menu.
If you have an issue/typo in either /etc/default/grub or in grub's scripts it creates a grub.cfg.new not a new grub.cfg, so one used to boot is not updated.
What does this show?
sudo update-grub

---

### Post by jet-bundle on 2022-02-01
```
$ sudo update-grub
[sudo] password for david: 
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.4.0-97-generic
Found initrd image: /boot/initrd.img-5.4.0-97-generic
Found linux image: /boot/vmlinuz-5.4.0-96-generic
Found initrd image: /boot/initrd.img-5.4.0-96-generic
Found linux image: /boot/vmlinuz-5.4.0-94-generic
Found initrd image: /boot/initrd.img-5.4.0-94-generic
Found linux image: /boot/vmlinuz-5.4.0-92-generic
Found initrd image: /boot/initrd.img-5.4.0-92-generic
Found linux image: /boot/vmlinuz-5.4.0-91-generic
Found initrd image: /boot/initrd.img-5.4.0-91-generic
Found linux image: /boot/vmlinuz-5.4.0-90-generic
Found initrd image: /boot/initrd.img-5.4.0-90-generic
Found Ubuntu 18.04.6 LTS (18.04) on /dev/nvme0n1p3
Adding boot menu entry for UEFI Firmware Settings
done
```

But there's still no option for 5.4.0.97 on the GRUB menu.

---

### Post by oldfred on 2022-02-01
First line is .97?
So does it not show when booting?

What does this show
sudo apt-get autoremove --purge

Or:
sudo apt-get  autoclean

I run several commands & know some are duplicate but differnt names as part of my houseclean script.

---

### Post by jet-bundle on 2022-02-01
```
~$ sudo apt-get autoremove --purge
[sudo] password for david: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  gir1.2-handy-0.0* gnome-shell-extension-prefs* libetonyek-0.1-1*
  libhandy-0.0-0* libjuh-java* libjurt-java* libllvm11* libmspub-0.1-1*
  libmwaw-0.3-3* liborcus-0.15-0* libreoffice-style-tango* libridl-java*
  libunoil-java* libwps-0.4-4* linux-headers-5.4.0-90*
  linux-headers-5.4.0-90-generic* linux-headers-5.4.0-91*
  linux-headers-5.4.0-91-generic* linux-headers-5.4.0-92*
  linux-headers-5.4.0-92-generic* linux-headers-5.4.0-94*
  linux-headers-5.4.0-94-generic* linux-image-5.4.0-90-generic*
  linux-image-5.4.0-91-generic* linux-image-5.4.0-92-generic*
  linux-image-5.4.0-94-generic* linux-modules-5.4.0-90-generic*
  linux-modules-5.4.0-91-generic* linux-modules-5.4.0-92-generic*
  linux-modules-5.4.0-94-generic* linux-modules-extra-5.4.0-90-generic*
  linux-modules-extra-5.4.0-91-generic*
  linux-modules-extra-5.4.0-92-generic*
  linux-modules-extra-5.4.0-94-generic* shim*
0 to upgrade, 0 to newly install, 35 to remove and 6 not to upgrade.
After this operation, 1,615 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 867632 files and directories currently installed.)
Removing gir1.2-handy-0.0:amd64 (0.0.13-1) ...
Removing gnome-shell-extension-prefs (3.36.9-0ubuntu0.20.04.2) ...
Removing libetonyek-0.1-1:amd64 (0.1.9-3) ...
Removing libhandy-0.0-0:amd64 (0.0.13-1) ...
Removing libjuh-java (1:7.2.5~rc2-0ubuntu0.20.04.1~lo1) ...
Removing libjurt-java (1:7.2.5~rc2-0ubuntu0.20.04.1~lo1) ...
Removing libllvm11:amd64 (1:11.0.0-2~ubuntu20.04.1) ...
Removing libmspub-0.1-1:amd64 (0.1.4-1build3) ...
Removing libmwaw-0.3-3:amd64 (0.3.15-2build1) ...
Removing liborcus-0.15-0:amd64 (0.15.3-3build2) ...
Removing libreoffice-style-tango (1:7.2.5~rc2-0ubuntu0.20.04.1~lo1) ...
Removing libridl-java (1:7.2.5~rc2-0ubuntu0.20.04.1~lo1) ...
Removing libunoil-java (1:7.2.5~rc2-0ubuntu0.20.04.1~lo1) ...
Removing libwps-0.4-4:amd64 (0.4.10-1build1) ...
Removing linux-headers-5.4.0-90-generic (5.4.0-90.101) ...
Removing linux-headers-5.4.0-90 (5.4.0-90.101) ...
Removing linux-headers-5.4.0-91-generic (5.4.0-91.102) ...
Removing linux-headers-5.4.0-91 (5.4.0-91.102) ...
Removing linux-headers-5.4.0-92-generic (5.4.0-92.103) ...
Removing linux-headers-5.4.0-92 (5.4.0-92.103) ...
Removing linux-headers-5.4.0-94-generic (5.4.0-94.106) ...
Removing linux-headers-5.4.0-94 (5.4.0-94.106) ...
Removing linux-modules-extra-5.4.0-90-generic (5.4.0-90.101) ...
Removing linux-image-5.4.0-90-generic (5.4.0-90.101) ...
/etc/kernel/postrm.d/initramfs-tools:
update-initramfs: Deleting /boot/initrd.img-5.4.0-90-generic
/etc/kernel/postrm.d/zz-update-grub:
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.4.0-97-generic
Found initrd image: /boot/initrd.img-5.4.0-97-generic
Found linux image: /boot/vmlinuz-5.4.0-96-generic
Found initrd image: /boot/initrd.img-5.4.0-96-generic
Found linux image: /boot/vmlinuz-5.4.0-94-generic
Found initrd image: /boot/initrd.img-5.4.0-94-generic
Found linux image: /boot/vmlinuz-5.4.0-92-generic
Found initrd image: /boot/initrd.img-5.4.0-92-generic
Found linux image: /boot/vmlinuz-5.4.0-91-generic
Found initrd image: /boot/initrd.img-5.4.0-91-generic
Found Ubuntu 18.04.6 LTS (18.04) on /dev/nvme0n1p3
Adding boot menu entry for UEFI Firmware Settings
done
Removing linux-modules-extra-5.4.0-91-generic (5.4.0-91.102) ...
Removing linux-image-5.4.0-91-generic (5.4.0-91.102) ...
/etc/kernel/postrm.d/initramfs-tools:
update-initramfs: Deleting /boot/initrd.img-5.4.0-91-generic
/etc/kernel/postrm.d/zz-update-grub:
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.4.0-97-generic
Found initrd image: /boot/initrd.img-5.4.0-97-generic
Found linux image: /boot/vmlinuz-5.4.0-96-generic
Found initrd image: /boot/initrd.img-5.4.0-96-generic
Found linux image: /boot/vmlinuz-5.4.0-94-generic
Found initrd image: /boot/initrd.img-5.4.0-94-generic
Found linux image: /boot/vmlinuz-5.4.0-92-generic
Found initrd image: /boot/initrd.img-5.4.0-92-generic
File descriptor 10 (/var/lib/dpkg/triggers/linux-update-5.4.0-90-generic (deleted)) leaked on lvs invocation. Parent PID 10366: /bin/sh
Found Ubuntu 18.04.6 LTS (18.04) on /dev/nvme0n1p3
Adding boot menu entry for UEFI Firmware Settings
done
Removing linux-modules-extra-5.4.0-92-generic (5.4.0-92.103) ...
Removing linux-image-5.4.0-92-generic (5.4.0-92.103) ...
/etc/kernel/postrm.d/initramfs-tools:
update-initramfs: Deleting /boot/initrd.img-5.4.0-92-generic
/etc/kernel/postrm.d/zz-update-grub:
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.4.0-97-generic
Found initrd image: /boot/initrd.img-5.4.0-97-generic
Found linux image: /boot/vmlinuz-5.4.0-96-generic
Found initrd image: /boot/initrd.img-5.4.0-96-generic
Found linux image: /boot/vmlinuz-5.4.0-94-generic
Found initrd image: /boot/initrd.img-5.4.0-94-generic
File descriptor 10 (/var/lib/dpkg/triggers/linux-update-5.4.0-91-generic (deleted)) leaked on lvs invocation. Parent PID 13210: /bin/sh
Found Ubuntu 18.04.6 LTS (18.04) on /dev/nvme0n1p3
Adding boot menu entry for UEFI Firmware Settings
done
Removing linux-modules-extra-5.4.0-94-generic (5.4.0-94.106) ...
Removing linux-image-5.4.0-94-generic (5.4.0-94.106) ...
/etc/kernel/postrm.d/initramfs-tools:
update-initramfs: Deleting /boot/initrd.img-5.4.0-94-generic
/etc/kernel/postrm.d/zz-update-grub:
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.4.0-97-generic
Found initrd image: /boot/initrd.img-5.4.0-97-generic
Found linux image: /boot/vmlinuz-5.4.0-96-generic
Found initrd image: /boot/initrd.img-5.4.0-96-generic
File descriptor 10 (/var/lib/dpkg/triggers/linux-update-5.4.0-92-generic (deleted)) leaked on lvs invocation. Parent PID 15913: /bin/sh
Found Ubuntu 18.04.6 LTS (18.04) on /dev/nvme0n1p3
Adding boot menu entry for UEFI Firmware Settings
done
Removing linux-modules-5.4.0-90-generic (5.4.0-90.101) ...
Removing linux-modules-5.4.0-91-generic (5.4.0-91.102) ...
Removing linux-modules-5.4.0-92-generic (5.4.0-92.103) ...
Removing linux-modules-5.4.0-94-generic (5.4.0-94.106) ...
Removing shim (15.4-0ubuntu9) ...
Processing triggers for mime-support (3.64ubuntu1) ...
Processing triggers for gnome-menus (3.36.0-1ubuntu1) ...
Processing triggers for libc-bin (2.31-0ubuntu9.3) ...
Processing triggers for desktop-file-utils (0.24-1ubuntu3) ...
(Reading database ... 721866 files and directories currently installed.)
Purging configuration files for linux-modules-extra-5.4.0-94-generic (5.4.0-94.106) ...
Purging configuration files for linux-modules-5.4.0-90-generic (5.4.0-90.101) ...
dpkg: warning: while removing linux-modules-5.4.0-90-generic, directory '/lib/modules/5.4.0-90-generic' not empty so not removed
Purging configuration files for linux-modules-extra-5.4.0-90-generic (5.4.0-90.101) ...
Purging configuration files for linux-image-5.4.0-92-generic (5.4.0-92.103) ...
Purging configuration files for linux-modules-5.4.0-92-generic (5.4.0-92.103) ...
Purging configuration files for libreoffice-style-tango (1:7.2.5~rc2-0ubuntu0.20.04.1~lo1) ...
Purging configuration files for linux-image-5.4.0-90-generic (5.4.0-90.101) ...
Purging configuration files for linux-modules-extra-5.4.0-91-generic (5.4.0-91.102) ...
Purging configuration files for linux-modules-extra-5.4.0-92-generic (5.4.0-92.103) ...
Purging configuration files for linux-image-5.4.0-91-generic (5.4.0-91.102) ...
Purging configuration files for linux-image-5.4.0-94-generic (5.4.0-94.106) ...
Purging configuration files for linux-modules-5.4.0-91-generic (5.4.0-91.102) ...
Purging configuration files for linux-modules-5.4.0-94-generic (5.4.0-94.106) ...

```

Some further information. I'm accessing GRUB from rEFInd, and when I do this the list of options hasn't changed. So, for example, I could select 5.4.0.91; but then this version wouldn't be found. On the other hand, if I look using GRUB customizer, I can see 5.6.0.97 and 5.4.0.96, as would be expected. But I can't get to that copy of GRUB from rEFInd.

---

### Post by oldfred on 2022-02-01
Looks like you housecleaned a lot of old kernels.

I thought rEFInd automatically found new kernels. But really only have used it for emergency boot.

Does direct boot of Ubuntu from UEFI boot menu work correctly?

Grub-Customizer replaces all of grub with proxy files, and that may confuse rEFInd.

---

### Post by jet-bundle on 2022-02-02
According to the F2 screen, there are two versions of rEFInd in the boot sequence, one linked to EFI/refind/shimx.efi and the other to EFI/refind/grubx.efi . But I can't see any difference in the effect. There's also an option in the boot sequence to boot into Ubuntu, and if I move that to the top I get the rEFInd version of GRUB (with the old kernel versions still there). But rEFInd itself no longer lists the old versions.

So the situation at present is this. If I boot into rEFInd, I can choose 20.04 or GRUB (or 18.04). The default for 20.04 is 5.4.0.97, and that crashes; but by tabbing I can boot to 5.4.0.96. If I choose GRUB instead, the default for 20.04 is 5.4.0.96, but the older versions also appear in the list (but don't work because they've been purged).

Well, I can live with that for the time being; but I'd like to use 5.4.0.97 in order to keep up-to-date (with or without rEFInd).

An oddity this morning is that the "Updates are available" popup appeared, so I opted to do this; but after updating the cache I was given an "error-repo-download-failed" message with advice to check my internet connection (which is working) -- see attached screen grab. Forcing a full upgrade gives the same result. Curiously, I have a similar problem on an old machine with a complicated multiboot setup, again using rEFInd, and in that case the modules for 5.4.0.97 failed to download at all. (Though two other machines, both using GRUB directly, have upgraded to 5.4.0.97 without any problem.)

---

### Post by oldfred on 2022-02-02
I use a local repository.

Issue may then be with repository?
If .97 crashes is it correctly installed? 
Do you have nVidia or other proprietary drivers that have to be included 

I found this in my notes:
"If the &#8220;apt-get upgrade&#8221; does not successfully complete then a flag is set and update-initramfs does not get to run, hence grub gets all messed up. You should be able to boot using the old kernel and then run the sudo update-initramfs &#8211;u -k command. Then run sudo dpkg &#8211;reconfigure. That should clear the upgrade flags and fix any broken packages."

---

### Post by jet-bundle on 2022-02-02
Problem solved.

I used sudo update-initramfs &#8211;u (adding -k gave an error, as did sudo dpkg &#8211;reconfigure). Then in rEFInd, selecting the default for 20.04 booted 5.4.0.07 successfully. I'll mark the thread as solved; thanks for your help.

(I still have the update problem, but I'll see how that goes over the next few days.)

---


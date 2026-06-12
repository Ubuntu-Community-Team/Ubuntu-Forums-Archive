---
title: "Fail to Boot (not even GRUB) after changing NVIDIA Driver."
date: 2019-08-05
forum: Installation &amp; Upgrades
---

### Post by philglau on 2019-08-05
16.04 LTS

I had a working system with nVidia 384.x driver.

In my infinite wisdom, under proprietary drivers, I saw the 430 was available and applied it.

Upon reboot I get:
[LIST]
[*]Bios Screen (X99 board)
[*]the Purplish Ubuntu color for a moment (full screen).
[*]No grub menu! Even when holding shift and/or escape.
[*]Rather than a grub menu or booting to the desktop, I see instead some boot log text on screen for a bit. (see attached image)
[*]Then it goes to completely black screen with single blinking underscore in upper right corner.
[/LIST]

Ctrl-alt-F1 does not drop me into CLI. Just sits frozen on the blinking underscore until power off.

I can boot to a 16.04 USB flash drive.  I ran boot-repair and got [this report]("https://paste.ubuntu.com/p/mfyf5H7V3M/") (boot repair report to paste.ubuntu) "sdb" is the drive that is no longer mounting.

My gut instinct is that I need to 'undo' the move to the current NVIDIA 430 driver and revert back to the working 384. But I don't know how to do this and I can't seem to get the grub menu to appear to allow me to boot into a recovery mode. Seems like most of the 'revert NVIDIA driver posts' assume that one can boot to the machine to begin with. 

There are 3 cards in the system: a GT-730 and two GTX-1070s. Normally I use the GT-730 to drive the monitors and the 1070s for CUDA work. 

Any help would be appreciated. Thank you in advance for your time.

- Phil

---

### Post by oldfred on 2019-08-06
I was concerned that your GT730 may not work with newer driver required for 1070's. My GT620 is now frozen at the 390.xxx series of drivers.
But this shows 430.xx should be good.
       Updated driver search by nVidia model, do not download, just check correct driver version
[http://www.geforce.com/drivers](http://www.geforce.com/drivers)

Do not know LVM, is it also encrypted?
You show sda as gpt but sdb as dos/MBR.
Boot-Repair likes to install grub to MBR of every drive in BIOS mode, but gpt drives need a bios_grub partition for grub to correctly install. It should reinstall ok to sdb only, using Boot-Repairs advanced mode. Make sure LVM is mounted, Boot-Repair may not auto mount it as it needs to see inside the LVM for fstab and make sure /boot is mounted, but it normally finds that in fstab & mounts it.

You have newer UEFI system, but installed on sdb in old BIOS/MBR configuration. You need to reboot Ubuntu live system in BIOS mode & add Boot-Repair to that.

---

### Post by CatKiller on 2019-08-06
> **philglau said:**
> 
My gut instinct is that I need to 'undo' the move to the current NVIDIA 430 driver and revert back to the working 384. But I don't know how to do this and I can't seem to get the grub menu to appear to allow me to boot into a recovery mode. Seems like most of the 'revert NVIDIA driver posts' assume that one can boot to the machine to begin with. 

Since you can boot a live image, you can mount your installed drive and then chroot into it. That will allow you to run commands as if you'd booted into your installation, but using the live environment as a support framework. You'd be able to run your commands there.

There have been issues of version mismatches for the compiler for the driver and the compiler used by the older LTS releases. I suspect that's exactly what you'll find if you comb through the logs: a version or option mismatch for the nvidia kernel module. It's come up a few times for both 14.04 and 16.04 already. The PPA team is small and don't seem to take as much care with packaging and testing as they could. I'd imagine that situation will improve once the newer drivers are available through the main repositories, which is planned to happen in the future.

---

### Post by philglau on 2019-08-07
First of all, thank you for your earlier response. I appreciate it.

I should have also indicated that I have very little Ubuntu admin experience. (I did check that 430 covers all my cards prior to attempting the 'upgrade')

I do know that my installed disk is LVM unencrypted.

> [COLOR=#000000]Since you can boot a live image, you can mount your installed drive and then chroot into it. That will allow you to run commands as if you'd booted into your installation, but using the live environment as a support framework. You'd be able to run your commands there.[/COLOR]

Regarding this option I've done:

[LIST=1]
[*]sudo vgscan
[LIST=1]
[*]which found volume group "ubuntu-vg" using metadata type lvm2
[/LIST]

[*][COLOR=#212529][FONT=Inconsolata]sudo vgchange -ay[/FONT][/COLOR]
[*]sudo lvdisplay and found my logical volume which in my case is called 'ubuntu-vg'
[LIST=1]
[*]ls -l /dev/ubuntu-vg shows 'root' and 'swap_1'
[/LIST]

[*]sudo mkdir /mnt/my_test
[*]sudo mount /dev/ubuntu-vg/root /mnt/my_test/root
[LIST=1]
[*]if I go into 'my_test/root' I can see all the normal structure of the drive I'm trying to boot, including my home directory
[/LIST]

[*]sudo chroot /mnt/my_test/root
[/LIST]

It drops me into "root@ubuntu:/#" (where there is no syntax highlighting or colored directory information) and 'exit' takes me back to the live Ubuntu CLI (which does have colored directory/syntax coloring)

However I'm at a loss as to what commands I should run in the chrooted environment to help resolve this problem or which logs to look at to look for signs of the ultimate problem. 

While there may be concomitant or coincidental issues, I still really believe it has mostly to do with the move to 430 since that was the only thing I did prior to reboot. What commands should I execute to either roll back to the 384 or simply use whatever native support Ubuntu provides for graphics cards so I can just get it back up and running.

I'm tempted to follow these [purge instructions]("https://ubuntuforums.org/showthread.php?t=2363945") but substitute [COLOR=#000000]*nvidia-384 *[/COLOR]
for where it indicates [COLOR=#000000][I]nvidia-375

[/I][/COLOR]If you have a moment, please let me know you thoughts on what commands I should be running in the chrooted environment to help roll back this cluster-f.

---

### Post by philglau on 2019-08-07
So just a follow up in case somebody else runs into this:

From the USB Ubuntu Install 'disk' I booted the machine and did the try without install option to get to a working desktop.

From the side bar I could see disk icons listed. Hovering over them I found my problem drive. Clicking it opened a GUI window showing me the drive contents allowing me to confirm it was the one I wanted.

This mounts it in "/media/ubuntu/5e23423...234j9-dsf-sdf" where the "5e23" is some sort of Drive ID

As suggested above I did:

```
sudo chroot 5e23423...234j9
```

which dropped me into a root terminal:

```
root@ubuntu:/#
```

I then did

```
sudo apt purge nvidia*
```

This gave an error: "sudo: unable to resolve host ubuntu: Connection refused" but also listed a bunch of nvidia stuff 

```
 The following package will be REMOVED:
    libcuda1-430* nvidia-430* nvicida-opencl-icd-430* nvidia-prime* nvidia-settings*
    5 files to remove and 2 not upgraded
    507 MB will be freed.
```

I selected '[Y]es' and it proceeded but then also gave the following error:

```
Error encountered while processing:
    nvidia-430
sh: 1: cannot create /dv/null: Permission denied
E: sub-process /usr/bin/dpkg returned an error code (1)
```

I rebooted anyways and it then allowed me to get the drive I wanted to boot (SUCCESS!), but with only one screen working.

From terminal on the now booting machine I again ran:
```
sudo apt purge nvidia*
```
And this time it seemed to have purged all the nvidia-430 stuff.

I attempted to reinstall using 

[LIST=1]
[*]sudo add-apt-repository ppa:graphics-drivers/ppa and then sudo apt-get update.
[*]Run sudo apt-get install nvidia-430
[*]reboot
[/LIST]

But this resulted in me being back to where I began. Something about -430 that my computer does not like. Anycase I redid all the steps listed above again, except the 'install nvidia-430'

Instead, I used "Software & Updates" from system settings and select "nvidia 384" from Additional Drivers. The Additional Drivers shows 384, 410, 415, 418 and 430.  The 384.130 version is listed as (proprietary) whereas the other as listed as (open source).

After 'applying' 384 and rebooting, my machine seems to be back to normal. Not sure what to make of the fact that 430 doesn't seem to work on my machine. (X99 board, i7-5930 @ 3.5GHz, 32GB RAM, one GT-730 and two GTX-1070s)

At this point, I'm not going to mess around with trying 410 to 418.

---


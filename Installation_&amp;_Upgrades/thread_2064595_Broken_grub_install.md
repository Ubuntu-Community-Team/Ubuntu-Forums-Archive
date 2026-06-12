---
title: "Broken grub install"
date: 2012-09-29
forum: Installation &amp; Upgrades
---

### Post by tarkawebfoot on 2012-09-29
It all started when I decided to try to install LVM2 on my Acer AO722 netbook. I have 12.04 Lubuntu installed on an OCZ Vertex 4 128G SSD, and it was working well enough up to this point.

I found to use LVM I needed grub installed on a non-LVM partition. So I used Gparted to shrink the existing partition and create a 500M partition, and the remainder of the space went to what will become an LVM partition.

I then used boot-repair to migrate grub to the new partition. I rebooted and found the grub install was broken.

I've spent the last week learning how grub works and have managed to get my system booting again (using the chroot method). Now, while the system boots into LXDE, the trackpad doesn't work even after using Fn-F7, and I can't go to a terminal. When I do Ctrl-Alt-F2, the screen starts behaving like the video driver is broken. I can switch back to F7 most of the time, but I see the background flickering, or the spaces divided at the wrong place and the trackpad still doesn't work.

After doing the grub-install and update-grub from the chroot, grub loads, but it boots into the menu. Selecting normal boot leads to the problems described above.

The Lubuntu live stick still boots normally, but doing the grub install from the live CD makes no changes to my HD, and usually hoses the usb stick. Thus I went the chroot method.

Here is my boot info from BR:

paste.ubuntu.com/1250311

How can I get grub working as well as it did when I installed the fresh system without reinstalling?

Thanx all in advance...

Brian D Myers

---

### Post by darkod on 2012-09-29
You never needed to do any of that, those instructions were old. These days LVM can work without the separate /boot partition. It can be inside the LVM.

I think the file /extlinux/extlinux.conf is messing it up for you. Otherwise the rest looks good.

Boot into live mode, open /dev/sda4 and move that file from there (you can move it inside your home folder or external usb for example, just in case you need it).

Restart and see if that helped. You might still need to reinstall grub2 after this, depending if it also got messed up, but the extlinux shouldn't be there I think.

PS. Looking at this more carefully, it seems the LVM is messed up. On some places it does show as LVM but on others not. For example, the parted listing doesn't show sda3 with lvm flag, and I trust parted a lot.
On another note, what do you have on the LVM because both /boot and / are outside (it's sda4 and sda1). So is there anything important in the LVM?

---

### Post by tarkawebfoot on 2012-09-29
Thanks for the reply darkod.

I moved the extlinux directory out of the /boot and into my home directory and did update-grub again. No change unfortunately. All problems still persist.

Do I need to do another grub-install?

About the LVM volume, there's nothing on it right now. I created that in order to copy my existing installation to it, allowing me to reformat the partition it resides on now.

I did find that I didn't need to do that while Googling for a solution to the boot problem. Oh well.

Anyway, I know I could just reinstall and be done with it, but I'm really doing this to practice for an attempt to rescue my primary Linux server. That has a serious problem with vanishing disk space, and I'd like to put LVM under it in case it happens again.

So I thought I'd try doing this on my netbook first. Guess that's what I get for thinking.

Brian

---

### Post by tarkawebfoot on 2012-10-01
Update...

So I thought, OK, since I don't need to have a non LVM boot partition any more, why don't I just install a fresh Lubuntu onto the LVM partition and see if I can boot that.

So I set up a logical volume on the sda3 partition and installed from the live usb to that partition. I checked that files were there after the install (before rebooting) and chroot'ed and installed LVM2.

Then I rebooted. No change. It's not booting from the new partition at all. It's still doing what it did before.

I ran parted and set the partition type of sda3 (which shows up normally now) to 8e and made sure it was bootable. It now lists as the boot partition and its system is 'Linux LVM'. The file system is still there as it should be. Never the less the system still tries to boot into the old setup.

Ahh, I think Darkod was correct about LVM being messed up. When I chroot into the install on sda3, there is no trace of the pvs, vgs, and lvs I created. Looks like the installer is not LVM aware, or wasn't able to detect it on my setup.

I was using instructions to install Ubuntu on an LVM partition, but I think those instructions were old. Is there any more up to date info?

Brian

---

### Post by darkod on 2012-10-01
Just use the Alternate Install CD (image) which has support for LVM and you are good to go. You can do everything in the installer, I prefer using the manual partitioning option since it gives you more control.

The grub2 bootloader should be installed correctly too.

Give it a shot, it's very easy.

---

### Post by tarkawebfoot on 2012-10-01
That appears to have worked. System now boots up in terminal mode.

I'll have to get X running again, but I should be able to figure that out.

It points out the last part of the process though: to move my install to LVM, I need to transfer my existing installation to the LVM volume. I need to find a way to transfer my existing installation to the new LVM. I suppose I should post a separate thread for that.

Either way, thanx Darkod, that at least fixed my broken grub install.

Brian

---


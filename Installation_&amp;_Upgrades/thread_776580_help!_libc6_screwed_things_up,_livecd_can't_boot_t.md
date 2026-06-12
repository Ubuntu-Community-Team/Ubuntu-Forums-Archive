---
title: "help! libc6 screwed things up, livecd can't boot to fix"
date: 2008-04-30
forum: Installation &amp; Upgrades
---

### Post by buckykat on 2008-04-30
okay, so the first part of this problem is that i was too impatient to wait for hardy about a month ago, so i installed the prerelease. soon afterwords, i got a really messed up version of libc6 from update-manager. that caused my entire ubuntu partition to fail(now unbootable). luckily i still have my windows partition. i googled the problem and found this:  [https://bugs.launchpad.net/ubuntu/+source/glibc/+bug/201673]("https://bugs.launchpad.net/ubuntu/+source/glibc/+bug/201673about") about how to recover from the bad update. i decided to wait and fix it when 8.04 final released. 

(zoom forward to now) i have a hardy final cd sitting here, the MD5 checked out, the test cd utility on the cd itself found no errors, but when i choose to boot the live cd, it shows the ubuntu startup screen with orange bar going back and forth for a few seconds, then dies. all power shuts off. when i try to boot windows after that, the windows xp bar-going-back-and-forth screen shows for a few seconds just like the ubuntu one, then dies like the ubuntu one. if i repeat this, on the third try it boots windows just fine(hence me being able to post this).
 
if i could get the livecd to work, i could follow the directions from launchpad(second part, first part would probably make it worse, as it happened soon after switching from 7.10.) help?

---

### Post by garyedwardjohnston on 2008-04-30
I hate debugging these things and would reinstall.

---

### Post by Rallg on 2008-04-30
Can you restore the Windows MBR from a Windows installer CD or DVD? Are you willing to trash existing files on your dysfunctional Ubuntu partition? If so, try this:

(1) Restore the Windows MBR (and if necessary the Windows bootloader) so that you can boot directly to Windows as if Linux does not exist. Do not proceed unless you can do this.

(2) Download and burn the "System Rescue CD" iso. It's a live Linux distro that's not intended to install, and (if necessary) can run in terminal mode if your video driver is incompatible. When it loads, it displays terminal text for awhile, then settles with a prompt. On many systems, typing "startx" (without the quotes) gets you a GUI. From there, you can launch GParted, and re-format you dysfunctional Ubuntu partition. That will leave you with a system that has function Windows and no Ubuntu.

The reason you must restore Windows' own boot is that when you install Ubuntu (or any Linux), you probably put the Grub bootloader on the Ubuntu partition, and changed the MBR so that it points to Grub. (When you load Windows via Grub, it points back to the Windows loader.) If you trash the Ubuntu partition without restoring the Windows MBR, you won't be able to boot Windows.

After using GParted, you can exit the System Rescue CD via its terminal, using
shutdown -r now
to reboot, or if necessary
sudo -s
shutdown -r now

(3) Finally, install Ubuntu anew.

I don't know whether or not System Rescue CD can grab documents from a Linux partition and move them to a safe place before re-formatting a partition.

It MIGHT be the case that if you cannot restore the Windows MBR, the new Ubuntu installation will conventiently straighten things out, since it can detect other operating systems on your hard drive. But I wouldn't rely on that unless I had no alternative.

---

### Post by buckykat on 2008-04-30
thanks for the advice, but i'd really rather keep the files i have on the ubuntu partition. also, the main question here is not, "how do i fix the libc6 fail?" that's covered in the launchpad page. the main question here is, "why doesn't the ubuntu livecd work, and how do i make it work?"

---


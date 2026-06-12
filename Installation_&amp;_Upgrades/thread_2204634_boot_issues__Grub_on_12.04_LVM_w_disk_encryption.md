---
title: "boot issues:  Grub? on 12.04 LVM w/ disk encryption"
date: 2014-02-09
forum: Installation &amp; Upgrades
---

### Post by fatmann66 on 2014-02-09
All, any help resolving this boot issue would be great!

my assumption is that there is an issue with grub, but i'm not really sure.

OS:
  Ubuntu 12.04 LTS 64bit running full disk encryption
Background:
I ran updates and a video driver update and rebooted.
system came up and prompted for crypto password and then booted to a blinking cursor.
I was still able to SSH to the box so I assumed that the video driver caused X to not load.  ran through  a tut. to remove video driver and reinstall X. then rebooted

at this point system wouldn't boot at all. monitor screen would display "unsupported video format" and would go into sleep mode.

I assumed that somehow grub was messed up and ran through a boot repair which provided this: [http://paste.ubuntu.com/6904979/](http://paste.ubuntu.com/6904979/)

not sure where to go from this point.
I get a grub menu on boot, but after picking an option I come to the same  blanks screen with "unsupported video format"

from a live-usb I am able to mount and unlock LVM partitions. all data and file structures seem are present. 

where to go from here?? I'm just not sure.
any suggestions?

thanks in advance,
Fatmann66

---

### Post by fatmann66 on 2014-02-09
update:

 within the grub menu I selected "older version"  picked the newest "old version" to boot. was prompted for my luks passcode and then was given a tty prompt. still no gui 
I guess this means grub is intacted and it may have been the last kernel update that caused the issue. any suggestions on where to go from here? tty prompt. still no gui

---

### Post by fatmann66 on 2014-02-09
update: from the old version  ran "startx" and received a unknown command error.  I must have uninstalled it as part of the video driver repair.
installed "Ubuntu-desktop"  once complete unity loaded up.

rebooted PC and booted into the newest version listed. saw a black screen from about 1 minute then was dropped done into a "initramfs" prompt.

not sure how to proceed from there?

---

### Post by fatmann66 on 2014-02-09
ok,
 when booting into the newest kernel  I see an alert: /dev/mapper/xxx doesn't exist.
when booting into the previous kernel the system boots fine.  I'm not sure it the update caused the above message or if that was caused by reinstalling grub?
either way the previous kernel is working fine. is there a way to remove the newest kernel and then reinstall it (hopefully resolving the issue and being up on the newest kernel?)
any ideas would help.
thanks,

---

### Post by Herman on 2014-02-09
A new /boot/initrd.img is installed with every new kernel. In an encrypted installation it has the job of decrypting the / file system so the kernel can mount it at at boot time.
If your initrd.img file is corrupted or incomplete or is failing to decrypt you / partition for some reason then that could be the cause of your error message: alert: /dev/mapper/xxx doesn't exist. (Because as far as the kernel is concerned, it doesn't exist, since it cannot read it to find the files in /etc/init, which it needs to continue booting).
It's relatively easy to make a new initrd.img with the mkinitramfs command, man mkinitramfs

If you want to use a GUI method you can probably use synaptic packager to uninstall the suspected faulty kernel and initrd.img. Just install synaptic if you don't already have it. Then open synaptic Package Manager and do a search for linux-image. You should be able to completely remove it as long as it's not the one you have booted at the moment and try installing it again.

---

### Post by fatmann66 on 2014-02-10
Herman, thanks for the reply. I'll take a look at what you suggested and see if maybe the initrd.img is causing the issue.  I'm currently booted on an older kernel so removing the one that was just installed might be the way to go. I'll look into it and give you an update once I try it.
thanks,

---

### Post by fatmann66 on 2014-02-13
I tried the above suggestion: in synaptic manager I removed Linux-image and Linux-header for kernel 3.5.45 and rebooted. the grub menu still had .45 has the primary boot kernel (do I have to run an update fro grub?)  selecting that open gives the same mapper error. 

I would have though after removing the kernel it would have shown back up when I scanned for updates, but this didn't happen either.  any suggestions where to go from here?

I'm still booting up on an old kernel at this point.
thanks,

---

### Post by fatmann66 on 2014-02-13
I was able to resolve the boot issue on the .45 kernel, although there is still some video card issues.  ultimately I used some of the commands from [this thread]("http://ubuntuforums.org/showthread.php?t=1632033"). 

First issuing a ```
cryptsetup luksOpen /dev/sda5 sda5_crypt 
```  Note: that sda5_crypt is the standard named when you uses the guided install from for full disk encryption on the 12.04 alt cd. you may have to change this depending on how you originally setup FDE.  

I confirmed that sda5_crypt was correct by looking at my etc/crypttab file.  As Herman pointed out the initrd.img file is kernel specific so I was able to boot using an old Kernel to confirm.

after issuing the lukOpen command you enter your password to decrypt the container
then mount the LVM partitions by issuing ```
lvm vgchange -a y
```
then ```
exit
``` to get out of initramfs prompt. you may have to confirm a normal boot message
the system should now finish booting. once logged in you have to repair initrd.img to do this do the following:

NOTE: I read a few post about the below command  on different sites and some people indicated that they had to change the UUID in the crypttab file. once they did the system still didn't boot and they went back and made more changes to the crypttab file to resolve the issue.  this seemed like  a waste of time. I know that my crypttab file was good because I could boot from an old kernel with out issue. I MADE NO CHANGES to by crypttab or fstab files

issue: [HTML]update-initramfs -k all -c[/HTML]
Hind sight: I probably would have  backed up the old initrd.img files or modified the above command to only update the .45 kernel. for me it didn't make a difference, but you never know.

I then rebooted and was able to boot  to the desktop (kind of)
it seems that  after post I loose video display. I know that the boot should hang (waiting for my decryption password) I typed this in blind and hit enter.  I heard the hard drive chatter so I knew it was finishing booting up. after  10sec or so the display came up and at the desktop login prompt.

---

### Post by Herman on 2014-02-13
Hey well done! :)
 I'm glad you got it solved. About the lack of a decryption password prompt at boot time, mine seems to do that sometimes too. It's not a new problem, I've just learned to accept it and just type my decryption password after I think enough time has passed for me to expect the system to have reached that stage of booting. I just think of it as extra security.

According to the man page for mkinitramfs, booting from an older kernel and running mkinitramfs -k -o /boot/<name and number for initrd.img> would have worked too.

---


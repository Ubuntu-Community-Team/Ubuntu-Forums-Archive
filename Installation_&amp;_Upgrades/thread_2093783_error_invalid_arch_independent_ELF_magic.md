---
title: "error: invalid arch independent ELF magic"
date: 2012-12-11
forum: Installation &amp; Upgrades
---

### Post by Atrytone on 2012-12-11
I've been running Ubuntu on my Lenovo ThinkPad for the last several months as a second partition alongside the original Windows 7 installation.  

Two things happened before I started having problems that I think might be related:

*I had to interrupt an upgrade process when it was trying to upgrade the the most recent version of Ubuntu.
*The computer went to sleep and experienced a graphics bug when I tried to wake it up.  I had to reboot by holding down the power button.

For a while I was just getting a blank screen with a cursor, so I booted from a USB with boot-repair.  I clicked 'Try Ubuntu' after booting from the USB and ran the boot repair utility.  It seemed to be successful and gave me the following link:

[http://paste.ubuntu.com/1426421/](http://paste.ubuntu.com/1426421/)

Now when I try to boot to the Ubuntu partition I get:

error: invalid arch independent ELF magic
grub rescue>

That's got to be the most amusing error message ever.  But, anyone know what I can do to fix this?

Thanks in advance!

---

### Post by oldfred on 2012-12-11
In this thread, they just reinstalled grub to the MBR.

Edit missed link:
[http://ubuntuforums.org/showthread.php?t=1965810](http://ubuntuforums.org/showthread.php?t=1965810)

Is your system BIOS/MBR as the follow up posts may not have been and UEFI/gpt is a lot different. 

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by Atrytone on 2012-12-11
I thought I did post the link from the boot repair.

I'm having trouble making sense of your post.  Do you have a recommended course of action or need more info?

---

### Post by oldfred on 2012-12-11
I meant to include a link where they just reinstall grub to the MBR. Added to my first post.

Did you use Boot-Repair to reinstall grub? It looks like you did, but then do you still get error?

---

### Post by Atrytone on 2012-12-12
Thanks for the replies, oldfred, now I'm making progress!

When I try this command
> sudo mount /dev/sda5 /mnt
in the terminal I get this error message:
> mount: can't find /dev/sda5/mnt in /etc/fstab or /etc/mtab

Looks to me like it's somehow looking in the wrong place for the bootable drive?


Yes, I when I ran the boot-repair utility one of the steps it reported taking was reinstalling grub.

---

### Post by oldfred on 2012-12-12
sudo mount /dev/sda5 /mnt 			 		

What you posted is missing the space after the 5? Best to copy & paste commands if at all possible. Some spaces may not look like spaces.

---

### Post by Atrytone on 2012-12-12
Newbie alert!  Thanks, now it makes sense why that space is there.

I got the grub prompt now.  I bet I can figure out from here how to get it to give me the nice boot menu so I can choose my OS.  I'll let you know if I run into problems.

Thanks again!

---

### Post by oldfred on 2012-12-12
If you are just at grub? or still grub rescue? It may not be easy.

Commands to manually boot.
       Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)
HOWTO: Boot & Install Ubuntu from the Grub Rescue Prompt 
[http://ubuntuforums.org/showthread.php?t=1599293](http://ubuntuforums.org/showthread.php?t=1599293)

---

### Post by Atrytone on 2012-12-12
Just at grub> now.  No more grub rescue.

---

### Post by oldfred on 2012-12-12
You can try manual boot commands as link to above.

You might just try boot repair again, but run the full grub uninstall/reinstall. Just make sure you have working Internet as it has to redown load a new copy of grub to reinstall it.

---

### Post by Atrytone on 2012-12-12
I tried running the boot repair utility again.

Then I tried following the nice instructions here: [http://howtoubuntu.org/how-to-repairrestorereinstall-grub-2-with-a-ubuntu-live-cd/](http://howtoubuntu.org/how-to-repairrestorereinstall-grub-2-with-a-ubuntu-live-cd/)

Still getting a grub> prompt instead of a boot menu.

Haven't been able to figure out (yet) which sequence of manual commands I need to boot directly from the grub> prompt.

---

### Post by oldfred on 2012-12-12
Did you do the full install & reinstall. When I went to post commands below I noticed you are missing the link to the initrd.img in root

Normal using the links in root, but script does not show initrd.img:
       set prefix=(hd0,5)/boot/grub
set root=(hd0,5)
linux (hd0,5)/vmlinuz root=/dev/sda5 ro
initrd (hd0,5)/initrd.img
boot

This may work, but if grub was not fullly configured?

 set prefix=(hd0,5)/boot/grub
set root=(hd0,5)
linux (hd0,5)boot/vmlinuz-3.0.0-21-generic    root=/dev/sda5 ro
initrd (hd0,5)/boot/initrd.img-3.0.0-21-generic 
boot

Another is the older -15 kernel. Change all the -21 to -15 to see if older version still works.

---

### Post by Atrytone on 2012-12-13
All of the variations I try of third line beginning with 'linux' give me the following error:

> error: file '/boot/grub/i386-pc/linux.mod' not found

Will investigate this error with my own google searches, but thought I'd post it here since you've been so helpful :)

---

### Post by oldfred on 2012-12-13
Your boot script showed grub2 1.99 in MBR. But it is grub2 2.00 that now has all the mod files in another sub-directory i386-pc. Or versions do not match.

So did you reinstall grub with a newer version of Ubuntu. Ubuntu now seems to require you to use the same version for consistency.

Or from Boot-Repair use it to chroot and totally uninstall and reinstall grub2 from inside your install to you have version consistency.

       To chroot, you need the same 32bit or 64 bit kernel. Best to use same version.
[https://help.ubuntu.com/community/BasicChroot](https://help.ubuntu.com/community/BasicChroot)
drs305 chroot to purge & reinstall grub2
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
kansasnoob- full chroot one line version with &&---- change sda3 to your install
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)

---

### Post by Atrytone on 2012-12-13
The version of Ubuntu I used to make my bootable usb and run the boot-repair was newer than my original Ubuntu install.  Is that what you're thinking is causing the problem?  I installed a newer version of grub and it's trying to boot to an older version of Ubuntu?

So uninstalling and re-installing grub might help, you seem to be saying.  I'll try to do that and I'll sort through your links.  Thanks again for the continued help.

---

### Post by Atrytone on 2012-12-18
I went ahead and just reinstalled Ubuntu as I didn't really have anything worth saving in my old install.  Thanks again for the help!

---


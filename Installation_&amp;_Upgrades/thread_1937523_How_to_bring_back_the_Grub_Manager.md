---
title: "How to bring back the Grub Manager?"
date: 2012-03-08
forum: Installation &amp; Upgrades
---

### Post by Saurabhdua on 2012-03-08
Hello Folks!

I were to FORMAT my Windows Partition & as a consequence, I have lost that list of options during BOOT that used to showcase Ubuntu OS Choice & corresponding Recovery images!

What should I do to recover Grub Manager? Help will be sincerely appreciated & is desperately required.

---

### Post by sikander3786 on 2012-03-08
Hi!

Can you still boot Ubuntu successfully? If yes, then Grub menu has just hidden itself as it only shows up by default if multiple OS are present. If you still want to see the Grub menu, you can press and hold down the <Shift> key from your Bios screen whenever you want to access the boot menu. You can also set it to show by default by tweaking the respective setting in the file '/etc/default/grub'. We can give you instructions once you confirm that Ubuntu is booting successfully.

Extremely doubtful, however it is possible to some extent that you are unable to boot Ubuntu either since you deleted the Windows partition. If this is the case, you need to boot an Ubuntu Live CD/USB and run and post the output of 'bootinfoscript' as per instructions here:

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

It would let us have a detailed look at your partitioning setup and then we can give you exactly 3 commands for re-installing Grub.

---

### Post by Saurabhdua on 2012-03-08
Thanks sikander3786!

On turning ON the System, Windows OS loads by default & I couldn't figure if I'll be able to boot Ubuntu sucessfully or else!? I'll go through the latter instructions soon & will keep you posted on the Outcome.

---

### Post by sikander3786 on 2012-03-08
> **Saurabhdua said:**
> Thanks sikander3786!

On turning ON the System, Windows OS loads by default & I couldn't figure if I'll be able to boot Ubuntu sucessfully or else!? I'll go through the latter instructions soon & will keep you posted on the Outcome.
So after formatting the Windows partition, did you re-install Windows? If yes, then it obviously replaced Grub with its own bootloader and you'll need to re-install Grub.

I am pretty hopeful that you didn't delete your Ubuntu partition accidentally while formatting/re-installing Windows. Output of the 'bootinfoscript' will tell us. ;)

---

### Post by Saurabhdua on 2012-03-08
Yes, the first theory of yours holds True!(Windows OS goes sucessfully installed) &, on using the LiveCD Iam able to access my Ubuntu Partition successfully..but alas, I couldn't make my "Mobile Broadband" aka Tata Photon + work with it inspite of repeated attempts & therefore outcome against 'bootinfoscript' in limbo!

So, how should I re-install Grub?

---

### Post by darkod on 2012-03-08
Reinstall grub (and other bootloaders):
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by Saurabhdua on 2012-03-08
Hello Darkod!

Iam not able to execute any of the mentioned commands since everything typed on the Terminal window  yields either an INVALID option OR an Incorrect syntax message.

Do I need to change this::"ubuntu@ubuntu:~$ " to make work & execute the referred commands as an Admin.?

---

### Post by darkod on 2012-03-08
The commands that have sudo in front are executed with root permission. But as long as you type the command exactly as in the tutorial, it should work.

Also note that linux makes a difference between capitals and small case, so when typing any linux commands (and path, folders, etc) you need to type exactly as it is.

If you try for example:
sudo fdisk -l (small L)

what does it return?

---

### Post by Saurabhdua on 2012-03-09
Hello Darkod!

That's what my question is..? How do we switch on to the Root mode? Iam the sole user & the Administrator of my machine. Iam pretty much a novice with Linux commands & the Terminal window.As far as the last suggested Command goes, I'll make an effort soon to reveal its Outcome.

---

### Post by darkod on 2012-03-09
First of all, when running in live mode from the cd you are not inside your hdd installation. So for example if you open the Documents folder don't expect to see your documents there. Live mode is live mode, used only for repair purposes.

When running in live mode, if you need to execute some terminal command as the root user, you add 'sudo' in front. That will make it execute as root. It is never recommended to actually try and login into your computer as root. Always use your user.

When running the hdd installation, the only difference from live mode is that when using 'sudo' in front of a command, it will ask you to enter your password. That is your ubuntu password, of your user. That will complete the verification to run the specified command in sudo mode.

So, when restoring grub2 from live mode, simply type the commands as they are specified (if they have 'sudo' in front type it) and that's it. Don't worry too much about your user, root user, etc. Just execute the commands to restore your grub2 to the MBR so your can continue booting ubuntu.

---

### Post by critin on 2012-03-09
> **Saurabhdua said:**
> Hello Darkod!

Iam not able to execute any of the mentioned commands since everything typed on the Terminal window  yields either an INVALID option OR an Incorrect syntax message.

Do I need to change this::"ubuntu@ubuntu:~$ " to make work & execute the referred commands as an Admin.?

Copy and Paste the commands into the terminal  One at a time and hit enter after each, let it do it's job and when it shows this again, :"ubuntu@ubuntu:~$ "  Paste the next command and hit enter.

---

### Post by Saurabhdua on 2012-03-11
Hello Darkod!

Excuse me for such intermittent & sporadic responses..but we need to move on.

Could you please have a glimpse against this::

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo fdisk-1
sudo: fdisk-1: command not found
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa8a8a8a8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2805    22531131    7  HPFS/NTFS
/dev/sda2            2806        4998    17613825    5  Extended
Partition 2 does not end on cylinder boundary.
/dev/sda5            2806        4901    16832512   83  Linux
/dev/sda6            4901        4998      780288   82  Linux swap / Solaris
ubuntu@ubuntu:~$ sudo grub
sudo: grub: command not found
ubuntu@ubuntu:~$ sudo mkdir /media/sda5
ubuntu@ubuntu:~$ sudo mount /dev/sda5_/media/sda5
mount: can't find /dev/sda5_/media/sda5 in /etc/fstab or /etc/mtab
ubuntu@ubuntu:~$ 

Please guide me through the rest.

---

### Post by Saurabhdua on 2012-03-11
Thanks Guys!

Iam now able to access the Ubuntu Partition quite successfully.Was making a stupid mistake of typing -1 instead of -l. Guess what,...I have to perhaps again go through the installation of Windows XP since it's partition has now started showing up::

Missing or Corrupted \WINDOWS\SYSTEM32\CONFIG\SYSTEM file.

Can anyone please volunteer to alleviate this woe now?

---

### Post by darkod on 2012-03-11
I have no idea about that XP error, it seems the file is missing. You might need to repair your XP installation.

That would again delete grub2 from the MBR so you would need to restore it again after XP is working.

Note that your mount command in the latest post was not correct, you had one underline instead of space. It should be:

```
sudo mount /dev/sda5 /media/sda5
```

---


---
title: "installing windows xp"
date: 2010-01-26
forum: Installation &amp; Upgrades
---

### Post by josephobrien2000 on 2010-01-26
Hi

I want to install windows xp on my ubuntu 9.1 laptop.
why?
because one of the primary uses of this laptop is to connect to my lcdtv and display multimedia. Ubuntu does not do this well beacuse of the ati radeon 9700 display chip which has terrible trouble dual displaying. Xp does this fine
So, Ive done a bit of research and have been put off by this. Its not a simple process is it?
1st Question, should i create a seperate partition for xp or just use the same partition as ubuntu?
2nd question. After installin xp, how can I setup the Grub2 to give me the choice of xp or ubuntu?
Thanks in advance

---

### Post by phillw on 2010-01-26
> **josephobrien2000 said:**
> Hi

I want to install windows xp on my ubuntu 9.1 laptop.
why?
because one of the primary uses of this laptop is to connect to my lcdtv and display multimedia. Ubuntu does not do this well beacuse of the ati radeon 9700 display chip which has terrible trouble dual displaying. Xp does this fine
So, Ive done a bit of research and have been put off by this. Its not a simple process is it?
1st Question, should i create a seperate partition for xp or just use the same partition as ubuntu?
2nd question. After installin xp, how can I setup the Grub2 to give me the choice of xp or ubuntu?
Thanks in advance

Hi, and welcome.

The easiest way is to set up one partition for xp of the size you want it to be & format it with NTFS - leave the remainder of the disk with no file system on it. (The LiveCD can do this for you)

Install xp onto the ntfs area (the only bit that xp will 'see')

Install Ubuntu onto the free area - grub2 will automatically add xp to the boot list choice.


If you already have ubuntu on and you're going to add xp onto it's own partition, then xp will overwrite the MBR - to get grub back, head over here --> [Grub/XP/Vista Bootloader - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1014708") 
Regards,

Phill.

---

### Post by josephobrien2000 on 2010-01-27
Hi

Thanks for the tip - nice and clear

I do have Ubuntu already installed. The HD has 160GB. There are two partitions - a very large one for ubuntu and aa very small one (presumably swap file)
So this is my step by step instructions.
1) boot up using live CD to create a 3rd partition for win xp
2) boot up with ubuntu to ensure all is fine
3) boot up with xp cd and isnatll onto the xp partition. I know for a fact that this will have no label (it'll say unknown volume - so perhaps I could label volume somewhere?)
4) presuming only xp will boot now, I need to reinstate grub2 so...
5) boot up with live cd
6) type
sudo fdisk -l
sudo mkdir /media/sda5

sudo mount /dev/sda5 /media/sda5
sudo grub-install --root-directory=/media/sda5 /dev/sda
6) seem ok to you?

---

### Post by garvinrick4 on 2010-01-27
The only thing that always works for me if I right click on the partition say sda5 and LABEL it say karmic on gparted.

sudo mkdir /media/karmic
sudo mount /dev/sda5 /media/karmic             space after sda5
sudo chroot /media/karmic

sudo cp /etc/resolv.con edit/etc/           To get wifi access



In other words karmic ( or what ever your LABEL after /media and all go's well in 9.10 and 10.04 for me.

---

### Post by josephobrien2000 on 2010-01-27
I woder how I repartition the hard disk?

---

### Post by Megafag on 2010-01-27
> **josephobrien2000 said:**
> I woder how I repartition the hard disk?

Using Gparted on the live ubuntu disk perhaps?

---

### Post by josephobrien2000 on 2010-01-28
Yes, tried that. No option to resize. greyed out on taskbar
Tried kdm partition manager and this should resize but cant get it to run as it refuses me as Im niot the administrator. bloomin am!

---

### Post by oldfred on 2010-01-28
greyed out usually means it is mounted. If both swap and the linux install are in an extended partition the entire partition is usually mounted as the liveCD's use the HD's swap. You have to run swapoff or click on the swap partitition to unmount it.

You cannot resize mounted partitions, so you cannot use gparted from your working Ubuntu to resize itself.

---

### Post by Cheesemill on 2010-01-28
Also bear in mind that Windows will only install to the first primary partition on a drive, so make sure the partition for installing Windows is first on your disk.

---

### Post by Dayofswords on 2010-01-28
windows xp boot loader is forceful and will install itself, and i dont think it can see ubuntu

that why you should go xp, then ubuntu

---

### Post by oldfred on 2010-01-28
Windows does not have to be on the first primary but at least one copy of windows has to be on a primary or have a primary partition with its boot files.

---

### Post by presence1960 on 2010-01-28
> **Cheesemill said:**
> Also bear in mind that Windows will only install to the first primary partition on a drive, so make sure the partition for installing Windows is first on your disk.

That is not true. I have had windows on sda2, sda3 and sda4. All primary partitions of course. What matters is that the disk you are installing windows to must be set in BIOS to be the first hard disk that boots because windows always attempts to write it's boot loader to the first disk that boots. Once the install is completed you may put the hard disk back in the boot order if required.

Currently I have Vista on sdc1 & windows 7 on sda3. When I installed them I made sdc first in the hard disk boot order in BIOS so their bootloader would be written to MBR of sdc. When installation was complete I moved sdc back to third in the hard disk boot order. Booted into Ubuntu and ran sudo update-grub to add windows to GRUB2.

---

### Post by presence1960 on 2010-01-29
> **Dayofswords said:**
> windows xp boot loader is forceful and will install itself, and i dont think it can see ubuntu

that why you should go xp, then ubuntu

That is incorrect also. What actually happens when you install windows to a primary partition on the same disk as Ubuntu is this:

1. Windows is installed to the primary partition.
2. Windows overwrites GRUB on MBR of the disk replacing it with windows  bootloader.

The solution is so simple. Boot up after the windows installation and make sure windows boots fine. If it boots fine boot from the Ubuntu Live CD & restore GRUB on MBR.

**_*That windows MUST be installed first is one of the biggest fallacies propagated on this forum by well intentioned but misinformed people.*_** Don't believe me read these links and see what you think:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

---

### Post by josephobrien2000 on 2010-01-29
Thanks for your help
Ive made some progress
I used Gparted when booting off the liveCD, not from ubuntu (on the computer)
Resized the partition to make space for XP
Formatted space to ntfs for XP and labelled it Xp so that it can easily be seen in th ewidnows install process
Windows installed
And as it has been previously stated, Grub on MBRis overwritten by windows bootloader.
 
Now...I used this [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708) mistakenl thinking I could then have a choice of ubuntu and xp at boot time
I dont
I managed to change the boot back to Ubuntu from xp
 
What I need to do now is put XP on the Grub2 list
Instructions on the web seem to give instructions for old grub, as they refer to menu.lit which no longer exisits.
 
Any ideas on how to get the choice of xp or ubuntu at boot time?
 
XP is on /dev/sda2
Ubuntu i on /dev/sda1
Both on same hard disk /dev/sda

---

### Post by presence1960 on 2010-01-29
Boot into Ubuntu and from terminal run ```
sudo update-grub
```

---

### Post by darkod on 2010-01-29
> **josephobrien2000 said:**
> 
Resized the partition to make space for XP


If I may jump in with important question not entirely related to the thread.
Are you allowed to resize the root partition like this? I was under the impression you have to resize the filesystem first with separate command, and then the actual partition. Or because in live desktop root is not mounted, Gparted will do the job?

I remember one thread where the OP was expanding root, and the filesystem remained same size. So I googled some command (was it resize2fs?) and that expanded the filesystem to fit the expanded partition.

But shrinking is opposite process and if you don't shrink the filesystem first, won't the partition shrink destroy it? Presence?

---

### Post by josephobrien2000 on 2010-01-29
found this
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
sudo update-grub
 
but I see presence1960 beat me to it!
 
Works a treat, now have Xp as an option, and it works fine
 
How can I delete the ubuntu recovery mode options?
 
As for darkod comments, maybe I did not explain correctly
simply used livecd, gparted, resized the ubuntu partition first (giving me 100GB of unallocated space), right clicked it, created a ntfs partition and all went well

---

### Post by darkod on 2010-01-29
> **josephobrien2000 said:**
> found this
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
sudo update-grub
 
but I see presence1960 beat me to it!
 
Works a treat, now have Xp as an option, and it works fine
 
How can I delete the ubuntu recovery mode options?
 
As for darkod comments, maybe I did not explain correctly
simply used livecd, gparted, resized the ubuntu partition first (giving me 100GB of unallocated space), right clicked it, created a ntfs partition and all went well

Yes, you did explain it right. Just I was under impression it doesn't work that way. Glad to know it works.

As for the recovery mode, it's advisable to keep it if sometimes your normal mode doesn't work. You can repair things in recovery mode.

But if you still want to remove it you should find more information about grub2 here:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by josephobrien2000 on 2010-01-31
many thanks to presence and darkod
all running fine 
as suspected, flash video prformance an dual screen  bette with xp

---


---
title: "Tired - Tried every trick, still I boot in GRUB&gt; Pls. help me reinstall my Grub2"
date: 2010-08-25
forum: Installation &amp; Upgrades
---

### Post by AlexanderDGreat on 2010-08-25
Hi can you pls. help me? I have to Dual Boot with Windows _BUT UBUNTU is installed first._ I've tried and read every Tutorial out there but I still can't GET it. Help! :(

Here's my setup: 2x physical 80gb Seagate hard disks

_1st hd:_
*** Used GPARTED in Ubuntu Live CD ***

NTFS (primary) Windows XP
sda1 - 20gb - C:\ WindowsXP
sda2 - extended
sda5 - logical 5gb D:\ Swapdrive
sda6 - logical 15gb E:\ Storage

EXT4 (logical) Ubuntu Lucid Lynx
sda7 - 1gb /boot
sda8 - 5gb /swap
sda9 - 24gb /

_2nd hd:_
sd**b**1 - 80gb /home

Now, here's my story:

1. Installed Ubuntu first on ext4 partition
2. Backed-up my MBR, name: ubuntumbr
3. Installed Windows afterwards on NTFS primary (windows will complain if OS is not in *primary partition* and *first partition* of the drive)
4. Now Ubuntu won't boot due to Windows wipes out MBR - understood.
5. Used Ubuntu Live CD, backed-up MBR again, name: windowsmbr
6. Up to this point, Windows boots fine, but I can't use Ubuntu anymore - understood.
7. Booted to Ubuntu Live CD again and restored ubuntumbr

[COLOR="Blue"]**_Question: _** Restored ubuntumbr. Why won't it automatically just boot Ubuntu? Since it's the default MBR _way before I installed Windows on step #3_? I thought grub2 is installed in MBR which is the first 512 bytes of ANY hard disk? Since Windows wiped it out, I'm assuming restoring this would also just restore grub2 and thus boot me to Ubuntu.[/COLOR][COLOR="Red"] BUT NO, I'm greeted by a GRUB> Command Line![/COLOR]

[COLOR="Green"]After restoring my very first MBR name: ubuntumbr, I was EXPECTING Ubuntu to BOOT without any problems, and just smooth sail to make grub2 detect Windows. But it's not what happened. Can you help me?[/COLOR]

So what tutorials have I read? I've almost been all over the place. Trying, chroot to my /mnt/boot, grub-install this and that, almost every partition I have already has, a boot/grub folder in them, for trying desperately.

I've seen every tutorials but somehow I always get a problem like, chroot in /bin/bash is / mounted? Also, when I grub-install, it says, installation complete no problems encountered. I boot then I'm greeted a grub> command line.

I've been doing this for 5 days already and still no luck. Please lend me a hand. Thank you for your time. :)

[COLOR="DarkOrchid"]PS The reason I backed-up windowsmbr is because if I restore it using Ubuntu Live CD. WindowsXP boot fine! What I can't understand is I restore my "other" backed-up ubuntumbr - Ubuntu won't boot and I'm greeted by a grub> CLI. Strange don't you think?[/COLOR]

---

### Post by oldfred on 2010-08-25
If you restored the full 512 you also restored the old partition table. I hope you did not change any partitions as part of your install. It is really easier just to reinstall grub or grub2 to the MBR from a liveCD.

So we can see what is where. From liveCD:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

Because you have a separate /boot partition you have to be careful as many instructions leave out the mounting of that partition which is critical to updating grub.
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")
kansasnoob on grub or grub2 reinstall
[http://ubuntuforums.org/showpost.php?p=9338226&postcount=41](http://ubuntuforums.org/showpost.php?p=9338226&postcount=41)

---

### Post by AlexanderDGreat on 2010-08-25
Hi oldfred, thank you for all those help. Sure, I'm very mindful of others if my question ever gets solved.

The question I want to ask, where exactly do you really RE-install grub2? In the root directory or the /boot directory?

I'm so stupid, but I also think everyone's leaving out this explanation. If I have a separate /boot they say, make sure you mount it at /mnt/boot --- so does this mean you install grub2 in the /mnt/boot ? Or you really install grub2 in /mnt - the root directory? Or do you install it in the /root directory but /mnt/boot is needed?

Whew...

---

### Post by AlexanderDGreat on 2010-08-25
I got it working! I used chroot.

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1912    15358108+   7  HPFS/NTFS
/dev/sda2            1913        9730    62792485+   5  Extended
/dev/sda5            1913        2549     5116671    7  HPFS/NTFS
/dev/sda6            2550        5099    20482843+   7  HPFS/NTFS
/dev/sda7            5100        5221      975872   83  Linux       **--->/boot**
/dev/sda8            5221        5829     4881408   82  Linux swap / Solaris
/dev/sda9            5829        9730    31333376   83  Linux     [B]--->/
[/B]
$sudo mount /dev/sda**9** /mnt
$sudo mount /dev/sda**7** /mnt/boot
$sudo mount --bind /dev /mnt/dev
$sudo mount --bind /proc /mnt/proc
$sudo mount --bind /sys /mnt/sys
$sudo chroot /mnt
$update-grub
$grub-install /dev/sda
$grub-install --recheck /dev/sda
$sudo umount -a

Thanks oldfred. Mounting /boot is important, I thought it was an optional step. Shame on me.

---


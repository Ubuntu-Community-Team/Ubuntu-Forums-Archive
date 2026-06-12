---
title: "two separate ubuntu installation on separate luks partitions"
date: 2021-01-01
forum: Installation &amp; Upgrades
---

### Post by cunfusu on 2021-01-01
I would like to have 2 separate Ubuntu installation in my system.

I also would like to have both installation on separate encrypted partitions with separate passwords.
The reason being that I want to keep 2 separate environment where one system cannot temper the other and vice versa. 
I would then use one for work and the other for personal use.

I need some help to understand better and validate my plan.

I've put some effort in understanding how the boot process work on linux on  uefi/gpt
And for what is my current understanding in order to achieve what I want I need a gpt partition table.
- The first partition is reserved to uefi
-  Then I need a partition /boot where as far as I understand lives the  kernel and the grub (is this correct?). There should be a way to encrypt such partition  but it's hard and inconvenient so most of the time is kept unencrypted
- Finally I need Luks encrypted volumes where to keep all the logical volumes (created with lvm) necessary for my installation.

Following a mix of this guide on [how to encrypt disks on ubuntu]("https://medium.com/@chrishantha/encrypting-disks-on-ubuntu-19-04-b50bfc65182a") and this arch guide on [how to encrypt using lvm over luks]("https://wiki.archlinux.org/index.php/Dm-crypt/Encrypting_an_entire_system#LVM_on_LUKS") I'm getting to the point where I have.

- esp (uefi) partition (fat32)
- ext4 partition to use as /boot
- one partition encrypted with luks (work)
  - one logical volume inside the luks (work) for swap
  - one logical volume inside the luks (work) for / (ext4)
- one partition encrypted with luks (personal)
  - one logical volume inside the luks (personal) for swap
  - one logical volume inside the luks (personal) for / (ext4)

Before proceeding with the installation I started having doubts that this process would work.
Do I need separate partitions to use as /boot for each installation?
To be honest I'm still a little bit confused on how the dual ubuntu does work (which grub would be in charge and how the grub handle luks partitions)
Can someone help me to understand? 

Also I still do not understand what the last steps(after ubuntu insatllation) on the [first guide I've mentioned]("https://medium.com/@chrishantha/encrypting-disks-on-ubuntu-19-04-b50bfc65182a") do since they look different from the arch guide. I have the feeling that what they do is to somehow instruct the whatever is involved in the boot process to handle the luks partition/s. 

Can you help me to fill the gaps?

---

### Post by cunfusu on 2021-01-01
Ok. while waiting I've decided to restart from scratch and make 2 partitions to use as /boot one for each ubuntu installation.

I've firs installed the first instance of ubuntu and it worked as expected.
Once the kernel loads I'm asked to insert the password.

I've then installed the second ubuntu. 
I was expecting now to see a grub sceen where to select which ubuntu to run but instead the 2nd ubuntu startup and I get prompted to insert the key for the second luks partition. 

apparently the new grub has overwritten the previous and does not recognize the previous installation. 

I've tried with grub-mkconfig but had no luck. 
the first installation still does not appear :-(

---

### Post by oldfred on 2021-01-01
With UEFI, there is /EFI/ubuntu/grub.cfg which is a 3 line grub configfile file to load the full grub.cfg in your install. Not sure if the same with encrypted installs if /boot inside LVM as I do not know nor use LVM nor encryption. I have multiple standard installs and have edited that 3 line grub.cfg or saved it & restored it, to be my main working install. It needs correct UUID & drive, partition for install that you want to boot.

Typically grub will find other installs with sudo update-grub, but you would have to mount your other install and decrypt it so os-prober can find it. Otherwise it is hidden and will not be found.

I also had to change mount of ESP to defaults from 0077 to easily see /EFI/ubuntu/grub.cfg. Years ago Ubuntu used defaults but changed to 0077. I believe that was for security reasons, and probably should change back to 0077.
```
[FONT=monospace][COLOR=#54ff54]**fred@z97-focal-kubuntu**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ cat /boot/efi/EFI/ubuntu/grub.cfg [/COLOR]
search.fs_uuid db535ec5-b653-4627-9f21-2645e1d7ca4e root hd0,gpt6  
set prefix=($root)'/boot/grub' 
configfile $prefix/grub.cfg
[/FONT]
```

Grub has some modules built in, but has lvm & encryption modules also.  Do you have insmod lvm and insmod luks or because it is an encrypted install did grub built that in? (more for my info as many questions on LVM & encryption).

---

### Post by cunfusu on 2021-01-01
> **oldfred said:**
> With UEFI, there is /EFI/ubuntu/grub.cfg which is a 3 line grub configfile file to load the full grub.cfg in your install. Not sure if the same with encrypted installs if /boot inside LVM as I do not know nor use LVM nor encryption. I have multiple standard installs and have edited that 3 line grub.cfg or saved it & restored it, to be my main working install. It needs correct UUID & partition/drive.

Typically grub will find other installs with sudo update-grub, but you would have to mount your other install and decrypt it so os-prober can find it. Otherwise it is hidden and will not be found.

Well what I currently have is:

1. efi partition
2. boot partition for ubuntu A (unencrypted)
3. boot partition for ubuntu B (unencrypted)
4. partition containing / for A (encrypted)
5. partition containing / for B (encrypted)

at the moment I'm able to use the installation B (installed after A which I was able to start before installing B)

Yes there is a grub.cfg in the efi partition. it contains the uuid of the partition 3
If believe this means that efi pass the ball to grub in the partition 3 during boot.

What I've tried to do from installation B is to get grub to update the additional grub.conf in partition 3 to also detect kernels in partition 2

I've mounted the partition 2 and run grub-mkconfig.
I'll try to repeat using grub-update this time

Do you know if I need to mount also the root partition of A or the /boot is enough for os-prober to see the A installation?

---

### Post by cunfusu on 2021-01-01
Bingo! grub-update worked this time.
It was necessary for me to mount / for A (mounting only the boot was not sufficient)
I'm not sure if I understand your question:
"Do you have insmod lvm and insmod luks or because it is an encrypted install did grub built that in?"

would I have to repeat the same process when I get new kernels or will grub auto magically fix itself?

---

### Post by oldfred on 2021-01-01
If your /boot boot is not encrypted then the 3 line grub.cfg would not need anything special.
I expect the full grub.cfg in your install has extra insmod commands. 

You may have to mount partition.
Ubuntu with standard installs adds link to the most current kernel. It used to be in / but now is in /boot.
And you then can manually create a boot stanza in 40_custom to boot the link and then will always be updated.

How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[https://www.gnu.org/software/grub/manual/grub/grub.html#Multi_002dboot-manual-config](https://www.gnu.org/software/grub/manual/grub/grub.html#Multi_002dboot-manual-config)
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)
[https://ubuntuforums.org/showthread.php?t=2076205&p=13787835#post13787835](https://ubuntuforums.org/showthread.php?t=2076205&p=13787835#post13787835)


Forum thread is now long. Often suggest reading first page & jumping to end and work backwards for more updated info. Not sure if any posts are for encrypted installs or not.

---

### Post by cunfusu on 2021-01-05
Ok It was quite easy.

I've added a menuentry to my 40_custom file:

```

&#10140;  ~   cat /etc/grub.d/40_custom
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry 'Work Kubuntu' {
        search --no-floppy --fs-uuid --set=root 1b0a7b5a-d724-4727-9ebc-06cd099ac37d
        linux /vmlinuz root=/dev/mapper/wvg-root ro quiet splash
        initrd /initrd.img
}

```

having care of
configuring the uuid after '--set=root' and the path (/dev/mapper/...) after 'root='


I've also updated the following variables in /etc/default/grub
```

GRUB_TIMEOUT_STYLE=menu 
GRUB_TIMEOUT=20
```

because previous values were hidden and 0 and last but not least
'sudo update-grub'

This is a quite minimal but apparently working configuration.

I would say that for now I consider this post as solved.
Thank you @oldfred!

---


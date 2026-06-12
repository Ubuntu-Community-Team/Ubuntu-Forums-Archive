---
title: "after upgrade to 16.04: &quot;ALERT! /dev/mapper/laptop--hp-root does not exist.&quot;"
date: 2017-01-26
forum: Installation &amp; Upgrades
---

### Post by mandavi2 on 2017-01-26
After I upgraded from 14.06 to 16.06 all new kernels would not work anymore. Despite my entire harddisk being encrypted via LUKS I'm not asked for a password. Instead I get following messages:
> Begin: Running /scripts/local-block ... lvmetad is not active yet, using direct activation during sysinit
  Volume group "laptop-hp" not found
  Cannot process volume group laptop-hp
done.
That gets repeated many times before I get:
> Gave up waiting for root device. Common problems: 
...
ALERT! /dev/mapper/laptop--hp-root does not exist. Dropping to a shell!

Old kernels booted just fine until I removed them by accident. Yeah, congrats, I know...

My configuration is shown by the [output of  Boot Info Scrip]("https://paste.ubuntu.com/23870703/")t.


[LIST]
[*]So I chrooted from a USB-Image and installed older kernels. But I get the same error message now with them too.
[*]I chrooted again to rebuild GRUB2 which went just fine, but didn't change anything.
[*]I tried 'update-initramfs -k all -c' but it didn't change anything.
[*]I tried to make the volumes available in initramfs [like this guy did]("https://ubuntuforums.org/showthread.php?t=1632033") after I'm dropped to a shell via 'cryptsetup luksOpen /dev/sda5 sda5_crypt' but initramfs tells me it doesn't know the command
[/LIST]

Do I need to add things to GRUB via insmod to have cryptsetup in the initramfs shell?
Or how do I proceed from here?

---

### Post by mandavi2 on 2017-01-27
I'm a little stuck here...
To decrypt my LUKS drive I seem to need cryptsetup which is provided by the module dm-crypt. I don't have that installed in /grub/i386-pc/.

It says on the [project page]("https://gitlab.com/cryptsetup/cryptsetup/wikis/DMCrypt") this tool is only for kernels below 4.x. So wouldn't it need to be installed on my machine as long as I still have 3.x kernels? And how is all the decryption done in 4.x kernels?

Any help is appreciated...

---

### Post by mandavi2 on 2017-02-02
I was able to solve it by chrooting into my system and changing /etc/crypttab from

```
sda5_crypt UUID=c990132c-5b5c-44a4-8c73-dfa0b247e0ad none luks
```
to 

```
luks-c990132c-5b5c-44a4-8c73-dfa0b247e0ad UUID=c990132c-5b5c-44a4-8c73-dfa0b247e0ad none luks
```

How your device is called you find out by issuing:
```
ls /dev/mapper/

control  laptop--hp-root  laptop--hp-swap_1  luks-c990132c-5b5c-44a4-8c73-dfa0b247e0ad

```

to have your /boot partition updated you need to
```
sudo update-initramfs -u all
```
and during boot I was asked for my password and booting worked again.

---


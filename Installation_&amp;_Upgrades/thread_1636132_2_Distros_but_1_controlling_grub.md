---
title: "2 Distros but 1 controlling grub"
date: 2010-12-02
forum: Installation &amp; Upgrades
---

### Post by dontgetshocked on 2010-12-02
I have 2 distros installed right now and generally keep the main one and install and look at other distros.My question is this; Can I install a second distro and not let it take over my frub/boot menu and NOT let it control the boot menu? If so how would I do it? I always get confused when I install the second distro when it asks what to do,use / or boot as the option etc...

Thanks,

---

### Post by oldfred on 2010-12-02
Almost all installs give you a choice on where to install the bootloader. But even Ubuntu now only shows it if you use manual install.

[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)

But even if you install the boot loader of the new system, just reinstall grub2 for Ubuntu. Just always have a liveCD available to use to reinstall grub2.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

### Post by uRock on 2010-12-02
Ubuntu will snatch control over grub after updates. Or at least it did on my machine with the last kernel update.

Background: I have ubuntu 10.04 installed. I installed 10.10 in a test partition a couple of months ago and allowed it to take over grub. When I was doing the last kernel update I was like, "now I have to boot into 10.10 and let grub update the boot list," but low and behold the whole grub menu had changed around and dropped the 10.10 kernel to the bottom of the list.

---

### Post by dontgetshocked on 2010-12-02
Well this leaves me without a clue as to what to do! Maybe I dont understand.I have 2 distros and do NOT want allow any other os to take over that boot menu and make itself the primary one.I am not sure as how to do this.I looked at the links but I dont see how they can help me.please provide more info.
Thanks,

---

### Post by uRock on 2010-12-02
Which other distros are you looking into installing?

---

### Post by drs305 on 2010-12-02
> **uRock said:**
> Ubuntu will snatch control over grub after updates. Or at least it did on my machine with the last kernel update.

Background: I have ubuntu 10.04 installed. I installed 10.10 in a test partition a couple of months ago and allowed it to take over grub. When I was doing the last kernel update I was like, "now I have to boot into 10.10 and let grub update the boot list," but low and behold the whole grub menu had changed around and dropped the 10.10 kernel to the bottom of the list.

What may have happened in your case is that the original installation information was stored in dpkg. It could be that when the grub-pc package was updated and Ubuntu retrieved the Grub2 install information from dpkg.

You can check the location dpkg points to by running the following and looking at the "grub-pc/install devices":
```
sudo debconf-show grub-pc
```

You can change the location by running:
```
sudo dpkg-reconfigure grub-pc
```

---

### Post by dontgetshocked on 2010-12-02
Right now I Mint 10 which has the main grub control as it was installed last.I also have Pinguy installed as well.But I am one of those people who just have to check out other distros.I cant see me ever leaving Mint but I would like to experiment with other distros,but do NOT want them taking control of me grub/menu.I know I can use startup manager to load whatever distro as first but this is not the same.Hope this helps explain.I am retired and stay at home and this is a hobby for me but I also have multiple sclerosis and this makes one minute Albert and the next Forest.So my brain power is  not too good these days.
Thanks,

---

### Post by ramaswamyps on 2010-12-02
you can remove grub2 and install older grub-0.9 then you can work with any other grub already working now.
follow the grub change procedure.

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by dontgetshocked on 2010-12-03
Thanks

---

### Post by uRock on 2010-12-03
> **drs305 said:**
> What may have happened in your case is that the original installation information was stored in dpkg. It could be that when the grub-pc package was updated and Ubuntu retrieved the Grub2 install information from dpkg.

You can check the location dpkg points to by running the following and looking at the "grub-pc/install devices":
```
sudo debconf-show grub-pc
```You can change the location by running:
```
sudo dpkg-reconfigure grub-pc
```
Thanks drs305. I was actually glad it did that, being I hardly ever boot the test install. I did just update the test install and it didn't steal grub back.

---

### Post by Mortesins93 on 2010-12-03
These are my partitions and I would like the sda2 partition to control grub:
```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6954    55857973+   c  W95 FAT32 (LBA)
/dev/sda2            6955       11122    33479460   83  Linux
/dev/sda3           11123       11294     1381590   82  Linux swap / Solaris
/dev/sda4           11295       12161     6964177+   5  Extended
/dev/sda5           11295       12161     6964146   83  Linux
```
How do I do it? I tried the "sudo debconf-show grub-pc" and this is what I get:
```
axel@axel-laptop:~$ sudo debconf-show grub-pc
  grub-pc/kopt_extracted: false
  grub2/kfreebsd_cmdline:
* grub-pc/install_devices: (hd0)
  grub-pc/postrm_purge_boot_grub: false
* grub2/linux_cmdline:
  grub2/kfreebsd_cmdline_default: quiet
* grub2/linux_cmdline_default: quiet splash
  grub-pc/chainload_from_menu.lst: true
  grub-pc/hidden_timeout: true
  grub-pc/timeout: 10
```
what does this mean?
Thank you in advance

---

### Post by drs305 on 2010-12-03
> **Mortesins93 said:**
> 
what does this mean?
Thank you in advance

It shows that (hd0) is your grub install device, but that makes sense since that's the only drive reported.

If you have two Ubuntu installations (sda2 and sda5), you can just run the following command while booted into that system:
```
sudo grub-install /dev/sda
```
Do not include the partition number.

If you happen to be in the other OS (sda2 but want sda5, or sda5 but want sda2), mount the other partition and then run:
```

sudo mount /dev/sdaX /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```
So if you were currently booted to sda5, the first command would mount /dev/sda2.

---


---
title: "Install Fedora 12 without messing up Ubuntu 9.10"
date: 2010-03-20
forum: Installation &amp; Upgrades
---

### Post by ulriksvensson on 2010-03-20
Hi all.

I would like to dual boot with Fedora 12 and Ubuntu 9.10. I've used Ubuntu for a couple of years and before that I used Fedora. I have Ubuntu 9.10 installed (and I've done quite a few tweaks) and I don't want to mess it up when I install Fedora.

I've googled this for a few days and I think I know basically what to do but I'm a bit afraid of destroying something. So here's what I've done and what I think I must do.

With gparted I have shrunk my only harddrive and made another partition on the rest. Here's the ouput of df -h:

```
/dev/sda1              61G  6,1G   51G  11% /                                                                 
udev                  500M  280K  500M   1% /dev
none                  500M  264K  500M   1% /dev/shm
none                  500M  196K  500M   1% /var/run
none                  500M     0  500M   0% /var/lock
none                  500M     0  500M   0% /lib/init/rw
```
Ubuntu 9.10 is on sda1 and I wish to install Fedora 12 on sda3.

Here's the output of fdisk -l

```
Disk /dev/sda: 100,0 GB, 100030242816 byte
255 huvuden, 63 sektorer/spår, 12161 cylindrar
Enheter = cylindrar av 16065 · 512 = 8225280 byte
Diskidentifierare: 0xf638eb4a

    Enhet Start     Början        Slut     Block    Id  System
/dev/sda1   *           1        7969    64010961   83  Linux
/dev/sda2           11789       12161     2996122+   5  Utökad
/dev/sda3            7970       11788    30676117+  83  Linux
/dev/sda5           11789       12161     2996091   82  Linux växling / Solaris
```
(Sorry about the Swedish...)

Next I would copy the vmlinuz and initrd.img files from the Fedora source to the /boot/  (on sda1 I suppose) directory, renaming them to vmlinuz-install and initrd.img-install.

Next I would have to edit the /boot/grub/grub.conf in order to be able to boot from the installation partition (sda3). I'm not sure of how to do this.

Finally reboot and follow the installation process and hope for the best (?).

Am I anywhere close?

---

### Post by zvacet on 2010-03-21
I don´t speak Swedish so I c an only guess what is on sda2 but it look your Ubuntu is on sda1.Correct me if I´m wrong.If sda3 is just formated and empty install Fedora on it.I believe Fedora installer will allow you to do that(choose partition on which you want to install it).After install it depend on you.You can use Fedora bootloader or you can [reinstall Ubuntu grub.]("https://help.ubuntu.com/community/Grub2#Reinstalling from LiveCD") Since you are using these two distros maybe you will find [this]("http://linuxsearch.org/") handy. ;)

---

### Post by tom4everitt on 2010-03-21
Installing fedora will normally do two things:

It will copy a lot of files to the partition you choose as /, and it will install a boot loader to the beginning of the hard drive. Since you want to keep your ubuntu boot loader, you should only to the file copying, not the boot loader installation.



So here's what to do:

DON'T copy vmlinux and intird to your existing ubuntu partition, that will only mess things up. 

Rather burn a fedora live cd, boot from it and enter the installer. At some point you'll be able to choose manual installation. 

When you reach the partitioner, you set the mount point of /dev/sda3 to '/' (and format it if its not the right file system already). 

You must also find an option to whether install boot loader or not (and where to install it to). Do NOT let it install a boot loader, cause then it will overwrite your ubuntu boot loader (its not too hard to recover the ubuntu boot loader, but its unnecessary messy). 

I don't exactly remember where the boot loader option is, it might be hidden under some 'advanced' button even. But look for and I think you'll find it. Don't let it perform the installation before you've found and unchecked it, the default option is to install a boot loader. 

Good luck!

---

### Post by ulriksvensson on 2010-03-21
Thanks a lot, I'll give it a go. I'll post back on how it goes.

---

### Post by ulriksvensson on 2010-03-21
I've booted from the live cd and I've tried to run the installation. I had to abort though:

> **tom4everitt said:**
> At some point you'll be able to choose manual installation. 

No, there was no such option. 

> **tom4everitt said:**
> When you reach the partitioner, you set the mount point of /dev/sda3 to '/' (and format it if its not the right file system already). 

There was no way to choose which partition to place Fedora. Only the usual "Replace existing Linux System, Use all disk space, Use free disk space" etc. I tried to choose "Use free disk space" but Anaconda complained about "not enough disk space..."

Is there another way?

---

### Post by tom4everitt on 2010-03-21
Okay, sorry I didn't really remember the details.

When you reach the step where you chose 'use free space', I think you should choose 'Advanced Storage Configuration'. See the image here:
[http://www.my-guides.net/en/content/view/174/26/1/1/#fedora_12_installation_guide](http://www.my-guides.net/en/content/view/174/26/1/1/#fedora_12_installation_guide)

There must a manual way to choose partition, I'm completely positive. And I guess this is where they hide it :)


One picture below that you see where to choose mount points that I talked about. 


And one picture below that you see where to uncheck install boot loader.


EDIT: Are you sure there's not a 'custom layout' under the free space option?

---

### Post by ulriksvensson on 2010-03-21
Yeah I think there is a "Custom layout"... I don't know wy I didn't think of that before. I'll give it a go again.

---

### Post by ulriksvensson on 2010-03-21
Ok, I've got Fedora 12 succesfully installed on sda3. I tried to start GRUB by pressing ESC during startup but nothing happened. I suppose I have to configure grub by adding Fedora in the configfile. Thanks for your help tom4everitt!

---

### Post by tom4everitt on 2010-03-21
Yes, it should still be your ubuntu grub in charge of the booting. 

If you installed ubuntu 9.10 from scratch (not upgrading from 9.04) so you have grub2, Fedora should automatically be added if you run:

sudo update-grub

otherwise you have to add an entry manually to /boot/grub/menu.lst

---

### Post by ulriksvensson on 2010-03-22
Yes I did a fresh install so it's grub 2. Also I ran sudo upadte-grub but haven't tried it yet.

---


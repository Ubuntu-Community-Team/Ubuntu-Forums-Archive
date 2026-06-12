---
title: "Broken boot record woes!"
date: 2010-02-13
forum: Installation &amp; Upgrades
---

### Post by Monroc on 2010-02-13
I'm about to throw my laptop out the window.

Installed Ubuntu on my Dell Lattitude E4300 ages ago, liked it, kept it.

Decided yesterday to install Windows on an empty partition, as I need a native environment to run games in for a LAN, I'm attending soon. Should be no problem, right? Ohh - the troubles...

Windows installation went smooth, but it decided to go evil on Grub and would only boot up in Windows...

After hijacking my wife's computer I found out Windows does not play well with other OS's bootwise. Thankyouverymuch.

No trouble I thought: I'll use my USB-boot-disk to boot back into a Ubuntu and set things right. Worked too, but no mouse or keyboard. I wasn't even able to get the caps lock-light to light up, when I hit the button (repeatedly and hard!), past loading of the Gnome loading screen. Much swearing followed then...

Finally I got a version of DSL (Damn Small Linux) down and got to transferred to my USB-stick with some application for Windows, which actually worked pretty well. I'm able to boot up in the Linux and use the keyboard, but still no mouse-support. Get a terminal up too, and thought I was able to fix things now. Time to be put down once more:

I though I was able to fix booting up in grub with the folloing commands:

sudo grub
> root (hd0, 2)
> setup (hd0)

(sda1 is the Windows-partition, sda2 is /, sda3 is boot-partition, sda4 is swap)

Grub complains over no disks and stuff like that. It will only recognize (hd0, 0) as the USB-stick and I can't seem to mount the harddisk-partitions. Mounting sda1 remounts the USB-stick, mounting sda2 - sdf6 and hda1 - hdf6 yields: "mount: relocation error: mount: undefined symbol: blkid_known_fstype", which I figure means something like "Why is idiot user trying to mount something, which is not there?"

I'm in tears. I've been without my beloved Linux-system now for 26 hours now, because the Linux-ISO's I've downloaded to put on my USB-Stick has either been corrupt or Windows has decided to terminate downloads for a varity of reasons.

A bit of help on how I can fix it so my computer boots up on grub once again would be greatly appriciated by my laptop and me.

---

### Post by tommcd on 2010-02-13
Are you running Ubuntu 9.10? If so, then the procedure to reinstall grub is a bit different since Ubuntu 9.10 uses grub2. Previous versions of Ubuntu used grub-legacy.

To restore grub2 from the Ubuntu live CD see this:
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)
Also this from grub guru Herman:
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Re-install_GRUB_from_Live_CD](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Re-install_GRUB_from_Live_CD)

---

### Post by Monroc on 2010-02-13
Thank you for your reply.

Yes - I use 9.10. I wasn't aware that it used grub2.

But this means pretty much that I need to get a Ubuntu-image to work on my USB-disk. As the standard one doesn't permit my keyboard or mouse to work for some odd reason, I guess I need to download the Alternative DVD and use it's "Boot to Terminal"-option, yes?

---

### Post by tommcd on 2010-02-13
> **Monroc said:**
> 
Yes - I use 9.10. I wasn't aware that it used grub2.

But this means pretty much that I need to get a Ubuntu-image to work on my USB-disk. As the standard one doesn't permit my keyboard or mouse to work for some odd reason, I guess I need to download the Alternative DVD and use it's "Boot to Terminal"-option, yes?
Can't you just boot from a live CD? according to this:
[http://www.dell.com/us/en/enterprise/notebooks/laptop_latitude_e4300/pd.aspx?refid=laptop_latitude_e4300&cs=555&s=biz](http://www.dell.com/us/en/enterprise/notebooks/laptop_latitude_e4300/pd.aspx?refid=laptop_latitude_e4300&cs=555&s=biz)
... your laptop should have an optical drive.
> Installed Ubuntu on my Dell Lattitude E4300 ages ago, liked it, kept it.
Does this mean that you did a dist-upgrade from Ubuntu 9.04? Or did you do a clean install of 9.10? 
If you did a dist-upgrade, you may still have files from grub-legacy along with grub2 on your system. If so, then see this:
[https://wiki.ubuntu.com/Grub2#Error%2015%20-%20File%20not%20found](https://wiki.ubuntu.com/Grub2#Error%2015%20-%20File%20not%20found)
If this was a dist-upgrade, then if it were me, then I would cut my losses and do a clean install of 9.10. Dist-upgrades in Ubuntu tend to be a bit of a gamble. (Much of this seems to be affected by all the 3rd party repos that so many people seem to be compelled to add to their system from what I have seen). This is not the case here though.
If this was a clean install of 9.10, then I would burn a live CD and follow the links I gave in my last post.

---

### Post by Monroc on 2010-02-13
Woohoo and hurray...

I originally installed 8.10, and upgraded to 9.04 and later to 9.10. If this is not safe, I'm puzzled why it is presented as such?

I *can* boot from both CD and USB-flash, but... neither keyboard and mouse work.

Installing everything all over again would be incredibly annoying, as I've used a lot of time to customize the system. I'm hoping for a way to fix the boot-record - nothing is wrong with the system apart from that..

---

### Post by amsterdamharu on 2010-02-13
Ok so you got dsl on a usb assuming you used unetbootin and have syslinux on there now. That can boot ubuntu of your harddisk and in turn you can re install grub when ubuntu runs off your harddisk.

Boot DSL, mount your mount partition and copy vmlinuz and initrd (same versions) to the root of your usb.

Check your usb for syslinuc.conf and add the following men item

```

label 4
menu label ^4 : boot ubuntu recover
kernel vmlinuz-2.6.32-11-generic
append initrd=initrd.img-2.6.32-11-generic ro root=/dev/sda2 single

```

When you copy your kernel and initrd you can rename them to vmlinuz and initrd that would make the menu easier to make:

```

label 4
menu label ^4 : boot ubuntu recover
kernel vmlinuz
append initrd=initrd ro root=/dev/sda2 single

```

If it doesn't work you might have done something wrong with the syslinux.conf and need to post it here, please do not edit the file in windows.

---

### Post by tommcd on 2010-02-13
> **Monroc said:**
> 
I originally installed 8.10, and upgraded to 9.04 and later to 9.10. If this is not safe, I'm puzzled why it is presented as such?

It is not that upgrading is not safe. It is just that doing a dist-upgrade seems to cause a lot of problems for a lot of people. I always do clean installs myself.
> **Monroc said:**
> 
I *can* boot from both CD and USB-flash, but... neither keyboard and mouse work.
I don't know why that would be so. How did you ever manage to install  Ubuntu in the first place then?
> **Monroc said:**
> 
Installing everything all over again would be incredibly annoying, as I've used a lot of time to customize the system. I'm hoping for a way to fix the boot-record - nothing is wrong with the system apart from that..
I have seen a great many people say this. Understand that reinstalling Ubuntu becomes easier the more you do it. I could recreate my system as it is now in less than 90 minutes. You will have to weigh the time spent on solving this against the time spent on reinstalling Ubuntu. I know that this is not an ideal solution. 
You need to get grub2 back on the MBR of your computer somehow. This is the ideal solution. The links I gave discuss how to do it. If you can boot from a usb stick, then perhaps you can reinstall grub2 from that. I would think the procedure would be the same.

---

### Post by amsterdamharu on 2010-02-13
If you feel like messing about with the system (other than resizing partitions) you can make a backup and put it back in a lot less time that 90 minutes.

Assuming you're not messing with your home dir just your system. To back up from your DSL usb:

```

#from the root to backup
tar -cvpzf backup/backup.tar.gz --exclude=backup --exclude=home --exclude=lost+found --exclude=media --exclude=mnt  --exclude=sys . 
#To restore use: 
#from the root to restore
tar -xvpzf backup.tar.gz -C . 

```Don't forget to backup all your MBR's and partition tables, this is run from the usb of course.

```

#!/bin/bash
for hds in $(fdisk -l | grep -i '^Disk /' | awk -F' ' '{print $2}');
do
    hds=$(echo $hds | awk -F'/' '{print $3}')
    hds=$(echo $hds | awk -F':' '{print $1}')
    echo $hds
    dd if=/dev/$hds of=$hds.bin bs=512 count=1
done
for hds in $(fdisk -l | grep -i '^/dev/' | awk -F' ' '{print $1}');
do
    hds=$(echo $hds | awk -F'/' '{print $3}');
    dd if=/dev/$hds of=$hds.bin bs=512 count=1
done
exit

```

Restoring is a bit tricky here best make a backup in a temp dir first (these files are very small but very important), you can do this by running the script in a temp dir.
to restore mbr of sda you can:
dd if=sda.bin of=/dev/sda bs=512 count=1
**never do of= before if= I** read that can destroy all data on your hd but never tried it myself.

---

### Post by Monroc on 2010-02-13
**tommcd**
Thank you for bearing with me - I was a bit steamed. HOWEVER - I've decided to waste the system and go for a reinstall. I'll install an ext2/3-driver in Windows (And pray it doesn't break the system like I've experienced before) and back up my /home-dir. Then I can repartition my harddisk as well :)

**amsterdamharu**
Thank you for your suggestions. I think that I'll reinstall Ubuntu, set it up, and make a backup which I can roll back to. Those commands seem bearable to deal with - even for me :)

---

### Post by amsterdamharu on 2010-02-13
You could try booting ubuntu off the usb stick, that shouldn't be too hard to do. From there you can make a backup of your home as well. I mean with booting is the ubuntu that is on your harddisk not the live cd version (see post 6).

Good luck and hope everything works well.

Happy (Chinese) new year.

---

### Post by Monroc on 2010-02-13
The trouble with booting off of the DSL on the USB-stick, is that it doesn't recognize my harddisk. fdisk -l returns only /dev/sda1, which is the USB-stick itself. Am I correct to assume, that if it did recognize the harddisk, it would be listed as well?

---

### Post by amsterdamharu on 2010-02-13
Yes, I think so unless sda **is** your harddisk and dsl runs only from memory. I use tinycore that's a lot smaller than damn small and never had any trouble with it.

If you want I can give a little howto as to getting it on your usb and have persistent applications. Basically it involves getting it on usb and fiddling around with the syslinux.conf

Right now I will celebrate new year and be out most of all tomorrow and maybe the day after so it might take a while before there is time for me to do so.

---

### Post by tommcd on 2010-02-14
> **Monroc said:**
> **tommcd**
Thank you for bearing with me - I was a bit steamed. HOWEVER - I've decided to waste the system and go for a reinstall. 
I am not familiar with DSL. Does it use a root account? If so, then try running **fdisk -l** as root and see if it finds your hard drive.
You can find out what /dev/sda1 is by mounting it and looking around:
```

(As root, or sudo)
mount /dev/sda1 /mnt
cat /mnt/etc/lsb-release

```
If the output of < cat /mnt/etc/lsb-release > reports back Ubuntu 9.10, then /dev/sda1 is Ubuntu. If /dev/sda1 is Ubuntu, then just follow this procedure to reinstall grub2 that I linked to earlier:
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)
or this:
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Re-install_GRUB_from_Live_CD](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Re-install_GRUB_from_Live_CD)
I am not sure if this would work from DSL. It won't hurt to try it though.
BTW, How exactly did you manage to install Ubuntu in the first place if your keyboard and mouse do not work when booting from a live CD or usb stick? Are you using a KVM switch or anything like that? If so, then try it without the KVM.
You could also try booting with a Knoppix live CD. Knoppix should recognize your hard drive and get your keyboard and mouse working:
[http://www.knoppix.net/](http://www.knoppix.net/)
Or ... just cut your losses and reinstall if you can. If you do not have a seperate home partition then this would be a good time to create one. See this:
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

---

### Post by debivofek9 on 2011-01-13
> **Monroc said:**
> The trouble with booting off of the DSL on the USB-stick, is that it doesn't recognize my harddisk. fdisk -l returns only /dev/sda1, [[COLOR=#000000]which[/COLOR]](http://www.tekbar.net/lv/hackers-and-security/powerful-pc-security-shield.html) is the USB-stick itself. Am I correct to assume, that if it did recognize the harddisk, it would be listed as well?This is what I'm looking for, Thanks for your instruction! It's good for reference.

---


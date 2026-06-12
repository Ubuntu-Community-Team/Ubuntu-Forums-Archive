---
title: "[launchpad] bug &quot;mounting root filesystems&quot;"
date: 2006-07-03
forum: Installation &amp; Upgrades
---

### Post by ubuntu_demon on 2006-07-03
I've posted about this bug "booting stalls during mounting root filesystem"on my blog :
[http://ubuntudemon.wordpress.com](http://ubuntudemon.wordpress.com)

This thread contains links to possible fixes :
[http://www.ubuntuforums.org/showthread.php?t=187656](http://www.ubuntuforums.org/showthread.php?t=187656)

Currently it links to :
[http://www.ubuntuforums.org/showthread.php?t=197956](http://www.ubuntuforums.org/showthread.php?t=197956)
[http://www.ubuntuforums.org/showpost.php?p=1088366&postcount=11](http://www.ubuntuforums.org/showpost.php?p=1088366&postcount=11)
[http://www.ubuntuforums.org/showpost.php?p=1098541&postcount=41](http://www.ubuntuforums.org/showpost.php?p=1098541&postcount=41)
[http://www.ubuntuforums.org/showpost.php?p=1231460&postcount=62](http://www.ubuntuforums.org/showpost.php?p=1231460&postcount=62)
[http://ubuntuforums.org/showthread.php?t=212839](http://ubuntuforums.org/showthread.php?t=212839)

This is the big discussion thread where people post their problems :
[http://www.ubuntuforums.org/showthread.php?t=186115](http://www.ubuntuforums.org/showthread.php?t=186115)

Please post your tips and/or fixes here :
[http://www.ubuntuforums.org/showthread.php?t=187659](http://www.ubuntuforums.org/showthread.php?t=187659)

What happened in my case :
For me my /dev/hda became /dev/hde after upgrading. On a fresh install I could produce exactly the same results. To solve it I had to edit my /etc/fstab and /boot/grub/menu.1st accordingly. Each time a new kernel gets installed I have to edit my /boot/grub/menu.1st again and change /dev/hda for /dev/hde.

See for example a part of my /boot/grub/menu.1st :
```

title           Ubuntu, kernel 2.6.15-25-686
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.15-25-686 root=/dev/hde6 ro vga=0×31a
quiet splash
initrd          /boot/initrd.img-2.6.15-25-686
savedefault
boot

```

Mind the line :”root (hd0,5)”. So grub needs the (translated) parameter /dev/hda6 while the kernel needs it to be /dev/hde6.

Let's search on launchpad and report all related bugs to "booting stalls during mounting root filesystems" right here in this thread.

Then we can contact the devs about this problem and send them all this information.

I'll start :

Mount Root Files System Failed
[https://launchpad.net/distros/ubuntu/+source/initramfs-tools/+bug/47768](https://launchpad.net/distros/ubuntu/+source/initramfs-tools/+bug/47768)

Dapper Beta: Boot process stalls on "Mounting root filesystem..."
[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/36667](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/36667)
with some explanation here :
[http://www.ubuntuforums.org/showpost.php?p=1094841&postcount=104](http://www.ubuntuforums.org/showpost.php?p=1094841&postcount=104)

mounting root filesystem stuck
[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/50313](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/50313)
with some explanation here :
[http://www.ubuntuforums.org/showpost.php?p=1197657&postcount=147](http://www.ubuntuforums.org/showpost.php?p=1197657&postcount=147)

**edit :**

udev enumeration should use /sys/bus not /sys/devices
[https://launchpad.net/distros/ubuntu/+source/udev/+bug/6367](https://launchpad.net/distros/ubuntu/+source/udev/+bug/6367)

**The devs know about this bug and we might see a dapper-update someday.** No need for searching launchpad anymore. See my third post :
[http://www.ubuntuforums.org/showpost.php?p=1212264&postcount=3](http://www.ubuntuforums.org/showpost.php?p=1212264&postcount=3)

---

### Post by ubuntu_demon on 2006-07-04
A very important comment on my blog :

> **Edward Mendelson]
Oh, the devs know all about this, and knew all about it before Dapper was released. Here&#8217 said:**
> https://launchpad.net/distros/ubuntu/+source/udev/+bug/6367[/url]


Thank you very much for this information!

---

### Post by ubuntu_demon on 2006-07-04
from [https://launchpad.net/distros/ubuntu/+source/udev/+bug/6367](https://launchpad.net/distros/ubuntu/+source/udev/+bug/6367) :

[quote=Scott James Remnant]
........
........
We find devices by walking the /sys/class, /sys/block and /sys/devices trees.

Upstream udev has settled on, instead, walking /sys/class, /sys/block and /sys/bus

The change from /devices to /bus means that rather than seeing the IDE controller as a child of the PCI Bridge, and thus logically before the internal IDE controller, it would see the IDE controller as a member of the PCI bus that appears later.

I'm not sure only a couple of weeks away from release is the right time to make such a major change to our hardware enumeration though -- we'll get this fix in edgy anyway when we resync with the upstream udev and kernel versions.
........
........

Rewriting udevplug to enumerate devices differently, and doing wide-spread testing of that; which is what I'm currently in the process of doing for edgy.

........
........

Interestingly, upstream udev produces the same apparent bug that we have ... so any other distro is broken too.

........
........

I've also iterated that the fix has been around for some time now, and that it would go into edgy when it opened (it's already partially there, awaiting builds) -- and that if we have no adverse effects in edgy, it could be backported to either dapper-updates or at least dapper-proposed or dapper-backports.

.........
.........

You mis-understand the group of people that need to test the fix.

We don't need the people who are affected by this bug to test it, we need everyone who isn't affected by it to test it to make sure nothing else breaks.
[/quote]

So the devs know about this bug and we might see a dapper-update someday.

---

### Post by ubuntu_demon on 2006-07-14
**Everyone please test this general workaround :**

[https://launchpad.net/distros/ubuntu/+source/udev/+bug/6367/comments/69](https://launchpad.net/distros/ubuntu/+source/udev/+bug/6367/comments/69)

[quote=Paul Sladen]
For those still wondering; The workaround for this issue involves specifying the partition to boot from by ID, rather than the transient location:

  1. Boot a desktop/LiveCD.
  2. Run sudo /sbin/dumpe2fs /dev/sdX | grep UUID
  3. tell 'grub' or 'lilo' to boot with that ID:

     linux ... root=UUID=d4c51a2a-d93f-4dc1-8717-9c3cdb4d41ce

and also adjust this in:

  /boot/grub/menu.lst
[/quote]

Replace sdX for sda, sdb, sdc, sdd, hda,hdb,hdc,hdd or whatever gparted on the livecd tells you it is.

You can post results either on launchpad here :
[https://launchpad.net/distros/ubuntu/+source/udev/+bug/6367/](https://launchpad.net/distros/ubuntu/+source/udev/+bug/6367/)
Or in this thread :
[http://ubuntuforums.org/showthread.php?p=1257154](http://ubuntuforums.org/showthread.php?p=1257154)

---

### Post by KenF on 2006-07-20
In terms of the drive ordering, there was a known issue introduced in
kernel 2.6.17.  Here is Linus' comment and patch (to a makefile, not code) on the LKML:

[http://lkml.org/lkml/2005/12/3/192](http://lkml.org/lkml/2005/12/3/192)

KenF
P.S.  Does anyone know if the non-AMD64 bit people experiencing
this problem?

---

### Post by big_gie on 2006-07-27
I managed to workaround the &#8220;booting stalls during mounting root filesystem&#8221; bug with my Intel P4 EMT64 with a Asus P5LD2-VM DH motherboard ([http://www.asus.com/products4.aspx?l1=3&l2=11&l3=0&model=1146&modelmenu=1)](http://www.asus.com/products4.aspx?l1=3&l2=11&l3=0&model=1146&modelmenu=1)).

The problem was that the motherboard contains many disk controllers:
Intel ICH7 DH South Bridge:
1 x UltraDMA 100/66/33
4 x Serial ATA 3Gb/s, RAID0, RAID1, RAID5, RAID10
ITE IDE controler:
1x UltraDMA 133/100

The HD was on the &#8220;ITE IDE controler UltraDMA 133/100&#8243; and the DVD on the &#8220;Intel ICH7 DH South Bridge UltraDMA 100/66/33&#8243;.

Saddly, only the &#8220;Intel ICH7 DH South Bridge UltraDMA 100/66/33&#8243; seem to be linux bootable (Windows XP x64 boots corectly). So the LiveCD boots (from &#8220;Intel ICH7 DH South Bridge&#8221;, install, but when I shutdown, the machine &#8220;trys&#8221; to boot from &#8220;ITE IDE controler&#8221; but can&#8217;t.

The workaround I used was to install normally with the livecd, shutdown, switch cables between the HD and DVD, and then boot into linux&#8230;

Ouf&#8230;.

---

### Post by ubuntu_demon on 2006-07-27
You can follow the bug here :
[https://launchpad.net/distros/ubuntu/+source/udev/+bug/6367](https://launchpad.net/distros/ubuntu/+source/udev/+bug/6367)

If you want to test the UUID workaround look here :
[http://www.ubuntuforums.org/showthread.php?t=216039](http://www.ubuntuforums.org/showthread.php?t=216039)

We don't need to search launchpad anymore. This thread has become obsolete. I'll close it.

---

### Post by ubuntu_demon on 2006-08-22
Here are workarounds (which need testing) :
[http://ubuntuforums.org/showthread.php?p=1257154](http://ubuntuforums.org/showthread.php?p=1257154)
[https://launchpad.net/distros/ubuntu/+source/udev/+bug/6367/comments/83](https://launchpad.net/distros/ubuntu/+source/udev/+bug/6367/comments/83)

---


---
title: "can I make a boot floppy?"
date: 2007-02-12
forum: Installation &amp; Upgrades
---

### Post by Pollywoggy on 2007-02-12
Is it still possible to make a boot floppy using the mkboot command so that I can start the machine if say, initramfs corrupts the boot image on the hard drive?

This has happened to me twice since I installed Dapper on one machine and then upgraded to Edgy.   I now have a system that I installed from an Edgy CD so I did not have to do a dist-upgrade, but today when I did an upgrade from "universe" and "multiverse" I saw that initramfs was called and that it made new images, which I suspect will not work.  What might happen the next time I reboot will be that the boot will stop and leave me at an initramfs shell with an error message saying it can't get a tty.

That is what happened the first two times I installed Ubuntu and then upgraded.

Can I make a boot floppy and would it save me if the machine will not boot?

---

### Post by Herman on 2007-02-12
Hello Pollywoggy,
> Is it still possible to make a boot floppy using the mkboot command so that I can start the machine if say, initramfs corrupts the boot image on the hard drive? I haven't tried that, but thank you for the idea, it sounds very interesting. From what I have been able to learn from searching the forums, that command makes a LiLo floppy disk.  I have read (in some very old posts), that we can do that, (or at least we used to be able to), but we need to install LiLo first. 
There is no harm in installing LiLo, even if we already have Grub installed. I have had Grub installed to MBR, and I have subsequently installed Lilo through synaptic before, and installed it (LiLo) to the Ubuntu partition. (Simultaneous with Grub being in MBR). The two bootloaders co-habitate perfectly well. Here is the link to my new [LiLo Page]("http://users.bigpond.net.au/hermanzone/p4.html") in case you will find it any help.  Thank you for the suggestion, I'll try it too, and if successfull I'll add it to the web page.

You can easily make your own Grub floppy disk and have a lot of fun experimenting with it, here's the way I do it, 
[How to make your own personalized Grub Floppy Disk]("http://users.bigpond.net.au/hermanzone/p15.htm#grub_floppy_howto_make")
I am sure you can copy a kernel and an initrd.img to it and use them to boot with, I have done that with a  USBdisk before, and it should work just as well with a floppy disk. You just need to make up a menu entry with the appropriate commands in the floppy disk's menu.lst file to select the floppy disk's owm kernel and initrd.img files.

Another thing I tried for fun was to make a second copy of menu.lst on a floppy disk and call it menu.2nd, and another called menu3rd, and so on. 
Then you can make an entry in the floppy disk's menu.lst to 'configfile' the next menu, and then the next one. You can make each menu.lst have a different colored menu or splashimage.
You can have a lot of fun with a grub boot floppy disk because you know that whatever ideas you want to try out won't upset your hard disk installed grub.
Read my third sig link for ideas about how you can modify your menu.lst and try them out in your grub floppy. You will see examples of the 'config' command in that link.

I don't think either of these would really be necessary as an emergency disk though, because when we receive a kernel update, usually the old kernels remain in our system as well as in our grub menu. The new kernel entries are merely placed on top of them. So if you want to boot by your old kernel and initrd.img, all you really need to do is scroll down a few lines in your grub menu.

Have fun, 
Regards, Herman :)

PS, please post back here if you try it and have any information to share.

---

### Post by Pollywoggy on 2007-02-12
Thank you, Herman.

The reason I had some doubts about putting a boot image on a floppy is that kernels are rather large these days and I am not certain there is sufficient space on a floppy for all the boot data.  I recall that when I used Debian, I tried this two or three years ago and mkboot complained there was not enough disk space on the floppy for the image, but at the time, I am not sure that I was using an initrd.  I am using an initrd now.  I think there might be a way to put the image on a CD instead or perhaps onto a pen drive.

Thanks for the reply, I will have a look at the URL's you posted.

---

### Post by Pollywoggy on 2007-02-12
There is indeed a problem.

I installed lilo and when I ran liloconfig, it gave me this:


LILO, the LInux LOader, sets up your system to boot Linux directly
from your hard disk, without the need for a boot floppy.

    WARNING!
        Your /etc/fstab configuration file gives device UUID=cdeb130b-eaa3-43cb-8e07-5aaf04584527 as the root
        filesystem device. This doesn't look to me like an "ordinary" block
device. Either your fstab is broken and you should fix it, or you are
using hardware (such as a RAID array) which this simple configuration
program does not handle.

You should either repair the situation or hand-roll your own
/etc/lilo.conf configuration file; you can then run /usr/sbin/liloconfig
again to retry the configuration process.
Documentation for LILO can be found in /usr/share/doc/lilo/.

I do not know how to proceed other than to reinstall Ubuntu and then not upgrade anything from universe or multiverse but if I do that, I will have a not very useful system.

I am not using RAID, btw and I have seen this error when I Googled for this problem, but I have seen no fixes.
Users of Debian are having similar problems after upgrading initramfs.  I wonder if it is possible to downgrade the initramfs-tools package and solved this or if I could install yaird instead and if that would solve it.

I also do not recall seeing an upgrade of initramfs-tools, so the version in Edgy might be the problem.

---

### Post by Pollywoggy on 2007-02-12
Here is my fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb2
UUID=cdeb130b-eaa3-43cb-8e07-5aaf04584527 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb4
UUID=79432297-1f52-4333-a5d3-f317c922bc5b /home           ext3    defaults        0       2
# /dev/hdb1
UUID=6E4C7B3B4C7AFCE1 /media/hdb1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdb3
UUID=6aa30864-047f-4258-9797-09516c579360 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0


Is udev what is messing things up?

---

### Post by Herman on 2007-02-12
Pollywoggy, 
I would not worry about that, your /etc/fstab looks fine to me. The inclusion of the UUID numbers in our /etc/fstab is a fairly recent innovation, and I guess LiLo has not been updated to expect that.
All filesystems have always had UUID numbers, but the inclusion of them in /etc/fstab hasn't been done, ( or at least not well known), before until Edgy Eft was released..Here is a link I have written explaining a little about it, [About Edgy Eft's new /etc/fstab files with UUID filesystem ID added]("http://users.bigpond.net.au/hermanzone/p10.htm#Edgy_Efts_new_etcfstab_files_with")
Perhaps LiLo needs a little updating to keep up with the rest of the advancing technology.
Don't worry, there is nothing wrong with your system.

I haven't tried yet, when I do I will see if I can just ignore the error message and carry on regardless.

---

### Post by Pollywoggy on 2007-02-12
> **Herman said:**
> Pollywoggy, 
I would not worry about that, your /etc/fstab looks fine to me. The inclusion of the UUID numbers in our /etc/fstab is a fairly recent innovation, and I guess LiLo has not been updated to expect that.
All filesystems have always had UUID numbers, but the inclusion of them in /etc/fstab hasn't been done, ( or at least not well known), before until Edgy Eft was released..Here is a link I have written explaining a little about it, [About Edgy Eft's new /etc/fstab files with UUID filesystem ID added]("http://users.bigpond.net.au/hermanzone/p10.htm#Edgy_Efts_new_etcfstab_files_with")
Perhaps LiLo needs a little updating to keep up with the rest of the advancing technology.
Don't worry, there is nothing wrong with your system.

I haven't tried yet, when I do I will see if I can just ignore the error message and carry on regardless.

I cannot ignore the message.  I have seen this before with my two prior installations when the machine would not boot after some unknown package was upgraded.  I saw initramfs messages about writing new images and when I rebooted, I was left at a BusyBox console with a prompt that looked like this:

(initramfs)

also errors indicating a tty could not be found.  I also saw something about my fstab being corrupted.  If I reboot the machine, I am almost certain it will not boot and then I can't fix it except with a reinstall.

---

### Post by Pollywoggy on 2007-02-12
BTW initramfs was not itself upgraded.  I know that because I checked /var/cache/apt/archive/ and there are no initramfs packages there.
It was something else that was upgraded that corrupted something.

It is raining here, which means it is rather likely we will have power outages.  If my machine is rebooted, I won't be able to get back in unless I find this problem and fix it.

thanks for your help.

---

### Post by Pollywoggy on 2007-02-12
I found this:
[http://www.mail-archive.com/ubuntu-bugs%40lists.ubuntu.com/msg159468.html](http://www.mail-archive.com/ubuntu-bugs%40lists.ubuntu.com/msg159468.html)

I believe that person had the same problem I have.

I removed the UUID's and restored my old fstab.  liloconfig no longer complains.
Now on to make a boot disk, but I am still not sure this thing will reboot properly.

---

### Post by Pollywoggy on 2007-02-12
I removed the ID's from my fstab and rebooted and my machine boots normally, using the old format fstab.

I made a lilo boot floppy but I don't believe it will work because the output of the mkboot command indicated insufficient space on the disk.  That is what I expected would happen.

I used the procedure you describe for making GRUB floppies and I have a floppy which I am about to test.  If it does not work, I know I can still boot the system, at least for now.

thanks

---

### Post by Herman on 2007-02-14
Hello again Pollywoggy,
I followed similar procedures and have updated my [LiLo Page]("http://users.bigpond.net.au/hermanzone/p4.html") at the same time, so it took me  longer. Sorry to have been so slow, I'll bet you thought I had abandoned the project.
I have arrived at the same problem, the Ubuntu kernel is 1.6 Mb, and a normally formatted  floppy disk can hold 1.44 Mb.
It looks like we will have to give up and make a bootable USBdisk or CD-ROM instead. I don't know how to make those with LiLo yet, but I have started reading up on LiLo and experimenting with it, just for fun.

There is info printed on the side of my floppy disk box that says they can hold up to 2.0Mb unformatted. If we still want to use a floppy disk for this we might still bb able to, but we'll have to look into how to format floppy disks more efficiently. I think I remember reading somewhere how to get a little more space on a floppy disk but I can't remember where. When I see that again I'll bookmark it.

In the meantime what I do know is how to make a Grub CD-ROM, and a Grub USBdisk, here are the links,
[                                                          How to make your own personalized Grub CD-RW]("http://users.bigpond.net.au/hermanzone/p15.htm#HOW_TO_MAKE_A_GRUB_CD")

[How to add Grub to your USB thumb drive]("http://users.bigpond.net.au/hermanzone/p15.htm#How_to_add_Grub_to_your_USB_thumb_drive.")
I have added a Ubuntu kernel and initrd.img to a USBdisk already, and used it for booting with. It is just a matter of copying a kernel and matching initrd.img to the device and adding an extra entry to the menu.lst file with the correct path for the kernel and initrd.img in the USBdisk or floppy disk.
For example, here is what I have for a boot entry,
```
#This entry was added by Herman for an emergency
#uses kernel on (fd0).
title         Ubuntu, Kernel on USB disk (Emergency mode)
root        (hd0,0)
kernel      /vmlinuz-2.6.17-10-generic root=/dev/hda7 ro quiet splash
initrd       /initrd.img-2.6.17-10-generic
boot
``` It might seem a little strange to you that I have 'root (hd0,0)' there but that's what works, because the USBdisk becomes (hd0,0), or at least it seems to think it is. Anyway, that's what I had to do to get it to work for me with my computer.
My first hard disk needed to be addressed as (hd1) in the USB disk's menu.lst to make it boot, bumping my (hd1) to (hd2), so all the menu.lst entries had to be edited differently than usual.

If you decide to try making a CD-ROM, I found it best to use CD-RWs for that, so they can be erased and re-written. If you are like me, you might need to have two or three tries before you will get it working right. :)

"There is simply nothing more fun than messing about with bootloaders"
Have fun, Regards, Herman

---

### Post by Pollywoggy on 2007-02-14
I did make a GRUB boot floppy using your instructions and it does work.  Thanks for writing that.

I fixed my fstab, that is what Ubuntu was corrupting.  My machine boots normally, no fancy ID numbers in my fstab.

---

### Post by Herman on 2007-02-17
> I did make a GRUB boot floppy using your instructions and it does work.  Thanks for writing that. No prob's, glad to be of help.  >  I fixed my fstab, that is what Ubuntu was corrupting.  My machine boots normally, no fancy ID numbers in my fstab. Okay, a few other people are doing that too, it will probably make things simpler for the user for now, but just remember you did it. It's easy to reverse in case the developers are planning to do something special in the future that we don't understand yet. I see these UUID numbers beginning to appear in menu.lst files too, in places.

I have some news on the floppy disk challenge.
I happened across the page where I though I remembered reading how to format a 3.5-inch to hold 1440-KB, 1680-KB, or 1920-KB floppy, respectively. It's in [LINUX: Rute User's Tutorial and Exposition]("http://rute.2038bug.com/rute.html.gz"), and more specifically, in this section here, [19.3.4 Creating MS-DOS floppies]("http://rute.2038bug.com/node22.html.gz#SECTION002234000000000000000")
I'm not sure yet whether this will really mean we can fit a Ubuntu kernel in a floppy disk, until I get time to play with this some more.
I found out we have fdutils in Ubuntu already by searching for it in synaptic. > Linux floppy utilities
This package contains utilities for formatting extra capacity
disks, for automatic floppy disk mounting and unmounting, etc.

The package includes the following items:

  * superformat: formats high capacity disks of (up to 1992k
    for high density disks or up to 3984k for extra density
    disks)
  * fdmount: automatically mounts/unmounts disks when they are
    inserted/removed.
  * xdfcopy: formats, reads and writes OS/2's XDF disks.
  * MAKEFLOPPIES: creates the floppy devices in /dev
  * getfdprm: prints the current disk geometry (number of
    sectors, track and heads etc)
  * setfdprm: sets the current disk geometry
  * fdrawcmd: sends raw commands to the floppy driver
  * floppycontrol: configure the floppy driver
  * General documentation about the floppy driver

Note that these utilities do not work for USB floppy drives, because
there is no direct access to the floppy controller.

 Homepage: [http://www.tux.org/pub/knaff/fdutils/](http://www.tux.org/pub/knaff/fdutils/)Wow! Up to 3984K on an extra high density floppy disk? I wonder how much those cost (if I can afford one), and where they might be for sale. All the floppies I have been able to buy lately are very low quality and have about a 50% success rate even for regular 1440K use. (Only every second one is usable, I thrown half in the rubbish bin).  The box claims 'high density' and '100% error free', so it must be my computer that's no good I guess, (my floppy disk drive might have dust in it, but it's strange that once I find a floppy disk that works, the same one will work for quite a while, but when I get a 'dud', it's a 'dud' for ever.
That's all for now,
Regards, Herman :)

---


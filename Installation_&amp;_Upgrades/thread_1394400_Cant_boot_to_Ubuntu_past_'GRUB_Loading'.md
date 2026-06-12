---
title: "Cant boot to Ubuntu past 'GRUB Loading'"
date: 2010-01-30
forum: Installation &amp; Upgrades
---

### Post by green0eggs on 2010-01-30
Hello forum.
I've just bought a new [laptop (with no installed OS)]("http://www.novatech.co.uk/novatech/laptop/range/x16hd.html") and have (excitedly) burned a live cd for Karmic Koala 64bit: several people on the [laptop manufacturer forums]("http://forum.novatech.co.uk/showthread.php?t=16016") have got working with this particular laptop.

The live session works fine but when I install and then reboot I get 'GRUB Loading' with a flashing underscore and nothing else happens.

I've found [this thread]("http://ubuntuforums.org/showthread.php?t=1307042") and [this bug report]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941") and have tried [reinstalling GRUB]("http://grub.enbug.org/Grub2LiveCdInstallGuide") to no avail.

I also have a live cd for 9.04 which I've tried to install and get a the same problem only now the message is 'GRUB Loading stage1.5' So I don't think it's a problem with the version of GRUB as described in the bug report thread.

[I read something else]("http://www.linux.com/community/forums?func=view&catid=18&id=4255") that said it could be a problem with the mbr being in some way geared towards Windows but I'm not sure. I tried following those instructions but nothing happened and then I just got the same error again.

Any help would be greatly received since obviously I'm pretty desperate to get my spangly (and expensive) new machine to work.

***Edit:** I also have a [thread at the manufacturers' forums]("http://forum.novatech.co.uk/showthread.php?p=247001#post247001"). But we're at a loss there too.*

---

### Post by Herman on 2010-01-30
You can download a Super Grub Disk with GRUB2 in it from Super Grub Disk - [Super Grub Disk]("http://www.supergrubdisk.org/index.php?pid=5"). 
Look for  the 1.21 SG2D Cdrom in one of the mirror sites. 
The one based on GRUB2 is called  sgd_cdrom_1.21.iso.gz and the last time I checked it was the latest.
If there's a more recent one, then get the most up to date version of Super Grub Disk.
Extract or unzip it and burn to a CD, or create your USB or floppy disc or whatever, according to what kind of file you downloaded, and boot your computer with it.

---

### Post by Herman on 2010-01-30
When your computer boots up, make sure you get some updates for it before you reboot and if you're lucky there might be something in the updates that might fix your problem.

Your system will probably offer you updates within the first few minutes by itself. 
If it doesn't, open a terminal and run 'sudo apt-get update'.
```
sudo apt-get update
```
Then after that's finished, run 'sudo apt-get upgrade'.
```
sudo apt-get upgrade
```

You should also try re-installing GRUB to MBR with '[FONT=monospace]sudo grub-install /dev/sda'.
[/FONT]```
sudo grub-install /dev/sda
```
The grub-install command will install a small code for GRUB in the hard disk's MBR, followed by some code in the first track of your hard disk, and also refresh the GRUB files inside your /boot directory in your Ubuntu installation, so it should fix your GRUB almost no matter what may have been wrong with it.

---

### Post by green0eggs on 2010-01-30
Thanks for the advice. 
I did attempt to reinstall GRUB from the live cds using [these instructions as well]("http://ubuntuforums.org/showthread.php?t=224351&") as the ones I linked to previously and the command ```
find /boot/grub/stage1
``` found no errors so I don't think it's a problem with the version. It seems to be installed in the right place and everything.

Cheers though
I'll give Super Grub a try later if nothing else works.

---

### Post by green0eggs on 2010-01-30
> **Herman said:**
> You can download a Super Grub Disk with GRUB2 in it from Super Grub Disk - [Super Grub Disk]("http://www.supergrubdisk.org/index.php?pid=5"). 
Look for  the 1.21 SG2D Cdrom in one of the mirror sites. 
The one based on GRUB2 is called  sgd_cdrom_1.21.iso.gz and the last time I checked it was the latest.

Yep, It's the latest: I downloaded the iso and burned and booted with it in the laptop and all I get is a flashing underscore??

---

### Post by Herman on 2010-01-30
Thank you.

The isolinux boot loader booted your Live CD.
Your Ubuntu Live CD booted and ran okay and you were able to install Ubuntu so it seems as if Linux works okay with your laptop's hardware.

Grub Legacy doesn't seem to be working in your hard disk. 
GRUB2 doesn't seem to be working from a LiveCD. 
We don't know the reason why not yet,  but the fact that the same thing happened from the Live CD as well as your hard disk seems to imply that there's something about some part of your computer's hardware that isn't compatible with GRUB. 
It's not likely to be your MBR or your GRUB files since the Super GRUB2 Disc would have bypassed all of those if it had loaded, but GRUB2 in the Super Grub Disc didn't even load properly. Possibly something in your computer's BIOS, but I'm only guessing. That's quite unusual if it's true.

Can we try LiLo boot loader instead to see if that one will work?
Try the following how-to, [Install Lilo from a Linux Live CD]("http://members.iinet.net.au/%7Eherman546/p4.html#Install_Lilo_from_a_Linux_LiveCD")

---

### Post by green0eggs on 2010-01-31
(Giving Lilo a go)
I'm in a livecd session (connected to the internet ok)

And am following the [instructions]("http://members.iinet.net.au/~herman546/p4.html#Install_Lilo_from_a_Linux_LiveCD")... I've checked the position of the boot flag and modified /etc/fstab as instructed. I'm now chroot and when I try to install lilo I get the message:
```
Package lilo is not available, but it is referred to by another package.
This may mean that the package is missing, has been obsoleted, or is only available from another source
E: Package lilo has no installation candidate
```
Now I checked in the GUI Synaptic Package manager and searched for... and found!?! the Lilo package.

Confused.

Er.. so I'm not sure how to proceed

---

### Post by Herman on 2010-01-31
LiLo should be available, I can get it in my Karmic installation and even in my Lynx.

Maybe try running sudo apt-get update first and then try to apt-get install lilo again.

If it still doesn't work try enabling more repositories, (although that shouldn't be needed), then run sudo apt-get update and sudo apt-get install lilo again.

EDIT: Also, check to make sure your computer is connected to the internet.

---

### Post by green0eggs on 2010-01-31
> **Herman said:**
> 
Maybe try running sudo apt-get update first and then try to apt-get install lilo again.

So apt-get update did something (I'd say it worked but there was a load of text and scrolling.

> **Herman said:**
> 
 try enabling more repositories, (although that shouldn't be needed), then run sudo apt-get update and sudo apt-get install lilo again.


I re-chroot-ed into the installed ubuntu and same message as above. I tried to edit my sources.list in the chroot mode which didn't work, then I opened a fresh terminal and edited the sources.list file for presumably the live cd session os. I enabled both universe and multiverse then back to chroot and apt-get install lilo gives the same unavailability message as above.

> **Herman said:**
> 
EDIT: Also, check to make sure your computer is connected to the internet.
Absodefinalutely. I'm writing this message from the live session itself.

---

### Post by Herman on 2010-01-31
Okay, I tried this myself and I found out that networking is not working inside the chroot. :oops:

Sorry about that, the how-to was tested at the time it was written but either I missed that problem at the time or things have changed since Ubuntu Dapper Drake.

I looked up **[how to chroot, simple and fast]("http://ubuntuforums.org/showthread.php?t=1156240"), **by taavikko, and we need to add another line to our chroot commands to get networking inside the chroot.
```
cp /etc/resolv.conf /mount/point/etc/resolv.conf
```Please refer to this link and chroot according to taavikko's insrtuctions and you should find that it works, it worked for me, [B][how to chroot, simple and fast]("http://ubuntuforums.org/showthread.php?t=1156240") - Ubuntu Web Forums.
[/B]

---

### Post by green0eggs on 2010-01-31
> **Herman said:**
> we need to add another line to our chroot commands to get networking inside the chroot.
```
cp /etc/resolv.conf /mount/point/etc/resolv.conf
```

...chroot according to taavikko's insrtuctions [B][how to chroot, simple and fast]("http://ubuntuforums.org/showthread.php?t=1156240") - Ubuntu Web Forums.
[/B]

Hey, thanks for the tip. So I managed to install lilo... here's the list of commands I entered: 
```
ubuntu@ubuntu:~$ sudo mkdir /mnt/ubuntu
ubuntu@ubuntu:~$ sudo mount -t ext4 /dev/sda1 /mnt/ubuntu
ubuntu@ubuntu:~$ sudo cp /mnt/ubuntu/etc/fstab /mnt/ubuntu/etc/fstab.backup
ubuntu@ubuntu:~$ gksudo gedit /mnt/ubuntu/etc/fstab
ubuntu@ubuntu:~$ sudo mount -o bind /proc /mnt/ubuntu/proc
ubuntu@ubuntu:~$ sudo mount -o bind /dev/ /mnt/ubuntu/dev
ubuntu@ubuntu:~$ sudo mount -o bind /sys/ /mnt/ubuntu/sys
ubuntu@ubuntu:~$ sudo cp /etc/resolv.conf /mnt/ubuntu/etc/resolv.conf
ubuntu@ubuntu:~$ sudo chroot /mnt/ubuntu /bin/bash
root@ubuntu:/# apt-get update
<Lots of stuff>
root@ubuntu:/# apt-get install lilo
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  mbr
Suggested packages:
  lilo-doc
The following NEW packages will be installed:
  lilo mbr
0 upgraded, 2 newly installed, 0 to remove and 274 not upgraded.
Need to get 407kB of archives.
After this operation, 1307kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://gb.archive.ubuntu.com jaunty/main mbr 1.1.10-2 [23.0kB]
Get:2 http://gb.archive.ubuntu.com jaunty/main lilo 1:22.8-7ubuntu1 [384kB]
Fetched 407kB in 0s (435kB/s)
Preconfiguring packages ...
Can not write log, openpty() failed (/dev/pts not mounted?)
Selecting previously deselected package mbr.
(Reading database ... 101998 files and directories currently installed.)
Unpacking mbr (from .../archives/mbr_1.1.10-2_i386.deb) ...
Selecting previously deselected package lilo.
Unpacking lilo (from .../lilo_1%3a22.8-7ubuntu1_i386.deb) ...
Processing triggers for man-db ...
Can not write log, openpty() failed (/dev/pts not mounted?)
Setting up mbr (1.1.10-2) ...
Setting up lilo (1:22.8-7ubuntu1) ...

WARNING: kernel & initrd not found in the root directory (/vmlinuz & /initrd.img)
WARNING: Do NOT reboot or LILO may fail to boot if your kernel+initrd is large.
WARNING: Please read /usr/share/doc/lilo/README.Debian

```

Then running liloconfig on the advice of a blue terminal:
```

root@ubuntu:/# liloconfig

```
Returned this message:```

WARNING!                                                                  &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474; Your /etc/fstab configuration file gives device /dev/hda1 as the root     &#9474; 
 &#9474; filesystem device. This doesn't look to me like an "ordinary" block       &#9474; 
 &#9474; device. Either your fstab is broken and you should fix it, or you are     &#9474; 
 &#9474; using hardware (such as a RAID array) which this simple configuration     &#9474; 
 &#9474; program does not handle.                                                  &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474; You should either repair the situation or hand-roll your own              &#9474; 
 &#9474; /etc/lilo.conf configuration file; you can then run /usr/sbin/liloconfig  &#9474; 
 &#9474; again to retry the configuration process. Documentation for LILO can be   &#9474; 
 &#9474; found in /usr/share/doc/lilo/.   


```
...so I opened a new terminal and edited the fstab file changing hda1 back to sda1 then in the old terminal, retrying:
```

root@ubuntu:/# liloconfig

```

returned:

```

&#9474; Booting from hard disk.                                                   &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474; You must do three things to make the Linux system boot from the hard      &#9474; 
 &#9474; disk. Install a partition boot record, install a master boot record, and  &#9474; 
 &#9474; set the partition active. You'll be asked to perform each of these        &#9474; 
 &#9474; tasks. You may skip any or all of them, and perform them manually later   &#9474; 
 &#9474; on.                                                                       &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474; This will result in Linux being booted by default from the hard disk.     &#9474; 
 &#9474; If your setup is complicated or unusual you should consider writing your  &#9474; 
 &#9474; own customised /etc/lilo.conf. To do this you should exit this            &#9474; 
 &#9474; configuration program and refer to the comprehensive lilo documentation,  &#9474; 
 &#9474; which can be found in /usr/share/doc/lilo/.

```

I entered 'y' and followed the prompts and what have you. And installed told lilo to sort out my mbr please, thank you and boot from sda1.

Now, as I write this my computer has just BOOTED to the installed OS... 

...BUT

I was looking at a screen with a text message (I'm sorry I forgot what the text said... I'll make a note of it when I try again tomorrow) and an ever growing stream of '............' for maybe 5-10 minutes and 6 or 7 spans of the screen in dots before anything happened (I'd resigned myself to thinking that this too had failed).

Is lilo usually this slow? Probably not... I'm guessing that the problem (whatever it is) that my machine has with GRUB is what causes the massively long wait for lilo.

--By the way, my most recent install is 9.04 (and thus GRUB 1.5) which gave a similar error.

***Edit**: I get a splash screen that says DEBIAN with a picture of a coffee, then some flickering and:*
```
Loading Lin_2.6.28img0.....................
```

---

### Post by Herman on 2010-02-01
We're making progress, I wish we could have fixed it by now, but sometimes we have to work for things and it seems like this is one of those times. 

LiLo probably would be a little bit slower than GRUB, especially the newest GRUB.
Five or ten minutes does seem like quite a long time, especially for a modern new computer like yours.

Maybe it will boot if you keep waiting for it long enough.
At least now we know the kernel started to boot. 

If it still doesn't boot you may be able to see what went wrong if you boot your Live CD again, mount your hard disk install and take a look inside your /var/log directory.
The /var/log/dmesg text file may contain some information and also the /var/log/kern.log might shed some light on what it's stopping at.
It might help us or it might only confuse us more, because it will be in a language that only a kernel developer can really understand. Some of might be plain enough to give us a clue I'm hoping. If you feel like posting some of it probably only the last 20 or 30 lines or less will do, unless there's something interesting further up, those files are quite long. 

I'm hoping it will boot for you though. :p

---

### Post by Herman on 2010-02-01
> **OS Compliance**
Microsoft Windows 7 32Bit & 64Bit, Microsoft Windows Vista 32Bit & 64Bit, Microsoft Windows XP 32Bit SP2 Only
:-k Hmmm, I was just perusing your system specs once again and right now I'm thinking maybe if it still doesn't work try an i386, (32bit) Ubuntu installation and see if that will work any better. It doesn't seem logical that it will make any difference since the Live CD booted and ran okay. Generally speaking though, the i386 Ubuntu will run on a lot more computers than the amd64 Ubuntu. I use the amd64 a lot too, but I have read that there's probably no real advantage unless we have more than 4 GB of RAM installed. Maybe the i386 Ubuntu will be worth a try if you still have problems with the 64bit.

---

### Post by green0eggs on 2010-02-01
> **Herman said:**
> 
LiLo probably would be a little bit slower than GRUB, especially the newest GRUB.
Five or ten minutes does seem like quite a long time, especially for a modern new computer like yours.

Maybe it will boot if you keep waiting for it long enough.
At least now we know the kernel started to boot. 

Sorry if I've been unclear: it *will* boot if I wait long enough. I can get into the installed version of ubuntu (9.04 32-bit at the moment).

But during the boot, the "Loading Lin_2.6.28img0" message stays up for a VERY long time defiantly not due to struggling hardware (it's silent when this happens: no hd noise or anything) and the fact that I have a screen full of "...'s" makes me think that whatever makes GRUB hang forever is preventing this Lin_2.6*** thingy from loading before seeming to finally let it load.

> **Herman said:**
> 
The /var/log/dmesg text file may contain some information and also the /var/log/kern.log might shed some light on what it's stopping at.
...
If you feel like posting some of it probably only the last 20 or 30 lines or less will do
The last 20 lines of dmesg seem to be about video/bluetooth devices being turned on etc so I've chopped out chunks that seem to be about booting (i.e. have the word 'boot'). Although I'll admit it reads pretty much like computer vomit to me. Let me know if I've cut off a bit that looks like it might be useful.

> **Herman said:**
> try an i386, (32bit) Ubuntu installation and see if that will work any better.
So the vers. 9.10 that I've been trying is the 64bit amd version and hangs at 'GRUB Loading'. The vers. 9.04 is 32bit and i386 which is from the same livecd as my current (old) machine has installed from. So I know there are no errors on the cd: it hangs at 'GRUB Loading1.5'. 

--> Following your instructions to install lilo + the 9.04 version is how I'm set up now.

[The chap who was helping me in the manufacturer forums]("http://forum.novatech.co.uk/showthread.php?p=247654#post247654"): who has the same model (but fitted with a different brand hd) and managed to install 9.10 straight-from-the-box has been unable to find any insightful BIOS settings.

Thank you for all your patience and persistence by the way!

---

### Post by Herman on 2010-02-02
Thanks green0eggs, I'll take a close look at those logs as soon as I get time.
I'm glad it's at least booting for you.
Maybe things will improve after a few updates.
Also, try taking a look though your BIOS settings and make sure everything in there is okay.

What make and model is your hard disk again?

---

### Post by green0eggs on 2010-02-03
> **Herman said:**
> 
I'm glad it's at least booting for you.

Yeah, I was pretty pleased. But it's not really useably fast... maybe I'm just impatient.

> **Herman said:**
> 
Also, try taking a look though your BIOS settings and make sure everything in there is okay.

Have been [comparing BIOS settings]("http://forum.novatech.co.uk/showpost.php?p=247863&postcount=17") with a working ubuntu install of the same model and that seems to be a dead end, since his works fine even on default settings.

> **Herman said:**
> 
What make and model is your hard disk again?
The entry in boot order is:
```
2: IDE HDD: SAMSUNG HM321HI-(PM)
```
...which I think lives [here]("http://www.samsung.com/global/business/hdd/productmodel.do?group=72&type=62&subtype=67&model_cd=448&tab=fea&ppmi=1159#"). (Although I've just this minute noticed that that link is for a slightly different model number, which I probably copied down wrong from the BIOS).

I've downloaded the 32-bit version of 9.10 and I'll give that a whirl when I get a blank CD. Probably tomorrow.

..And I've had Kernel switches recommended as a possibility. Which I'll have to read up on then give a try.

---

### Post by Herman on 2010-02-03
> Have been [comparing BIOS settings]("http://forum.novatech.co.uk/showpost.php?p=247863&postcount=17") with a working ubuntu install of the same model and that seems to be a dead end, since his works fine even on default settings. What about the BIOS versions?

Neither GRUB2 nor your Linux kernel seem to get along too well with the BIOS you have now. I took at look at your logs and although I'm not a kernel developer and can't really make much sense of them, I do seem to get the general impression your problems could have something to do with your BIOS, but I'm not sure, it's just a guess really.

The same motherboards can have different BIOS versions and you can flash your BIOS with some other BIOS version, normally there are a few available for free download at the motherboard manufacturer's website.
This is not necessarily part of your problem though, just an idea, but it might be something to investigate.

I have even read of BIOSes in some new computers being coded deliberately to prevent Linux from being able to boot in that machine. I have no idea why manufacturers would do that, but it's conceivable.
Or it may simply be a buggy BIOS. Again, I'm only trying to guess, I'm not sure really.

EDIT: You tube link: [*Richard STALLMAN* vs locked *BIOS* & DAVDSI]("http://www.youtube.com/watch?v=vSH_kKOXMs4")

Regardsd, Herman :)

---

### Post by green0eggs on 2010-02-13
> **Herman said:**
> What about the BIOS versions?

I've asked him but no response just yet.

The BIOS is [Phoenix SecureCore]("http://www.phoenix.com/oem-odm/technical-support/downloads/securecore-1") and there's not a lot of information that I can find nor anything I could download and flash the existing BIOS.

---

### Post by adrian15 on 2010-03-02
> **green0eggs said:**
> 
The live session works fine but when I install and then reboot I get 'GRUB Loading' with a flashing underscore and nothing else happens.


I recommend you to do a manual installation and setup a 500 MB /boot partition. Herman might help you with more specific instructions on how to do that.

I bet that trick will fix your problem (or maybe not but it is worth a try ;)).

adrian15

---

### Post by RJARRRPCGP on 2010-03-02
The HDD likely is on its last leg. (because of the boot taking as long as 5 minutes!)

---

### Post by green0eggs on 2010-03-04
> **RJARRRPCGP said:**
> The HDD likely is on its last leg. (because of the boot taking as long as 5 minutes!)

I managed to take it back. 

Before I returned, the manufacturers' sent it to tech support and they tried several tests/fixes nothing managed to fix GRUB and there was nothing wrong with the HD.

But yeah, it's all academic now as I no longer have the machine.

---


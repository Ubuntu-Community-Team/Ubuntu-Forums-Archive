---
title: "GRUB changed version how get orig version back"
date: 2015-12-28
forum: Installation &amp; Upgrades
---

### Post by Kris_M on 2015-12-28
New clean install a week ago.
14.04.3 has been running fine for a week as dual boot with win7.  It is what I use.

booted to Boot-Repair to check it out and apparently pressed the wrong button.  I had to play with grub customizer for a bit and all is well, but I notice that I now have 
GRUB  2.02~beta2-9ubuntu1.6

Don't know what I had before.  How do I get the current default.
have [URL="http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd"]
http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd[/URL]
should I do it?

Thanks!

EDIT:
I tried
sudo grub-install /dev/sda
sudo update-grub
but still same GRUB version.

What version do other 14.04.3 folks have?  I thought 2-22 was the current...

---

### Post by matt_symes on 2015-12-28
Hi

Chrooting into my 14.04 install gives

```

matthew-xu-16-04:/ % lsb_release -d && dpkg -l | grep grub
Description:    Ubuntu 14.04.3 LTS
ii  grub-common                                                 2.02~beta2-9ubuntu1.6                      amd64        GRand Unified Bootloader (common files)
ii  grub-gfxpayload-lists                                       0.6                                        amd64        GRUB gfxpayload blacklist
ii  grub-pc                                                     2.02~beta2-9ubuntu1.6                      amd64        GRand Unified Bootloader, version 2 (PC/BIOS version)
ii  grub-pc-bin                                                 2.02~beta2-9ubuntu1.6                      amd64        GRand Unified Bootloader, version 2 (PC/BIOS binaries)
ii  grub2                                                       2.02~beta2-9ubuntu1.6                      amd64        GRand Unified Bootloader, version 2 (dummy package)
ii  grub2-common                                                2.02~beta2-9ubuntu1.6                      amd64        GRand Unified Bootloader (common files for version 2)
matthew-xu-16-04:/ %
```

If you're using grub-pc then it looks like you're fine with that version.

You can use

```
apt-cache policy <package_name>
```

to get the installed package and the candidate version you may install from your sources.

Kind regards

---

### Post by grahammechanical on 2015-12-28
I am using xenial xerus (16.04 development version) and it has grub 2.02~beta2-33.

So, why do you think that 2.22 is the current version? Is grub doing what it is supposed to do? So, what is the problem? You most likely have the current default Grub for 14.04.3. It may be upgraded in the future.

---

### Post by Kris_M on 2015-12-28
Super! Thanks!!!

thanks for the apt-cache command!!!

> **grahammechanical said:**
> I am using xenial xerus (16.04 development version) and it has grub 2.02~beta2-33.

So, why do you think that 2.22 is the current version? Is grub doing what it is supposed to do? So, what is the problem? You most likely have the current default Grub for 14.04.3. It may be upgraded in the future.

Just saw your post. Thanks. I knew that Boot-Repair had done something because the bootup menu had changed - I was looking at "lubuntu" and windows was gone, so I -->assumed<-- it had changed the program, especially because I "didn't think Ubuntu would be running a beta" LOL.  However it correctly booted into 14.04.3 Unity.  In my subsequent googling I realized that idea (about betas) was wrong, but saw the number 22 a few times,though not in relation to 14.04.3,  So I thought I'd better ask.  Everything was running perfectly and "grub customizer" quickly had the menu back in order, so apparently all it changed was the cfg.  I was lucky!

I was playing with Boot-Repair on a stick(usb) only because I wanted an out in case I actually mangled my MBR - in windows I didn't worry about that because I had things like Acronis trueimage and easeus backing it up every time. (I always try to prepare for catastrophic (disk) failure).  Since I spent the last few days almost totally on 14.04.3(no windows), I thought It would be nice to look in to things like that.  I still don't have a backup of my MBR via Linux (and don't know yet how to get one) though it looked like B-R could pretty much re-create one.  It would be nice to have one tied to my clonezilla backup images but I don't think C-Z has that capability.  GPARTED might help in that, too... (I realize now that when I was over at MicroCenter yesterday getting 4 usb3 flash drives, I should have gotten 8! LOL)

So, thanks for looking in! - In spite of myself, I think I am okay!  I had run 16.04 a bunch of times as a live but found I couldn't play a video in a browser tab (my only "problem" with 14.04.3 was sound cutouts every 15-30 seconds, which I finally got rid of (notice I didn't say fixed!) ) so I wanted to check that on 16.04 .  Alpha1 is coming out in a few days, I think, so I'll try again with that.  If it doesn't work then I'll start a thread in dev and maybe wind up having to learn how to post a bug via Launchpad. Or realize what I'm doing wrong!!! :D

Thanks!

---

### Post by oldfred on 2015-12-29
We rarely suggest backing up a MBR. 
It always has been relatively easy to mount install partition and reinstall grub to MBR with live installer. Boot-Repair also makes it very easy. Same with Windows fixMBR or Boot-Repair can add a generic Windows type boot loader.
But what is important is to have a current version repair disk or installer that can load a repair console for the current installed version of every operating system you have.

---

### Post by Kris_M on 2015-12-29
> **oldfred said:**
> We rarely suggest backing up a MBR. 
It always has been relatively easy to mount install partition and reinstall grub to MBR with live installer. Boot-Repair also makes it very easy. Same with Windows fixMBR or Boot-Repair can add a generic Windows type boot loader.
But what is important is to have a current version repair disk or installer that can load a repair console for the current installed version of every operating system you have.

Yes, because MBRs rarely actually go, unless the whole spindle goes in which case the backup MBR is worthless. It's good to hear you second Boot-Repair!  It seemed to have a lot of good options while I was playing with it. Is there anything else I should have on hand?

But as to "current version", I am assuming that the versions of things like clonezilla, gparted, and boot-repair are, in fact, the latest, though my only assurance is to get it from a site that looks like it is, or is close to the source.  SourceForge is good... But updating (getting a more recent iso) frequently, is, I agree, very important.  For win I have a bunch of CDs and sticks of various age for stand-alone work. I tend to stay current with both Acronis and Easus, and since I am not uefi (win7) I am running a relatively crude system - most stand-alone stuff works.  So I figure I am likely to have something that will work in any event.  For Linux I know only what I have found in the past week or so - my past work was maybe 3 years ago and not debian. Much has changed!  I backup with Backups of course and Clonezilla (partition to image)(needed to use it maybe a dozen times so far)(love it!).  But I am already thinking toward a triple boot with 16.04.1 or something when that comes out, so I can parallel process with 14.04.3 , so trying to think of what I need to protect myself so I don't have to re-invent the wheel too often - LOL. So any recommendations you have, PLEASE fire away!!!

I've got about 7 partitions on a 250GB SSD (most NTFS) that is perhaps a year old. Sammy 840 EVO. A 1T HD for all those huge windows backups, big ISOs, etc Handy when I was testing win10 in a VM. GA-Z87N-WIFI (wifi card removed) 650 GTX Ti.  1KW UPS.

Thanks!

---

### Post by oldfred on 2015-12-29
I stopped burning multiple CD/DVD as repair tools. And learned how to boot ISO directly from grub with its loopmount command.
So I create flash drives with several tools. I typically have the newest gparted ISO from gparted, SuperGrub, parted magic, Knoppix, several Ubuntu versions. I want to create one using rEFInd also, but have not tried it yet.
I also have SSD & 1TB HDD. So I create smaller partitions on each drive just for ISO. I do not have Windows but then have multiple installs of Ubuntu on both drives as well a full install (wtih more ISO) on flash drive. My real problem is MicroCenter is only a few miles away and behind counter are flash drives. And every time I go they are lower in cost or both lower in cost & next size up. Now I only buy the USB3 versions as they also work on USB2 and are a bit faster. I do now try to limit my trips to MicroCenter as I now have trouble keeping track of which are backups & which are repair tools.

---

### Post by Kris_M on 2015-12-29
Huge thanks!!!!!!!  Many ideas!!!  Much googling! much still to do!!!

For others reading this
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
I learned to put ISOs in /boot/grml and run update grub to have it nicely put these ISOs into the GRUB menu.  This worked with UBUNTU 16.04, though not with CloneZilla.  I remember reading a sentence somewhere that UBUNTU ISOs were specially made to use this feature.  I will use this for testing/installing builds in the future. Thanks!!!

I tried putting SuperGrub2 on a stick but no luck booting from it so I'll have to play with that more. Also yet to try parted magic, and Knoppix, so, much yet to try!  I did grab the deb for rEFInd but yet to install it (yes I backed up!)(I know it's a beta)(but I want to play!)

I also realized I was one BIOS back so flashed F6 to my mobo last night. - supposed to help K cpus (I'm i5-4670K). No change that I  can see so far.

Multiple installs on BOTH drives...  hmmmm  and a full install on a stick! more hmmmmmm  Both interesting ideas, especially as I wean myself off windows(and thus the need for frequent 35gbx2 backups).

Yes to USB3 - MUCH faster!!!  It would be hard having a MicroCenter so close - it at least takes me close to an hour to get there (public transportation and all) so fortunately that helps with the restraint.  I tend to get 8gb USB3 ($4.49) - dirt cheap!  Was reading something on the supergrub2 site about multibooting from a stick, so that idea is batting around but only saw installers that had to be run under win so will look at it more. Maybe should be getting 16gb sticks... esp to full install...

Okay back to the supergrub2 problem - I used tuxboot to write it to the stick.  Maybe the ISO I got is bad.  

Off to play!!!

Thanks again!!!!!!!!!

---


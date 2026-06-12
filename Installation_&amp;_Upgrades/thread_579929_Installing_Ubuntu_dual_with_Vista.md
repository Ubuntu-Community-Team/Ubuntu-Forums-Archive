---
title: "Installing Ubuntu dual with Vista"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by dc_jt on 2007-10-18
Hi

I had trouble installing the old version of Ubuntu with Vista, I think because my hard drive is 2 x 250GB so it was not partitioning properly. Im not entirely sure as I never actually got round the problem.

However I really want to install Ubuntu and have been waiting for this release to try again. Does anyone know if it is any better than the last one in terms of dual booting with Vista?

Thanks

---

### Post by Dead_$partan on 2007-10-18
I have been dual booting Linux and windows since 5.04, and all of them have run fine.  7.04 is what I have just now and it dual boots perfectly fine with Vista.  Just install vista 1st, create a partition say 50% of your overall space(or whatever you want) and when it comes to installing Gutsy just create another partiton and install gutsy there and youre done.

---

### Post by dc_jt on 2007-10-18
I done that but when installing Ubuntu it didnt recognise the partitions it just showed 2 partitions of 250gb each. My hard drive is 500gb but on my tower ive got a sticker saying 2x250gb so not too sure how it works really. I had set like 40gb partitioned but as I say this wasnt mentioned when installing Ubuntu.

Any idea why?

See this link: [http://ubuntuforums.org/showthread.php?t=557280&highlight=dual+boot+vista](http://ubuntuforums.org/showthread.php?t=557280&highlight=dual+boot+vista)

---

### Post by tnaseem on 2007-10-18
I've never had problems dual booting with 7.04 (feisty) or the new 7.10 (gutsy). Both Ubuntu and Vista run fine.

The way I did it was to install another hard disk for the Ubuntu install. I plugged this in as the 'first' SATA drive and the original Vista as the 'second'. I installed Ubuntu as normal on the first drive, it picked up Vista and added that to the Grub loader. All worked fine! I can can boot into either from there.

However, with Gutsy I'm having major problems with setting the resolution using my ATI gfx card and monitor setup. Something that used to work fine in Feisty! But that's [another story]("http://ubuntuforums.org/showthread.php?t=579881")...

---

### Post by Dead_$partan on 2007-10-18
dc: what version of ubuntu are you trying is it the live disc or the alternative disc?  Also do you know how your systekm is configured?  If its 2x250GB drives do you know if they are configured as raid at all?  You said below your hard drive is 500GB if windows was reporting this I wiould be thinking you have a RAID 0 configured, this could potentially raise the need for some extra steps to have ubuntu properly recognise the hard disk partitions.   

Also, do you know what type of drives they are?  SATA, SCSI, SAS etc?  Most likely SATA but it's best to be sure.

If you had windows installed as default or had it insatlled on the total space then there would be no room for installing Linux so you would either need to resize your Vista partiiton or wipe the HD clean and manually partition.  I dont want to get too far into this without knowing more information on your setup and install methods.

---

### Post by dc_jt on 2007-10-18
Hi it is the live disc and im really not sure about the other questions how can I check?

By the way I had Win XP installed when bought the computer but installed Vista when it was released.

Thanks for the help...

---

### Post by Dead_$partan on 2007-10-18
is it an OEM PC like Dell or HP you have?

With regards to the other questions, you can check the BIOS and device manager.  If it is RAID it will say somehtinbg about the RAID array when its going through POST.  Might say soming like logical volume 0, striped.

---

### Post by dc_jt on 2007-10-18
This is my PC

[http://www.pcworld.co.uk/martprd/product/seo/216880](http://www.pcworld.co.uk/martprd/product/seo/216880)

Ill go into the BIOS now and see what it says

---

### Post by dc_jt on 2007-10-18
Just checked and on boot up it says RAID_VOLUME(O) RAIDO(STRIPE)

Something like that anyway, went off before I had a chance to see anything else.

This any help to you?

Thanks again

---

### Post by Scroobytec on 2007-10-18
Yes from the info you have supplied it looks like you have two 250 Gb HDD's that are set-up as RAID 0.

I would think that they are SATA.

---

### Post by dc_jt on 2007-10-18
So how do I overcome my problem? :(

---

### Post by dc_jt on 2007-10-19
Anyone?? Please help!!!

I done it with Suse a while ago but cant do it with Ubuntu?!?!

---

### Post by ElSeeDee on 2007-10-19
This is what I did on my laptop. It came with XP. I wiped that and did a clean install of Vista Ultimate.
Click on Start.
Right-click on My Computer.
Click on Manage.
Click on Disk Management.

Now use the disk manager to resize the Windows partition, leaving however much space you are wanting to allocate for Ubuntu. When it's done doing it's thing, re-boot with the live CD. Then install using the Guided-Use largest unallocated space (not sure of the exact verbiage there). And when the install is done, GRUB should come up on the re-boot allowing you to choose which OS to boot to.

Hope this helps.

---

### Post by dc_jt on 2007-10-19
Hi

Thanks for the reply, I did exactly that and the partitioning seems to work. I end up with c drive having 330gb and then 160g "not allocated", which seems right.

However when I go to install Ubuntu, the option "Manual - use the largest continuous free space" doesnt appear.

Instead it just says guided - use entire disk. Then it has two options sda and sdb both saying 250gb each.

Why arent I geting the option to use the largest continous space??

---

### Post by Aqualung on 2007-10-19
> **ElSeeDee said:**
> Now use the disk manager to resize the Windows partition, leaving however much space you are wanting to allocate for Ubuntu. When it's done doing it's thing, re-boot with the live CD. Then install using the Guided-Use largest unallocated space (not sure of the exact verbiage there). And when the install is done, GRUB should come up on the re-boot allowing you to choose which OS to boot to.These are precisely the steps I followed. Well, guess what, GRUB didn't come up, instead I got this "Missing operating system" message.:mad::mad:

Thank God for Hiren's Cd, otherwise I would've been screwed.:mad:

---

### Post by dc_jt on 2007-10-19
Why dont I get the option though? Is it because my hard drive is 2 x 250gb and not just 1 x 500gb?

---

### Post by Dead_$partan on 2007-10-19
Hi dc, sorry for not getting back sooner, have been working.

As far as I know, the Live CD doesn't have functionality for RAID, you will need to download the alternative install disc.

---

### Post by dc_jt on 2007-10-19
Hi

No problem, thanks for getting back to me anyway.

Ill download the alternative when Im home, is there anything different I need to do before installing or is it the same method?

---

### Post by ElSeeDee on 2007-10-19
Sorry. Didn't know LIVECD didn't support RAID.

---

### Post by Dead_$partan on 2007-10-19
The alt CD is simple enough but it is all text based.  Just read whats on the screen and you should be fine.

---

### Post by DeanFX on 2007-10-19
I partitioned 20gb....and i ran the installation for ubuntu...Now I think i found the drive when i hit "Manual" and it says 20178mb, i think that is it, but it says i have to hit new partition for that.....

what system type is it? because I want to run dual OS with ubuntu and windows vista.

Please help! :) :KS

---

### Post by Dead_$partan on 2007-10-19
You will need to set the partition to root (/) and swap (swp).  Divide that 20GB partiiton further by creating a swp file usually about 1GB in size and create the rest as /.

---

### Post by kyrmia on 2007-10-19
I have partitioned 20MB space before booted with the Ubuntu 7.10 CD which i have as root "/"
Now, Do I need to have all three partitions{ swp & /.} before Installing the Ubuntu OS?
When I tried to install with only 20MB partition by selecting this option "shrink the volume in windows and use the largest contiguous free space for installing ubuntu"
At the last stage of the installation process, :mad:the migration assistant does not show Vista/Longhorn:mad: Does this mean Ubuntu does not see Vista installed in a different partition?
Will I have problems with WinVista if I continue to install, will I be able to boot back into Vista?

_Here are my Specs._

HP Pavilion tx1210us
1.9 GHz AMD Turion 64 X2 TL-58 processor, 160 GB hard drive, 2 GB RAM (max), LightScribe DVD-/+RW drive
Connectivity: 3 USB, 1 FireWire, 1 VGA, 1 ExpressCard 34, 1 headphone, 2 microphone, 1 S/PDIF out, 5-in-1 memory card reader
Quad-mode Wi-Fi LAN (802.11a/b/g/n), 10/100 Ethernet, Nvidia GeForce Go 6150 video card with up to 287 MB shared memory
Pre-installed with Windows Vista Home Premium (with Media Center capabilities)
:lolflag:

---

### Post by dc_jt on 2007-10-20
I tried using the alternate disk and when it comes to the partitioning part it now has four options. 

They are something like:
-  use entire disk
- guided ...(cant remember what it said but it had 'with LMV' on the end or something like that)
- guided ...(cant remember what it said but it had 'with encrypted LMV' on the end or something like that)
- manual

When I went to manual it still just showed the 2 x 250gb drives, didnt say anything about the 70gb I had partitioned?!

What does the LMV thing mean?

---

### Post by Dead_$partan on 2007-10-20
dc: You may need to install RAID drivers by using a floppy disk.  You will likely need to find out what make the RAID controller is and go to the companies website and download the RAID drivers.  You then need to put them onto a floppy disk and type linuxdd(it may be linux dd or linux-dd i cant remember), setup should then ask where the RAID drivers are and you would type fda and press enter.  Setup should continue as normal from there and it should pick up your disks configured in the right way.   If it doesn't, one of the more experienced users will need to assist because this is about as far as my knowledge goes on this im afraid.  It may be that Linux doesnt fully support your RAID controller but like I say one of the more experienced users may be able to help.

kyrmia: I have never shrunk a windows partition using Linux before, I have heard it can cause issues so I usually do a clean format/install.  Shrinking the partition as done either 1 of 2 things, it has deleted  windows by installing Ubuntu over the top or it is simply not mounting the windows partition,  You can see how your drive is partitioned by typing sudo fdisk -l, you should see something like..

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
**/dev/sda1   *           1       16971   136314880    7  HPFS/NTFS**
/dev/sda2           16972       19348    19093252+  83  Linux
/dev/sda3           19349       19457      875542+   5  Extended
/dev/sda5           19349       19457      875511   82  Linux swap / Solaris

Disk /dev/mmcblk0: 512 MB, 512229376 bytes
16 heads, 63 sectors/track, 992 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x00000000

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1   *           1         992      499851+   6  FAT16

**The part highlighted in bold is my windows partition.

---


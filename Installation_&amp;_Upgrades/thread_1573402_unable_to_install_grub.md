---
title: "unable to install grub"
date: 2010-09-12
forum: Installation &amp; Upgrades
---

### Post by xenton on 2010-09-12
Hi, 

I've only ever dealt with windows before, this is my first time so please bear with me.

I have a dual boot windows 7 xp system with the windows 7 bootloader handling things.

My system consits of 2 raid arrays with 2 hd each

The first array has my xp and win 7 installs on  and a fair bit of unpartitioned space.

Second array has one large NTFS partition where my documents, music etc. is stored.

I made a new unformatted partition of 20 gigs for linux and one of 2 gigs for the swap file in windows.

Installed unbuntu 10.04 from CD, I was amazed when it saw my raid arrays immediately and felt realived.

All went well until it tried to install grub and it failed couldn't install to dev/sda.

I've done some reading on here and I gather I need to install to the raid array rather than one of it's partitions.

Will this overwrite the win 7 boot loader?

I was planning to use EasyBCD to add grub to my win 7 boot loader as I will be primarily using windows 7,  at least at first.

If grub does overwrite my win 7 boot loader will it see both my xp and win 7 installs, and can you set it to boot to an OS of choosing after a timeout like the win 7 bootloader.

Thanks for your time.

---

### Post by Troublegum on 2010-09-12
> **xenton said:**
> Hi, 
All went well until it tried to install grub and it failed couldn't install to dev/sda.

I've done some reading on here and I gather I need to install to the raid array rather than one of it's partitions.


What **exactly** went wrong? Was there any error message? 

> **xenton said:**
> 
Will this overwrite the win 7 boot loader?

 
I think Win 7 install its boot loader in the MBR of its disk. That's grubs first choice too, so with default settings, grub will overwrite the Win 7 bootloader. 

**It is not recommended to install grub to a partition. The better way would be to install it to the mbr of the disk. **So, /dev/sda (NOT /dev/sda1, /dev/sda2, ...) is usually a good choice for installing grub.

> **xenton said:**
> 
If grub does overwrite my win 7 boot loader will it see both my xp and  win 7 installs, and can you set it to boot to an OS of choosing after a  timeout like the win 7 bootloader.

Yes, grub detects Windows XP and Windows 7 and offers to boot them. At first, you're new linux installation is the default choice and the default will be booted after a few seconds, but you can use the arrow keys to navigate to Windows and hit ENTER to boot Windows. 
Afterwards, you can select your default choice (in linux) by editing /etc/default/grub in linux.


> **xenton said:**
> 
 I was planning to use EasyBCD to add grub to my win 7 boot loader as I will be primarily using windows 7,  at least at first.

Seems like thats a Windows program. Thats not necessary. Grub is highly  configurable. You can of course set Windows to come first in the list or  set it as default. I, personally, use a modified version of grub called  burg that is capable of displaying a high-resolution graphical menu  instead of the boring black screen. 

However, if you decide on not using grub and use the Windows Bootloader with EasyBCD, there's a guide with screenshots here:
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

---

### Post by xenton on 2010-09-12
Thanks for your reply.

The installation was at 93% and an error message poped up in a box titled "unable to install grub to dev/sda"

There was a big white cross within a red circle and it told me that it was a fatal error.

It gave me the option to install grub to a different location, which presented a drop down list.

It also gave me the option to continue without installing a boot loader or to exit the installation.

After trying a few other partitions from the drop down list, and being greated with the same error, I eventually clicked continue without installing a bootloader option.

Thanks for that guide, but seeing as grub is just as configurable and you say there's a pretty graphical alternative I will probably stick with grub.

Whichever way I decide to go, it would appear I need to install grub (or grub 2) to the MBR.

I'll use the search function and try and find out how to do that now.

Thanks very much

oh how do I get burg would I still need to install grub first and does it take any longer to boot via burg than grub?

---

### Post by Troublegum on 2010-09-12
Hi,


i'm not sure about that grub error. It may be related to the raid array, but I have no idea. :(
Do you have a hardware raid or software raid? And what raid level? What hardware (motherboard?, raid?) do you use?

I suggest to look into the grub problem first before worrying about fancy menus with burg.
burg will actually replace grub. but in order to install burg, you need a running ubuntu installation first. 
I have uploaded a photo from my grub installation, you can select different themes. 
[[IMG]http://img714.imageshack.us/img714/8576/cimg2688small.th.jpg[/IMG]]("http://img714.imageshack.us/i/cimg2688small.jpg/") [[IMG]http://img814.imageshack.us/img814/8526/cimg2683small.th.jpg[/IMG]]("http://img814.imageshack.us/i/cimg2683small.jpg/")
Thats the burg homepage: [http://code.google.com/p/burg/](http://code.google.com/p/burg/)

---

### Post by xenton on 2010-09-12
Hi, 

It's hardware raid on my motherboard both arrays are raid 0.

Motherboard is a KN1 Sli Lite which uses the NVidia nForce raid controller

---

### Post by Troublegum on 2010-09-12
Hi,

I googled a few minutes. I think youre RAID controller might be a so called "FAKEraid" controller?!
 According to the ubuntu wiki, installing ubuntu on a fakeraid might be tricky: 
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by xenton on 2010-09-12
Hmm, 

Thanks very much for finding that out.

It seems very odd that the installer seesmy raids and  all my partitions (lists my 1st raid array as dev/mapper/ATA RAID nvidia_abjcfaad (Stripe) ) and seems to be dealing with my raid just fine, copies all the files to the right place and then fails installing the bootloader.

Given the warning right atop that article and the fact that it only has specific instructions upto 9.10 and I'm trying to install 10.04 I don't think I'll bother.

Thanks very much for all your help anyhow.

---

### Post by xenton on 2010-09-12
Ah.......

After a little more reading it would seem that ubuntu 10.04 is fine with fakeraid, its grub 2 that will not work with fake raid.

Might read some more tomorrow, bed calls now

---

### Post by xenton on 2010-09-13
Right after some more reading grub 2 should be working with fakeraid,.

First thought I have the 10.04 LTS desktop CD image, could it be I need a more current release?

The problem:
The installer sees my raid arrays fine I click on the advance tab at step 8 and tell it to install grub to the **array **which has my linux partition on it. However I get an error message saying it grub couldn't be installed to dev/sda, which is not even what I'm trying to do.

I continue the installation without installing a bootloader.

I now boot from the CD use the synaptic package manager, first remove grub, then reinstall the version is 1.98

I am picking my **raid array **from the list as below:

[IMG]http://i524.photobucket.com/albums/cc323/xenton/ubuntu/grubconfig.png[/IMG]

I am then greeted with the following error:

[IMG]http://i524.photobucket.com/albums/cc323/xenton/ubuntu/Screenshot-Debconfonubuntu.png[/IMG]

---

### Post by Troublegum on 2010-09-13
Hi xenton, 

I'm glad you didn't give up yet. :)
> **xenton said:**
> 
First thought I have the 10.04 LTS desktop CD image, could it be I need a more current release?

Version 10.04[COLOR=Red].1[/COLOR] got released a few weeks ago (?), which fixes a lot of bugs in 10.04. There is an updated CD-image on ubuntu.com. 
There were also a few grub-related bugs that got fixed (see [https://wiki.ubuntu.com/LucidLynx/ReleaseNotes/ChangeSummary/10.04.1](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes/ChangeSummary/10.04.1)). But I don't know if ***this*** bug is fixed yet. But I'd say it's not a bad idea to try the new cd-image.


> **xenton said:**
> 
The problem:
The installer sees my raid arrays fine I click on the advance tab at step 8 and tell it to install grub to the **array **which has my linux partition on it. However I get an error message saying it grub couldn't be installed to dev/sda, which is not even what I'm trying to do.

It seems, the Ubuntu installer ignores your choice for the installation location. 
Your idea to continue nevertheless and fix the issue from within the live-cd is not bad.
However, in order to restore/install grub for your hard-drive installation, you have to chroot into the freshly installation. That way, you can make persistent changes to your installation.

There is a GRUB2 article in the Ubuntu wiki that describes how to restore the grub installation using a Live-CD. In your case, you don't want to restore but to install grub, but I think it may be worth trying it nonetheless. 

[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD]("https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD")

When you follow theses steps, one step is to install grub into the mbr of /dev/sda:
```
grub-install /dev/sda
```Since you want a different installation location, you would have to replace all these commands with the appropriate paths, of course. 

It may be necessary to install the grub package first *after you chrooted into your installation* via 
```
apt-get install grub-common grub-pc
```I hope you get this sorted out. :)

---

### Post by xenton on 2010-09-13
> **Troublegum said:**
> Hi xenton, 

I'm glad you didn't give up yet. :)

Version 10.04[COLOR=Red].1[/COLOR] got released a few weeks ago (?), which fixes a lot of bugs in 10.04. There is an updated CD-image on ubuntu.com. 


I'm sure I stumbled across posts as far back as April, from people saying they had a successful fake raid install straight off the install CD.

> **Troublegum said:**
> 
It seems, the Ubuntu installer ignores your choice for the installation location. 


Yeah that seems to be the stumbling block with the installer

> **Troublegum said:**
> 
Your idea to continue nevertheless and fix the issue from within the live-cd is not bad.
However, in order to restore/install grub for your hard-drive installation, you have to chroot into the freshly installation. That way, you can make persistent changes to your installation.


I had a feeling I was missing something simple hopefully thats's it!

Right I'm going to try the new version, see if that manages a successful install, then, if not, will have another crack and installing grub from the live-CD

Thanks for all your help

---

### Post by xenton on 2010-09-13
Right, 

I already had 10.04.1, so it's either try the alternative CD or go for the beta 10.10.

Still trying to install grub from the live CD atm, following the guide you linked.

I'm thinking I need to mount my linux partition*** /dev/mapper/nvidia_abjcaad3*** then chroot into it, then update grub, then install grunb to ***/dev/mapper/nvidia_abjcaad*** which is the raid array which contains my linux partition but:

I'm failing on the first step of mounting my installed linux partition.

As you can see from this screen of Disk utility my linux install is ***/dev/mapper/nvidia_abjcaad3***

[IMG]http://i524.photobucket.com/albums/cc323/xenton/ubuntu/Screenshot-21GBHardDisk-dev-mapper-nvidia_abjcfaad3DiskUtility.png[/IMG]

Here's what happens trying to mount it in terminal:

```
ubuntu@ubuntu:~$ sudo mount /dev/mapper/nvidia_abjcaad3 /mnt
mount: special device /dev/mapper/nvidia_abjcaad3 does not exist

```If I ***sudo fdisk -l*** I get the following

```
ubuntu@ubuntu:~$ sudo fdisk -l
Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5
Warning: invalid flag 0x9ea1 of partition table 5 will be corrected by w(rite)

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xffffffff

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *         218        9425    73963260    7  HPFS/NTFS
/dev/sda2           28766       92537   512244736    7  HPFS/NTFS
/dev/sda3           92538       95123    20772045   83  Linux
/dev/sda4            9426        9674     2000001    5  Extended
/dev/sda5   ?      189818      339188  1199816685+  20  Unknown

Partition table entries are not in disk order

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000300

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   ?       85953      219970  1076494370   9b  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sdc2   ?       83026      217141  1077280818   80  Old Minix
Partition 2 does not end on cylinder boundary.
/dev/sdc3           83175      218220  1084743981   9e  Unknown
Partition 3 does not end on cylinder boundary.
/dev/sdc4   ?       67251      107204   320920970+  50  OnTrack DM
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6b69f593

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      243202  1953520033+   7  HPFS/NTFS
```Which would indicate my linux partition is at _**/dev/sda3**_

However, trying to mount this gives the same error:

```
ubuntu@ubuntu:~$ sudo mount /dev/sda3 /mnt
mount: special device /dev/sda3 does not exist
```
I'm hoping I'm missing something simple here or getting my syntax wrong.

Any help would be gratefully received

---

### Post by Troublegum on 2010-09-13
Hi xenton,


I am puzzled because I've never used a RAID setup before. I'm not familiar with that.

Do you remember the partition name you chose during install? Or did you let the installer make the partitioning automatically?
Another program is the "gparted" partiton manager. I think it comes with the live-cd and is somewhere in the menu under system -> settings? It might give another overview of the available partitions.

Your mount syntax seems alright. I don't know what the error is. :(
Anyone?

---

### Post by ronparent on 2010-09-13
In 10.04 the grub 2 bootloader will not mount to any disk that is part of the raid set. The raid set name and all of the raid partitions in the set are listed in that order in /dev/mapper/. To install the boot loader on a raid set, you have to install it to the raid set by name. This can be done after the fatal error on install by following the instruction in this: [https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) GRUB 2

---

### Post by xenton on 2010-09-14
Hi and thanks, 

> **ronparent said:**
> In 10.04 the grub 2 bootloader will not mount to any disk that is part of the raid set. The raid set name and all of the raid partitions in the set are listed in that order in /dev/mapper/. To install the boot loader on a raid set, you have to install it to the raid set by name. This can be done after the fatal error on install by following the instruction in this: [https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) GRUB 2

I booted off the Live CD mounted my linux partition and then used it's mountpoint location but I got an error

```
ubuntu@ubuntu:~$ sudo grub-setup -d /media/7dee85c7-4395-4a60-a279-e1960599dc90/boot/grub /dev/sda
grub-setup: error: no signature.
You have a memory leak (not released memory pool):
 [0x23bf740]
```

I went for method 2 in the guide you directed me too, as the other methods involved mounting a raid partition from within terminal, which doesn't work with raid partitions.

I apologise in advance if I missed something or misunderstood your instructions, but I could see no part of the guide you pointed me at with instructions specific to my situation (fakeraid), and I am completely new to linux and ubuntu.

---

### Post by Troublegum on 2010-09-14
Hi xenton, 

you didn't want to install grub to /dev/sda, did you? 
With the command you've entered, you've specified /dev/sda as target. 
Didn't you want to install grub to your raid device?


I don't have a immediate solution, but it seems another user has a similar problem. See [http://ubuntuforums.org/showthread.php?t=1574017](http://ubuntuforums.org/showthread.php?t=1574017) 
Maybe we can work that out together.

---

### Post by ronparent on 2010-09-14
Troublegum is right - you have to write the boot loader to the overall raid device. The first device listed after control in /dev/mapper/ - ie /dev/mapper/nvidia_abjcaad.

---

### Post by xenton on 2010-09-14
Thanks guys, 

Of course! It was getting a bit late was hoping it'd be something simple, lets have another go see what we get.

Right I'm pretty sure I'm doing the right thing, but getting a similar error:

```
ubuntu@ubuntu:~$ sudo grub-setup -d /media/7dee85c7-4395-4a60-a279-e1960599dc90 /dev/mapper/nvidia_abjcfaad
grub-setup: error: cannot stat /media/7dee85c7-4395-4a60-a279-e1960599dc90/boot.img.
You have a memory leak (not released memory pool):
 [0x25d3740]
```

Any ideads?

---

### Post by xenton on 2010-09-14
I just had a read of the other thread and tried this:

```
ubuntu@ubuntu:~$ sudo mount /dev/mapper/nvidia_abjcfaad3 /mnt
```and then this

u```
buntu@ubuntu:~$ sudo grub-install --root-directory=/mnt/ /dev/mapper/nvidia_abjcfaad
You have a memory leak (not released memory pool):
 [0x1e4f1e0]
You have a memory leak (not released memory pool):
 [0x12951e0]
You have a memory leak (not released memory pool):
 [0xece730]
You have a memory leak (not released memory pool):
 [0xf10730]
You have a memory leak (not released memory pool):
 [0x120b750]
Installation finished. No error reported.
```More memory leak errors but that last line looks promising, I'm going to try a reboot now and see what happens, wish me luck :p
[U][B]
EDIT:[/B][/U]
Read that other post properly and found he had success a different way so I tried that

I had already done
```
sudo mount /dev/mapper/nvidia_abjcfaad3 /mnt
```

Then i did this:
```
ubuntu@ubuntu:~$ sudo mount --bind /dev /mnt/dev
ubuntu@ubuntu:~$ sudo mount --bind /proc /mnt/proc
ubuntu@ubuntu:~$ sudo mount --bind /sys /mnt/sys
ubuntu@ubuntu:~$ sudo chroot /mnt
root@ubuntu:/# dpkg-reconfigure grub-pc

```
Left as it was but selected my raid root*** /dev/mapper/nvidia_abjcfaad*** from the list and then I got:
```
You have a memory leak (not released memory pool):
 [0x7f9fc0]
You have a memory leak (not released memory pool):
 [0x161dfc0]
You have a memory leak (not released memory pool):
 [0x10a16c0]
You have a memory leak (not released memory pool):
 [0x8ed6c0]
You have a memory leak (not released memory pool):
 [0x20b36e0]
Installation finished. No error reported.
Generating grub.cfg ...
You have a memory leak (not released memory pool):
 [0x7c7fa0]
You have a memory leak (not released memory pool):
 [0x201efa0]
You have a memory leak (not released memory pool):
 [0x1a096a0]
You have a memory leak (not released memory pool):
 [0x1cd0fa0]
You have a memory leak (not released memory pool):
 [0x2573fa0]
You have a memory leak (not released memory pool):
 [0xf396a0]
You have a memory leak (not released memory pool):
 [0xb2dfa0]
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
You have a memory leak (not released memory pool):
 [0xbdbfa0]
You have a memory leak (not released memory pool):
 [0x1ee6fa0]
You have a memory leak (not released memory pool):
 [0x109f6a0]
Found memtest86+ image: /boot/memtest86+.bin
You have a memory leak (not released memory pool):
 [0x95efa0]
You have a memory leak (not released memory pool):
 [0xf5ffa0]
You have a memory leak (not released memory pool):
 [0x9a96a0]
ls: cannot access /media/Storage: No such file or directory
ls: cannot access /media/Storage: No such file or directory
ls: cannot access /media/Storage: No such file or directory
ls: cannot access /media/Storage: No such file or directory
Found Windows 7 (loader) on /dev/mapper/nvidia_abjcfaad1
You have a memory leak (not released memory pool):
 [0x9f8fa0]
You have a memory leak (not released memory pool):
 [0x1a69fa0]
You have a memory leak (not released memory pool):
 [0x11306a0]
done

```

Now I'm going to reboot :p

---

### Post by drs305 on 2010-09-14
OK. Good luck! ):P

While I'm here - a request for anyone who edits Community docs (not the wiki) and knows about Grub 2 and RAID...  I wrote the G2 doc but there is nothing about RAID. There is a reason for that - I've never used RAID and know almost nothing about it. The doc sorely needs a RAID section, so have at it if you are willing and capable!

[https://help.ubuntu.com/community/Grub2]("https://help.ubuntu.com/community/Grub2")

---

### Post by xenton on 2010-09-14
We have success!!!!

A big thank you to you guys for all your help.
That was far easier than getting windows 7 to work with my raid setup, and I was an experienced windows user!!

To give a little something back, I plan on putting together a guide with lots of pictures to help others;two people with different raid setups on different machines have had success with the same method now so this could help many others.

Am I right in thinking that after my 
***sudo grub-install --root-directory=/mnt/ /dev/mapper/nvidia_abjcfaad***

Grub was not fully set up and wouldn't have worked, my basis for this is that after I ran 
***dpkg-reconfigure grub-pc*** it found my windows 7 bootloader and generated grub.cfg which didn't happen previously.

Off to cook dinner now, then will start the guide.

Again thank you so much.

It may be burg time next!

---

### Post by drs305 on 2010-09-14
Congrats on your success!

Sometimes after Grub2 is installed you have to run "sudo update-grub" one more time for it to find Windows and some other OS's. Normally it isn't necessary. Don't know if it would have worked in your situation or not.

For your project, you might consider calling it something like "HOWTO: ..." and submitting it in the Tutorials and Tips forum. It won't be immediately available - forum staff have to take a look at it. We can use some good documentation on this subject.

---

### Post by Troublegum on 2010-09-14
Hi xenton, 


I am glad you worked it out. =D> Have fun with your new linux system. 
If you need help customising grub or burg, don't hesitate to mail me. 

> It may be burg time next!
if you can install grub, you should be able to install burg too, since burg is basically grub with more features.

It's just
burg-install instead of grub-install
and update-burg instead of update-grub. See [http://code.google.com/p/burg/wiki/InstallUbuntu](http://code.google.com/p/burg/wiki/InstallUbuntu)




> 
Grub was not fully set up and wouldn't have worked, my basis for this is that after I ran 
dpkg-reconfigure grub-pc it found my windows 7 bootloader and generated grub.cfg which didn't happen previously.
I think 
```
sudo update-grub
```
would have worked too.

---

### Post by xenton on 2010-09-14
> **drs305 said:**
> Congrats on your success!

Sometimes after Grub2 is installed you have to run "sudo update-grub" one more time for it to find Windows and some other OS's. Normally it isn't necessary. Don't know if it would have worked in your situation or not.

For your project, you might consider calling it something like "HOWTO: ..." and submitting it in the Tutorials and Tips forum. It won't be immediately available - forum staff have to take a look at it. We can use some good documentation on this subject.

I will defiantly do that!

> **Troublegum said:**
> Hi xenton, 


I am glad you worked it out. =D> Have fun with your new linux system. 
If you need help customising grub or burg, don't hesitate to mail me. 


if you can install grub, you should be able to install burg too, since burg is basically grub with more features.

It's just
burg-install instead of grub-install
and update-burg instead of update-grub. See [http://code.google.com/p/burg/wiki/InstallUbuntu](http://code.google.com/p/burg/wiki/InstallUbuntu)





I think 
```
sudo update-grub
```would have worked too.

It seems fairly straightforward once you get your head around how linux handles the raid, much easier than windows 7, but it was so much trouble for me as windows 7 didn't support my raid driver 'out the box' 

Thanks to you all for all your help :D :D

---

### Post by xenton on 2010-09-14
I have just posted my guide to the tutorials section, so it should be up once approved by a mod. Thanks again for all the help guys :p

---

### Post by xenton on 2010-09-14
> **Troublegum said:**
> Hi xenton, 

if you can install grub, you should be able to install burg too, since burg is basically grub with more features.

It's just
burg-install instead of grub-install
and update-burg instead of update-grub. See [http://code.google.com/p/burg/wiki/InstallUbuntu](http://code.google.com/p/burg/wiki/InstallUbuntu)


got burg package installed and installed burg like I did grub, resulted in me booting to the grub recovery screen.

Reinstalled grub from live CD as before and now it boots straight into Ubuntu no grub screen shown no option to boot into windows


Will have another look tomorrow, tiredness has just hit like a wall.

---

### Post by Troublegum on 2010-09-14
> **xenton said:**
> 
Will have another look tomorrow, tiredness has just hit like a wall.


hm, did you try another?
```
sudo update-grub
```

it also possible that grub is set to boot without prompt?
Make sure to comment out GRUB_HIDDEN_TIMEOUT in /etc/default/grub.
Or GRUB_TIMEOUT is set to 0?

---

### Post by xenton on 2010-09-14
I was just heading back to post I tried 'sudo update-grub' and everything is now back to normal!

Will have another look at Burg tomorrow, might start a new thread, might mail you if the offers still open?

---

### Post by Troublegum on 2010-09-15
Sure. :)
And I'll keep me eyes open for new threads.

The burg developer is also registered in this forum as burg123. 
Burg has a thread here: [http://ubuntuforums.org/showthread.php?t=1371288](http://ubuntuforums.org/showthread.php?t=1371288)

---

### Post by phillipdhall on 2010-09-15
XENTON,

I am currently going through your same headache, new to Linux and trying to multiboot on a motherboard RAID0 array.

I think the only difference is that I have half a dozen operating systems installed and they move/change frequently, and so I use a third party bootloader (GAG) in the MBR, and each OS partition contains it's own bootrecord.

I'd really like to install GRUB2 to the Linux "/" partition so that GAG can call it. 

It may be worth noting that each time I re-partition the array and restore OS images to appropriate partitions, I have to use PTEDIT.exe (from a DOS disk) to correct the "hidden sectors" field in each logical partition boot record. I thought this might be the problem with my Linux partition, but there appears to be no boot record on the partition to correct! There are only 2 sectors before the partition start (instead of the standard 63 for my windows based partitions).

At any rate, I'm looking forward to your guide. Any chance you can PM it to me until they get it posted in tutorials?

Thanks,

Phil

---

### Post by xenton on 2010-09-15
Have just PM'd it to you. Hope it helps. You'll be wanting to use the /dev/mapper/ listing for you Linux partition instead of the listing for the root of the raid array so once you launch 
```
dpkg-reconfigure grub-pc
```

Select your linux partition rather than the root of your raid array as per the guide.

---

### Post by lubberlick on 2010-10-06
I have spent 2 days working on this particular subject and would like to thank those of you in this thread for finally pointing me in the right direction. I would like to add my exact simple steps to resolving this issue for anyone else who stumbles accross this thread.

I used the steps located here [https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

However I only used steps 6 7 8 and 9. And I changed them to work with the fakeraid on my system.

To gather the information needed from your Ubuntu LiveCD "try it" browse System->Administration->Disk Utility.

[IMG]http://i53.tinypic.com/nc05d1.jpg[/IMG]

The partitions you might need to work with are located in Peripheral devices.

The steps to reinstall grub2 that i used were as follows from the Community Documentation. (copy paste)

keep in mind that /dev/mapper/sil_bgajdjdcagdh is only valid for my machine and used for display purposes. You will need to use your own raid device ID.


[LIST=1]
[*]**sudo mount /dev/sdYY /mnt [COLOR=Red]  --Change /dev/sdYY to /dev/mapper/sil_bgajdjdcagdh5 (your ubuntu install[/COLOR])**
[*]Mount the critical virtual filesystems: [B]
sudo mount --bind /dev  /mnt/dev[/B]
 **sudo mount --bind /dev/pts  /mnt/dev/pts**
 **sudo mount --bind /proc /mnt/proc**
 **sudo mount --bind /sys  /mnt/sys**
[*]Chroot into your normal system device: 
**sudo chroot /mnt**
[*]If there is no /boot/grub/grub.cfg or it's not correct, create one using
 **update-grub**
[*]Reinstall GRUB 2: 
**grub-install /dev/sdX[COLOR=Red]  -- change /dev/sdX to /dev/mapper/sil_bgajdjdcagdh  (your fakeraid)[/COLOR]**
[/LIST]

also reverse steps 4 and 5 as you will need to update-grub after you install in order for it to configure your multiple operating systems installed.

---

### Post by xenton on 2010-10-08
I'm glad you got this working, well done. You seem to have arrived at the same ultimate solution as I did [here]("http://ubuntuforums.org/showthread.php?t=1574765") which confirms it works, which is good news.

---


---
title: "Ubuntu 10.04 Question"
date: 2010-03-11
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Oreo_King on 2010-03-11
Since Lucid Lynx is going to be released pretty soon I thought I'd upgrade from Jaunty over to Lucid.  If I remember right Karmic started using GRUB 2.

Here's the thing, I have a dual boot system on my computer consisting of Windows XP and Ubuntu 9.04.

If I wipe Ubuntu's partition and install Ubuntu Lucid will I have any GRUB problems?

Since right now I'm guessing have GRUB Legacy and Lucid will most likely use GRUB 2.

Any thoughts?

---

### Post by overdrank on 2010-03-11
Hi and moved to Lucid Lynx Testing and Discussion. :)

---

### Post by VMC on 2010-03-11
> **Oreo_King said:**
> Since Lucid Lynx is going to be released pretty soon I thought I'd upgrade from Jaunty over to Lucid.  If I remember right Karmic started using GRUB 2.

Here's the thing, I have a dual boot system on my computer consisting of Windows XP and Ubuntu 9.04.

If I wipe Ubuntu's partition and install Ubuntu Lucid will I have any GRUB problems?

Since right now I'm guessing have GRUB Legacy and Lucid will most likely use GRUB 2.

Any thoughts?
Your concern regarding Grub2 shouldn't be a concern depending on how many hard drives and what type and where you place your /boot.

I'm a tad bit confused about two things you stated.
(1) upgrade Jaunty over to Lucid
(2) wipe Ubuntu's partition and install Ubuntu Lucid

Are you going to do one or both of the two?

First thing to do is backup. I would clone the partition in question just so you can revert in the case of a catastrophe.

---

### Post by Oreo_King on 2010-03-11
Hah, sorry, I'll clarify a bit.

Uh I only have one hard drive.

I don't know what you mean by what "type", as to where it is I don't know exactly. When I installed Jaunty I basically let the installer do everything, I just chose the install side by side with Windows option. It overwrote the MBR if I remember. (sorry I'm not the most learned in matters with Linux)

Oh! Okay here's what I meant: In my system there's two partitions, one for XP and one where Jaunty is at. I was going to format (or delete) the second partition so that it would be free to install Lucid Lynx when it came out. Or install Lucid over it.

About the cloning thing, what should I do? (you don't have to tell me exactly I can try and figure it out :) ) 

Should I use Clonezilla? I've never used cloning software but I hear a lot about it.

---

### Post by VMC on 2010-03-12
By "type", I meant SATA, IDE.

As far as using Clonezilla. That's a good choice. You need an external or someplace safe to image it to. I use to use Clonezilla, as on rare occasions I still do, but I mainly use partclone. Its proven reliable and I'm use to it. Clonezilla will use partclone also and a few other tools at its disposal.

One thing you can now do is download boot_info_script (see my blue link), and run it. The results are in a file called RESULTS.txt.
It will tell you everything you need to know regarding boot info.

---

### Post by Kevbert on 2010-03-12
You should have very few problems regarding XP and grub2 with 10.04. However I would wait a little bit longer until 10.04 becomes a little more stable (especially if your using a Nvidia display adapter). There are also some ubiquity (installer) problems. If you intend to use this PC as your default machine I'd wait at least 1 month after release. The alternative is to try running 10.04 with 9.04 and XP as a multiboot system and see how you get on.

---

### Post by Oreo_King on 2010-03-12
Oh as for type, it's PATA.

The boot info script took me a while to make it run, haha, in the end I ran it in sudo nautilus. Here's the info it's kinda long: 


> Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders, total 160836480 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xadb6adb6

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    93,980,249    93,980,187   7 HPFS/NTFS
/dev/sda2          93,980,250   160,826,714    66,846,465   5 Extended
/dev/sda5          93,980,313   157,742,234    63,761,922  83 Linux
/dev/sda6         157,742,298   160,826,714     3,084,417  82 Linux swap / Solaris
I only copied what I thought was important. So I guess the boot is on the first drive with Windows XP.

Also I have three questions regarding cloning:

1. So if Ubuntu was to get super corrupted or crash or whatever an image would restore it back as new?

2. How big would an image be? As big as what's it's copying or? (so I can know what size of a drive to get)

3. Would cloning really work in a dual boot setting? I mean if I tried to restore an image would it restore itself to a partition or just delete both Windows and Ubuntu and install itself?

Hello Kevber, aww, I was hoping to install it the minute it came out...

---

### Post by VMC on 2010-03-12
> **Oreo_King said:**
> 
I only copied what I thought was important. So I guess the boot is on the first drive with Windows XP.Don't confuse the MBR with XP's partition. their totally different.

> **Oreo_King said:**
> 
1. So if Ubuntu was to get super corrupted or crash or whatever an image would restore it back as new?
2. How big would an image be? As big as what's it's copying or? so I can know what size of a drive to get)

3. Would cloning really work in a dual boot setting? I mean if I tried to restore an image would it restore itself to a partition or just delete both Windows and Ubuntu and install itself?

1. Ans- It would restore it to the state of your last image - date & time.
2. Ans- Clonzilla has a default compression. Which is much smaller then the OS. You can request a tighter compression, but it just takes longer.
3. Ans- Clonezilla has the ability to clone parts of a hard drive(partitions), or the whole hard drive.

Reading your boot_info_script, your using grub legacy. I would take Kevbert's suggestion and use either 9.04 or 9.10. That way your using the newer grub2 boot loader. There is a **learning** curve involved :)

---

### Post by Oreo_King on 2010-03-12
For the third question I meant if I was to restore one of my two partitions using an image would it mess up the other partition?

Like if I installed Ubuntu's image, would it mess up XPs?

So there would be no GRUB issue if I installed Lucid Lynx right? GRUB 2 wouldn't lose Windows XP or something? That's what I want to know. :)

---

### Post by VMC on 2010-03-12
> **Oreo_King said:**
> For the third question I meant if I was to restore one of my two partitions using an image would it mess up the other partition?

Like if I installed Ubuntu's image, would it mess up XPs?

So there would be no GRUB issue if I installed Lucid Lynx right? GRUB 2 wouldn't lose Windows XP or something? That's what I want to know. :)

Depending on where you place that image and what program you used.
After you re-image the partition in question you need to issue 'sudo blkid' to see if there are any conflicts and if you MBR grub points to the partition you just re-image then issue the command 'update-grub' from that partition. Clear as mud?! :)

---

### Post by Oreo_King on 2010-03-14
Ahhh! Haha, kind of. 

Well eventually I'll figure it out...and if everything blows up in my face...well you have to learn somewhere. :) (though I really hope it won't)

Thanks for the help though.

---

### Post by ndefontenay on 2010-03-14
After I booted to live CD, I went to Gparted, cleaned my current ubuntu partition.

Then I launch the install, choose to install on the next available contiguous space and voila.

---

### Post by Bucky Ball on 2010-03-14
> **Kevbert said:**
> I would wait a little bit longer until 10.04 becomes a little more stable (especially if your using a Nvidia display adapter). There are also some ubiquity (installer) problems. If you intend to use this PC as your default machine I'd wait at least 1 month after release. 

Wait six. LTS is all I use as I need stability and a spanking new OS is unlikely to give you that. If you like to tweak, experiment and help the community with bug reports, go ahead and install now. There is no rush but if you really want to be on the bleeding edge, download the nightly builds. ...

---

### Post by Oreo_King on 2010-03-15
@ndefontenay: I'm hoping that will happen when I follow a similar approach when Lucid is released. If not VMC's suggestion on CloneZilla will help out.

@Bucky Ball: That's completely true, Bucky Ball. Jaunty was my first Ubuntu (and Linux) version that I had contact with and that was before I knew what LTS was.  I think from now on I'll also wait for the next LTS release.

However I'm one that likes up to date packages and I don't like being stuck with software that's been succeeded. A prime example being Firefox and to a lesser degree OpenOffice.

---

### Post by Bucky Ball on 2010-03-15
An LTS version is only really superceded by another, not a regular release.

Best thing, and I will eventually get round to doing this, is to run an LTS version when you need reliability and on another partition stick the latest greatest bells and whistles release to doodle with and tweak.

---


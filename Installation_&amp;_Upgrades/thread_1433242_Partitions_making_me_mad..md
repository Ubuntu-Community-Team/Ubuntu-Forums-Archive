---
title: "Partitions making me mad."
date: 2010-03-18
forum: Installation &amp; Upgrades
---

### Post by H-Baranov on 2010-03-18
Such a marvellous way to make a first post.
A quick search of the forum and a browse through the latest posts did not reveal the answers to my questions. 

So get comfy. :popcorn:

I'm trying to put Ubuntu onto my 1TB Western Digital External Harddrive. ("So what's the problem H-B?" you're all going, I'm sure.)

Put simply, I have files on there already, and I like my files. They make me happy at night when all I want to do is blow up Nazis or invade Russia with 20 tank divisions and suchlike. They are my games, my photos and most importantly, they are the overflow from my already creaking internal hard-drive.

So. ("Finally") I want to partition my existing stuff into a safe little bubble, away from the big scary Linux-ness - because like I said, it's important to me and it has nowhere else to go. 

This said, Ubuntu's default install partition is "BURN IT ALL!" which makes me do this - ](*,)

And when I try and manually partition it, it says my root file isn't defined. Odd that, cos looking at the feedback Ubuntu gives me on the lovely shiny partition setup-editor-doodah, it's only changed in the respect that I've told you not to turn all 1TB with roughly 1/20th of that occupied, into it's latest host...

Which makes me do this - :mad:](*,)](*,)](*,)

So, delightful forum folks. Any thoughts?
(You can relax now!)

---

### Post by uRock on 2010-03-18
I recommend backing up your data before partitioning your HDD. It may be easier to fire up the LiveCD in the make no changes mode and open the System menu, go to Administration> GParted or Partition Editor, whichever it lists in the menu, then use that to shrink the NTFS partition with all of your "hapiness" then create one large "extended" partition within the free space. Within the Extended partition create;
1.5GB Swap partition,
8GB EXT4 partition,
and one more partition utilizing the rest of the space as an EXT4 partition.

Now you are ready to install. When the partitioning part of the installer comes up select the above partitions and designate them as;
8GB EXT4 mount point= /
Remaining EXT4 mount point =/home

The swap will automatically mount as swap during the install.

Regards,
Ronnie

---

### Post by H-Baranov on 2010-03-18
When I go to GParted it says that my max and minimum size are the entire Terabyte. :S Is it because this is NFTS?

---

### Post by phillw on 2010-03-18
> **H-Baranov said:**
> When I go to GParted it says that my max and minimum size are the entire Terabyte. :S Is it because this is NFTS?

Hi, and welcome to the forums,

from your 1st post, you'll fit right in :D

Okies, as you're running Windows, to save a lot of pain do a de-frag of your disk. Tomorrow, when it has finished ;-) Use the **windows** disk utility tool to shrink your existing windows installation by however much room you wish to give ubuntu. 10GB is enough, but on a 1TB drive, you can possibly afford a little more.

Leave the area you have decreased by unformatted (I recall it is called either unformated or unused - it's quite evident that it is no longer part of windows).

Then re-boot into windows and ensure it is happy (this can take more than one reboot).

Once Win is happy, and you have your unused space, boot with the LiveCD and simply tell it to use the free space on your hard-drive.

All will be well in the world :-)

Regards,

Phill.

---

### Post by H-Baranov on 2010-03-18
I'm actually stuck running the Live CD. My windows is corrupt. (The boot sector nuked itself - Cannot find file WINDOWS/CONFIG/WINDOWS32/SYSTEM) and my setup disk is in Lincolnshire... I am in Manchester, I'm also skint, and unable to legally drive on the motorway, never mind owning a car. Attempts to get a setup disk or to burn an XP setup disk have failed, miserably. Thus since I have two papers due in after the weekend, and the post is TOO SLOW, I'm running to Ubuntu in order to be able to procrastinate in the leisure of my own student squat.

I probably should have mentioned that.

I just want to get my homework done... ](*,)

Is it worth just running it live for as long as I need it, and worrying about fixing it later?

---

### Post by phillw on 2010-03-18
If you're running Vista or Win7, you can download a recovery disk via this How-To, which will allow Windows to re-install its MBR --> [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

If you're running xp-home, I can get a link for that. I don't know of one for xp-professional.

If you need an xp-home recovery disk, then Private Message me and I'll go dig the link up for it. You'll need to have the badge with your license number on the computer for it to work - It isn't and I will not give a method of getting a 'hacked' version. I may not like Microsoft, but I'm against pirates for their OS's as Ubuntu is free :-)

The LiveCD can burn an iso disk, once you have downloaded it.

If you have a memory-stick (usb - about 2GB) then you can install ubuntu onto that in persistance mode, which will allow you to access documents etc from the Windows area, edit and save them onto it.

Regards,

Phill.
P.S. I'm in warrington, so it's not impossible for me to get a disk to manchester.

---

### Post by srs5694 on 2010-03-19
> **phillw said:**
> 10GB is enough, but on a 1TB drive, you can possibly afford a little more.

Technically, yes, 10GB is enough to install Ubuntu. IMHO, though, on a modern system you should devote *at least* three times that much disk space to Linux, and possibly much more, depending on your intended uses. To elaborate, looking at the one Ubuntu system I've got booted at the moment (a dedicated MythTV system), I've got 5.3GB in basic system files. A desktop computer is likely to have more in the way of installed software. For instance, my MythTV box doesn't have Firefox or OpenOffice.org installed. My main desktop system (which runs Gentoo, not Ubuntu) has just over 10GB of system files. Another system I've got (running Fedora) has 7.5GB of system files.

Add to the system files any user files you might generate or use -- documents, digital photos, multimedia files, etc. Depending on your needs, those numbers could be fairly small or truly huge. Individuals will have to judge that for themselves, but I personally would want at least 10GB for these purposes. That would give me enough space to master a single-layer DVD and store the resulting image along with the original files, but not much more.

I read a thread today from another user who complained that he'd been given bad advice on this forum about Ubuntu's disk space requirements. He was rightly miffed at having to take the time and effort to resize partitions after installing Ubuntu, when he could have set up a bigger partition much more easily at the start. I wouldn't want somebody else to feel similarly put out by this.

---

### Post by uRock on 2010-03-19
I have had Edubuntu and Ubunstu Studio along with Most of the debian-science packages installed and never used more than 10GB in the / partition.

---

### Post by H-Baranov on 2010-03-19
My dad is currently conversing with the IT guys at work about getting an xp home .iso sent to me.If that fails he'll have one to me by tonight.

I do have a legit license number though, so don't worry about a hacked version.

Oh, and I might be able to wangle an exty off a friend which is all nice and formatted already :D

---

### Post by phillw on 2010-03-19
kewl !!

I have 9.10 on an usb-stick, it's my "if everything else fails" backup ;-)

You'll have to ask for one next birthday / Christmas ;-)

I got mine from the ubuntu shop, less than twenty quid for a pre-installed 4GB stick, but they're out of stock - I'm guessing next stock will be of 10.04 in about 2 months time.

Regards,

Phill.

---

### Post by srs5694 on 2010-03-19
> **iRock said:**
> I have had Edubuntu and Ubunstu Studio along with Most of the debian-science packages installed and never used more than 10GB in the / partition.

You can certainly get away with this in the *root (/)* partition, but only if you've got *additional* partitions for /home and perhaps other filesystems. The original 10GB suggestion in this thread, though, was to shrink the Windows partition by 10GB and give that 10GB to Linux. Following that advice, Linux would have 10GB for *all* its partitions. IMHO, that's not enough on a modern system. It's also being very miserly on a 1TB disk. If all you can spare from a 1TB disk is 10GB (1%), you need to either do some serious housecleaning on that disk or you need a second or bigger disk! ;)

---


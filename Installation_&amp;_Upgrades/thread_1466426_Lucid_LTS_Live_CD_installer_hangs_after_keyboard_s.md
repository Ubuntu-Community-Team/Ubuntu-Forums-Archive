---
title: "Lucid LTS Live CD installer hangs after keyboard selection (Step 3)"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by andyevans01 on 2010-04-30
Can anyone suggest a way I can get past this?  I have successfully installed Lucid RC on my EeePC 701 netbook at home, but using the same live CD on my Acer Aspire at work, it hangs after the keyboard selection stage (step 3) of the install process.  

Does anyone have any suggestions on how to gather diagnostics, or of any workarounds I might try. After looking through the threads on this forum I have tried the "nomodeset" and removing "quiet splash" from the boot options - bot made no difference at all.

If I allow the live CD to boot it all seems to go fine, and I get the live system up on the PC. Trying to do an install from this system gives me the same hang as it does without loading the live system first.

Any help would be gratefully received.

Best regards

Andy.

---

### Post by cybrt3k on 2010-05-01
Also having the same issue trying to install from USB on an Asus 1005HA.

---

### Post by discostoo on 2010-05-01
I'm having the same issue. Or rather, almost the same issue. Mine hangs immediately after selecting the time zone. The little circular "please wait" cursor appears, then stays there forever.

Here are a few things I've tried, with no success:

[LIST]
[*]Leaving it alone for hours, hoping it was just taking a really long time. No Dice.
[*]Unplugging any hardware that might be causing a problem, including the network card. No dice.
[*]Burning it to CD, DVD, and booting from a USB key. No dice.
[*]Trying every combination of kernel options I could find in the forums, and setting most combinations found in the "more options" menu in the boot screen. No dice.
[*]Booting into the live environment, then installing from there (instead of just choosing "install" directly). No Dice.
[/LIST]

I would appreciate any help in installing this great new long term service release. You know, what with its increased stability and all.

Note: I have *not* tried just upgrading from my 9.10 install, and I will not try this. If I can't get a live CD to boot, there's no way I would voluntarily hose my current system by upgrading.

Thanks!

---

### Post by happ on 2010-05-01
I had the same problem. I solved it changing disk configuration in BIOS from AHCI to IDE. After installation I changed it back to AHCI. So far it works, with some complaining during boot.

---

### Post by discostoo on 2010-05-01
Mine was already set to IDE. For kicks, I tried switching it to AHCI and trying again, but with the same result.

---

### Post by grigoresculiviu on 2010-05-04
I have the same issue.
Switched to AHCI and back with no results.
Going to any of the available consoles will show no text.

I don't know if it is relevant but pressing 'Break' key shows the image below.
[ATTACH]155485[/ATTACH]

Any idea?

---

### Post by S3nd41 on 2010-05-04
I'm having the exact same problem. Tried different keyboard settings but to no avail, any way to troubleshoot this problem?

---

### Post by Skaperen on 2010-05-04
I had the same problem on one computer.  Turns out the geometry in that partition table used 256 heads per cylinder.  That IS valid (and fdisk can handle it) despite a lot of documentation that says otherwise.  But the installer partition editor can't (and apparently a lot of other software can't, either).  My solution was to boot into a live CD, erase the MBR to binary zero and do over (let the installer make a new MBR how it likes).  If you have no data on the drive to keep, try that.

**WARNING: THESE STEPS WILL LOSE ALL DATA ON THE SPECIFIED DRIVE!**

1.  Boot to a live CD.
2.  Open terminal.
3.  Do command "sudo dd if=/dev/zero of=/dev/sda bs=512 count=1"
4. Boot again and do the install.

**WARNING: THE ABOVE STEPS WILL LOSE ALL DATA ON THE SPECIFIED DRIVE!**

---

### Post by S3nd41 on 2010-05-05
Hello Ska,

What can I use to check if my disk is using 256 or 512?

Thank you!

EDIT: Checked it with Gparted and it does seem that it's 256. Do I need to backup the entire disk or just the boot partition?
Tried erasing my MBR and I could install it like that but, obviously, i want my old partitions back so I restored the old MBR and I'm back to where I was.
Maybe if I create my Ubuntu partition and move it to the first sector it'll work? Or if I just flag it as the boot partition?!

---

### Post by Rajji on 2010-05-06
Hey all, 

I tried all the above on my inspiron mini v10 but when booting on live (usb) it still hangs at step 3.

I also tried net install and there it hung on partioning scanning disks.

So can someone give some more tips.

THX

---

### Post by S3nd41 on 2010-05-06
If I create an image of my windows partition, run the above command and then restore it back to a new partition after changing the blocksize to 512, will it work?

---

### Post by Skaperen on 2010-05-06
> **S3nd41 said:**
> Hello Ska,

What can I use to check if my disk is using 256 or 512?

Thank you!

EDIT: Checked it with Gparted and it does seem that it's 256. Do I need to backup the entire disk or just the boot partition?
Tried erasing my MBR and I could install it like that but, obviously, i want my old partitions back so I restored the old MBR and I'm back to where I was.
Maybe if I create my Ubuntu partition and move it to the first sector it'll work? Or if I just flag it as the boot partition?!
I assume you mean it's 256 as in number of heads.  512 isn't a valid option for that.  The block size (number of octets per sector) is 512 (new disk drives in the very near future will be 2048 or 4096 ... so beware).

What you need to do is get the EXACT sector number (LBA) for each partition you want to keep, write it down on paper (first sector and last sector for each, and which partition number).  Then in a live CD (do "sudo bash" first to be root), erase the MBR, then create a new MBR with a tool like "fdisk" that allows exact sector entry (in "fdisk" type the "u" command to toggle the entry mode).  Check the geometry with the "p" command (fdisk).  If it is still 256 heads, you need to switch to the "extra functionality expert" mode to change it.  Once you've entered LBA sectors with the geometry set, it should store the CHS addresses (geometry isn't literally stored ... it's figured out each time).  Save the MBR and then try to mount the partitions to see if you can access the files.  If you can, maybe you can make a backup at this time.  Once satisfied, go back and try the install, again.

---

### Post by S3nd41 on 2010-05-08
Hello Ska,

Thank you for your reply. 
I kinda subverted the process, created a disk image of my Win7 partition with Ghost running off BartPe, then erased the MBR, created the linux and swap partitions, installed and will (eventually) restore my Win7 partition.

Now I'm having a problem related to my gfx card but I'll create a post about that : )

Tyvm!

---

### Post by discostoo on 2010-05-08
Here's the output of fdisk -l, I don't really know what all this junk means:

```

$ sudo fdisk -l /dev/sda

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00066051

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *           1       10334    83007823+   7  HPFS/NTFS
/dev/sda3           10335       77825   542121457+   5  Extended
/dev/sda5           10335       17037    53841816   83  Linux
/dev/sda6           17038       69801   423826798+  83  Linux
/dev/sda7           69802       76852    56637126   83  Linux
/dev/sda8           76853       77825     7815591   82  Linux swap / Solaris

```

And here's something from the cfdisk manpage:

> 
When partitioning an empty large modern  disk,  picking  255  heads  and  63 sectors/track  is  always  a  good  idea.   There is no need to set the number of cylinders, since cfdisk knows the disk size.


This disk was partitioned by Ubuntu, in Ubuntu, for Ubuntu. And it's worked with every other version before this, and several other distros. I don't see how rewriting my disk would make the installer not hang. And if this *is* necessary, then there's no way in hell I'm ever installing 10.04.

Does anyone have any ideas about fixing this?

---

### Post by grigoresculiviu on 2010-05-08
I have just been able to install ubuntu. It seems the reason for my problems were the way I created the USB stick installer.
Initially I created it by using usb-creator-kde from 9.10 in order to install a 10.04 image. This resulted in an unusable image as I descrebed in an earlier post.
Now I'm using the unetbootin-windows-442.exe from windows and it works fine.

---

### Post by bfarina on 2011-07-22
After beating my head against a wall for days while trying to install from a USB stick, I read on another site that simply trying a different stick might work.  I dug around, found an old 1GB stick, installed the OS on that and presto, it installed on my netbook on the first try.

:guitar: Whooooo!

---

### Post by mattotoole on 2011-07-26
I'm having the same problem, as are many others.  I've searched around and found suggestions like the above -- trying different installation media, etc.

I've had no luck with any of that.

I'm using a Thinkpad T42.  It hangs while booting the system from a USB stick.  But if I select Install, which fails at select keyboard, then cancel the installer, it leaves me with a functioning system, running from the USB.

I don't know why it boots fine from one but not the other.

I was getting error messages about sd0, so I removed my CD drive which isn't working.  I got past that, to where I'm getting error messages about gParted causing installation to fail.  So I tried starting gParted from the menu and it crashes.  I believe there's a bug filed about gParted causing installation failure at select keyboard.

Any ideas?

I'm going to keep trying.

---


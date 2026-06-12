---
title: "GRUB won't install with Windows 7"
date: 2012-06-15
forum: Installation &amp; Upgrades
---

### Post by barefootNH on 2012-06-15
Yesterday I tried to install 12.04 onto a factory-fresh Acer Aspire One 722 that has Windows 7 Home Premium already installed, but it resulted in an error that I had never even heard of before: it said GRUB can't be installed with Windows 7. I have no idea what to do next.

After a week of updating and more updating and beating on my new Windows 7 laptop, making sure everything was working, I felt that it was ready for a real operating system.

Before I tried to install 12.04 onto my new laptop I made a liveCD (onto a USB flash drive) and booted from that (keeping the 'network boot' as the first boot option in the BIOS, a well-known hardware bug in the Aspire One), and ran 12.04 through its paces, and it seemed to work perfectly, including audio, video, wireless, and my VPN configuration.

I first used Windoze to repartition the massive, single 500 GB partition into something more intelligent before attempting to install 12.04. I loaded the alt-64 iso onto a USB flash drive and started in. 

The installer got all the way to the end where it said that it detected Vista already installed, and do I want to work along side of it (do I want to dual-boot, or whatever its wording was, which I expected it to ask). (Yes, it said it detected Vista; since I have seen Vista and Windows 7 associated together in the media regarding certain problems, I just assumed they are somehow related and that the installer wasn't really making a critical mistake.) I of course said 'yes', but an error then appeared that GRUB couldn't be installed with Windows 7 (or something like that). I aborted the installation, turned to the Web for help, but there isn't any help!

My first experience with Linux was Ubuntu 9.04. I installed 9.04 (barf), 9.10 (barf), 10.04 (nice!!!), and 11.04 along side of factory-fresh Vista on my other Acer laptop, and it installed flawlessly each time. Over these years I've also installed K/X/L/Ubuntu/Mint/openSUSE/32/64 on numerous desktops of various pedigrees that already had Windoze XP, and they always installed flawlessly, so this problem took me by surprise. 

Searching the Web I did find some old comments (3-4 years old) about Vista causing problems during GRUB installation, and that a bootloader other than GRUB was needed, but there were mixed results with all of those answers.

This problem must be a very common one, but I don't see any answers or comments in the official (and always ancient) documentation about this, nor have I found any recent unofficial support. I see some comments and help regarding Vista blocking other bootloaders, with inconsistent results, but I don't see any definitive answers. Windows 7 isn't new!

Thank you for your help!

---

### Post by darkod on 2012-06-15
Why the alternate, since you alreayd had the live cd to try and it worked, why not simply install with that?

In any case, have you tried using the manual partitioning/install? It gives you more control and sometimes avoids some issues that the auto method can't figure out. Although I can't see why the alt-64 would fail too.

If I remember correctly, the question about how you want to install is towards the beginning, not the end of the process. I wonder if something weird took place.

I would try the manual way anyway, with the live or alt cd, your choice.

---

### Post by wilee-nilee on 2012-06-15
That model from a quick search uses a amd processor.
[http://us.acer.com/ac/en/US/content/series/aspireone722](http://us.acer.com/ac/en/US/content/series/aspireone722)

---

### Post by barefootNH on 2012-06-15
> **darkod said:**
> Why the alternate, since you alreayd had the live cd to try and it worked, why not simply install with that?

In any case, have you tried using the manual partitioning/install? It gives you more control and sometimes avoids some issues that the auto method can't figure out. Although I can't see why the alt-64 would fail too.


I used alternate to do a manual install to include encrypted LVM. All that worked fine because I followed a tutorial. The tutorial was outdated (written for 11.04), and there were a couple extra screens in 12.04, but it went fine.

Everything seemed normal until the end when the problem occurred trying to install GRUB.

---

### Post by barefootNH on 2012-06-15
> **wilee-nilee said:**
> That model from a quick search uses a amd processor.
[http://us.acer.com/ac/en/US/content/series/aspireone722](http://us.acer.com/ac/en/US/content/series/aspireone722)

That's correct. I would not think that would affect the installation of 12.04; am I wrong? I know for a fact that there are different OEM versions of Windows depending on whether it's being installed on an Intel or an AMD (it affects just one bit in the registry!).

It also has 4 GB DDR3, 500 GB HD; incredible for such a tiny laptop.

Being so very popular, I never expected any glitch trying to install Ubuntu onto an Aspire One, especially since they used to be offered with a version of Linux. I definitely think it's a Windoze problem. There's new alphabet soup these days: EFI, GPT, and stuff like that; maybe that has something to do with it.

Then there's that recent stink about Microsoft protecting the hard drive  or MBR or whatever to prevent any other operating systems from being  installed onto the computer.  Maybe that's it?

---

### Post by darkod on 2012-06-15
If you run in live mode:
```
sudo fdisk -l
```

it will show whether the first partition is EFI system partitions and whether the disk is with gpt table. If it is, it complicates thing a little but I think it's doable (never tried it though).

---

### Post by wilee-nilee on 2012-06-15
> **barefootNH said:**
> That's correct. I would not think that would affect the installation of 12.04; am I wrong? I know for a fact that there are different OEM versions of Windows depending on whether it's being installed on an Intel or an AMD (it affects just one bit in the registry!).

It also has 4 GB DDR3, 500 GB HD; incredible for such a tiny laptop.

Being so very popular, I never expected any glitch trying to install Ubuntu onto an Aspire One, especially since they used to be offered with a version of Linux. I definitely think it's a Windoze problem. There's new alphabet soup these days: EFI, GPT, and stuff like that; maybe that has something to do with it.

**Then there's that recent stink about Microsoft protecting the hard drive  or MBR or whatever to prevent any other operating systems from being  installed onto the computer.  Maybe that's it?**

I'm not sure if this has been implemented yet but that was my first thought, I believe some computers are released now with this lock though.

But your best help here is the other helper darkod really.

---

### Post by darkod on 2012-06-15
On top of the above, depending what fdisk says, you can always try to chroot into the installation from live mode, and try to install grub2 to the MBR.

I see two potential problems, while waiting to see if you are in EFI mode:
1. EFI + GPT without the necessary bios_grub partition. Grub2 wouldn't install in this case.
2. The encrypted LVM without separate /boot partition. Earlier a separate /boot was a must with LVM, these days it seems it's not but I don't know about using encrypted LVM. In case it needs it, do you have separate /boot?

If you decide to try something with chroot, I also don't have experience with mounting encrypted LVM from live mode.

---

### Post by barefootNH on 2012-06-15
> **darkod said:**
> If you run in live mode:
```
sudo fdisk -l
```it will show whether the first partition is EFI system partitions and whether the disk is with gpt table. If it is, it complicates thing a little but I think it's doable (never tried it though).

I just happened to have it sitting right here with a liveUSB!

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x3800937d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    27265023    13631488   27  Hidden NTFS WinRE
/dev/sda2   *    27265024    27469823      102400    7  HPFS/NTFS/exFAT
/dev/sda3        27469824   283469823   128000000    7  HPFS/NTFS/exFAT
/dev/sda4       283471870   976771071   346649601    f  W95 Ext'd (LBA)
Partition 4 does not start on physical sector boundary.
/dev/sda5       283471872   795471871   256000000    7  HPFS/NTFS/exFAT
/dev/sda6       795473920   976771071    90648576   83  Linux
```[FONT=Courier New]
[/FONT]
Windoze (or Acer?) uses the first 13GB (sda1) as a recovery partition, from where the buyer is to generate their own recovery DVDs, or in this case, recovery USB sticks.

The next 100 MB partition (sda2) Windoze calls System Reserved. From looking at the above output it's apparently the boot partition.

The next partition (sda3) WAS the entire remainder of the hard drive: almost 500 GB. I used Windoze to shrink sda3 down to about 125 GB, with the rest being Extended (although they didn't call it that). 

I then made sda5 to be about 250 GB (for use as a shared data partition between Windoze and Linux), and then made sda6 to be about 125 GB to be the Linux partition. (Between GB and GiB, and their restore files in the way, and then their MFT being in the way, I'm satisfied with what Windoze floundered around with and finally gave me regarding the inaccuracies in all the sizes!  lol)

---

### Post by darkod on 2012-06-15
OK, that's msdos table, which means you are not using EFI since win7 can't work on msdos with EFI.

So, if you try another install now, but select the manual partitioning, delete sda6 and from the unallocated space make a 300-500MB /boot and use the rest as encrypted LVM. Do you know to do the installation manually or you depend on the auto method?

I hope it will works manually, especially with separate /boot even if they say it's not needed any more.

---

### Post by barefootNH on 2012-06-15
> **darkod said:**
> On top of the above, depending what fdisk says, you can always try to chroot into the installation from live mode, and try to install grub2 to the MBR.

I see two potential problems, while waiting to see if you are in EFI mode:
1. EFI + GPT without the necessary bios_grub partition. Grub2 wouldn't install in this case.
2. The encrypted LVM without separate /boot partition. Earlier a separate /boot was a must with LVM, these days it seems it's not but I don't know about using encrypted LVM. In case it needs it, do you have separate /boot?

If you decide to try something with chroot, I also don't have experience with mounting encrypted LVM from live mode.

If encrypted LVM is more trouble than it's worth then I'll forget about it and use Ubuntu's "encrypted home directory" technique that I've used in the past. I just wanted the additional security, it looked rather easy (and it was by following the tutorial), and I wanted to experiment and get the experience.

If I abandon the encrypted LVM, I might then add a partition for use by TrueCrypt.

I do not have a separate /boot because there is already a boot partition, and a tutorial said I didn't need one if there is already a boot partition (which there is if Windows is already installed). A /boot is required if Linux is the only OS. Just quoting what I read. Please correct me if I'm wrong.

---

### Post by darkod on 2012-06-15
Sounds wrong to me. The windows system reserved is still ntfs while ubuntu would use ext2/3/4. They probably meant if /boot already exists. This might be the step missing.

Ubuntu will definitely not put any of its boot files on sda2. That is the partition only for the win7 boot files. Other OSs can't use it.

---

### Post by barefootNH on 2012-06-15
> **darkod said:**
> Sounds wrong to me. The windows system reserved is still ntfs while ubuntu would use ext2/3/4. They probably meant if /boot already exists. This might be the step missing.

Ubuntu will definitely not put any of its boot files on sda2. That is the partition only for the win7 boot files. Other OSs can't use it.

I've never set up a /boot before. When Windows is already installed, the most I've ever done, and seen done in the tutorials is setting up /, /home, and swap. It's in those tutorials where I've seen stated that a /boot is not required.

Or am I now crossing into different territory because I'm trying to use LVM?!

And yes I'm familiar with manual partitioning and using the manual installation, and that's what I used with the Alternate64 iso.

---

### Post by darkod on 2012-06-15
On a "standard" install boot is just a folder in / unless set up otherwise.

But LVM is a whole different ball game, especially encrypted. As I said in one of my earlier posts, until recently grub couldn't even boot LVM (unencrypted) without separate /boot partition. I guess it couldn't find them on the LVM or load the module, or what ever.

I have seen it mentioned that now grub2 can boot LVM just fine without separate /boot, but that was for unencrypted also. Not sure if the same applies for encrypted.

And just in case, anyway, I would still rather use separate /boot with LVM regardless whether encrypted or not, just the same as when it was necessary.

Give it a shot, what do you have to lose, 30mins of your time. :)

---

### Post by barefootNH on 2012-06-15
> **darkod said:**
> On a "standard" install boot is just a folder in / unless set up otherwise.

But LVM is a whole different ball game, especially encrypted. As I said in one of my earlier posts, until recently grub couldn't even boot LVM (unencrypted) without separate /boot partition. I guess it couldn't find them on the LVM or load the module, or what ever.

I have seen it mentioned that now grub2 can boot LVM just fine without separate /boot, but that was for unencrypted also. Not sure if the same applies for encrypted.

And just in case, anyway, I would still rather use separate /boot with LVM regardless whether encrypted or not, just the same as when it was necessary.

Give it a shot, what do you have to lose, 30mins of your time. :)

Yes, I want to do this to learn and get the experience.

I think I can "steal" a little time here at work to do this; I'm doing this now.

---

### Post by barefootNH on 2012-06-15
> **barefootNH said:**
> Yes, I want to do this to learn and get the experience.

I think I can "steal" a little time here at work to do this; I'm doing this now.

YES!!! That was it!

Set up 500MB for /boot prior to LVM (was sda6), continued to set up encrypted LVM as before (was sda7), and it went perfectly. 

I now got the expected GRUB boot menu, booted successfully to 12.04, restarted and booted successfully to Windoze 7.

Looks like it's a success!

Thank  you!

---

### Post by darkod on 2012-06-15
You are welcome. Enjoy it now.

Please mark the thread as Solved, you can do that in Thread Tools.

---


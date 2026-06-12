---
title: "Partitioning for dual boot"
date: 2014-05-08
forum: Installation &amp; Upgrades
---

### Post by luis_valdivieso2 on 2014-05-08
Hi I want to have both ubuntu and windows. I initially had Windows7,  then tried to install Ubuntu "alongside with it" but it caused me to  lose windows. So now I'm trying to do it in reverse. I know I have to  resize my big partition to make space for the windows NTFS and then have  another NTFS if I want to share between them. So I get the general  idea, however I can't seem to resize the sda3 from a Ubuntu  Live CD (as suggested in some tutorials).

"sudo parted -l" gives me this:
> Model: ATA WDC WD10EARX-32N (scsi)
 Disk /dev/sda: 1000GB
 Sector size (logical/physical): 512B/4096B
 Partition Table: gpt
 
 Number  Start   End     Size    File system  Name                          Flags
  1      17.4kB  134MB   134MB                Microsoft reserved partition  msftres
  2      134MB   135MB   1000kB                                             bios_grub
  3      135MB   994GB   994GB   ext4
  4      994GB   1000GB  6374MB
 
 
 Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
 has been opened read-only.
 Error: Can't have a partition outside the disk!         


Currently in gparted

Do I have to unmount sda3 to be able to shrink it? I have found a few tutorials about partitioning but I can't proceed to the next steps because I can't resize sda3...

Yes, I already have backed up my personal files.

---

### Post by Slopsbucket on 2014-05-08
Hi Luis,

Yes, the partition needs to be unmounted before you can resize it.

Try booting from a live disk and then running Gparted.

If your Ubuntu disk doesn't have gparted then you can download a Gparted boot disk, just google for it.

Cheers,

Andrew.

---

### Post by luis_valdivieso2 on 2014-05-08
Thank you.  I did boot from a liveCD. I was afraid to unmount because I read somewhere it could potentially cause problems. Just wanted to make sure. 


Should I split it 33/33/33? NTFS for Windows OS, Ubuntu and sharing? What's the ideal/recommended size for each section? Also what's the pros and cons of having my $home separate from my primary sda?

---

### Post by Slopsbucket on 2014-05-08
Hi Luis,

Please understand that I'm no guru here, just another user like yourself.

I boot 4 systems at the moment, although after trying Ubuntu for a few days I think both my Fedora's are going to get dumped.

The problem you may have is different boot systems. My Windows is the old XP which requires the old MBR type boot sector (now called Legacy boot). It can't exist on the same harddrive as the newer systems using UEFI boot.

However, if your Windows is either Win7 64 bit UEFI or Win8 there shouldn't be a problem.

As for how much space is required, my old WinXP only has 150 Gb. The system itself only requires about 3 Gb and the rest is just for games. I've even got Sims3 running in there with about a dozen expansion packs and I've still got 40 Gb free.

Because I like to play around with different systems so much I always keep one harddrive just for storage of stuff I want to keep like pictures and my music collection. Saves me a lot of heartache when I want to play with a new system, especially considering how cheap harddrives are these days. If the installer is as confusing as Ubuntu's then I just unplug my storage drive before installing, guarrantees that it won't suffer from any mistakes.

Cheers,

Andrew.

---

### Post by luis_valdivieso2 on 2014-05-08
> **Slopsbucket said:**
> Hi Luis,

Please understand that I'm no guru here, just another user like yourself.

I boot 4 systems at the moment, although after trying Ubuntu for a few days I think both my Fedora's are going to get dumped.

The problem you may have is different boot systems. My Windows is the  old XP which requires the old MBR type boot sector (now called Legacy  boot). It can't exist on the same harddrive as the newer systems using  UEFI boot.

However, if your Windows is either Win7 64 bit UEFI or Win8 there shouldn't be a problem.

As for how much space is required, my old WinXP only has 150 Gb. The  system itself only requires about 3 Gb and the rest is just for games.  I've even got Sims3 running in there with about a dozen expansion packs  and I've still got 40 Gb free.

Because I like to play around with different systems so much I always  keep one harddrive just for storage of stuff I want to keep like  pictures and my music collection. Saves me a lot of heartache when I  want to play with a new system, especially considering how cheap  harddrives are these days. If the installer is as confusing as Ubuntu's  then I just unplug my storage drive before installing, guarrantees that  it won't suffer from any mistakes.

Cheers,

Andrew.
I don't have any windows yet, just Ubuntu. I had windows7 but lost it. Now I'm making place to re-install the windows7 OS again and hopefully be able to boot both.


[IMG]http://i.imgur.com/fqO3VMB.png[/IMG]

Is this reasonable? What should I do with sda1, sda2 and sda4? Leave them as they are or format them?  Sorry this is the first time I do this I want to make sure I'm not making a big mistake in this step.

---

### Post by Slopsbucket on 2014-05-08
Hi Luis,

the 128 MB partition you've left for NTFS isn't big enough for anything. and reducing the size of your sda3 partition is going to make room AFTER or behind that partition so sda1 will still be useless.

Also, Windows really does not play very nicely with other operationg systems, if you install Windows after installing Linux it will wipe out the Linux boot partition (deliberately) and you will have to re-install the linux boot partition again.

I suggest you wait until you've got your new copy of Win7. Install Windows first, during setup you can tell it to only format 150 Gb of the drive.

Then once that's sorted install Linux, I would suggest that If you're still using Windows as much as Linux then you only allow another 150 Gb for the Linux /home partition, that should leave about 600 Gb of free space on the end of the drive that you can format to NTFS so that both systems can access the files in there.

I'm sorry but installing Linux first and then trying to put Windows in afterwards really is making life harder than it needs to be.

Cheers,

Andrew.

---

### Post by luis_valdivieso2 on 2014-05-08
> **Slopsbucket said:**
> 
I'm sorry but installing Linux first and then trying to put Windows in  afterwards really is making life harder than it needs to be.

Cheers,

Andrew.

Well I'm following this tutorial and they're doing it with Ubuntu first then Windows. They have simple commands to reset the MBR to use GRUB 2,  then mount the Ubuntu partition and point GRUB2 to the right sda. It doesn't look so bad lol.


> the 128 MB partition you've left for NTFS isn't big enough for anything.  and reducing the size of your sda3 partition is going to make room  AFTER or behind that partition so sda1 will still be useless.
I didn't change it though. It was already at 128 MB but I couldn't make it bigger or move it. So I only formatted it to NTFS but initially it was something else. Does windows really need to be installed on sda1? I thought I could just put it in that other NTFS I created.

Should I delete all other partitions? I only need 3 right?

---

### Post by luis_valdivieso2 on 2014-05-09
So I've seen two methods of doing this. One method uses a USB 64 bit  Ubuntu to reinstall GRUB2 after Windows erases it. And the other method  only uses command lines from a Ubuntu LiveCD. Since command line seems quicker this is what  I'm trying first:

  > sudo mount /dev/sda1 /mnt

This will mount your ubuntu / partition.

Next in terminal run:

sudo grub-install --root-directory=/mnt/ /dev/sda

This will reset the MBR to have GRUB 2 and point it to sda1. You can then reboot and you should be good to go.

Now  my question is do I have to mount and point to sda1? Because if you  look at the pictures I took, I'm pretty sure all my Ubuntu files are in  sda3. So I'm thinking I need to change sda for sda3 in the command lines  but I'm not 100% sure..

---

### Post by luis_valdivieso2 on 2014-05-09
So I couldn't install windows Vista (which I need to then upgrade to windows7 :/ )

[IMG]http://i.imgur.com/IKu9Hi7.jpg[/IMG]

After a quick search I learn that:

> Booting from GPT is only supported for 64 bit editions of Windows 7 (and Vista) on UEFI based systems.


I have a 64 bit edition of Vista.. So I'm guessing my system isn't UEFI based? How can I know?

What are my options now? I'm stuck with a GPT style partition and Windows Vista... pls help. I used the format option but "new" is greyed out.

---

### Post by luis_valdivieso2 on 2014-05-09
delete this post pls. I wanted to edit above post

---

### Post by oldfred on 2014-05-09
Is your system both UEFI & BIOS?

Windows will only install to a gpt partitioned drive with UEFI.
Both Windows & Ubuntu will only install to MBR(msdos) drives in BIOS boot mode.

You have a gpt partitioned drive and the first 128MB is a system reseved which Windows often makes when formatting with gpt. But does not confirm if system is UEFI or not.
You can convert your Ubuntu install to UEFI if needed.
But you really should have an efi partition near the beginning of the drive if installing in UEFI mode.

The standard Windows 7 DVD only installs in BIOS mode and will just convert  a gpt drive to MBR and leave it with backup gpt table incorrectly. You then have to use fixparts to fully convert to MBR.

You can convert a Windows 7 DVD to a flash drive an make updates to have it work with UEFI.

But bottom line we need to know first if system is both UEFI and BIOS.

---

### Post by luis_valdivieso2 on 2014-05-09
> **oldfred said:**
> Is your system both UEFI & BIOS?

Windows will only install to a gpt partitioned drive with UEFI.
Both Windows & Ubuntu will only install to MBR(msdos) drives in BIOS boot mode.

You have a gpt partitioned drive and the first 128MB is a system reseved which Windows often makes when formatting with gpt. But does not confirm if system is UEFI or not.
You can convert your Ubuntu install to UEFI if needed.
But you really should have an efi partition near the beginning of the drive if installing in UEFI mode.

The standard Windows 7 DVD only installs in BIOS mode and will just convert  a gpt drive to MBR and leave it with backup gpt table incorrectly. You then have to use fixparts to fully convert to MBR.

You can convert a Windows 7 DVD to a flash drive an make updates to have it work with UEFI.

But bottom line we need to know first if system is both UEFI and BIOS.
What's the best way to know if my system is BIOS, UEFI or both?

I ran this command: 

dmesg | grep "EFI v"

And it returned nothing. Someone said this means my system is using BIOS otherwise it would return something about EFI. I also tried "/sys/firmware/efi" and it didn't find anything.

So from what I'm understanding, the HDD I'm using (which I replaced) is GPT but my CPU system is BIOS.

I was still able to install Ubuntu but I can't reinstall Vista. Which makes little sense to me because Windows7 was running just fine before on the same disk and CPU.

---

### Post by oldfred on 2014-05-09
But did you convert drive to gpt with the Ubuntu install? But I do not think it would have just automatically converted to gpt unless drive is  over about 1.5TB and you are using entire drive.

Almost no installs of Vista and only a few installs of Windows 7 used UEFI by default. 

Windows will not install to a gpt partitioned drive unless you boot installer in UEFI boot mode.
And even Windows 7 DVD must be converted to flash drive and updated to include UEFI boot capability. Not even sure I have ever seen similar instructions for Vista.

---

### Post by luis_valdivieso2 on 2014-05-09
> **oldfred said:**
> But did you convert drive to gpt with the Ubuntu  install? But I do not think it would have just automatically converted  to gpt unless drive is  over about 1.5TB and you are using entire  drive.
Is it possible that a virus converted my drive to GPT? Because the  main reason why I installed Ubuntu was because I couldn't boot my  Windows7 anymore, I couldn't even launch safe mode, boot repair or  system restore. So I assumed it was a virus.

If it's not a virus,  then it's Ubuntu when I tried to install it "alongside with Windows"  using the recommended settings. This completely erased all my windows  files and, I assume, converted the drive to GPT. This was a noob mistake  from my part as I didn't understand that I had to manually  resize the partitions back then. I simply trusted Ubuntu's recommended  settings.

Now I've been using Ubuntu for a while, but recently  tried again to have both OS. I used a Ubuntu Live CD and gparted to  resize my sda3 partition to make unallocated/NTFS space for windows and  for sharing. But now I can't install Vista, because as you said, it can  only install on a GPT drive on a UEFI system.

That is all I know. I doubt I converted it myself to GPT because I don't even know how.

So  is there any way at all to convert my drive to something else than GPT?  Or to make a EFI disk partition within my BIOS system? I don't mind  losing my files because I have them backed up already. But preferably  without losing too much.

---

### Post by oldfred on 2014-05-09
Is your system new enough to have UEFI?
Never heard of a virus, but you may have clicked on something to change drive to gpt.

You can convert a drive to MBR, but have to reinstall grub2's boot loader and update fstab. Be sure to have good backups. And working Ubuntu repair or live mode installer to run all the fixes.

       Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)
You then need to use gdisk to convert from gpt to MBR
[http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr](http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr)

---

### Post by luis_valdivieso2 on 2014-05-09
> **oldfred said:**
> Is your system new enough to have UEFI?
Never heard of a virus, but you may have clicked on something to change drive to gpt.

You can convert a drive to MBR, but have to reinstall grub2's boot loader and update fstab. Be sure to have good backups. And working Ubuntu repair or live mode installer to run all the fixes.

       Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)
You then need to use gdisk to convert from gpt to MBR
[http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr](http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr)
Thank you very much for the help and the links! I will try that and report back. :)

And my system is from like 2008. So I don't think it's UEFI compatible.

---

### Post by oldfred on 2014-05-10
Only because you have that Windows system reserved 128k partition, that says you created the gpt partitioned drve from Windows or Windows tools. Linux would not create that. That partition is a Windows requirement on gpt drives and must before the first NTFS system (bootable) partition, so Windows seems to just create it by default on newly partitioned gpt drives.

---


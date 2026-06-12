---
title: "Dual-boot problems"
date: 2018-06-04
forum: MINT
---

### Post by arraveci on 2018-06-04
Hi, I apologise if this is the wrong sub-forum to post this in, and if I'm on the wrong site entirely- I've got linux mint cinnamon, but I don't think the problem is with linux per se.

I dual-booted my laptop awhile back, starting from windows 10 and adding a partition with linux, using grub as the main boot loader etc, and it's been working fine for the most part, experienced some slow down over time which I thought was normal wear but now my windows won't boot any longer. Linux works just fine, and I've tried boot-repair, it first thought that there wasn't enough space in my windows partition, so I deleted a portion of files. It's since stopped giving that notification and the recommended repair doesn't pick up anything wrong.

When I try to boot up the windows partition through grub, it either gives a black screen with randomly coloured dashes across it in a sort of pattern, or it brings me to a repair and diagnostics section, where it gives me the options to reset, return to a system restore point (which doesn't work because I don't think I made one), return to a previous version which also doesn't work (though I thought that the partition with windows recovery should be able to handle that), or command prompt etc, but nothing's worked thus far. I've tried resetting, and it gets to a certain point before it starts undoing the changes for some reason that it won't tell me.

If anyone can provide any help I'd be very grateful, even if it's just in pointing out it's a lost cause and maybe pointing me towards accessing the files in the windows partition through linux so that I can transfer them over, and potentially deleting windows outright to just run linux, any help would be appreciated, though I would definitely prefer to keep windows available since that's what I'm used to using.

Thanks for the time you've taken even to read this!

---

### Post by oldfred on 2018-06-04
Did a Windows update (which may have been in back ground) turn fast start up in Windows back on?

Just to confirm configuration is otherwise ok.
       May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by arraveci on 2018-06-04
Hi oldfred, this is one of the summary reports since I'd stopped getting the memory error for the partition: [http://paste.ubuntu.com/p/RP59mjyZny/](http://paste.ubuntu.com/p/RP59mjyZny/)

Is this running the correct version of boot-repair? I can run it again and get a new one if that would be more helpful, or if it's the wrong version (not the ppa version), I can install that instead and run it. Otherwise is there a way for me to check if fast start up has been turned back on from linux?

---

### Post by oldfred on 2018-06-05
Moved to Mint sub-forum.

Looks like you have UEFI hardware as it mentions Haswell.
But both Windows & Mint are installed in BIOS boot mode with MBR(msdos) partitioning.
You cannot easily convert from BIOS/MBR to UEFI/gpt, so just be sure to always boot in BIOS boot mode.

Your partitioning is very strange.
Windows normally has a 100MB boot partition, but you have all Windows boot files in the larger NTFS partition. That does work, just not the standard configuration.
Your sda4 says Xenix which just about has to be wrong and that may have been some of the issues?
Do not know what it was, but vendors often have a recovery partition, was it that? With my one Windows system once I made the backups it offered to delete the vendor back up partition.

Windows 10 really works better with UEFI. It will turn fast start up on with updates.
And grub only boots working Windows or Windows that does not have fast start up on or need chkdsk which often is required after abnormal shutdown.
And then you have to use your Windows repair/recovery flash drive and its repair console to temporarily install the Windows boot loader to MBR and repair Windows. 
Then you need your Ubuntu live flash drive to reinstall grub to MBR. Not sure how often Windows does this, but have seen it on last major update and others have reported it.

So always have a Windows repair flash drive and Ubuntu live installer, so you can fix your system.

With UEFI, you can always directly boot Windows from UEFI as both Windows & Ubuntu's boot loaders are installed and each works independently.  So while best to still have repair flash drives, you often can just reboot via UEFI into Windows an make fixes.

---


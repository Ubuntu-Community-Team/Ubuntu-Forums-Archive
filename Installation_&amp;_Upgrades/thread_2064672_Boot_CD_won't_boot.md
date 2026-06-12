---
title: "Boot CD won't boot"
date: 2012-09-29
forum: Installation &amp; Upgrades
---

### Post by karat on 2012-09-29
I have a similar problem.  I tried two different bootable CDs.  The 9.08 CD didn't even get recognized and got bypassed during booting, while the 12.04 CD said "Error reading volume label" before the menu and "Error reading file.  Press any key to continue" after making any selection.  Both install CDs work on my old laptop.  Both were burned on different machines, but neither by the machine I'm installing onto.  The installing machine (ie the new one I got today) can read both CDs and list the contents of each.  It can also boot a windows install disk.

I am currently downloading an image to burn from the drive of the machine I am installing on, but why should that matter?  If I can't read a CD burned on another machine, doesn't that mean my drive is broken?

What other information can I get?  What other tests can I run?

Thanks

PS I'm not clear on the etiquette of reusing threads versus starting new ones.  Please let me know if I should start my own thread instead.

---

### Post by oldfred on 2012-09-29
Moved to your own thread although issue is similar. When issues are the same and you can contribute to OP's issues then being in the same thread is ok ( I think.). Not a hard/fast rule. 
But most boot issues are unique as hardware varies, versions vary and other issues. Best to be separate issue.

How far do you get on booting. Do you get accessibility icons, have you tried boot options?

What hardware is it you are installing into?

---

### Post by karat on 2012-09-30
> **oldfred said:**
> Moved to your own thread although issue is similar. When issues are the same and you can contribute to OP's issues then being in the same thread is ok ( I think.). Not a hard/fast rule. 
But most boot issues are unique as hardware varies, versions vary and other issues. Best to be separate issue.

How far do you get on booting. Do you get accessibility icons, have you tried boot options?

What hardware is it you are installing into?

I don't get the accessibility icons with either disc.

I tried F12 to boot off the 12.04 disc, but I got the error messages above, followed by a kernel panic.  Just now, I tried F2 to edit the priority menu, and the DVD/CD was after HDD (even though it went to the DVD/CD first for other discs).  This did get me to boot the 9.08 CD.  It did not get the 12.04 disc to work, though it works in my old laptop.

I'll keep the 9.08 disc as a plan B.  Obviously, I'd rather try to get 12.04 to work first.  I've just finished downloading the 12.04 image again so that I can burn a DVD from the same drive.

But why would it matter which machine burned the DVD?

Other details: It's a Lenovo P580-308725. I just got it today and am trying to create a dual boot with the preinstalled windows.  The windows installer works, but I got the impression that it's not the same thing as creating an Ubuntu partition.

---

### Post by karat on 2012-09-30
I just burned my own disc image (64 bit), and I got the same result.

Does it matter that the 64 bit image says amd64 when I have an Intel 64-bit chipset?  (The download page only has 32 bit and 64 bit options, so does amd64 cover both AMD and Intel?)

---

### Post by Bashing-om on 2012-09-30
karat; Hi ! Welcome to the forum .

Let me see if I can help.
1. I suggest you d/l the .iso and burn to cd-r vice DVD, and burn at lowest speed. verify the .iso with md5sum.
2. set boot priority to boot the cd 1st; verify the install disk and your hardware with the "try ubuntu" option.
3. Windows is finniky about a lots of things. rule: use windows tools for windows problems, and linux tools for ubuntu situations. Use windows disk manager to set aside space for ubuntu ..leave the space as "unallocated or free" ubuntu installer can format and install in the "unallocated space.

Here are helpful links to get you up dual booting:
[http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/](http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/)
[https://help.ubuntu.com/community/DualBoot/Windows](https://help.ubuntu.com/community/DualBoot/Windows)
[http://ubuntuforums.org/showthread.php?t=2059640 dual boot & UEFI advise](http://ubuntuforums.org/showthread.php?t=2059640 dual boot & UEFI advise)
[ttp://ubuntuforums.org/showthread.php?t=1974392 <-Dual booting UEFI](ttp://ubuntuforums.org/showthread.php?t=1974392 <-Dual booting UEFI)
and if you have large disk:
[http://ubuntuforums.org/showthread.php?p=12254717#post12254717](http://ubuntuforums.org/showthread.php?p=12254717#post12254717)

Feel free to ask, we look forward to seeing you on ubuntu.
[INDENT]kind regards <==BDQ

[/INDENT]

---

### Post by karat on 2012-09-30
> **Bashing-om said:**
> karat; Hi ! Welcome to the forum .

Let me see if I can help.
1. I suggest you d/l the .iso and burn to cd-r vice DVD, and burn at lowest speed. verify the .iso with md5sum.
2. set boot priority to boot the cd 1st; verify the install disk and your hardware with the "try ubuntu" option.
3. Windows is finniky about a lots of things. rule: use windows tools for windows problems, and linux tools for ubuntu situations. Use windows disk manager to set aside space for ubuntu ..leave the space as "unallocated or free" ubuntu installer can format and install in the "unallocated space.

Here are helpful links to get you up dual booting:
[http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/](http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/)
[https://help.ubuntu.com/community/DualBoot/Windows](https://help.ubuntu.com/community/DualBoot/Windows)
[http://ubuntuforums.org/showthread.php?t=2059640 dual boot & UEFI advise](http://ubuntuforums.org/showthread.php?t=2059640 dual boot & UEFI advise)
[ttp://ubuntuforums.org/showthread.php?t=1974392 <-Dual booting UEFI](ttp://ubuntuforums.org/showthread.php?t=1974392 <-Dual booting UEFI)
and if you have large disk:
[http://ubuntuforums.org/showthread.php?p=12254717#post12254717](http://ubuntuforums.org/showthread.php?p=12254717#post12254717)

Feel free to ask, we look forward to seeing you on ubuntu.
[INDENT]kind regards <==BDQ

[/INDENT]

1) Done.
2) Try Ubuntu doesn't work because it can't read the disc.  It can't read either disc, though my other machine can.

Also, the 9.08 install disc does work, but the partitioner doesn't.  I'm working on starting another thread for that.

---

### Post by karat on 2012-09-30
The more I read, the more I'm convinced that 9.08 can't deal with the EFI situation -- the system came preinstalled with 4 partitions already used(*).  I'd really like to get 12.04 working.

(*) And I need to go to the store tomorrow to get more blank discs.  I used my last to burn an image of 12,04 which didn't work.

---

### Post by oldfred on 2012-09-30
Since it is a new computer, you do need the new version to have UEFI. And UEFI only is on the 64 bit version. 

When you boot from the UEFI/BIOS in UEFI mode you should get two choices to boot Ubuntu. One choice is efi and the other BIOS, legacy, AHCI or whatever you system calls it.

How are you copying ISO to CD? You do not copy as one ISO but install so it is many files and bootable. I now prefer USB but some also have issues with flash drives.

Also instructions for CD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to CD.
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by karat on 2012-09-30
> **oldfred said:**
> Since it is a new computer, you do need the new version to have UEFI. And UEFI only is on the 64 bit version. 

When you boot from the UEFI/BIOS in UEFI mode you should get two choices to boot Ubuntu. One choice is efi and the other BIOS, legacy, AHCI or whatever you system calls it.

How are you copying ISO to CD? You do not copy as one ISO but install so it is many files and bootable. I now prefer USB but some also have issues with flash drives.

Also instructions for CD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to CD.
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

I don't get a choice of how to boot Ubuntu.  The two 12.08 DVDs both go to the EFI menu (after giving an error on not being able to read the volume label).  After selecting any option it gives another error about not reading a file (it doesn't say which) and goes into kernel panic.

I am copying from ISO to DVD using Windows "burn to disc" feature.  (Remember that I only have access to Windows on that machine.)  I have another disc that was burned via Ubuntu on another machine,  Both discs boot and verify on my old laptop.

Now, I'm off to buy more CD and DVD blanks.  Perhaps I will purchase a USB drive as well.  However, I am bothered by the idea that none of these things will actually fix the problem, as I have evidence that the discs work and the drive on the new computer works.

I suspect the problem is the driver on the 12.08 disc and that making more copies isn't going to do any good.

Does anyone have any suggestions what I should try before returning the machine and purchasing something that isn't a Lenovo?

---

### Post by karat on 2012-09-30
Purchased more blancs (CD-R and DVD-R) as well as a USB drive.

The BIOS boot manager won't boot off a USB drive.

Really not sure what I can do now that has a likely chance of working.

---

### Post by karat on 2012-09-30
Same problem with CD-R, even though it verifies correctly.  By now, I'm pretty sure the problem is that the install image is correct but incompatible with the hardware.  Should I try 32 bit?  An older version of Ubuntu install disc (but newer than 9.08)?  Any other suggestions?

---

### Post by oldfred on 2012-09-30
I know any old versions will not work with your new system. Not sure what you have as there never was a 9.08 in Ubuntu. 

You need at least 12.04 and some may have better success with the 12.10 when it comes out in Oct. It is in beta now so I cannot really suggest a new user try it yet.

You should not be trying to boot with BIOS but with UEFI, if Windows is installed in UEFI. Have we confirmed Windows is in UEFI mode?

I have not heard of a new computer that will not boot from USB. Although I understand with the future Windows 8, you have to turn secure boot off first as you are only allowed with secure boot to boot Windows. Perhaps Lenovo has turned that on already? Also check other settings in UEFI/BIOS for locked system settings. Manual may have more info.

---

### Post by oldfred on 2012-09-30
Some users with Lenovo's posted here that their model worked. But even the same model later may have a different chip and cause issues.

[http://ubuntuforums.org/showthread.php?t=2062676](http://ubuntuforums.org/showthread.php?t=2062676)

---

### Post by karat on 2012-09-30
> **oldfred said:**
> I know any old versions will not work with your new system. Not sure what you have as there never was a 9.08 in Ubuntu. 

You need at least 12.04 and some may have better success with the 12.10 when it comes out in Oct. It is in beta now so I cannot really suggest a new user try it yet.

You should not be trying to boot with BIOS but with UEFI, if Windows is installed in UEFI. Have we confirmed Windows is in UEFI mode?

I have not heard of a new computer that will not boot from USB. Although I understand with the future Windows 8, you have to turn secure boot off first as you are only allowed with secure boot to boot Windows. Perhaps Lenovo has turned that on already? Also check other settings in UEFI/BIOS for locked system settings. Manual may have more info.

No, I have not confirmed Windows is in UEFI mode.

The BIOS doesn't have an entry for USB, so I don't see any way to boot from USB.

Also, I have 30 days to return the machine if something is wrong, so waiting a month is not an option.

---

### Post by karat on 2012-09-30
> **oldfred said:**
> When you boot from the UEFI/BIOS in UEFI mode you should get two choices to boot Ubuntu. One choice is efi and the other BIOS, legacy, AHCI or whatever you system calls it.

I never get these options.  Perhaps I get the Error: Cannot read volume label message instead?  But then it jumps straight to the menu that the documentation says is the EFI menu (as opposed to the accessibility icons).

If I go into the BIOS, it says "UEFI Boot [Enabled]"

There are 3 entries in the boot order: DVD/CD, HDD, and network.  Even if I press F12 while booting, there is no option for the USB drive.

I tried USB again, and it booted from USB, even though I tried it before.  I still got the Error: Cannot read volume label, but I don't have a problem reading the file I had problems with on DVD-R or CD-R.

Now, I need to deal with the fact that the machine came with 4 primary partitions already created.  I read the documentation and I understand that more than 4 is a problem for MBR, but I'm not 100% clear on what to actually do about it.

I'm still not sure why the CD/DVD doesn't work.  I'm concerned because I want to make sure there isn't anything wrong with the drive itself.  If there is a hardware problem, I want to be able to return it.  Any explanations about why I would have these problems?  How about speculation whether or not I would have problems with the drive later on?

---

### Post by oldfred on 2012-09-30
I do not know Windows burn to disk program. How is it copying it? It cannot be just a copy of the ISO to the disk, but has to be an extraction and make the CD or USB a bootable device. Ubuntu automatically does that, but Windows default is normally just a copy. 

Did you follow the instructions on the Ubuntu site for making the CD or USB as a bootable device.

---

### Post by oldfred on 2012-09-30
You should keep one thread on your boot issues.

I gather is it now booting, you are not in UEFI mode but MBR(msdos) and have the issue of 4 primary partitions.

[http://ubuntuforums.org/showthread.php?t=2064980](http://ubuntuforums.org/showthread.php?t=2064980)

---

### Post by karat on 2012-10-01
> **oldfred said:**
> I do not know Windows burn to disk program. How is it copying it? It cannot be just a copy of the ISO to the disk, but has to be an extraction and make the CD or USB a bootable device. Ubuntu automatically does that, but Windows default is normally just a copy. 

Did you follow the instructions on the Ubuntu site for making the CD or USB as a bootable device.

I am 100% certain that I am burning the CD properly and not just copying the file.

Evidence: On a *different* laptop, I can boot from it and it verifies correctly when I select that from the initial CD menu.  Also, I can see the contents of it, and it's not just a single file.

I did follow the instructions.  The CD works on my old laptop.  I would like to understand why it wouldn't in my new one.  This is important to me since it may indicate a problem with the drive or a hardware incompatibility with Ubuntu (perhaps the drive works and the Ubuntu install CD works, but they don't work together).  In this case, I have the option of returning the laptop for a full refund, so I would like to determine for certain whether or not there is a problem.

> **oldfred said:**
> You should keep one thread on your boot issues.

I gather is it now booting, you are not in UEFI mode but MBR(msdos) and have the issue of 4 primary partitions.

[http://ubuntuforums.org/showthread.php?t=2064980](http://ubuntuforums.org/showthread.php?t=2064980)

Yes, I started another thread on that issue and only mentioned it briefly here.  That issue is resolved, but I do want to understand what's going on with the boot CD.  (For reference, I did boot from USB, but it only seems to boot from USB about half the time.  I don't know how to reliably boot it.  It helps if I plug in the drive and *then* reboot, rather than plugging it in when it's not on.)

UEFI and MBR:
The firmware says UEFI is enabled.  The 4 partition limit tells me that the disk was created with MBR. My understanding is that UEFI supports both GPT and MBR.  MBR has the partition limit, GPT does not.  However, I believe you can have UEFI enabled and still have the disk formatted with MBR, which is why I've been having some trouble understanding what you're trying to say about UEFI and MBR.  We may be using terms differently.

However, it's not clear to me if this is relevant or not.  12.04 was the first Ubuntu to support UEFI, from what I understand.  It's also the version that I can't boot from CD -- I can boot previous versions.  So, it might be relevant.  I just don't know.

The information I am looking for:
1) Ideally, I'd like a potential explanation of why the CD doesn't boot (and this is why I'm continuing the thread "Boot CD won't boot" even though I can boot from USB as a workaround).
2) If this seems possibly just a one-off issue that I have no reason to believe will haunt me again down the line (when it's too late to return the laptop), I could settle for a pointer to a software package that could test my drive and make sure it works correctly from within Ubuntu.

I bought this laptop on the condition that I could return it if it was not compatible.  Ultimately, I want to determine whether or not there is an incompatibility issue before my opportunity for a refund expires.

---

### Post by oldfred on 2012-10-01
Most UEFI systems also have a BIOS mode. Some early or simplified one's seem to look for an efi partition to boot and if not found default to the MBR to boot.

If you have an efi partition and gpt partitioning, then you are booting in UEFI mode. If MBR(msdos) partitioning you have to have a boot loader in the MBR.

Best to post this. If UEFI you must use 64bit versions. You can download into your Ubuntu installer or download as a full repairCD or USB.
Post link to BootInfo report that it gives you.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by karat on 2012-10-01
> **oldfred said:**
> Most UEFI systems also have a BIOS mode. Some early or simplified one's seem to look for an efi partition to boot and if not found default to the MBR to boot.

If you have an efi partition and gpt partitioning, then you are booting in UEFI mode. If MBR(msdos) partitioning you have to have a boot loader in the MBR.

Best to post this. If UEFI you must use 64bit versions. You can download into your Ubuntu installer or download as a full repairCD or USB.
Post link to BootInfo report that it gives you.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

While UEFI is enabled in the firmware, it is booting off an MBR system, as seen by the inability to create more than 4 partitions.

I already installed boot repair to help me resolve some booting issues.  Unfortunately, I am currently at work, so I will have to post the link when I get home.

I can also add that when I try to boot the ubuntu live CD, it gives an error message Error Reading Volume Label and then drops to a menu to install or try live -- without giving a choice of EFI or BIOS/Legacy or displaying any accessibility icons.  From that menu, any option gives an error reading files and kernel panic.

---

### Post by oldfred on 2012-10-01
It would be UEFI that would give choice, not Ubuntu or grub menu. 

Both sets of files are on the 64bit version and only from UEFI menu would you get a choice. If you hae UEFI turned off, or are using 32bit version it will just boot the the install or try menu.

---

### Post by karat on 2012-10-01
[http://paste.ubuntu.com/1254875/](http://paste.ubuntu.com/1254875/)

Still not entirely sure how this is relevant.

---

### Post by karat on 2012-10-01
Aha.  I may have figured out what was wrong.  I went back and checked the error message that flashes briefly before disappearing and it says "error prefix not found."  (The volume label error was a completely different once that I conflated with this one.  My error)  "Error prefix not found" is a known bug and considered harmless, but searching for the accurate error text and lenovo gets me:

[http://ubuntuforums.org/showthread.php?t=2035376](http://ubuntuforums.org/showthread.php?t=2035376)

That link suggests the ubuntu directory that points to itself was the problem for someone else with a Lenovo laptop.  That offers a reasonable explanation why my Lenovo has a problem with the same thing (which is also on my disk).  So, if I install ISO Master and remove the cyclic folder, I should be good...

Thanks to the community, especially oldfred.

---


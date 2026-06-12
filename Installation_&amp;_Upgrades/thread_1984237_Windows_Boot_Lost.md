---
title: "Windows Boot Lost"
date: 2012-05-21
forum: Installation &amp; Upgrades
---

### Post by asearle on 2012-05-21
Hi Everyone,

I have installed 12.04 over an existing dual-boot installation and find that although the Ubuntu installation worked fine, my system no longer dual-boots.

I imagine that Ubuntu has somehow overwritten my Windows-boot (in the MBR?).

So my question is whether there is an easy way to fix this?  Can I re-install and tell Ubuntu to somehow pick up and to allow the Windows boot?  Or do I need to re-install Windows and then re-install Ubuntu? (I hope not!)  Or maybe there is a utility that can handle/fix this?

Any tips that you can give me would be a great help.

Regards and thanks,
Alan Searle

---

### Post by cortman on 2012-05-21
> **asearle said:**
> Hi Everyone,

I have installed 12.04 over an existing dual-boot installation and find that although the Ubuntu installation worked fine, my system no longer dual-boots.

Did you make sure to choose to install it over the existing UBUNTU system and not just wipe out both systems?
If so, you should be able to get Windows back by simply updating grub- in Ubuntu-

```
sudo update-grub
```

should do the trick.

---

### Post by drs305 on 2012-05-21
If Windows wasn't appearing in the menu, the solution above should work.

If that isn't the issue, try the GUI app Boot Repair. Link in my signature line.

---

### Post by asearle on 2012-05-21
Many thanks, the sudo update-grub suggestion worked perfectly.

I have another problem which is that my Windows partition seems to be corrupted but I don't think this has got anything to do with Linux because from Linux I can see the partition and all the files seem to be OK.

I think it's Windows so I will probably re-install Windows anyway.

Thanks very much for your tips.

Regards,
Alan

---

### Post by cortman on 2012-05-21
Glad it's fixed.
BTW, before you reinstall Windows run CHKDISK from the DOS prompt- could save you some hassle and fix it as well.
Mark the thread [SOLVED] if you would, with the thread tools in the upper right. Thanks, and good luck!

---

### Post by asearle on 2012-05-22
I am on the point of re-installing Windows but am curious to find out what happened:

As it is, Ubuntu boots fine and Windows is available in the Grub prompt.  But when I select windows, I get this message ...

"Error reading drive
Restart with Ctrl-Alt-Del"

... and nothing more.

I then tried inserting a Windows installation disk and that disk could also not detect the drive (for an install) so my next move will be to reformat the whole disk with GParted.

So, from within Ubuntu the drive seems fine.  And with Knoppix (GParted) I ran a check and that came back OK.  Indeed, from Knoppix I could see that the Windows partition is set to boot.

It is not critical (this time) that I fix this but under other circumstances this could be an enormous hindrance and so I would really like to know what has happened.

Yes, why does "Update-Grub" find the drive but neither the Windows dual-boot nor the Windows install-CD?  That's strange, isn't it?

Anyway I hope that someone can help provide an explanation.

Regards and many thanks,
Alan Searle

---

### Post by wilee-nilee on 2012-05-22
You might just run the bootscript in drs305's signature (post #3) and post the results.txt, so we can look at the set up to see if windows is missing any boot files.

---

### Post by asearle on 2012-05-22
I ran a boot repair which completed successfully and produced the following output ...

[http://paste.ubuntu.com/1000906/](http://paste.ubuntu.com/1000906/)

... but still get the "Error reading drive" message.

Indeed, it seems that grub is working correctly and my Windows partition is OK but somehow the drive/partition is not being found or cannot be read by grub(?).

I have looked through the diagnostic output but am not sure exactly what I need to check.

If anyone can help me with this either by identifying something strange in the diagnostics or recommending other action that I could take then that would be a great help.

Many thanks,
Alan Searle

---

### Post by darkod on 2012-05-22
That looks more like windows error. The moment you select windows from the boot menu, it passes the boot process to windows.

Maybe it needs chkdsk to be run or something.

Try this, have your finger in the F8 button, and as soon as you select windows and hit Enter, hit F8 immediately.

That should load XP advanced menu. See if you can boot Safe Mode.

If you can, try something like:
chkdsk c: /r /f

in command prompt.

PS. On first look I can't notice anything wrong in the script results.

---

### Post by asearle on 2012-05-22
Many thanks for this tip.

I gave it a try (with F8) but still could not get into Windows (to run chkdsk).

It looks like Windows is shot and I will have to re-install.  That's OK but it would have been great to have been able to fix it.

I'll wait a while to see if anyone else has an idea and, if not, I'll reformat the whole disk and start from scratch.

Many thanks for your tips and suggestions.  I've discovered some useful commands and tools that will certainly come in handy in the future.

Regards,
Alan

---

### Post by cortman on 2012-05-22
> **asearle said:**
> Many thanks for this tip.

I gave it a try (with F8) but still could not get into Windows (to run chkdsk).

It looks like Windows is shot and I will have to re-install.  That's OK but it would have been great to have been able to fix it.

I'll wait a while to see if anyone else has an idea and, if not, I'll reformat the whole disk and start from scratch.

Many thanks for your tips and suggestions.  I've discovered some useful commands and tools that will certainly come in handy in the future.

Regards,
Alan

Yes, it looks like a Windows reinstallation is in order...

---

### Post by asearle on 2012-05-23
Many thanks for your help with this problem and I do hope that you can help me with one last detail ...

I decided to clear and reformat the disk in order to re-install Windows.  As the computer has no floppy drive I did this with Knoppix and GParted which seemed to be an easy process:

- I cleared the partition table
- I created a FAT32 drive
- I formatted it as FAT32
- I set the boot flag
- I checked (from within Knoppix) that the drive was visible

... then I rebooted.

But each time I get the message "This is not a bootable disk".

I both checked the boot sequence in BIOS and also explicitly selected Hard Drive at boot.  But it still would not boot.

I tried the same thing with another spare computer that I have but got the same result.

In the past I have either worked with Ubuntu (which installs no problem) or have formatted drives with a DOS disk (setting the bootable flag).

My suspicion is that I am doing something wrong with GParted but can't see what that might be.

Can anyone suggest a solution or an alternative tool for simply getting a disk bootable (either as FAT32 or as NTFS).

I wish I could be using Linux but for this particular thing it has to be Windows.  What a pain !!!

Many thanks for your help.

Yours,
Alan Searle

---

### Post by asearle on 2012-05-23
I tried again, this time formatting as NTFS and got the message BOOTMGR is missing.

I'm sure that it must be something really simple that I am doing wrong.

Many thanks for any tips.

Yours,
Alan

---

### Post by wilee-nilee on 2012-05-23
.

---

### Post by darkod on 2012-05-23
First of all, why are you using FAT32 and not NTFS?

Even if it's for XP I would make the partition NTFS.

Second, if you plan to dual boot on the same hdd, don't create a single partition taking the whole disk. Later you would have to shrink it to make unpartitioned space for ubuntu. Create a partition only with the size you want to allocate to windows, not the whole disk. If you want the whole disk to be for windows, yes, the partition can take the whole disk.

Third, the no bootable disk is because it can't detect a boot flag on any partition. In Gparted, right-click the partition you want to use for windows, select Manage Flags and activate the boot flag. Windows needs this.

After that do the installation on that partition and it should go fine.

---

### Post by asearle on 2012-05-23
I agree and, yes, I have switched to NTFS and have reduced the partition to 20 GB (ready for Ubuntu).

And I have set the "boot" flag.

But now I get the message (on both the computers that I am testing with) "BOOTMGR MISSING".

I have tried setting this with GParted on Knoppix and on an Ubuntu live CD but still get the same result.

Is there maybe some other flag that I need to set?  Or is it something in the BIOS?

Many thanks for any ideas that you have.

Yours,
Alan

---

### Post by black veils on 2012-05-23
i'm confused, doesnt booting from a Windows installation disc allow you to sort all that?  whats with all the predefined partitions and boot flag?

---

### Post by asearle on 2012-05-23
Yes, I'm sure that, in the past I have done it exactly the way you describe and it working fine.  I'm confused too.

I've been googling on this error message and there is some feedback saying that a SATA driver needs to be installed.

It seems unlikely but maybe it's because I am trying to install (old) XP which has a problem with one or other aspect of my hardware (but on two PCs?)

Anyway, I am feed up with all this and my idea now is to go out and give Bill Gates several hundred Euro by buying a copy of Windows7 to see if that is better at installing.  I hate doing that but I can't think what else to do.

All I can say is that I'd rather be Linuxing:  There were never any installation problems on these PCs with Ubuntu.

I'll give the forum feedback on the results of all of this.

Regards,
Alan

---

### Post by darkod on 2012-05-23
bootmgr missing is windows message. Do you get this when booting from the cd? Because that sounds like it's trying to boot from the hdd, and there is nothing to boot since it doesn't have windows on it, right? So, of course it would give bootloader error.

XP will rarely detect a SATA hdd. You would have to go into bios and change the sata mode to IDE if it allows it. XP by default doesn't include sata drivers.

---

### Post by asearle on 2012-05-23
It booted fine from CD but not from HDD.

So I believe it is the SATA issue.

As it is, I bought Windows 7 today (it wasn't so expensive) and it installed fine.

I mostly use Windows within VirtualBox and it works absolutely fine there.  So I will now steer clear of installing XP on newer PCs.  But anyway I only need it very rarely.

Many many thanks for your help, your tips and your consideration.

Regards,
Alan

---


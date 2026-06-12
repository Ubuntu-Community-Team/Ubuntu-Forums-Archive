---
title: "Ubuntu on Asus Vivobook S200E"
date: 2013-02-17
forum: Installation &amp; Upgrades
---

### Post by swithuncrowe on 2013-02-17
I got a Asus Vivobook S200E, which came with Windows 8 preinstalled. I booted Arch Linux from a USB stick and deleted all the partitions and installed Arch, but then couldn't get it to boot off the hard disk. I think this is because of EFI.

I read some success stories with Ubuntu, so I created a 64 bit 12.10 USB, but this also doesn't work. I get the GRUB screen offering to try Ubuntu without installing or to install Ubuntu. If I pick either, I just get a blank screen. There is some activity on the USB stick, but then nothing. If I hit enter, there is some more activity, and then nothing. Ctrl+Alt+Del will often reboot the computer.

I've tried modifying the boot parameters, e.g. gfxpayload=text, removing quiet and splash, adding nomodeset. But with no success.

Is this another symptom of a EFI problem, or something else? I hope someone can help. Thanks.

---

### Post by pantropik on 2013-02-19
I believe you'll need to go into the UEFI config utility, by pressing some key or key combination as the device powers on, and find something like "enable legacy boot" and turn it on. You should be able to google the exact steps.

---

### Post by swithuncrowe on 2013-02-20
Yes, I had enabled CSM - Compatibility Support Module - but on its own, that didn't work. What finally did the trick was changing the disk from GPT to MBR. Now I can boot off the disk in non-EFI mode.

---

### Post by Jay_E on 2013-02-20
Hello Smithuncrowe

I am having similar problems.
One question.

What do you mean by " changing the disk from GPT to MBR" ??

I looked up [http://en.wikipedia.org/wiki/GUID](http://en.wikipedia.org/wiki/GUID) Partition Table
and see what is is - but how did you do the change?

For grins, this is what I tried...
[http://ubuntuforums.org/showthread.php?t=2118052](http://ubuntuforums.org/showthread.php?t=2118052)

If I may - a second question?
How do you get to "boot repair"?
T H A N K  Y O U,
Jay

---

### Post by oldfred on 2013-02-20
@Jay_E
See your thread.

Often whether UEFI or BIOS you may have video issues. Particularly with nVidia or AMD. And some of the very new systems need other boot parameters to work around some new hardware.

       How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by swithuncrowe on 2013-02-20
I hadn't come across GPT disks before. There was a 1007K empty partition at the beginning of the disk. I think one is supposed to install the boot loader in that, but I couldn't figure out how to do it. With a combination of gdisk, cfdisk and gparted, I got rid of the empty partition, and was able to install the bootloader in the MBR. Sorry I can't be more specific. But now I can boot with the old BIOS (CSM) and GRUB.

---

### Post by oldfred on 2013-02-20
But your Windows 8 uses gpt and UEFI, so it will not work now.

Generally best not to convert to MBR. Windows only boots from gpt with UEFI and UEFI has to have gpt.

But Ubuntu will boot from BIOS or BIOS mode with either gpt or MBR.

Windows has specific partition requirements for Windows with UEFI.
       Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)
Order on drive is important:
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

---

### Post by swithuncrowe on 2013-02-21
I'd already removed Windows8. If I'd wanted to keep it, I might have been more careful. But I didn't have anything to lose.

---


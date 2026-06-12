---
title: "How do I install Windows XP and overwrite Ubuntu?"
date: 2010-03-18
forum: Installation &amp; Upgrades
---

### Post by MasterMac on 2010-03-18
I want to know if it is possible to install Windows XP inside of Ubuntu 9.10 and delete Ubuntu. I want to make this netbook dual boot and I know I need to have XP installed first to make the process easier. Is there any way to do this? ](*,)

---

### Post by phillw on 2010-03-18
Hi and welcome to the forums,

As you already have ubuntu on, in your case it is okay to put windows on afterwards, it just needs an extra step at the the end.

Use the LiveCD to boot from and then make a partition (has to be a primary partition numbered 1, 2, 3 or 4) as NTFS at what size you want the Windows area to be (Just as if you were making an area for ubuntu if windows was already on, except you're making the file type NTFS)

Pages 3 and 4 here --> [http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)  have the screen shots for making room for windows. ***Don't use their instructions for Grub, use the link the bottom of this post ***

Once you have that area, boot with the XP install disk and it will pop itself into the free area you have made for it.



Check it is booting okay, then head over to [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)  to re-instate grub.

It's not really anymore complicated than Windows XP on 1st, just the additional step at the end.

Regards,

Phill.

---

### Post by MasterMac on 2010-03-18
Well I am not able to use a install disk. I am using a netbook so I have no cd drive. I have an ISO image on my HDD. Everytime I try to run the ISO it opens in Archive Manager.:-s

---

### Post by MasterMac on 2010-03-18
Also, would it be possible to just overwrite Ubuntu by installing XP? I am very new to Ubuntu and I have used Windows all my life and I could make it dual boot so much easier with windows installed.

---

### Post by wdaniels on 2010-03-18
> **MasterMac said:**
> Well I am not able to use a install disk. I am using a netbook so I have no cd drive. I have an ISO image on my HDD. Everytime I try to run the ISO it opens in Archive Manager.:-s

You will need an XP install disk to install it. You cannot boot a disk image from within a running system (on any OS, except inside a virtual machine, which is no use).

But once you have an XP install disk, I'm quite certain it will not have any problem just overwriting everything that already exists...that is the MS way.

---

### Post by norseman-has-a-laptop on 2010-03-18
why not use a vmachine instead of dual booting ???

---

### Post by wdaniels on 2010-03-18
> **norseman-has-a-laptop said:**
> why not use a vmachine instead of dual booting ???

On a netbook? Possible, but I wouldn't advise it :D

Anyway, sounds more like he bought a cheaper netbook without XP, downloaded an ISO from somewhere and wants us to help him install it.

Or perhaps I'm just getting cynical in my old age :P

@MasterMac You can probably write your ISO to a USB stick and boot from that, but you'd do better seeking guidance on a Windows forum if you want to try it.

---

### Post by norseman-has-a-laptop on 2010-03-18
> **wdaniels said:**
> On a netbook? Possible, but I wouldn't advise it :D

Anyway, sounds more like he bought a cheaper netbook without XP, downloaded an ISO from somewhere and wants us to help him install it.

Or perhaps I'm just getting cynical in my old age :P

@MasterMac You can probably write your ISO to a USB stick and boot from that, but you'd do better seeking guidance on a Windows forum if you want to try it. why would you not advise a vmachine on a netbook lol

old you say lol ha ha ha im sure if your still bloging your not old enough then lol

---

### Post by MasterMac on 2010-03-18
So I could make a Live USB for XP and just run it and it would overwrite?

There would be no point in me running a VM. I have 1 GB of RAM lol

---

### Post by norseman-has-a-laptop on 2010-03-18
sounds about right

---

### Post by MasterMac on 2010-03-18
Ok I'll give that a try. Thanks guys :D

---

### Post by wdaniels on 2010-03-18
> **norseman-has-a-laptop said:**
> old you say lol ha ha ha im sure if your still bloging your not old enough then lol

I guess I'm just a grumpy young man then ;) Or at least I am today for some reason. Got told I need glasses yesterday, so starting to feel the years creeping up 8)

> **MasterMac said:**
> So I could make a Live USB for XP and just run it and it would overwrite?

Perhaps not a "live" XP (don't think Windows can do that), but at least a bootable install disk from the ISO image. Note that you can't just copy the file onto the USB drive, it's a bit more involved. Like I said, best to check with Windows people about that one.

> **MasterMac said:**
> There would be no point in me running a VM. I have 1 GB of RAM lol

I used to have an XP VM with about 380MB that ran OK for the few little things I needed XP for. Ubuntu works perfectly fine with 512MB. I was thinking more the CPU being the bottleneck, the small screen being awkward, and possibly disk space being short.

Though perhaps the newer netbooks are sufficient in these areas; I only have an old 4GB/512MB 600MHz 800x480 netbook, and I can't imagine running a VM on that :D

---

### Post by MasterMac on 2010-03-18
Perhaps not a "live" XP (don't think Windows can do that), but at least a bootable install disk from the ISO image. Note that you can't just copy the file onto the USB drive, it's a bit more involved. Like I said, best to check with Windows people about that one.



[QUOTE]

Well I know there is more to it than just copying the ISO but in theory, would that work?

---

### Post by wdaniels on 2010-03-18
> Well I know there is more to it than just copying the ISO but in theory, would that work?

Yes, you can certainly write an ISO image onto a USB drive, and in theory, assuming that your BIOS can boot from USB media (almost certainly yes) and assuming that Microsoft has not done anything peculiar to the Windows setup that would make it fail when running from a non-CD media (who can say, except somebody who has tried it of course) then it will work.

In theory, nothing in the process can tell the difference, unless it chooses to look, or makes a stupid (or deliberate, perhaps a misguided effort to prevent piracy?) assumption.

Once you get that far, I have no doubt that the Windows setup will not worry about Ubuntu being on the disk already. It may ask you to confirm deleting the existing partition or something. It will certainly overwrite the boot loader and everything else, because I've seen that often enough as an issue on these boards.

But, you know, it would be much simpler to do what was suggested to you initially, without deleting Ubuntu.

---

### Post by norseman-has-a-laptop on 2010-03-18
i messed around with it and yes it seems easier to load ubuntu after you have xp on it and i would have to say piutting the image on a disc is a good idea or a usb either or

---

### Post by MasterMac on 2010-03-24
Ok thanks guys. I got everything up an running. Windows 7 and I am going to dual boot with Ubuntu. Thanks for all your help.:p

---


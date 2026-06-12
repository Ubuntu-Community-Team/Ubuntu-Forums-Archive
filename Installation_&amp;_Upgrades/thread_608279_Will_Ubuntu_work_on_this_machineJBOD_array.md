---
title: "Will Ubuntu work on this machine/JBOD array"
date: 2007-11-09
forum: Installation &amp; Upgrades
---

### Post by TV-VCR on 2007-11-09
Will Ubuntu work on this machine?

Motherboard - [COLOR=Blue]_[Intel D975XBX2]("http://www.newegg.com/Product/Product.asp?Item=N82E16813121059")_[/COLOR]
Graphics - [COLOR=Blue]_[BFG Nvidia GeForce 8800GTX]("http://www.newegg.com/Product/Product.asp?Item=N82E16814143093")_[/COLOR]
Audio - [COLOR=Blue]_[Asus Xonar D2]("http://www.newegg.com/Product/Product.aspx?Item=N82E16829132001")_[/COLOR] (onboard also available)
Processor - [COLOR=Blue]_[Intel Core 2 Duo E6600]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819115003&Tpk=Intel%2bCore%2b2%2bDuo%2bE6600")_[/COLOR]
Memory - [COLOR=Blue][U][Patriot 4GB (2x2)]("http://www.newegg.com/Product/Product.asp?Item=N82E16820220227")
[/U][/COLOR]Disk drive - [COLOR=Blue]_[Lite-on DVD/CD RW drive]("http://www.newegg.com/Product/Product.asp?Item=N82E16827106082")_ [/COLOR]and Atapi DVD RW drive
Hard drives - 2 of [COLOR=Blue]_[Seagate ST3500630AS]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822148136&Tpk=Seagate%2bST3500630AS")_[/COLOR], 1 of [COLOR=Blue][U][Seagate ST3750640AS]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822148134")

[/U][/COLOR]However, 1 of the ST3500630AS and the ST3750640AS are joined together as a JBOD (the other drive is a backup drive). Could/how would I install Ubuntu on the JBOD along with Windows Vista?

This involves the Gutsy release.

Cheers.

---

### Post by Laserbeast on 2007-11-09
Yes it will work.

---

### Post by TV-VCR on 2007-11-09
> **Laserbeast said:**
> Yes it will work.

Sweet! :KS

But what about installing it on the JBOD with vista?

---

### Post by Laserbeast on 2007-11-09
> **TV-VCR said:**
> Sweet! :KS

But what about installing it on the JBOD with vista?

I've always gone with a full-out RAID array, but if you can partition a JBOD, then yep.

---

### Post by TV-VCR on 2007-11-09
> **Laserbeast said:**
> I've always gone with a full-out RAID array, but if you can partition a JBOD, then yep.

Can you answer the question I've asked here? Make sure to read the whole thread. ;)

[http://www.pro-networks.org/forum/about99851.html&highlight=](http://www.pro-networks.org/forum/about99851.html&highlight=)

Thanks.

---

### Post by Laserbeast on 2007-11-09
> **TV-VCR said:**
> Can you answer the question I've asked here? Make sure to read the whole thread. ;)

[http://www.pro-networks.org/forum/about99851.html&highlight=](http://www.pro-networks.org/forum/about99851.html&highlight=)

Thanks.

A little confusing but I'll give this advice.

So you currently have 3 drives? Why don't you use the one you have for Vista (I'm guessing Chris_Vista), then install Ubuntu on either of the two, with the other one set as a backup drive?

With the GRUB boot loader, you can boot into multiple drives, not just partitions.

---

### Post by TV-VCR on 2007-11-09
> **Laserbeast said:**
> A little confusing but I'll give this advice.

So you currently have 3 drives? Why don't you use the one you have for Vista (I'm guessing Chris_Vista), then install Ubuntu on either of the two, with the other one set as a backup drive?

With the GRUB boot loader, you can boot into multiple drives, not just partitions.

You have absolutely *no* idea how much data on DVD and another drive I have and need to transfer! It'd take up over 550 GB! I would dedicate at least 200 GB to Ubuntu and the rest to Vista. That's why I really need to make a JBOD then partition it.

---

### Post by PilotJLR on 2007-11-09
Just FYI... you know that with JBOD, if one disk fails (and it will eventually) then you will likely lose everything?

Invest in a raid 5 NAS! Or make one.

---

### Post by TV-VCR on 2007-11-09
> **PilotJLR said:**
> Just FYI... you know that with JBOD, if one disk fails (and it will eventually) then you will likely lose everything?

Invest in a raid 5 NAS! Or make one.

Look, can you people just tell me how to make this work instead of voicing your own opinions??

And also FYI, It's easier to recover data from a JBOD, because the files are files. Unlike a RAID0 where fragments of the files are scattered across drives. I think you confused the two.

---

### Post by TV-VCR on 2007-11-10
Help?

---

### Post by PilotJLR on 2007-11-10
Chill out, guy. Your response there is inappropriate and condescending.

I am trying to help you by providing some advice. I use storage arrays at work that cost a whole lot more than your PC, so I'm familiar with these concepts. Despite that fact that "files are files" in a JBOD, and not striped, you will still lose your partition table. Unless you fully understand (or can pay a recovery company) how to recover raw data without benefit of a partition table, etc, then you will lose everything.

Basically any disk controller under $400 uses a feature most call "fake RAID". Google that. If you setup a JBOD using fake raid and a Vista driver, then in actuality Vista and the CPU will control writes to the JBOD, which clearly makes a problem for linux.
Likewise, linux can setup JBOD's / fake RAID at the kernel level, which clearly makes a problem for Vista.

The solution... a HARDWARE raid controller. Again, when you see a little pci card with Raid written on the box, and it costs $100, then we're talking fake RAID. You need a card that handles i/o and parity (if need be) on an asic, and presents the results to the OS as a logical volume.

---

### Post by TV-VCR on 2007-11-10
I'm kinda broke after spending $2,500 on a system.

I just want to use the mobo's raid controller.

---

### Post by TV-VCR on 2007-11-10
Still need help.

---

### Post by PilotJLR on 2007-11-10
I've explained in my last post why this isn't going to work...

You're basically asking for 2 very different OS's to control the same volume group in software, yet never have any corruption. This is why hardware raid controllers exist.

---

### Post by TV-VCR on 2007-11-10
I am sorry if I sounded rude.

I guess I will just move Vista to the larger hard disk and put Ubuntu on the current Vista drive.

How do I do this? [http://www.pro-networks.org/forum/about99912.html](http://www.pro-networks.org/forum/about99912.html)

---

### Post by PilotJLR on 2007-11-10
It will be a little tricky, unfortunately. I would recommend using an imaging tool like G4L to copy an image of the small drive on the new drive... then boot the new drive and resize the NTFS partition to fill the new, larger disk.
This very well may cause Vista to re-activate, but I don't know for sure.

Of course, back up everything important before you do any of this!

---


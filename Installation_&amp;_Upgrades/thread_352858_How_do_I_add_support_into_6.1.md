---
title: "How do I add support into 6.1?"
date: 2007-02-03
forum: Installation &amp; Upgrades
---

### Post by AndyInNYC on 2007-02-03
I presently have a MegaRAID i4 card in my system - which 6.06 supports.  6.1 will not install since it appears to have dropped support for this card.

If I install an IDE drive and put the OS on it, how can I modify the OS to support the RAID array/card?  I don't mind having the array for data and the OS on it's own HD.

Thanks.

Andrew

---

### Post by po0f on 2007-02-04
AndyInNYC,

Did the card work out of the box with Dapper?  If so, you are going to have to find out which module/driver the kernel was using.

---

### Post by AndyInNYC on 2007-02-04
From what I gather reading on Fedora forums and other places, the card uses the megaraid driver, not the megaraid_mbox driver.

Assuming that the mbox driver is being loaded, how do I override that and use the megaraid driver?  Is the megaraid driver even present in 6.1?

Andrew

---

### Post by po0f on 2007-02-04
AndyInNYC,

I believe the driver you are looking for is shipped with Edgy's kernel:
```
[FONT="Courier New"]$ find /lib/modules/2.6.17-10-generic/ -type f -iname "megaraid*"
/lib/modules/2.6.17-10-generic/kernel/drivers/scsi/megaraid/megaraid_mbox.ko
/lib/modules/2.6.17-10-generic/kernel/drivers/scsi/megaraid/megaraid_mm.ko
/lib/modules/2.6.17-10-generic/kernel/drivers/scsi/megaraid/megaraid_sas.ko
/lib/modules/2.6.17-10-generic/kernel/drivers/scsi/megaraid.ko
[/FONT]
```

Check to see if any of the megaraid drivers are loaded after a fresh boot:
```
[FONT="Courier New"]$ lsmod | grep megaraid[/FONT]
```

If the megaraid driver is loaded, you should be good to go.  If not, and one of the other drivers are loaded, remove it and insert the megaraid driver (assuming the megaraid_mbox driver was loaded):
```
[FONT="Courier New"]$ sudo modprobe -r megaraid_mbox
$ sudo modprobe megaraid[/FONT]
```

If everything is working now, blacklist the drivers you do not want loaded by opening up /etc/modprobe.d/blacklist in your favorite text editor and adding entries for them:
```
[FONT="Courier New"]blacklist megaraid_mbox
blacklist megaraid_mm
blacklist megaraid_sas[/FONT]
```

To make sure megaraid is loaded on boot, add an entry for that in /etc/modules:
```
[FONT="Courier New"]megaraid[/FONT]
```

HTH

---

### Post by AndyInNYC on 2007-02-04
Golly,

I ask for a detailed answer 'cause I'm a newbie, and what do I get .....?

A perfectly clear, detailed answer which clearly addresses the problem and the answer.

Have I been transported to 'Alternate World' or something.

I'll install 6.1 on an IDE drive and try the drivers as suggested.  Since 6.1 won't install onto the RAID array (it doesn't see it) and your answer doesn't preempt the install, that seems to be the best way to go about solving the problem - plus it avoids having the OS and swap on the RAID 5 array and wasting space.


Question: If I allow multiple drivers to load with the mprobe command, should the OS only use the one which is relevant, or will it bomb out with the multiple loads?

Andrew

---

### Post by AndyInNYC on 2007-02-05
Ah, it's never so simple.

I have verified with find that the megaraid.ko driver is on the machine.

I used lsmod to see which drivers were installed (megaraid_mbox and megaraid_mm).

I used modprobe to remove _mbox and _mm and add megaraid

I edited the blacklist file and added megaraid to /etc/modules

Now, when I boot the machine, even with the blacklist, megaraid_mbox, megaraid_mm and megaraid ALL load.

I can see MEGARAID in the device driver section, but can't see the drives which are attached anywhere.

After using the modprobe -r command and also adding megaraid, I also don't see the drives on the megaraid controller.

Any additional suggestions?

Andrew

---

### Post by AndyInNYC on 2007-02-05
Well,

If I can follow various other threads from other distros, it would seem that the new megaraid kernel device driver (if that's the right phrase) has dropped support for the MegaRAID 511 (the i4 which I have).

It would appear that the only way I'm going to get it going under 6.1 is to recompile the driver from Dapper.

As should be obvious from anyone reading my posts, this is completely beyond my skill set in linux.

Assuming I had a new megaraid.ko file, would I just cp it over the existing megaraid.ko file in the scsi subdirectory?

Is creating a new megaraid.ko file from the Dapper version and emailing it to me a trivial task for someone who actually knows which end of the keyboard faces which way under linux?

Closer and closer to a solution - but can't seem to get there by myself.


This file (if it attaches) seems to add 511 support, but when I use the binary, I get invalid format.


andrew

---

### Post by po0f on 2007-02-05
AndyInNYC,

It would be nice if you could mix and match kernel modules from different versions, but that's not how it works.  ;)

Could you post links to where people are saying that the new megaraid driver isn't compatible with your card?  I'd like to see which versions they are talking about.

---

### Post by AndyInNYC on 2007-02-06
[http://www.ubuntuforums.org/archive/index.php/t-201858.html](http://www.ubuntuforums.org/archive/index.php/t-201858.html)


This is one link; a search on yahoo of +MegaRAID +dropped +support turns up more.

Any thoughts on how to get this up and running under Ubuntu?

Andrew

---

### Post by bubba on 2007-03-19
This has been broken in Ubuntu for awhile.  The last kernel that works properly is  2.6.12-10-686 if you want to track that down and install it (should be in the dapper tree).   The last installable version for this card should be Hoary.

I've been around and around with Ben Collins about this.  I don't see this getting fixed.

Here are some URL's that may help in your fight:

[https://launchpad.net/ubuntu/+source/linux-source-2.6.12/+bug/32752](https://launchpad.net/ubuntu/+source/linux-source-2.6.12/+bug/32752)

---

### Post by AndyInNYC on 2007-03-19
bubba,

Thanks for the reply.  It's actually not a bug, driver support for the device has been dropped.

The question I have, is what would it take for someone who can rebuild kernels, etc. to take the driver from a working earlier revision and compile it into 6.1?

Obviously I can't do this or I wouldn't ask, but since the source is available it seems like a 'doable' project.


Andrew

---

### Post by slicksurf on 2007-05-07
Hi,

This problem is driving me nuts too. I have absolutely no idea why I can't see the raid array in ubuntu. In windows this works fine, the array is present and working. In ubuntu it just doesn't work. I've tried loading the megaraid driver by removeing _mbox and _mm and modprobe megaraid, but still nothing in /dev/.
Interestingly with all megaraid devices unloaded, I loaded each module in turn and ran dmesg. Only when I ran modprobe megaraid_mbox did the card get identified and it tried to scan for an array.
Is something fundementally wrong here? The LSI megaraid i4 should work with the legacy driver, yet here it clearly isn't. With the _mbox driver it identifies the card type and bios revision correctly, yet according everything I've read online this shouldn't be the case. Can anyone assist?

Regards

---

### Post by AndyInNYC on 2007-05-07
slick,

the new drivers specifically DROP support for the i4.  That's the problem.  I can't understand why legacy hardware support is dropped in Linux, but that's what happended here.  One would think that an i4 version would be included which didn't support whatever new features were to be had, but that's not the case.

Andrew

---

### Post by slicksurf on 2007-05-07
Hi Andrew,

I read your plight with the megaraid i4 and I am at a loss as to how to deal with this without having to buy another controller. I just spent an age setting up Ubuntu the way I want, getting to grips with Zoneminder and all its associated woes, and now I'm lumbered with a raid card I can't use. I'm not giving up just yet, I come from Windows server background, but I needed CCTV which consumed to much resource hence my switch to linux and I also need a reliable raid array. I will continue to read in to how I can possibly get the legacy drivers to load, they are there.
I still confused as to why the card and the drives are recognised when the bios is disabled, but I've just noticed that the 2 drives that are giving me IO error on the megaraid in this configuration are also giving IO errors on the motherboards on board ide without the megaraid (they dont in windows, they are the newer Segate PATA 400gb drives). I may be on to something here. Could you try your card with the bios jumper pins shorted and see what you get, remember to have your arrays setup before disabling the bios.

Regards 
Sam

---

### Post by slicksurf on 2007-05-07
Ohhhh Hope...
[http://www.suseblog.com/?p=156](http://www.suseblog.com/?p=156)

I'll try this when I get a chance this week if I can. If it works, :lolflag: if not ](*,) 

Regards

Sam

---

### Post by AndyInNYC on 2007-05-08
I saw that once upon a time, but I don't have the linux skills to follow the directions - if you get it working, I'm all ears.

I actually went on eBay and purchased the 3ware 8 port IDE card; I now have a few i4 cards sitting in a bin somewhere.  If you get it up and running I can configure a secondary linux machine to redundantly back up my redundant arrary.

Andrew

---

### Post by slicksurf on 2007-05-08
This is just getting silly now, a friend told me to check the PCI ID of the megaraid card using lspci vs the megaraid and megaraid_mbox together with [http://pciids.sourceforge.net/pci.ids](http://pciids.sourceforge.net/pci.ids) which lists all the PCI IDs.
The megaraid mbox has the correct wildcarded PCI ID. But I was told that this driver wont work with this card, which the PCI ID website lists as 

101e  American Megatrends Inc.
	0009  MegaRAID 428 Ultra RAID Controller (rev 03)
	1960  MegaRAID
		1028 0511  PowerEdge Cost Effective RAID Controller ATA100/4Ch

Great, that explains why megaraid_mbox keeps loading. The megaraid module doesn't have a PCI ID that matches this, and thus won't work. So I now read that I could either change the BIOS of the card, or patch the kernel..... I may end up with a dead PCI card soon....

---

### Post by AndyInNYC on 2007-05-08
Slick,

I'm not sure how changing the BIOS would fix anything unless you have some specific patched BIOS that identifies itself incorrectly but still works correctly.

The full driver recompile referenced in the SUSE page would probably work, but I couldn't ever pull that off.  If someone has the ability to recompile this stuff and get us a working .ko (or whatever the needed files are) file, that would be wonderful.

Did you do the work in the link you referenced?

Andrew

The good news is that my 3ware card is working flawlessly and is still supported.  If I can get the i4 to work, I'm going to drop it in a machine with 3 x 500 and install trixbox and some other stuff.

---

### Post by slicksurf on 2007-05-08
YES!!!! It worked, I've posted this in a new thread for clarity (easier to sport thread title). Looks like your card will be back in use again Andrew. There doesn't appear to be major improvement in later firmware versions.

[http://ubuntuforums.org/showthread.php?p=2618555#post2618555]("http://ubuntuforums.org/showthread.php?p=2618555#post2618555")

---


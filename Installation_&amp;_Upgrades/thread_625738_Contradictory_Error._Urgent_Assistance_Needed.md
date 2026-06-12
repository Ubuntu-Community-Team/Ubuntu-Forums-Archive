---
title: "Contradictory Error. Urgent Assistance Needed"
date: 2007-11-28
forum: Installation &amp; Upgrades
---

### Post by mastergandalf19 on 2007-11-28
Hey folks.

First things first. The Error is in the text based install engine, when i try to install, it performs an integrity check, and says that a nvidia debian installer package is corrupted. I dont see how this can be when i burnt the disk at 4x, and did the md5 sum check and the two hashes matched. Could it be that i need to install in safe graphics mode? I did have an Nvidia Geforce FX 5200 in my PCI slot, but i removed and uninstalled it because it was causing so many IRQ interupts. I run a small bedroom project studio, and i really need this software. Ive had stack errors, and job control errors on other install disks before 7.10 aswell.

I downloaded the alternate i386 x86 image from canonical via http. Should I use the torrent files? Do they get better integrity checks? Is it my wireless dropping packets that could cause these corruptions?

Any suggestions/help welcome

Many thanks. Matt.

Pentium 4 2.8Ghz
512mb DDR Pc2700
64mb Intel Extreme Onboard Graphics
120gB Samsung HDD 7200
ALesis Mixer firewire
NEC DVD RW Drive
Netgear wireless adapter

---

### Post by reikoshea on 2007-11-28
the torrent download does do a hash check on every block, so yes, it does have a better integrity check.

i doubt thats the problem though if this has happened in the past.

---

### Post by athomson on 2007-11-28
Hi,

I have gotten this from quite a few distro's not just Ubuntu. Everytime it turned out to be the media and/or the cd-burner. Most times the media. Also I have found that writing to a erasable [RW] media is a no-no, it will pass an md5 or sha1 hash and then fail in the middle of loading.  In some  cases I have found that using a USB attached cd-burner also produces these types of problems.

What you could do is this, run the md5 hash on the install image and then run it again on the cdrom that you created.  This example is run from Ubuntu.

md5sum install.iso

md5sum /dev/scd0 

They should match.

---
You may want to boot in to your BIOS verify the settings for the video too.  Some BIOSes want you to clear the logs, else they seem to "remember" previous cards.  Not suppose to happen, but it does.

Andy

---

### Post by mastergandalf19 on 2007-11-28
Hey. 

Great Help, but problem was with cd burning program. Was burning too quickly, just burnt at x2 and it was fine. Another problem now. During the install process a lot of files are not available, says something about no network controller? It tries to download the packages, but because my wireless card isnt configured to use with linux in the first place, seems an odd way to install? I thought that all of the files were on the disk ready to be copied accross like a standard windows install.

Does it need a hardline ethernet connection to the motherboard ethernet slot or is there a way that I can configure it to use my wireless adapter during the install to get these missing packages?

Or is this another integrity problem?

Cheers Matt

---

### Post by athomson on 2007-11-28
Matt,

Well, I was close on the cdrom/burner/media as being the culprit.  Hmm I guess two out of three is okay.  

---

The installation process is centered around "some" default minimal set of packages. It's pretty hard to include every nuance of motherboards, adapters, and so forth, on a single cdrom, so in many cases it will require access to the net to get a particular package.   The default repository is the cdrom, or it should be.

Now on to your problem.  Having a fixed network adapter does make it easier, it may work with your wireless, depends on what you have. 

If it did pick up your network card you will see it here:

System->Administration->Network

If it's present, it may just be a matter of configuring it.If it's not present, then you will need to grab the driver for it and put it on a USB or cdrom so it can be installed.  

It would also be useful to see what was detected on the pci bus.

Applications->Accessories->Terminal

sudo -i

lspci

You can view the boot messages and see what it thinks you have for a wireless adapter.

dmesg | less

Post your wireless card type, the lspci results, and if possible, only the section of dmesg that identifies the network.  Keep it short.  

Andy

---

### Post by mastergandalf19 on 2007-11-29
Ok. Netgear WGv132. I cant get to a desktop to run those commands you suggested either. I have the official driver disk thoughm would that help?

Ill try hardwiring it to the ethernet today in my office. Willpost results.

Oh and formatting the free space on my hard drive annihilated my XP master boot record. Joy. 

Thanks again.

---

### Post by athomson on 2007-11-29
Hi,

Just on the off chance, check to see what kernel you are booting.  Is it the generic one? or is it the i386 one? The generic one is the one you want, it has a lot of the wireless drivers with it, including some of Netgear ones.  If you find you have the i386 one you should be able to install the generic one off the cdrom, you can use apt-get or synaptic to do this.

If this is not this case, then you will have to use the ndiswrapper.  Here is a HOWTO that provides the step-by-step instructions.

[http://ubuntuforums.org/showthread.php?t=612458]("http://ubuntuforums.org/showthread.php?t=612458")

---
Andy

---

### Post by mastergandalf19 on 2007-11-29
Well i downloaded the Ubuntu Studio Alternate install CD for Intel x86 architectures from the downloads section of ubuntu studios site. WOuld that automatically use the i386 kernel? Is there a way to tell the DVD install which kernel to use?

Ill try that wrapper and see if it works. 

Thanks again

---

### Post by mastergandalf19 on 2007-11-29
Any ideas anyone? Remove my wireless card?

Thanks Matt

---


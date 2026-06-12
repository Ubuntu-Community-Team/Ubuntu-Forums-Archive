---
title: "SATA Drives not recognised"
date: 2006-09-26
forum: Installation &amp; Upgrades
---

### Post by Kamakazie! on 2006-09-26
Hey,
I have just built a new PC and want to dual boot between XP and Ubuntu.

I setup XP on a 120gig partition of my 250gig main hard drive. I want to install Ubuntu on the free 120gig that is unused.

Files will be stored on my 320gig storage drive that i will probably format with ext3 so i can access it from both XP and Ubuntu.

Now when it comes to partitionijng the drives in the installation, the lolading bar comes up but GParted never starts. When opening Gparted on it's own, it says that it can't find any hard drives.

I have the MSI K9A motherboard with the new ATI S600 southbridge. Could this have something to do with it? I mean the liveCD loads up fine, just no disks can be found. 

Could it be a disk error?

Thanks.

---

### Post by happy-and-lost on 2006-09-26
SATA1 or SATA2?

---

### Post by wilcal on 2006-09-26
Historically Linux Kernel Ver. 2.6.10 (about)
and older had problems with SATA drives.
I can't tell you at what point it went good
but at (about) 2.6.12 and newer the SATA
addressing problem went away.

I use GParted Ver. 0.3.1-1 and that release
has no problem with SATA drives.

---

### Post by Kamakazie! on 2006-09-26
SATA 2 drives.
Using 6.06 live isntall. I am gonna try 6.06.01 now as i saw it fixed some live cd problems. Maybe it will help with this.

---

### Post by happy-and-lost on 2006-09-26
Aah. AFAIK, Linux doesn't support SATA 2 yet. :(

---

### Post by pseudonym on 2006-09-26
I think the graphical installer has been known to cause problems on some systems. You may therefore have better luck downloading the alternate .iso and burning that. This will give you the text installer, which is not hard to use and has better compatibility.

If you still have problems you could also try partitioning your disks before installing Ubuntu. To do that, download the GParted live cd .iso from [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php) and fire that up first.

Also, have you researched the linux support for that motherboard? It's pretty new, so may not be too well supported yet?

HTH

---

### Post by pseudonym on 2006-09-26
> **happy-and-lost said:**
> Aah. AFAIK, Linux doesn't support SATA 2 yet. :( It's not the speed that's the issue, it's whether the particular disk controller is supported. I use SATA 2 drives on my machine, although I have to jumper them for SATA 1 speed because my controller is SATA 1. But I'm sure there are plenty of newer m/bs out there with SATA 2 controllers which work perfectly with linux.

---

### Post by Kamakazie! on 2006-09-26
Partitioning them first is not the problem as it doesn't even recognise the drives. 

It is a new motherboard so that may well be the problem. Hmmmm maybe i will wait for the next release. Problem is i really want to get the storage drive up and running with Ext3 first even if it means using it with Windows for the time being.
Will try the GParted livecd first.

---

### Post by Kamakazie! on 2006-09-26
well there is no joy with the GParted live CD. It has a problem with my monitor?!?

When i choose the 32 bit depth it gives an error. 24bit depth and the screen goes blank.
oh dear.

---

### Post by jharr on 2006-09-26
There's a couple of things you can do to help give us more info. If your network card works, open up a terminal from the live CD and run:

1. `dmesg > Desktop/dmesg.txt`
2. `lspci > Desktop/lspci.txt`

then post those here as an attachment. dmesg (diagnostic messages) spits out kernel diagnostic information. When the kernel sees a device and recognizes it (such as an SATA controller, and drives) it spits out information about those in the dmesg buffer. lspci lists off the devices on your PCI bus. This will show what chipset that device is reporting as.

That should help us diagnose the problem.

---

### Post by BriGy86 on 2006-09-26
> **pseudonym said:**
> It's not the speed that's the issue, it's whether the particular disk controller is supported. I use SATA 2 drives on my machine, although I have to jumper them for SATA 1 speed because my controller is SATA 1. But I'm sure there are plenty of newer m/bs out there with SATA 2 controllers which work perfectly with linux.

that is pretty much my set up, I haven't been able to install kubuntu yet because my drive is not seen either, I have a SATA 2 drive (WD) that is clocked down to SATA 1 speeds because thats all my mother board has for controllers (its an asus a7v880, with AMD athlon XP) What did you do to get yours to work?  help would be great, im a complete linux newbie

---

### Post by pseudonym on 2006-09-27
> **BriGy86 said:**
> that is pretty much my set up, I haven't been able to install kubuntu yet because my drive is not seen either, I have a SATA 2 drive (WD) that is clocked down to SATA 1 speeds because thats all my mother board has for controllers (its an asus a7v880, with AMD athlon XP) What did you do to get yours to work?  help would be great, im a complete linux newbie You don't have any IDE hard drives (CDs/DVDs don't matter) plugged in as well, do you? This is a known issue when installing to a SATA drive - the installer can get confused. It's remedied by temporarily unplugging the IDE drive while you complete the installation.

I've been running linux on SATA drives since kernel 2.6.8, without any problems. I just made sure to set the BIOS to boot from 'SATA/SCSI' (that's my system, yours may be well be different), and that no IDE hard drives were connected. In fact, my BIOS allows me to disable the primary IDE controller, so I did that for good measure, since I no longer use IDE hard drives anyway (just have my DVD connected on secondary master) - but that shouldn't make a difference. It can also help to make sure you are running the latest BIOS for your motherboard.

---

### Post by BriGy86 on 2006-09-27
I have an IDE drive as well, sorry, but when i run the live disk it only can see the IDE drive and not the SATA one, currently I have used partition magic to make an ext3 partion for kubuntu and I also made a swap partition, as far as i can tell i can just install on those partitions and it should leave my windows partition along right?  I cloned my drive incase i run into problems though, wish me luck

Ill run the live disk once again and see if i can install it on the SATA (ill also disconnect the IDE drive)

---

### Post by BriGy86 on 2006-09-28
I successfully installed kubuntu last night on my SATA drive, but after applying all availible updates it loads VERY slow, it takes about 15 to check 2 things on boot up, I noticed in the boot loader it now has the groups for kubuntu, one with what i assume is the original kernal, and the other i assume is the updated kernal, the updated one is the one that doesn't work, and ideas?

---

### Post by Kamakazie! on 2006-09-28
> **jharr said:**
> There's a couple of things you can do to help give us more info. If your network card works, open up a terminal from the live CD and run:

1. `dmesg > Desktop/dmesg.txt`
2. `lspci > Desktop/lspci.txt`

then post those here as an attachment. dmesg (diagnostic messages) spits out kernel diagnostic information. When the kernel sees a device and recognizes it (such as an SATA controller, and drives) it spits out information about those in the dmesg buffer. lspci lists off the devices on your PCI bus. This will show what chipset that device is reporting as.

That should help us diagnose the problem.

Here they are. I think the lspci output might indicate exactly why none of the drives are found... it hasn't got a clue what the controllers are!

EDIT: I removed some of the content from the dmesg.txt as it was too big to upload. Took out blocks on one of the NICs, the processor and bluetooth connectivity. Didn't think that would be important.

---

### Post by Kamakazie! on 2006-09-28
anyone?

---

### Post by pseudonym on 2006-09-29
> **BriGy86 said:**
> I successfully installed kubuntu last night on my SATA drive, but after applying all availible updates it loads VERY slow, it takes about 15 to check 2 things on boot up, I noticed in the boot loader it now has the groups for kubuntu, one with what i assume is the original kernal, and the other i assume is the updated kernal, the updated one is the one that doesn't work, and ideas? But you can actually make it to the login screen, right? And once you are logged in, the system runs well? 

To show us if anything strange might be going on, you should make a compressed copy of the syslog file and attach it in your reply. Do that by opening up a terminal and running - ```
sudo cp /var/log/syslog /tmp/syslog
cd /tmp
sudo chmod 666 syslog
gzip syslog
``` then upload the zipped file from this location. This is a log of system events. There is also a bootlog but it is currently not working in Ubuntu, so don't bother with that.

Also, if you haven't already noticed, there are some great tips for speeding up the boot process [here]("http://www.ubuntuforums.org/showthread.php?t=89491&highlight=boot+speed+sysv-rc-conf"). Can help quite a lot to spped things up.

---

### Post by pseudonym on 2006-09-29
> **Kamakazie! said:**
> Here they are. I think the lspci output might indicate exactly why none of the drives are found... it hasn't got a clue what the controllers are! Right, and dmesg is full of interrupt assignment errors. I don't think your board is supported yet in Linux.

What to do? It's only a matter of time, so keep that extra hard drive space free :) From time to time, you can try downloading live CDs which run recent kernels to check the support for your hardware. Knoppix is good for this. Obviously, also keep an eye out on linux forums as well for other owners of your board who report success in getting it to work in Linux.

---

### Post by BriGy86 on 2006-09-29
> **pseudonym said:**
> But you can actually make it to the login screen, right? And once you are logged in, the system runs well? 

To show us if anything strange might be going on, you should make a compressed copy of the syslog file and attach it in your reply. Do that by opening up a terminal and running - ```
sudo cp /var/log/syslog /tmp/syslog
cd /tmp
sudo chmod 666 syslog
gzip syslog
``` then upload the zipped file from this location. This is a log of system events. There is also a bootlog but it is currently not working in Ubuntu, so don't bother with that.

Also, if you haven't already noticed, there are some great tips for speeding up the boot process [here]("http://www.ubuntuforums.org/showthread.php?t=89491&highlight=boot+speed+sysv-rc-conf"). Can help quite a lot to spped things up.

actually no, i've tried a few different times and it just sits there with the kubuntu logo now (no matter what kernal i choose), i can use recovery mode for both kernals, i'll try running those commands after i get off work today, and if all else fails i can take pics of the screen for you

thanks for your help

*EDIT*

i didn't get a chance to mess with it tonight the next time ill be able to take a look is some time after 7:30 P.M. on sat.

---

### Post by Kamakazie! on 2006-09-29
> **pseudonym said:**
> Right, and dmesg is full of interrupt assignment errors. I don't think your board is supported yet in Linux.

What to do? It's only a matter of time, so keep that extra hard drive space free :) From time to time, you can try downloading live CDs which run recent kernels to check the support for your hardware. Knoppix is good for this. Obviously, also keep an eye out on linux forums as well for other owners of your board who report success in getting it to work in Linux.

no suprise tehre then.
thanks for the help. i will keep checking around. now to find something to partition to ext3 from windows that is free! If something even exists.

---


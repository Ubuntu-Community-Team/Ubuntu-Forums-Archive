---
title: "DPT SCSI adapter"
date: 2010-01-07
forum: Installation &amp; Upgrades
---

### Post by alevin2352 on 2010-01-07
My office is running a billing program using SCO Open server 5.0.4 and I am trying to migrate things to Linux;  I took a functioning SCSI hard drive and DPT SCSI control board from the old machine and am trying to get it "seen" under Ubuntu;  Searching with Google I found that there is a dpt (DPT Controller SCSI driver) that can be loaded at boot time by placing the following line in loader.conf(5):

dpt_load="YES".

Even though I found this via a Ubuntu forum, it seems that these instructions apply to a different form of Unix...(?BSD)...Am I correct?  If not, could you point me to how I can do this?

thanks

alan levin

---

### Post by dstew on 2010-01-07
What version of Ubuntu do you have? I assume this is a PCI SCSI controller. Do you see it in the list of pci hardware in the output of **lspci**? How about in the output of **sudo lshw**? You can also try **lsscsi** to list SCSI devices. Even though no drives are connected at least the adapter should appear as a SCSI device. Post the output of these commands to the forum if you do not understand them.

If you see it in lspci but no driver has claimed it in lshw, look in the Hardware Drivers window (System --> Administration --> Hardware drivers) to see if there is a third-party driver for the card.

---

### Post by alevin2352 on 2010-01-07
I see it in lspci and here is the info about it in lshw:

0000000-800fffff(prefetchable)
           *-scsi UNCLAIMED
                description: SCSI storage controller
                product: SmartCache/Raid I-IV Controller
                vendor: Adaptec (formerly DPT)
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: scsi bus_master
                configuration: latency=160 maxlatency=8 mingnt=4
                resources: ioport:ec00(size=32) memory:80000000-80007fff(prefetchable)


There are no entries in system admin hardware drivers.  

Can I adapt a driver for free BSD to Ubuntu?  I'm using 9.1.   

Thanks for your help1

alan

---

### Post by dstew on 2010-01-08
The fact that the SCSI adapter is unclaimed means you will need to install a driver for it. I will look around later to see if I can find one for you. I do not know much about free BSD. Do you have the manufacturer's name, or web site? Perhaps there is source code for a driver that can be compiled.

---

### Post by alevin2352 on 2010-01-08
The manufacturer was DPT, who is long gone and no web site.  I guess my question is whether a driver found for BSD can somehow be reworked to use in Ubuntu...

Thanks for your help!

alan

---

### Post by dstew on 2010-01-08
DPT was purchased by Adaptec, which has very good product support. I looked at their site, and found a page that includes instruction on installing a SmartRaid IV SCSI adapter on a RedHat or SuSE Linux system, but they specifically say you need to look at the [Linux DPT Hardware RAID HOWTO]("http://www.ram.org/computing/linux/dpt_raid.html") for instructions on using the older DPT hardware. That page is pretty old though, and the links to the driver source are missing. 

The driver is named EATA DMA. I have seen that it was at one time included in Linux kernels, but since the hardware is considered obsolete I am not sure it is any more. You could try```
sudo modprobe eata_dma
```and see what you get.

I am sure you could find the source code for the old driver, and compile it to the newer kernels, but I am not sure it would work. Anyway, it seems to me that this is a job for experts in kernel modules, and I can't help you much with that.

---


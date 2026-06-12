---
title: "Ubuntu Server 12.04LTS Installation on Hardware RAID1"
date: 2013-03-09
forum: Installation &amp; Upgrades
---

### Post by briancachia on 2013-03-09
Hi,

I have been trying to install Ubuntu server on my rackmount server that supports hardware raid (it's been set up in the bios ). When I go to partition to logical volume that is supposedly created with the RAID1 configuration I find the 2 listed physical drives with their respective details of course.

my question is, how would i go to install ubuntu server on this machine with a raid1 setup please?

Thanks and i apologize for the lack of knowledge in the matter, I have no experience in raid configurations.

---

### Post by papibe on 2013-03-09
Hi briancachia. Welcome to the forums ):P

When you use hardware RAID, only one device per RAID is presented to the OS. Thus, the OS doesn't even know that is working on RAID.

If in the installation process you are seeing both devices, my first guess would be that your RAID1 is not set up properly.

Let us know how it goes.
Regards.

---

### Post by briancachia on 2013-03-09
thanks for your reply papibe,

when i m in bios and I view the logical drives a logical drive is listed so i m guessing that the RAID1 has been configured correctly eh?

Is there any know issues for 12.04LTS server for this kind of configuration?

Thanks again

---

### Post by tgalati4 on 2013-03-09
What is the server hardware?  Many servers have separate RAID BIOS that you need to boot into with Control-S (Dell PowerEdge for instance).  When in RAID BIOS, you set up the configuration and save it.  It also helps to update the motherboard BIOS and RAID BIOS at this time, so you can benefit from fixes before installing your operating system.  Once you have done this, the installation generally goes smoothly.

---

### Post by darkod on 2013-03-09
Is it HW raid or fakeraid? Fakeraid is only SW raid, hence it's called fake. It usually needs a driver for the array device to be detected properly. But the server version usually would have most driver to support this.

With the desktop version you could boot into live mode first, activate the fakeraid with:
sudo dmraid -ay

and then install because the raid device will show as single disk.

But in the server version you have no live mode so I'm not sure you could do something similar or how it would work.

Just for reference, about a year ago I installed Server 10.04 LTS to a very old PowerEdge 850 and the raid device set up was shown as a single /dev/sda device to Ubuntu. It had no issues installing on it.

---

### Post by briancachia on 2013-03-09
The server's motherboard is an intel one with a Xeon processor and 1GB Ram. I m pretty sure its HW RAID since its an intel configuration that is done through bios, no other software is used apart from the configuration utility provided by intel. I shall be trying to install 11.10 Oneiric Ocelot later today. but for now i'll call it a day. thanks for the help guys much appreciated :)

---

### Post by darkod on 2013-03-10
When we say it's working like SW raid that doesn't mean it's a particular program that shows up. Just that it works on software level without its own dedicated HW. In fact, the configuration being from Intel might actually mean it's fakeraid since most dedicated cards/chips are from Adaptec or LSI...

---

### Post by briancachia on 2013-03-10
hmm ic, then I m not quite sure what it is if its HW or SW RAID. I m not sure whether i mentioned this before but it is a rackmount server so from that i assumed it was HW RAID. Still hardware or software raid the RAID1 is supposed to be configured before the installation of ubuntu and therefore I am supposed to see the logical drive not the 2 physical ones. This morning I tried installing ubuntu 11.10 server but still the same result. Both physical drives showed up and no logical ones.

---

### Post by darkod on 2013-03-10
Boot the machine with the desktop live cd in live mode, and see if it shows one sda device (the array) or two separate disks. Live mode can also help you check the chipset of the raid controller (doesn't matter if it's HW or fakeraid). You should be able to check this with listing all PCI devices with:
```
lspci
```

That can help you troubleshoot further, whether the ubuntu server version recognizes this raid chipset or not, whether it needs a specific driver, etc.

If in live mode you see something like /dev/mapper/... that usually means fakeraid. If you need to activate it first you can do it with the command I posted in post #5.

---

### Post by briancachia on 2013-03-10
That s a good idea i don't know why I didn't think of that before. But i m afraid its too late now since i found another solution although not what I wanted exactly. I managed to disable the SATA for RAID option from the bios so that the server could boot up without RAID and then I did a SW RAID provided by the ubuntu partitioner. Still installing let's hope it works. :) thanks for the help again :)

---

### Post by darkod on 2013-03-10
If you can change the SATA mode in bios that is another pointer that we are talking only about fakeraid, not HW raid.

In this case what you did is actually better, since mdadm SW raid is recommended over fakeraid. So, stick with it.

---


---
title: "How to turn my internal HD into a bootable external HD?"
date: 2012-05-25
forum: Installation &amp; Upgrades
---

### Post by woodfire on 2012-05-25
Hi, I just upgraded my laptop hard disk and put the replaced into an enclosure to make it an external HD. It has Windows 7 and Ubuntu 12.04 installed on two separate partitions. I am wondering if it is possible to make this external HD bootable while still keep the Ubuntu system - I can boot into Ubuntu from the external HD. 

Thanks,

---

### Post by HalfNote5 on 2012-05-26
> **woodfire said:**
> Hi, I just upgraded my laptop hard disk and put the replaced into an enclosure to make it an external HD. It has Windows 7 and Ubuntu 12.04 installed on two separate partitions. I am wondering if it is possible to make this external HD bootable while still keep the Ubuntu system - I can boot into Ubuntu from the external HD. 

Thanks,

You can, but only if your BIOS supports booting from USB devices (though most do these days).

You'll need to mark your Windows partition as an "active" partition in the Disk Manager under Windows but I'm unsure how that'll affect the preinstalled Ubuntu.

What you may have to do is re-install on the external disk.

Also, Windows may BOOT from a USB but it DOES NOT want to install to it.  Ubuntu will - I've done it several times for various reasons.

---

### Post by TheFu on 2012-05-26
I would add that if the enclosure or PC connection is only USB2, then the** performance will suffer, badly.** It is good enough in a pinch/emergency, but not good enough for daily use, IMHO.

USB3 or eSATA would be as fast as an internal connection. eSATA behaves just like an internal SATA connection - highly recommended. **eSATA rocks** in the way that ssh, rsync, and fire rock.  

I've had performance issues with USB3 devices - this could be settings or hardware problems or bus contention.  I don't know, but when more than 3 requests are made to the same USB3 device, all the requests seem to get stuck for 20-30 seconds.

---

### Post by woodfire on 2012-05-26
Thanks a lot. 

I know how to install Ubuntu onto external HD and boot from that. My question was how to avoid re-installation, and just use the pre-installed ubuntu system as it was on "internal hard disk". I tried to search on the forum but didn't really find a related thread. 
 

> **HalfNote5 said:**
> You can, but only if your BIOS supports booting from USB devices (though most do these days).

You'll need to mark your Windows partition as an "active" partition in the Disk Manager under Windows but I'm unsure how that'll affect the preinstalled Ubuntu.

What you may have to do is re-install on the external disk.

Also, Windows may BOOT from a USB but it DOES NOT want to install to it.  Ubuntu will - I've done it several times for various reasons.

---

### Post by C.S.Cameron on 2012-05-26
Have you tried booting Ubuntu from the external drive as is?
It should work.

---

### Post by woodfire on 2012-05-26
I tried but the hard disk is not bootable. I did some research but it seems that it requires formatting to make the external hard disk bootable- I don't want to format the whole disk and reinstall ubuntu over over again. 

I believe there must be someone who can help me out from this forum. :popcorn:  

> **C.S.Cameron said:**
> Have you tried booting Ubuntu from the external drive as is?
It should work.

---

### Post by oldfred on 2012-05-26
As C.S.Cameron said, if it booted from the internal, it should boot from the external. But your BIOS does have to support booting from external drives.

To see what is where run the Bootinfo report:

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration.

---

### Post by woodfire on 2012-05-26
unfortunately I had a problem with installation of boot-repair

[I][B]sudo apt-get install -y boot-repair && boot-repair
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package boot-repair[/B]
[/I]

> **oldfred said:**
> As C.S.Cameron said, if it booted from the internal, it should boot from the external. But your BIOS does have to support booting from external drives.

To see what is where run the Bootinfo report:

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration.

---

### Post by oldfred on 2012-05-26
Boot repair is not in the UBuntu repository. You have to add its repository before trtrying to install it.

```
sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update
```

---

### Post by HalfNote5 on 2012-05-26
Also, as an added measure, maybe check the partition's boot flags using gparted. 

Also, when you boot your machine, it might have USB boot capability, but it may not be ENABLED by default in the BIOS to use USB devices under normal boot sequence.

Try, instead, using your manual boot menu (usually either f12 or f9) on startup, and specifying your USB device.

Also, I have a few new Acers that I love very much, but their mistake in pre-loaded settings is frustrating: they have the f12 boot menu disabled, and you have to enable it in the BIOS and THEN use it.  ; )

Cheers!

---

### Post by woodfire on 2012-05-26
I did run that line before, it was fine though. 
> **oldfred said:**
> Boot repair is not in the UBuntu repository. You have to add its repository before trtrying to install it.

```
sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update
```

---


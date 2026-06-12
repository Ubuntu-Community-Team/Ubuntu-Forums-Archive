---
title: "Install CD hardlocks before installation begins (possible USB issue?) 6.10 Ubuntu"
date: 2007-03-29
forum: Installation &amp; Upgrades
---

### Post by Cool Matty on 2007-03-29
OK, so here's what's going on.

I stick the CD in. Reboot the PC. The CD loads. I get to pick my boot options normally.

Upon picking any install option, it hard locks only seconds later.

Since I am running an IBM Thinkpad laptop with only 120MB RAM, I am using the alternative install CD.

Removing the "quiet" boot option shows that the boot seems to be dying at the USB driver loading. The last line in the window before it hard locks is:

[        35.23578] ohci_hcd 0000:00:14.0: irq 10, io mem 0x2400000

I have tried numerous boot options, including:

nousb
noapic
nolapic
debian-installer/probe/usb=false
mem=120m   (The amount of RAM I have)

None of these resolves the error. At this point, I'd be perfectly fine with no usb support at all. I just want the blasted thing to run. Nothing I seem to do is keeping the thing from loading USB drivers during this initial CD boot!

Any help would be great, and if you require more of the boot messages, I can provide some.

---

### Post by slayerboy on 2007-03-30
First, do you have anything plugged into the USB ports?

Second, 120MB of RAM is not really enough.  I don't think it would be causing an issue like this, but you'd be better off trying xubuntu first.

Also, you might want to run a memory test to see if it's possible faulty memory.  This is not a common amount of memory, as you most likely would have 128MB.  Which is probably a combination of two 64MB memory chips, it might only report 120 MB in the bios.  A memory test will tell if one or both of the memory chips are faulty.

---

### Post by otakumark on 2007-03-31
Typically with an older machine with limited memory, the memory is shared with it's video device, which in this case may be an S3 or Intel integrated video adapter utilizing 8mb of memory. It is very, very common to see lower reported memory amounts than what is expected because of this.

---

### Post by slayerboy on 2007-03-31
> **otakumark said:**
> Typically with an older machine with limited memory, the memory is shared with it's video device, which in this case may be an S3 or Intel integrated video adapter utilizing 8mb of memory. It is very, very common to see lower reported memory amounts than what is expected because of this.
oh yeah..... good point....;)

---


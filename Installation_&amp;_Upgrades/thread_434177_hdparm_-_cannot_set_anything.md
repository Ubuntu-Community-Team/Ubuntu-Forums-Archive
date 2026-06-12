---
title: "hdparm - cannot set anything"
date: 2007-05-05
forum: Installation &amp; Upgrades
---

### Post by finalzero on 2007-05-05
Right, I am getting quite annoyed with Feisty and beginning to think its not quite fit for purpose.

I had to do an OS dance to get the bloody thing working as the upgrade on an existing (tweaked) system falls flat on its face.

Now I am finding Feisty Fawn treats all my drives as SATA,  even though I don't use SATA.  Now I was very much aware of the performance of my system when I was running Edgy and I took the time to tune the hard disk performance on that build to a point where I was getting some very fast access times and my desktop experience was good.

Now that I am running Feisty, I decided to take some performance stats and compare the results with Edgy and I found the following:

My drives are running in 16bit compatibility mode
No dma
Compatibility mode = 33mhz

Now that is not right, in Edgy I had my drives using 32bit access with DMA, unmasked irq mode and ATA100 access.  To confirm I compared read and write times and they are abysmal with Feisty Fawn.

hdparm does not work period - its next to useless now and only good for testing read/write performance on the drives. As such I am also unable to burn anything as I cannot set the DMA switch on my burners.

And lastly what is up with the swap disk, I noticed its now redundant and not being used anymore?

Thanks,

Fz

---

### Post by Stephen Howard on 2007-05-06
Try sdparm instead.

---

### Post by Stephen Howard on 2007-05-06
That said, I have no idea how unified the scsi/ide scheme is - particularly as I don't believe there's a 1:1 correlation between ide & scsi performance tweaks.

If you do try it, I'd be interested in hearing how you go.

---

### Post by Stephen Howard on 2007-05-06
Swap is working on my Feisty install:
```

[FONT="Fixedsys"]stephen@mercury:/proc$ vmstat
procs -----------memory----------       ---swap-- -----io---- -system-- ----cpu----
 r   b   swpd   free  buff   cache      si   so    bi   bo     in     cs    us    sy   id    wa
 1   0   44784  29372 13912  135400     0    2     36   339    272    624   20    4    75    2[/FONT]
```

---

### Post by finalzero on 2007-05-06
sdparm does not work, complains about the wrong drive parameter.

---

### Post by Stephen Howard on 2007-05-06
Here's a related conversation from [freshmeat]("http://freshmeat.net/projects/hdparm/").  I think it answers your questions??  

> [»] sata drive usage?
by waltermh - Jun 27th 2005 11:53:24

is hdparm useful with sata drives, does it work with sata drives?

when i try hdparm -d /dev/sda i get
[root@localhost ~]# hdparm -d /dev/sda

/dev/sda:

so i cant tell if its off or on, doing hdparm -v -I /dev/sda gets me this:
[root@localhost ~]# hdparm -v -I /dev/sda

/dev/sdc:
IO_support = 0 (default 16-bit)
readonly = 0 (off)
readahead = 256 (on)
geometry = 30515/255/63, sectors = 251000193024, start = 0
HDIO_DRIVE_CMD(identify) failed: Inappropriate ioctl for device

I dont get that last part, when i try hdparm on my ata drive i can get all info.

[reply] [top] 



--------------------------------------------------------------------------------

[»] Re: sata drive usage?
by Mark Lord - Jun 27th 2005 12:15:24


> is hdparm useful with sata drives, does

> it work with sata drives?

SATA drives in the 2.6 kernel are handled by the new "libata" SCSI driver. If you add the "ATA passthru" patch (from Jeff Garzik) to your kernel, then hdparm can work with those drives.

Some flags, like "-d", are not supported by libata. Currently, ALL SATA hard drives use DMA, so there is no need for -d. But eventually libata will have to implement ATA PIO (for CF cards..), and at that time it may (or not) begin to support the "-d" flag.

[reply] [top] 



--------------------------------------------------------------------------------

[»] Re: sata drive usage?
by waltermh - Jun 27th 2005 12:26:58

thanks will try google for that patch i guess, never patched a kernel before i have seen people online get numbers from -tT option for sata around 1000+ for cache, and 100+ for buffer, and i am getting 520-530 and 50-65 respectively i am testing on 2 drives that dont do anything but hold backup files getting 60-65 buffer, and my main drive getting 54 buffer, of course testing multiple times, just hoping i can get numbers higher io support is at 16 bit default, i get an error when switching to 32bit, is that one of those currently unsupported features?

[reply] [top] 



--------------------------------------------------------------------------------

[»] Re: sata drive usage?
by Mark Lord - Jun 27th 2005 12:38:39

If "hdparm -I /dev/sda" works (uppercase -I), then your kernel already has the passthru patch. The I/O 16 bit only applies to non-DMA IDE drives. Since SATA drives all use DMA, that setting doesn't matter and is not supported by libata. About the only flags you can play with to improve things are the "-A" (read-ahead) and "-W" (write-caching). A few people think -W1 is a bad idea, but as a kernel developer I generally crash my machine daily, and -W1 has never cost me any data while saving me hours of time (it really speeds up many machines). Cheers

[reply] [top] 

---

### Post by finalzero on 2007-05-08
> **Stephen Howard said:**
> Try sdparm instead.

Doesn't work, I have IDE drives so it fails to recognize the hdd's

---

### Post by DrSpirograph on 2007-08-05
I ended up building my own kernel to get around this.

If you want to use the kernel or follow instructions as to how, check it out here:
[http://drspirograph.com/blog/archives/2007-08-05-Non-libata-kernel.html](http://drspirograph.com/blog/archives/2007-08-05-Non-libata-kernel.html)

---


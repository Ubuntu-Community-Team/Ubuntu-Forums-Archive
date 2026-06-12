---
title: "Install/Use ubuntu on a defected hd"
date: 2008-01-12
forum: Installation &amp; Upgrades
---

### Post by mrgamer on 2008-01-12
dear ubuntuists, i've recently discovered a slightly annoying issue with one of my harddisk drives...
i was using it as NTFS storage, and when i went for repartition it, my OSes started discovering bad sectors: this implies that both windows and any linux distribution goes very slow reading it cause of reading errors

using badblocks seems that most of my bad sectors are in the first 1000 blocks of the hd (using as blocksize 4096, ext3 default for my partitions), so i just thinked about skipping the first 10MB of harddrive and partition the rest!

doing like:
```
                          cfdisk (util-linux-ng 2.13)

                              Disk Drive: /dev/sdc
                       Size: 120000000000 bytes, 120.0 GB
             Heads: 255   Sectors per Track: 63   Cylinders: 14589

    Name        Flags      Part Type  FS Type          [Label]        Size (MB)
 ------------------------------------------------------------------------------
                            Pri/Log   Free Space                      109494.93 
    sdc1        Boot        Primary   Linux ext3                       10503.69

```

after that i've formatted that only partition with "mkfs.ext3 -c /device", he found some sporadic bad sector, but he succeded in formatting the partition

the *annoying* problem is that at every boot he spams me with stuff like:
```
[    9.860000] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[    9.868000] ata3.00: (BMDMA stat 0x64)
[    9.872000] ata3.00: cmd c8/00:58:30:00:00/00:00:00:00:00/e0 tag 0 cdb 0x0 data 45056 in
[    9.872000]          res 51/01:00:4f:00:00/00:00:00:00:00/e0 Emask 0x1 (device error)
[    9.912000] ata3.00: configured for UDMA/133
[    9.916000] ata3: EH complete
```

slowing boot! afaik the errors he reads are not in the partition (or it would be ext3 to spam them)

what i wanna do is just use that hd as a storage with absolutely non-important data on it, so there is a way to suppress those errors or to format the hd in a way it skips the bad sectors completely ?

Link to complete dmesg and smartctl responses:
[http://pastebin.com/m2ee7e435](http://pastebin.com/m2ee7e435) - **dmesg**
[http://pastebin.com/m6dc9c534](http://pastebin.com/m6dc9c534) - **smarctl -a -d ata /device**

---

### Post by Wiebelhaus on 2008-01-12
Honestly man , Let the dead horse lie ,[ Hdd's are dirt cheap now.]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822144102")

---

### Post by amo-ej1 on 2008-01-12
i second sx66gns, you should now that those errors will spread, making the medium very unreliable, the walking on eggs kinda things. Also the errors will slow your system. First there is an error, some correction, so that costs time, then they have printed, which is also extremely heavy to do from a kernel. Then syslog captures those messages, and writes them to disk. Hence these errors will trigger MORE errors.... 

The only thing you could do if you suspect a part of the disk being bad, is to adapt your partition table so the 'bad' part of the disk isn't used. This might help on some occasions but the ideal solution is a shiny new cheap hard disk ;)

---

### Post by Wiebelhaus on 2008-01-12
Aye , The primary concern here is Stability and then Data Retention , neither you will get from a failing hard drive.

---


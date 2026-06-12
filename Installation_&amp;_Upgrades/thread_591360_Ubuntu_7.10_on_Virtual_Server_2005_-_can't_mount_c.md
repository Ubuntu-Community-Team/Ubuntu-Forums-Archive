---
title: "Ubuntu 7.10 on Virtual Server 2005 - can't mount cd-rom"
date: 2007-10-25
forum: Installation &amp; Upgrades
---

### Post by olsor@yahoo.com on 2007-10-25
Hi,
I'm trying to install ubuntu 7.10 server as a virtual machine under MS Virtual Server 2005 R2 SP1 but am having a problem. I get an error from the installer that says "Can't mount cd-rom", which is confusing since the installer is actually running from my cd-rom drive. Since the installer can't mount my cd-rom drive, the installation is halted. I'm running a DELL poweredge 2950.
Thanks
Ray

---

### Post by Francois Koutchouk on 2007-11-01
Same problem -- did anyone find a solution?

---

### Post by olsor@yahoo.com on 2007-11-02
Well, I'm able to get around the problem by using the mini installer iso and then install everything from the network connection. But, I still have the problem that my ubuntu VM does not recognize my cd-rom drive at all. I think it has something to do with the default adapter driver it tries to use does not work correctly with my dell Poweredge IDE adapter. Anyone have any recommendations?
Thanks

---

### Post by rodharden on 2007-11-02
I getting this message too, although I change sereval option on this virtual machine at my Virtual Server 2005 R2 SP1 . 
I think that the community modified the Windows's Default VM CDROM driver and now the installation cannot find it. 
I can't figured out how to make this work. For this moment, i will continue using my ubuntu 7.04 VM.

---

### Post by guismai on 2007-11-06
Same pb !!! and a big Youpi for MS !!!

---

### Post by Macfox on 2007-11-09
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/155607](https://bugs.launchpad.net/ubuntu/+bug/155607) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Same issue here. Seems the updated kernel in v7.10 doesn't play nice with VS 2005 SP1

Here's the errors I get booting Server v7.10 (Kernel 2.6.22-14-generic)

(transcribed form screen. Might be a typo or two, but see screen shot for exact error.) 

```
cdrom-detect: Searching for Ubuntu installation media...
ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
ata2.00: cmd a0/01:00:00:00:00/00:00:00:00:00/a0 tag 0 cdb 0x28 data 2048 in
ata2.00: res 40/00:02:00:0c:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
ata2: soft resetting port
ata2.00: configured for MWDMA2
ata2: EH complete

....

ata2: soft resetting port
ata2.00: configured for MWDMA1
sr 1:0:0:0: [sr0] Result hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
sr 1:0:0:0: [sr0] Sense Key : Aborted Command [current] [descriptor]
Descriptor sense data with sense descriptors (in hex)
         72 ob 00 00 00 00 00 0e 09 0c 00 00 00 02 00 00
         00 0c 00 00 a0 40
sr 1:0:0:0: [sr0] Add. Sense: No additional sense information
end_request:I/O error, dev sr0, secotr 64
ata2: EH complete
isofs_fill_super: bread failed, dev+sr0, iso_blknum=16, block=16


```



Rob

---


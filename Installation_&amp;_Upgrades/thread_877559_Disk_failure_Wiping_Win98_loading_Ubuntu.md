---
title: "Disk failure Wiping Win98 loading Ubuntu"
date: 2008-08-01
forum: Installation &amp; Upgrades
---

### Post by mjlackner on 2008-08-01
I was finally satisfied enough to complete my install and repartition over my Win98 (FE...please laugh at me here).  I encountered a disk failure @ 66% complete, and was not able to recover.  Now I cannot boot the machine at all, getting an "Operating System not found".

Apparently this machine won't boot from one of my two CD drives (1 RW, the other R Only).

I'm stuck.

---

### Post by Pumalite on 2008-08-01
Get rescuecd and take a look:
[http://www.sysresccd.org/Download](http://www.sysresccd.org/Download)

---

### Post by mjlackner on 2008-08-02
Sysrescuecd was really very productive, though not solved.  I get intermittant results booting from CDROM.  90% of the time I still get "Op Sys not found".  I was able to get SysRescue to boot twice, and Ubuntu to boot once.

Regardless, the Ubuntu install did still not complete normally...many HD errors.  SysRescue was able to boot, I could mount my second CDROM, and get to UbuntuCD, though was still not able to load new, non-Win98 boot to HD.  Under SysRescue, I was able to run 'badblocks' on HD and found none.

Very perplexing.  No rhyme or reason why inconsistent BIOS issues with CDROM booting.

The system has 1 hard drive(master), 1 floppy (physically slave to HD, but disabled in BIOS.  I have 2 CDROMs; 1 RW Ricoh, another R-Only.  I have them setup in BIOS as Secondary Master (R-Only), and Secondary Slave (RW).  Through all this gyration, I have Set boot on Secondary, set HD & Floppy to [NONE] in BIOS, and achieve the 10% Boot on R-Only.

As an aside, I did come across the Legacy USB, so my USB keyboard now works for both machines...KVM investment realized.

Thanks Pumalite for the recommend on SysRescue.  I learned a lot today.  It is a cool tool.

-Mark

---


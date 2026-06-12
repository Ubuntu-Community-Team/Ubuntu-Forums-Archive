---
title: "DMRAID and loading multiple partitions configured in the (Fake)RAID controller"
date: 2007-12-18
forum: Installation &amp; Upgrades
---

### Post by Jusitn_taco on 2007-12-18
**Clarification RAID Disk = Physical Disk, Drive = Configured disc allocation in the RAID controller**

Before I begin I will give some background information. I have setup my ATI (Really Promise RAID controller) RAID from my M2R32-MVP motherboard. There are 2 RAID Disks and I created 2 drives, a 20GB and a 120GB drive. 

Now because I did 2 drives instead of 1 drive I have 2 meta descriptions associated to the RAID. One for each drive. In order to detect each drive separately I copied the pdc.c and pdh.h files (from the DMRAID source) and set them to the offset position of the 2nd drive while the original files were the 1st drive. I compiled everything properly but when it comes time to detect the disks DMRAID detects both meta description but only chooses one. 

I used this command to get the output of the detection:  dmraid -tay -vvvv -dddd 

Here is the output:

WARN: locking /var/lock/dmraid/.lock
NOTICE: skipping removable device /dev/hdb
NOTICE: /dev/sda: asr     discovering
NOTICE: /dev/sda: ddf1    discovering
NOTICE: /dev/sda: hpt37x  discovering
NOTICE: /dev/sda: hpt45x  discovering
NOTICE: /dev/sda: isw     discovering
NOTICE: /dev/sda: jmicron discovering
NOTICE: /dev/sda: lsi     discovering
NOTICE: /dev/sda: nvidia  discovering
NOTICE: /dev/sda: pdc     discovering
NOTICE: /dev/sda: pdc metadata discovered
NOTICE: /dev/sda: pdc2    discovering
NOTICE: /dev/sda: pdc2 metadata discovered
/dev/sda: "pdc2" and "pdc" formats discovered (using pdc)!
NOTICE: /dev/sda: sil     discovering
NOTICE: /dev/sda: via     discovering
NOTICE: /dev/sdb: asr     discovering
NOTICE: /dev/sdb: ddf1    discovering
NOTICE: /dev/sdb: hpt37x  discovering
NOTICE: /dev/sdb: hpt45x  discovering
NOTICE: /dev/sdb: isw     discovering
NOTICE: /dev/sdb: jmicron discovering
NOTICE: /dev/sdb: lsi     discovering
NOTICE: /dev/sdb: nvidia  discovering
NOTICE: /dev/sdb: pdc     discovering
NOTICE: /dev/sdb: pdc2    discovering
NOTICE: /dev/sdb: sil     discovering
NOTICE: /dev/sdb: via     discovering
NOTICE: /dev/sdc: asr     discovering
NOTICE: /dev/sdc: ddf1    discovering
NOTICE: /dev/sdc: hpt37x  discovering
NOTICE: /dev/sdc: hpt45x  discovering
NOTICE: /dev/sdc: isw     discovering
NOTICE: /dev/sdc: jmicron discovering
NOTICE: /dev/sdc: lsi     discovering
NOTICE: /dev/sdc: nvidia  discovering
NOTICE: /dev/sdc: pdc     discovering
NOTICE: /dev/sdc: pdc metadata discovered
NOTICE: /dev/sdc: pdc2    discovering
NOTICE: /dev/sdc: pdc2 metadata discovered
/dev/sdc: "pdc2" and "pdc" formats discovered (using pdc)!
NOTICE: /dev/sdc: sil     discovering
NOTICE: /dev/sdc: via     discovering
NOTICE: /dev/hda: asr     discovering
NOTICE: /dev/hda: ddf1    discovering
NOTICE: /dev/hda: hpt37x  discovering
NOTICE: /dev/hda: hpt45x  discovering
NOTICE: /dev/hda: isw     discovering
NOTICE: /dev/hda: jmicron discovering
NOTICE: /dev/hda: lsi     discovering
NOTICE: /dev/hda: nvidia  discovering
NOTICE: /dev/hda: pdc     discovering
NOTICE: /dev/hda: pdc2    discovering
NOTICE: /dev/hda: sil     discovering
NOTICE: /dev/hda: via     discovering
NOTICE: /dev/sdd: asr     discovering
NOTICE: /dev/sdd: ddf1    discovering
NOTICE: /dev/sdd: hpt37x  discovering
NOTICE: /dev/sdd: hpt45x  discovering
NOTICE: /dev/sdd: isw     discovering
NOTICE: /dev/sdd: jmicron discovering
NOTICE: /dev/sdd: lsi     discovering
NOTICE: /dev/sdd: nvidia  discovering
NOTICE: /dev/sdd: pdc     discovering
NOTICE: /dev/sdd: pdc2    discovering
NOTICE: /dev/sdd: sil     discovering
NOTICE: /dev/sdd: via     discovering
DEBUG: _find_set: searching pdc_cghdi
DEBUG: _find_set: not found pdc_cghdi
DEBUG: _find_set: searching pdc_cghdi
DEBUG: _find_set: not found pdc_cghdi
NOTICE: added /dev/sda to RAID set "pdc_cghdi"
DEBUG: _find_set: searching pdc_cghdi
DEBUG: _find_set: found pdc_cghdi
DEBUG: _find_set: searching pdc_cghdi
DEBUG: _find_set: found pdc_cghdi
NOTICE: added /dev/sdc to RAID set "pdc_cghdi"
DEBUG: checking pdc device "/dev/sdc"
DEBUG: checking pdc device "/dev/sda"
DEBUG: set status of set "pdc_cghdi" to 16
DEBUG: checking pdc device "/dev/sdc"
DEBUG: checking pdc device "/dev/sda"
DEBUG: set status of set "pdc_cghdi" to 16
pdc_cghdi: 0 39062272 striped 2 128 /dev/sdc 0 /dev/sda 0
INFO: Activating stripe RAID set "pdc_cghdi"
NOTICE: discovering partitions on "pdc_cghdi"
NOTICE: /dev/mapper/pdc_cghdi: dos     discovering
NOTICE: /dev/mapper/pdc_cghdi: dos metadata discovered
DEBUG: _find_set: searching pdc_cghdi1
DEBUG: _find_set: not found pdc_cghdi1
NOTICE: created partitioned RAID set(s) for /dev/mapper/pdc_cghdi
pdc_cghdi1: 0 39053952 linear /dev/mapper/pdc_cghdi 63
INFO: Activating partition RAID set "pdc_cghdi1"
WARN: unlocking /var/lock/dmraid/.lock
DEBUG: freeing devices of RAID set "pdc_cghdi"
DEBUG: freeing device "pdc_cghdi", path "/dev/sdc"
DEBUG: freeing device "pdc_cghdi", path "/dev/sda"
DEBUG: freeing devices of RAID set "pdc_cghdi1"
DEBUG: freeing device "pdc_cghdi1", path "/dev/mapper/pdc_cghdi"


Does anyone know how to detect the 2 drives or am I up **** creak?

*********************************************************************
I just tried reversing the offsets in the 2 files and I still get the same drive. I think this is because my Dataoffset variable is set to 0. Does anyone know how to determine you dataoffset? I looked at the meta data dump and theres no obvious value.

---

### Post by Desperate on 2008-01-11
Hi Jusitn_taco,
same problem here and lots of data on the disk I don't want to loose. 
Was told that Knoppix should/would be able to fix it, ordered it but not in yet.

Good to know that I'm not the only one struggling with this :)
Good luck and if.... please PM me, I'm running from the live cd so email is not up yet.

Richard

---


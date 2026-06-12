---
title: "ext3 usb drive crashes intrepid"
date: 2008-09-04
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by sintacto on 2008-09-04
after latest update my usb drive messes up the cpu to 100%
and the load meter is all red if you know what i mean. it wont mount or show up in lsusb. 

dmesg = 1148.929077] sd 4:0:0:0: [sdb] Sense Key : No Sense [current] 
[ 1148.929087] sd 4:0:0:0: [sdb] Add. Sense: No additional sense information
[ 1148.930326] sd 4:0:0:0: [sdb] Sense Key : No Sense [current] 
[ 1148.930337] sd 4:0:0:0: [sdb] Add. Sense: No additional sense information
[ 1148.931572] sd 4:0:0:0: [sdb] Sense Key : No Sense [current] 
[ 1148.931583] sd 4:0:0:0: [sdb] Add. Sense: No additional sense information
[ 1148.932827] sd 4:0:0:0: [sdb] Sense Key : No Sense [current] 
[ 1148.932838] sd 4:0:0:0: [sdb] Add. Sense: No additional sense information
[ 1148.934076] sd 4:0:0:0: [sdb] Sense Key : No Sense [current] 
[ 1148.934086] sd 4:0:0:0: [sdb] Add. Sense: No additional sense information
[ 1148.935201] sd 4:0:0:0: [sdb] Sense Key : No Sense [current] 
[ 1148.935212] sd 4:0:0:0: [sdb] Add. Sense: No additional sense information
[ 1148.936328] sd 4:0:0:0: [sdb] Sense Key : No Sense [current] 
[ 1148.936339] sd 4:0:0:0: [sdb] Add. Sense: No additional sense information
[ 1148.937450] sd 4:0:0:0: [sdb] Sense Key : No Sense [current] 
[ 1148.937461] sd 4:0:0:0: [sdb] Add. Sense: No additional sense information
[ 1148.938699] sd 4:0:0:0: [sdb] Sense Key : No Sense [current] 
[ 1148.938710] sd 4:0:0:0: [sdb] Add. Sense: No additional sense information
[ 1148.939824] sd 4:0:0:0: [sdb] Sense Key : No Sense [current] 
[ 1148.939835] sd 4:0:0:0: [sdb] Add. Sense: No additional sense information
[ 1148.941077] sd 4:0:0:0: [sdb] Sense Key : No Sense [current] 
[ 1148.941089] sd 4:0:0:0: [sdb] Add. Sense: No additional sense information

well a few lines of it

when i unplug it everything goes back to normal
it is 80 gig all ext3 

any ideas?

---

### Post by sddfdds on 2008-09-04
I reported a similar bug here:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/264789](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/264789)

Although I dont get 100% cpu usage or crashes, myself.

---

### Post by sintacto on 2008-09-05
thanks ill follow that bug.
my cpu goes way up to 100% i thought my usb drive went bad or i had a virus? in it. but it mounts with a pretty desktop icon in a gutsy laptop.

---

### Post by sddfdds on 2008-09-05
Yea, my drive is running fine on a usb-ata adapter, plugged ironically in the usb hub of the enclosure that isn't recognized.

---

### Post by sintacto on 2008-09-05
ive tried other usb ports but still dont work
any one have ideas?

---

### Post by sintacto on 2008-09-05
I did get a lsusb while its plugged in
.yavapai@desktop:~$ lsusb
Bus 005 Device 003: ID 03f0:3202 Hewlett-Packard photosmart 1215
Bus 005 Device 002: ID 03f0:1502 Hewlett-Packard Photosmart 420 Series
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c01a Logitech, Inc. M-BQ85 Optical Wheel Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 059b:0177 Iomega Corp. Hi-Speed USB-to-IDE Bridge Controller
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
I'ts device 005 iomega usb hard drive formated to ext3

this is the end of dmesg:
[  611.217767] sd 4:0:0:0: [sdb] Add. Sense: No additional sense information
[  611.218753] sd 4:0:0:0: [sdb] Sense Key : No Sense [current] 
[  611.218763] sd 4:0:0:0: [sdb] Add. Sense: No additional sense information
[  611.219881] sd 4:0:0:0: [sdb] Sense Key : No Sense [current] 
[  611.219890] sd 4:0:0:0: [sdb] Add. Sense: No additional sense information
[  611.221008] sd 4:0:0:0: [sdb] Sense Key : No Sense [current] 
[  611.221019] sd 4:0:0:0: [sdb] Add. Sense: No additional sense information
[  611.280327] usb 1-4: USB disconnect, address 5
[  611.285442] scsi 4:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[  611.285458] end_request: I/O error, dev sdb, sector 156301488
[  611.285474] Buffer I/O error on device sdb, logical block 156301488
[  611.285519] Buffer I/O error on device sdb1, logical block 1
[  611.285528] Buffer I/O error on device sdb1, logical block 2
[  611.285536] Buffer I/O error on device sdb1, logical block 3
[  611.285543] Buffer I/O error on device sdb1, logical block 4
[  611.285551] Buffer I/O error on device sdb1, logical block 5
[  611.285559] Buffer I/O error on device sdb1, logical block 6
[  611.285566] Buffer I/O error on device sdb1, logical block 7
[  611.285574] Buffer I/O error on device sdb1, logical block 8
[  611.285582] Buffer I/O error on device sdb1, logical block 9
[  611.285603] scsi 4:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[  611.285612] end_request: I/O error, dev sdb, sector 63
yavapai@desktop:~$

---

### Post by sddfdds on 2008-09-07
I installed beagle on this system, and last night when i also had the drive lock up with the AddSenses, and again tonight, I realized that the Add Sense stuff was happening when beagle was stuck trying to index the same directory.  Something funny with this directory seems to be confirmed because I tried to copy it to a different drive, which again set off the Add Senses.  I was able to delete the directory though, so hopefully tomorrow when I try running beagle again, it will index everything successfully.  I'm also going to re-run e2fsck even though it was successful before.  Should I try running e2fsck with -c as well to check for badblocks, or is that something that would have spit out an error with normal e2fsck in the first place?  The odd thing about all this though, it doesnt really make sense why the drive went straight to the AddSenses when it was in the usb enclosure instead of the adapter I'm currently using.

---

### Post by sintacto on 2008-09-08
thanks Jason
Ive also tried e2fsck and didn't help
i don't have a way to connect the 3.5'' drive up besides usb 
to trouble shoot it elsewhere. 
again heres my problem it might be different enough to file a bug but your bug #264789 dosn't seem to begetting much attention.
ext3 usb drive 80gigs wont mount it did with 8.04 and before.
worked in 8.10 at first after an update a few days ago (2.6.27-2-generic)
it stopped working.
1) plug it in. right away cpu 100% till i unplug it.
2) doesn't mount 
3) it still works with my laptop 2.6.22-generic

---


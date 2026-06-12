---
title: "ext2 cdrom block size problem"
date: 2009-03-30
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by replab_robin on 2009-03-30
I have an upto date jaunty as of March 30 12:00 UTC running on fairly old hardware.

When I try to mount some old ext2 formatted cdroms (from 1999) I'm getting an error message that says the blocksize is wrong.

The command I use is

# mount -t ext2 -oro /dev/cdrom /media/cdrom

in dmesg I'm seeing this

[238920.146718] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[238920.146727] sr 1:0:0:0: [sr0] Sense Key : Medium Error [current]
[238920.146733] sr 1:0:0:0: [sr0] Add. Sense: L-EC uncorrectable error
[238920.146740] end_request: I/O error, dev sr0, sector 1310720
[238920.146749] Buffer I/O error on device sr0, logical block 163840
[238938.647154] EXT2-fs: blocksize too small for device.
[238956.271213] EXT3-fs: blocksize 1024 too small for device blocksize 2048.
[239003.760187] EXT2-fs: blocksize too small for device.
[239066.680811] EXT2-fs: blocksize too small for device.

This is not lethal for me as I have managed to read these disks using dd on windows to raw copy the whole cd to a flash memory stick which is mountable as ext2 on my netbook which is running 8.10. Reason I want to use the cdrom directly is to eliminate error.

---


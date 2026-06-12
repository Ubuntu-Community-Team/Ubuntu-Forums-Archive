---
title: "After upgrading from 14.10 to 15.04, can no longer mount Android Phone"
date: 2015-05-06
forum: Installation &amp; Upgrades
---

### Post by jon-carmicheal on 2015-05-06
Hello Ubuntu community,

I have recently upgraded my Dell Inspiron 14R from Ubuntu 14.10 to 15.04.  While I was on 14.10, I had no problems with mounting my Android phone (HTC One M7 with Android 5.0.2).  I could open the device in the file manager and view/copy/create the content on the phone like a USB drive.  But since upgrading to 15.04, I have not been able to mount the phone.  When I plug in the phone, I get a pop-up saying something like Unable to mount "Android Phone."  Then the Nautilus file manager automatically opens to the "Android directory" but shows no contents.  

I've tried searching a few forums, but everything I've found so far seems too complicated for something that should (and did) "just work."  I'm not opposed to complicated, if that's what it takes, but I'm guessing there's something simple here that has gotten messed up during the upgrade.

Please let me know if there are any logs or screenshots, etc, that would help in troubleshooting this issue.

EDIT:  Since posting, I have taken these logs:
```
$ mtpfs -h
Unable to open ~/.mtpz-data for reading, MTPZ disabled.
Listing raw device(s)
Device 0 (VID=0bb4 and PID=0dea) is a HTC HTC One (MTP+UMS+ADB).
   Found 1 device(s):
   HTC: HTC One (MTP+UMS+ADB) (0bb4:0dea) @ bus 2, dev 7
Attempting to connect device
Android device detected, assigning default bug flags
Error 1: Get Storage information failed.
Error 2: PTP Layer error 02fe: get_handles_recursively(): could not get object handles.
Error 2: Error 02fe: PTP: Protocol error, data expected
Listing File Information on Device with name: (NULL)
LIBMTP_Get_Storage() failed:-1
```

-Jon

---

### Post by radek.manda on 2015-10-26
Hello All, same behaviour for me from migration from 14.10 to 15.04:

> mtpfs -h
Unable to open ~/.mtpz-data for reading, MTPZ disabled.
Listing raw device(s)
Device 0 (VID=04e8 and PID=6860) is a Samsung Galaxy models (MTP).
   Found 1 device(s):
   Samsung: Galaxy models (MTP) (04e8:6860) @ bus 1, dev 9
Attempting to connect device
ignoring libusb_claim_interface() = -6PTP_ERROR_IO: failed to open session, trying again after resetting USB interface
LIBMTP libusb: Attempt to reset device
Android device detected, assigning default bug flags
Error 1: Get Storage information failed.
Error 2: PTP Layer error 02fe: get_handles_recursively(): could not get object handles.
Error 2: Error 02fe: PTP: Protocol error, data expected
Listing File Information on Device with name: (NULL)
LIBMTP_Get_Storage() failed:-1

---


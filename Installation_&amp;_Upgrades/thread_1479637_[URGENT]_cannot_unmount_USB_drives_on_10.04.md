---
title: "[URGENT] cannot unmount USB drives on 10.04"
date: 2010-05-10
forum: Installation &amp; Upgrades
---

### Post by kakyoism on 2010-05-10
unmount seems to hang forever.... I then usually would just unplug my drives. Then maybe 20 minutes later there is a pop-up error box saying
```
Unable to stop MyDrive" DBus error .... did not receive a reply. Possible causes include: the remote application did not send a reply
```

It's urgent! Please help!

---

### Post by kakyoism on 2010-05-10
below is my dmesg at the time when umount hangs.

They are all NTFS drives. Here is my dmesg (partial, the complete one was too long to post here):

```
 ength = 1238
[257249.400044] ===>rt_ioctl_giwscan. 11(11) BSS returned, data->length = 1341
[257272.376285] usb 2-5.2: reset high speed USB device using ehci_hcd and address 9
[257309.301050] ===>rt_ioctl_giwscan. 9(9) BSS returned, data->length = 1074
[257356.373268] usb 2-5.2: reset high speed USB device using ehci_hcd and address 9
[257362.377251] usb 2-5.2: reset high speed USB device using ehci_hcd and address 9
[257369.298743] ===>rt_ioctl_giwscan. 10(10) BSS returned, data->length = 1238
[257429.301682] ===>rt_ioctl_giwscan. 11(11) BSS returned, data->length = 1306
[257446.383737] usb 2-5.2: reset high speed USB device using ehci_hcd and address 9
[257456.388319] usb 2-5.2: reset high speed USB device using ehci_hcd and address 9
[257489.298563] ===>rt_ioctl_giwscan. 10(10) BSS returned, data->length = 1280
[257526.385364] usb 2-5.2: reset high speed USB device using ehci_hcd and address 9
[257549.300050] ===>rt_ioctl_giwscan. 8(8) BSS returned, data->length = 903
[257562.385334] usb 2-5.2: reset high speed USB device using ehci_hcd and address 9
[257609.300576] ===>rt_ioctl_giwscan. 8(8) BSS returned, data->length = 936
[257669.301544] ===>rt_ioctl_giwscan. 8(8) BSS returned, data->length = 929
[257702.380551] usb 2-5.2: reset high speed USB device using ehci_hcd and address 9
[257729.401917] ===>rt_ioctl_giwscan. 8(8) BSS returned, data->length = 936
[257762.381395] usb 2-5.2: reset high speed USB device using ehci_hcd and address 9
[257789.301285] ===>rt_ioctl_giwscan. 8(8) BSS returned, data->length = 936
[257796.390007] usb 2-5.2: reset high speed USB device using ehci_hcd and address 9
[257849.301047] ===>rt_ioctl_giwscan. 8(8) BSS returned, data->length = 971
[257894.385301] usb 2-5.2: reset high speed USB device using ehci_hcd and address 9
[257909.301055] ===>rt_ioctl_giwscan. 10(10) BSS returned, data->length = 1238
[257969.300548] ===>rt_ioctl_giwscan. 8(8) BSS returned, data->length = 971
[258029.301281] ===>rt_ioctl_giwscan. 9(9) BSS returned, data->length = 1041
[258048.381333] usb 2-5.2: reset high speed USB device using ehci_hcd and address 9
[258089.299266] ===>rt_ioctl_giwscan. 11(11) BSS returned, data->length = 1278
[258094.370498] usb 2-5.2: reset high speed USB device using ehci_hcd and address 9
[258149.301078] ===>rt_ioctl_giwscan. 9(9) BSS returned, data->length = 1039
[258209.301050] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 689
[258232.373364] usb 2-5.2: reset high speed USB device using ehci_hcd and address 9
[258269.301010] ===>rt_ioctl_giwscan. 9(9) BSS returned, data->length = 1074
[258316.385842] usb 2-5.2: reset high speed USB device using ehci_hcd and address 9
[258329.301550] ===>rt_ioctl_giwscan. 11(11) BSS returned, data->length = 1341
[258336.389261] usb 2-5.2: reset high speed USB device using ehci_hcd and address 9
[258352.387314] usb 2-5.2: reset high speed USB device using ehci_hcd and address 9
[258389.298565] ===>rt_ioctl_giwscan. 8(8) BSS returned, data->length = 971
[258440.389772] usb 2-5.2: reset high speed USB device using ehci_hcd and address 9
[258449.300742] ===>rt_ioctl_giwscan. 8(8) BSS returned, data->length = 971
usb 2-5.2: reset high speed USB device using ehci_hcd and address 9
[293669.297532] ===>rt_ioctl_giwscan. 9(9) BSS returned, data->length = 1074
[293729.300547] ===>rt_ioctl_giwscan. 11(11) BSS returned, data->length = 1306
[293789.300044] ===>rt_ioctl_giwscan. 12(12) BSS returned, data->length = 1442
[293822.391954] usb 2-5.2: reset high speed USB device using ehci_hcd and address 9
[293849.300542] ===>rt_ioctl_giwscan. 9(9) BSS returned, data->length = 1074
[293862.369267] usb 2-5.2: reset high speed USB device using ehci_hcd and address 9
[293876.377327] usb 2-5.2: reset high speed USB device using ehci_hcd and address 9
[293909.298210] ===>rt_ioctl_giwscan. 12(12) BSS returned, data->length = 1444
[293969.297005] ===>rt_ioctl_giwscan. 11(11) BSS returned, data->length = 1339
[294029.300364] ===>rt_ioctl_giwscan. 11(11) BSS returned, data->length = 1341
[294070.373300] usb 2-5.2: reset high speed USB device using ehci_hcd and address 9
[294089.301437] ===>rt_ioctl_giwscan. 12(12) BSS returned, data->length = 1442
[294149.297036] ===>rt_ioctl_giwscan. 11(11) BSS returned, data->length = 1341
[294209.301336] ===>rt_ioctl_giwscan. 9(9) BSS returned, data->length = 1135
```

---

### Post by vaiocomputer on 2010-05-11
This might be different, if not probably so, but I've noticed that occasionally when I leave an external drive or another partition mounted for an extended period of time, I won't be able to unmount anymore because I don't "have permissions." So I just shutdown the system and unplug the device then.

---

### Post by kakyoism on 2010-05-11
Thanks, but that sounds pretty wrong to me. On Hardy or later there wasn't this problem at all.

---

### Post by iponeverything on 2010-05-11
It may be a known bug, I found this with

[http://www.google.com/search?hl=en&source=hp&q=Unable+to+stop+DBus+error+site%3Alaunchpad.net](http://www.google.com/search?hl=en&source=hp&q=Unable+to+stop+DBus+error+site%3Alaunchpad.net)

If this looks like the same bug that you have encountered, it will help to raise its profile if you add a comment to the bug report.

If it does not look like the same bug, look over a few of the other launchpad matches and open a new report if you find that its a new bug..

---

### Post by kakyoism on 2010-08-24
is there a solution to this problem?

I'm going crazy about this!

I've seen quite a few kernel upgrades but this problem persists. It never happened to me in Hardy!

---

### Post by kakyoism on 2010-09-26
Still the same. 
I can't stand this anymore. The only way to solve this problem so far is to press the power button. I don't think my machine would like that.

---


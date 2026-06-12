---
title: "HP Compaq Mini 110 integrated webcam no longer working"
date: 2010-04-07
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by HolidayQueen on 2010-04-07
I just opened up cheese and was unable to detect webcam.
I went into emesene's webcam options and it could detect no device either. :(


Edit...just plugged in my usb lifecam, that one works.
Why is the integrated one not turning when i openup cheese?

---

### Post by cariboo on 2010-04-08
I have the same netbook, my webcam works as it should. Do you have the proper drivers installed? Open up a terminal and type:

```
lsmod | grep uvcvideo
```

The output should show if the correct module is loaded.

---

### Post by HolidayQueen on 2010-04-08
output:


uvcvideo               56990  0 
videodev               34361  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev

i also checked the BIOS, there is no setting for the webcam.

---


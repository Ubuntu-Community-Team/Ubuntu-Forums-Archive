---
title: "Acer Aspire Cristal Eye webcam not working"
date: 2009-10-05
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Giwex on 2009-10-05
Before to proceed to signal the bug in launchpad I would like to know if anybody here is having the webcam on Acer Aspire laptops (mine is 2920z) recognized by karmic.
In Jaunty it was working out of the box but in karmic (I tried it since Alpha 4) is not working (tried with Cheese, camorama, luvcview, skype).

Thanks

---

### Post by blakamin on 2009-10-06
Sorry about taking so long (Been meaning to reply for a day. work got in the way). Cheese works on my Acer Aspire 4520. No Problems.

---

### Post by Giwex on 2009-10-07
Thanks a lot for your reply. What is the output of lsusb in your case? mine says Ali USB2.0 camera

---

### Post by blakamin on 2009-10-07
Bus 002 Device 002: ID 064e:a101 Suyin Corp. Acer CrystalEye Webcam

---

### Post by Giwex on 2009-10-07
It looks it's a different webcam :(

---

### Post by H4F on 2009-10-07
Acer Aspire 5720 everything works here

---

### Post by Giwex on 2009-10-07
To avoid any doubt mine is 
```
Bus 001 Device 003: ID 0402:5606 ALi Corp. USB 2.0 Camera
```
working perfectly under Jaunty, not even starting under Karmic (tested also -12 kernel) ](*,)

---

### Post by rudy.b on 2009-10-07
Works on my Acer Aspire One ZG5 with Karmic beta.

```
Bus 001 Device 002: ID 064e:d101 Suyin Corp. Acer CrystalEye Webcam
```

---

### Post by taavikko on 2009-10-07
HP laptop with: 5986:0137 Acer, Inc
is working correctly here.

have you tested with "gstreamer-properties" if the video-tab and test works?

---

### Post by Giwex on 2009-10-07
Yes, tried. Not working :(

---

### Post by DavidOC on 2009-10-07
Acer Aspire One A150, the camera works on mine.

---

### Post by mudi on 2009-10-07
Hmm, my 'Chicony Electronics Co., Ltd' 'Webcam' on an Acer Aspire One works.

---

### Post by Giwex on 2009-10-09
Problem solved (partially): the webcam is broken (doesn't work with Vista and just tried also with Jaunty):frown:

---


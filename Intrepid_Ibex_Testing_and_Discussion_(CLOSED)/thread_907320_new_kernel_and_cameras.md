---
title: "new kernel and cameras"
date: 2008-09-01
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by avb on 2008-09-01
After latest kernel upgrade to 2.6.27 both of mine cameras stoped working.
One is:
[ 6440.896646] pac207: Pixart Sensor ID 0x27 Chips ID 0x00
[ 6440.899637] pac207: Pixart PAC207BCA Image Processor and Control Chip detected (vid/pid 0x093A:0x2468)

Second is:
[ 6824.554973] gspca: probing 046d:092e
[ 6824.562841] gspca: probe ok


in both cases /dev/video0 is created but cheese and skype client doesnt show nothing.  Should i fill a bugreport?

---

### Post by junior aspirin on 2008-09-01
maybe this bug? i get a similar problem with usb sticks and my camera
[https://bugs.launchpad.net/ubuntu/+source/hal/+bug/251781](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/251781)

---

### Post by avb on 2008-09-01
mine problem appears only on 2.6.27. :) And this bug was fixed by it. So i think its a different issue.

---

### Post by grumpymole on 2008-09-02
Might be related to [this bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/255678")?

Regards

---


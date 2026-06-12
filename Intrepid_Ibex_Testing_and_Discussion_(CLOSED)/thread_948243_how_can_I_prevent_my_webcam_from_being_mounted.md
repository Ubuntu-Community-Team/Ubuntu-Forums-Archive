---
title: "how can I prevent my webcam from being mounted ?"
date: 2008-10-15
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by luctor on 2008-10-15
I have and old Trust camera that can also be used as a webcam.
When my (gspca) cam is plugged in, it is automaticly mounted and after that no /dev/video0 is created.I don't need to mount it as I don't use it as a regular camera.

I have to manually unmount the camera and unload the modules gspca_spca500 and gspca_main. After manually modprobing gspca_spca500 /dev/video0 is created and I can work with the camera.
I use webcam to upload snapshots to my website and that works fine.
Camorama still needs the v4l fix described somewhere else on the forum.

So  ... how do I stop it from being mounted at bootup and/or plugging it in ?

tia,

Rob

---

### Post by loell on 2008-10-15
probably writing [a udev rule]("http://www.reactivated.net/writing_udev_rules.html")? then maybe just automate what you did, unmount whenever it is plugged.

---

### Post by luctor on 2008-10-15
Did some googling and I think I need to edit /etc/udev/rules.d/45-libgphoto2.rules.

---


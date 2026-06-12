---
title: "HP tx2500z webcam doesn't work with Intrepid RC"
date: 2008-10-26
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by baosheng on 2008-10-26
I have an HP tx2500z laptop. The webcam on my screen worked fine with alpha version of Intrepid. But it doesn't work with beta and RC now. When I turned on "cheese", the LED indicator just blink once and then nothing in the cheese window. Can someone help me?

---

### Post by gali98 on 2008-10-26
It does work, but cheese is still pretty buggy right now. 
Make sure you are updated:
sudo apt-get update &&sudo apt-get upgrade
then make sure you luvcview installed
sudo apt-get install luvcview
Then test it again. I know someone who got it working pretty consistent with ekiga..
Kory

---

### Post by baosheng on 2008-10-26
Not really...

forrest@Xem:~$ luvcview 
luvcview 0.2.4

SDL information:
  Video driver: x11
  A window manager is available
Device information:
  Device path:  /dev/video0
Stream settings:
  Frame format: YUYV (MJPG is not supported by device)
Unable to set format: Input/output error
 Init v4L2 failed !! exit fatal

---


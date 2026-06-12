---
title: "Logitech Quickcam Webcam video too dark"
date: 2008-10-21
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by vishzilla on 2008-10-21
As the title says my webcam seems to work fine but the image is too dark.

these are some of the commands which I put in and I don't find any possible errors

```
 lsmod | grep gspca
gspca_spca561          19328  0 
gspca_main             29312  1 gspca_spca561
videodev               41344  1 gspca_main
usbcore               148848  5 gspca_spca561,gspca_main,ehci_hcd,uhci_hcd
```

```
lsusb
Bus 001 Device 003: ID 046d:092e Logitech, Inc. QuickCam Chat
```

```
dmesg | grep spca
[   18.578611] gspca: main v2.2.0 registered
[   18.582191] gspca: probing 046d:092e
[   18.642229] gspca: probe ok
[   18.642271] usbcore: registered new interface driver spca561
[   18.642305] spca561: registered
```

I have completed all the updates

---

### Post by vishzilla on 2008-10-21
bump. anyone?

---

### Post by flyingbrass on 2008-10-21
Check out [http://www.spinics.net/lists/vfl/msg39018.html](http://www.spinics.net/lists/vfl/msg39018.html)

---

### Post by vishzilla on 2008-10-21
Thanks. I can adjust the exposure levels but the settings doesn't remain after a reboot. Any other workarounds?

---

### Post by vishzilla on 2008-10-21
does anybody have the same problem?

---

### Post by ronacc on 2008-10-22
what app are you using to monitor the cam ? I haven't played with my cam in awhile and I can't remember the app to use , mine is a logitech 046d:0920  it is recognised and the driver loads but I get no pic .

---

### Post by vishzilla on 2008-10-22
I am using Cheese and Skype to monitor it. I do get a pic, but its too dark

---

### Post by Polygon on 2008-10-22
if it helps, my logitech quickcam 3000 doesn't even work anymore in intrepid, it just shows a green screen now.

---

### Post by vishzilla on 2008-10-22
> **Polygon said:**
> if it helps, my logitech quickcam 3000 doesn't even work anymore in intrepid, it just shows a green screen now.

its seems kernel has the latest gspca included. and some of the threads in UF mentioned writing files like gamma, red, blue, green into /sys/module/gspca/parameters but the directory path in intrepid is different and i'm unable to write these files into the /sys/module/gspca_main/parameters directory.

---

### Post by vishzilla on 2008-10-22
Filed a bug report here [https://bugs.launchpad.net/bugs/287336](https://bugs.launchpad.net/bugs/287336)

---


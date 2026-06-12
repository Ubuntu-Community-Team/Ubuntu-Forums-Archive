---
title: "logitech trackman marble usb mouse and jaunty"
date: 2009-03-23
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by techno-mole on 2009-03-23
hello all.

i have a trackball mouse which has 4 buttons, the usual left click and right click, and 2 smaller buttons which on intrepid i had set up as a scroll button (eg - you could hold the button down and move the ball and pages etc would scroll) and a middle click button (left button for scroll right for middle click)  i used this method - [https://help.ubuntu.com/community/Logitech_Marblemouse_USB](https://help.ubuntu.com/community/Logitech_Marblemouse_USB)  to get it working.

it was working fine until i upgraded to jaunty this morning, im assuming it is down to a change or 2 with the way jaunty does things.

is there a way i can get this working again ? or is it a no go with jaunty ?

cheers

---

### Post by marcog42 on 2009-03-24
I had the same problem.  I found that running the following in a command line fixed the issue, but didn't work after a reboot:

```
xinput set-button-map "Logitech USB Trackball" 1 8 3 4 5 6 7 2 9
```

Running it again after a reboot makes it work again, but I'm not sure how to make it stick, and haven't had too much time to work on it.

---

### Post by techno-mole on 2009-03-24
well ive tried the command and it works (i knew some one out there would have the same issue)

it may be a bit of a hack, but just adding that command as a start up program works, eg (in jaunty) --> system --> preferences --> start up applications, once there just paste the command into the command field (add a comment if you feel the need) and it should work, least it does for me.

it may be more appropriate to make a small script to run at start up.

cheers

---

### Post by Taiebot65 on 2009-03-24
I  think you should report a bug against xserver-xorg-input-mouse
if you are quick enough maybe a fix will be released before RC

---

### Post by kmoffat on 2009-04-22
FYI:
In Ubuntu 9.04 I added the following file, /etc/hal/fdi/policy/mouse-wheel.fdi, and my Logitech Marble Mouse, plugged in to USB, has scroll wheel functionality, apparently both verticle and horizontal, at least in Firefox, while holding the small left button and moving the ball:

<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.product" string="Logitech USB Trackball">
      <merge key="input.x11_options.Buttons" type="string">5</merge>
      <merge key="input.x11_options.ButtonMapping" type="string">1 8 3 4 5 6 7 2 9</merge>
      <merge key="input.x11_options.EmulateWheel" type="string">true</merge>
      <merge key="input.x11_options.EmulateWheelButton" type="string">8</merge>
      <merge key="input.x11_options.EmulateWheelTimeout" type="string">300</merge>
      <merge key="input.x11_options.XAxisMapping" type="string">6 7</merge>
      <merge key="input.x11_options.YAxisMapping" type="string">4 5</merge>
      <merge key="input.x11_options.ZAxisMapping" type="string">4 5</merge>
      <merge key="input.x11_options.Emulate3Buttons" type="string">true</merge>
    </match>
  </device>
</deviceinfo>

---


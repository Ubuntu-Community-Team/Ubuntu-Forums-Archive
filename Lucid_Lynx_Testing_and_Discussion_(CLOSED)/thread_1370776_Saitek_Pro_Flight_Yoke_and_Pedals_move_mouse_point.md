---
title: "Saitek Pro Flight Yoke and Pedals move mouse pointer"
date: 2010-01-02
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by sparker256 on 2010-01-02
Found something interesting today. If I move my Saitek Pro Flight yoke or Pro Flight pedals it will move the mouse pointer. The mouse is a USB with a USB to PS2 adapter plugged into a PS2 KVM switch. 

The pedals when moved anywhere will put the mouse pointer into the upper left corner. When the yoke is moved left and right the pointer moved left and right. When it is pushed in and out it moves the pointer up and down.

I sure did not see this in Karmic and not sure where to even look as to why this is happening.

Thanks Bill

---

### Post by phillw on 2010-01-03
> **sparker256 said:**
> 
I sure did not see this in Karmic and not sure where to even look as to why this is happening.

Thanks Bill

Hi, can you confirm it is a new, improved (?), feature of 10.04, or one in 9.10 that you hadn't noticed ?

Regards,

Phill.

---

### Post by sparker256 on 2010-01-03
> **phillw said:**
> Hi, can you confirm it is a new, improved (?), feature of 10.04, or one in 9.10 that you hadn't noticed ?

Regards,

Phill.

Hi Phill,

I have just been back in my 9.10 install and this behavior is not there. I did every thing I could think of including running X-Plane and the mouse pointer only moved when I moved the mouse and not when my Saitek Pro Flight Yoke or Pedals were moved. 

Now on Lucid (10.04) that is another story. Whenever I move the yoke or pedals they move the pointer. Another thing is if the pedals are not plugged in and I plug them in sometimes it puts the pointer in the upper left corner and is locked in that position. If that happens A reboot is in order. 

Thanks for your reply and what would I file a bug against?

Bill

---

### Post by phillw on 2010-01-03
> **sparker256 said:**
> Hi Phill,

I have just been back in my 9.10 install and this behavior is not there. I did every thing I could think of including running X-Plane and the mouse pointer only moved when I moved the mouse and not when my Saitek Pro Flight Yoke or Pedals were moved. 

Now on Lucid (10.04) that is another story. Whenever I move the yoke or pedals they move the pointer. Another thing is if the pedals are not plugged in and I plug them in sometimes it puts the pointer in the upper left corner and is locked in that position. If that happens A reboot is in order. 

Thanks for your reply and what would I file a bug against?

Bill

Good question - I was dreading you saying that !!!

I've had a look at the various main options and cannot find one to suit your particular issue (That's not to say there isn't one) --> I can only suggest the 'catch all' of a text only bug reported by --> [https://bugs.launchpad.net/ubuntu/+filebug?no-redirect=](https://bugs.launchpad.net/ubuntu/+filebug?no-redirect=)

Give them as much info as you can, the fact it doesn't appear in 9.10, you can repeat it after a reboot, etc - there's not a lot to go on, so it may be difficult for them to nab it. You may find that they come back to you to ask for more information. Also include your kernel version, hardware (processor, ram etc) how upto date your 10.04 is etc.

Regards,

Phill.

---

### Post by sparker256 on 2010-01-03
> **phillw said:**
> Good question - I was dreading you saying that !!!

I've had a look at the various main options and cannot find one to suit your particular issue (That's not to say there isn't one) --> I can only suggest the 'catch all' of a text only bug reported by --> [https://bugs.launchpad.net/ubuntu/+filebug?no-redirect=](https://bugs.launchpad.net/ubuntu/+filebug?no-redirect=)

Give them as much info as you can, the fact it doesn't appear in 9.10, you can repeat it after a reboot, etc - there's not a lot to go on, so it may be difficult for them to nab it. You may find that they come back to you to ask for more information. Also include your kernel version, hardware (processor, ram etc) how upto date your 10.04 is etc.

Regards,

Phill.

Will file a bug report and give as much info as I can. I plugged in my old Microsoft Sidewinder Precision Pro joystick and get the same behavior. It is a gameport type with a gameport to USB adapter. When I move the joystick I move the pointer.

If anyone else has a joystick, yoke, pedals, steering wheel, please let me know if you are seeing the same behavior. 

Have filed this bug report.

[https://bugs.launchpad.net/ubuntu/+bug/502631](https://bugs.launchpad.net/ubuntu/+bug/502631)

Thanks Bill

---

### Post by zikade on 2010-01-03
Yep, it seems to be a consistent new feature. However, consider yourself lucky - you can unplug your joystick. My laptop has those nifty accelerometers and they seem to be recognized as a joystick as well. And, boy, if my dvd-drive starts spinning my cursor gets quite busy...

---

### Post by sparker256 on 2010-01-03
> **zikade said:**
> Yep, it seems to be a consistent new feature. However, consider yourself lucky - you can unplug your joystick. My laptop has those nifty accelerometers and they seem to be recognized as a joystick as well. And, boy, if my dvd-drive starts spinning my cursor gets quite busy...

When I plugged in my old joystick I thought how many other devices could be affected. Accelerometers were certainly not what I was thinking. Please add your name to the bug as affected and add any other comments as needed.

[https://bugs.launchpad.net/ubuntu/+bug/502631](https://bugs.launchpad.net/ubuntu/+bug/502631)

Bill

---

### Post by ronacc on 2010-01-03
I get this too , added comment and me-too to your bug , I wonder if this has anything to do with moving away from hal ?

---

### Post by sparker256 on 2010-01-03
> **ronacc said:**
> I get this too , added comment and me-too to your bug , I wonder if this has anything to do with moving away from hal ?

Not sure, I have another strange difference in how the USB ports act differently with a port reset. I have written a program to reset the usb ports like you had unplugged and replugged then. It works like I wanted in Karmic but not in Lucid. I am waiting for this bug to get fixed to see if the problem is still there. My home cockpit runs on USB so have learned more than I wanted about USB under Linux and think something is different. 

Bill

---

### Post by ronacc on 2010-01-03
the only thing I have noticed is that when you rt click on the icon of a mounted usb stick there is an extra option , I think it just used to be unmount and eject , now it is unmount eject and safely-remove ( atleast I don't remember safely remove being there before).

---


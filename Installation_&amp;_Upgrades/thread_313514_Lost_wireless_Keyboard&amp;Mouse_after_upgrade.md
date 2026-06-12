---
title: "Lost wireless Keyboard&amp;Mouse after upgrade"
date: 2006-12-06
forum: Installation &amp; Upgrades
---

### Post by pcolamar on 2006-12-06
I just upgraded Dapper to Edgy on my HP desktop (t.5050 - AMD64)  following the official method but now the HP wireless Keyboard & mouse  are not recognized

Edgy starts but I cannot type or click anything.

All comes back when I boot with the old kernel 2.15.xxx

Any suggestion ?

Thanks
Palmer

---

### Post by aliyanage on 2006-12-06
what kinda wireless keyboard and mouse do you have? could you tell me the brand model etc... ?

aliyanage

---

### Post by pcolamar on 2006-12-07
It's the original HP Kb&mouse wireless that comes bundled with the desktop. It comes with the classic Radio(Infrar ??) receiver that get's attached toi the USB port.

Palmer

---

### Post by aliyanage on 2006-12-07
okay well, I have some from logitech and what happened with me was that I just had to push the connect button on the mouse as well as on the keyboard.

If you have the possibility and have a receiver try to push connect button on receiver then on mouse and keyboard. That helped me out...

---

### Post by pcolamar on 2006-12-08
Aliyanage,
  I 'll give a try this evening although the blue LED on the receiver box is not lit up as in WinXP.

I have the impression that the USB radio device is not recognized.

Thanks so far,
Palmer

---

### Post by demboos on 2006-12-08
I had the same problem with Logitech wireless KB and mouse. 

In my case it helped when I plugged the receiver into another USB port.

---

### Post by pcolamar on 2006-12-10
Ok, I tried both demboos and aliyanage suggestion.
Pushing the " sync" button on receiver and keyboard did not help because the receiver is not powered and actually there is an error on the tty that says error -110 th3 USB device 3-2 does not accept to be allocated .....".
Then I plugged the receiver to another usb port unplugging all the other usb devices (printer & camera). In this case the keyboard works no metter which usb port is connected to. 
Everything stops again after restarting if the USBcam and the USB printer are reconnected.
Apparently only 2 usb devices can be attached to the PC at the same time.

Any hint ? Is there any limitation in the kernel to the number of USB devices that can be attached ??

I might try to upgrade the kernel to 2.18.xx or above.

---


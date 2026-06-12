---
title: "USB Problems"
date: 2007-05-19
forum: Installation &amp; Upgrades
---

### Post by steve11 on 2007-05-19
Just installed 7 but now no usb's are working:confused:

---

### Post by slipperhead on 2007-05-19
can you press escape while grub is loading and edit the kernal line(press e to edit) to add irqpoll.(press enter and then b to boot) this fixed the no usb problem for me

the kernal line is the one that has quiet splash etc. on it, just incase like me you didnt know.

---

### Post by steve11 on 2007-05-21
Thanks
So after Splash enter space then irqpoll then enter then b to boot?

I have tried this and no joy when I go back to check the edited line in the kernal the  irqpoll is not visable
 any other ideas?

---

### Post by slipperhead on 2007-05-21
what i did is : press esc while grub is loading, you should have a list of ubuntu kernals so 
                      press e to edit the one at he top
go to the line that starts kernal /boot... quiet splash
press e again
 add a space then irqpoll
press enter
then b to boot

sorry for repeating myself, i was doing it as i typed it

if it works you will need to edit your menu list - but we can sort that out later!

---

### Post by slipperhead on 2007-05-21
i dont know if the irqpoll will be visible, you could test a usb device and see if it works

---


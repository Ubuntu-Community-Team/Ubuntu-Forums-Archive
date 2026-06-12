---
title: "VirtualBox USB"
date: 2010-08-23
forum: Installation &amp; Upgrades
---

### Post by eyeamok on 2010-08-23
I only have one problem left, I have 10.04 installed, I have Virtual Box installed with an XP Machine to use UPS Worldship. I set up the USB Filters just like I did on my laptop, but it says Unavailable and wont recognize anything I plug into usb port. When running and I right click on the usb icon at bottom they show up but shaded and will not let me select any uSB device. In Device Manager USB appears to be installed but NO DEVICES SHOW UP. Any ideas as to why??? 

I also have a thermal printer hooked to com1 serial, any ideas as to how I make my Virtual Machine recognize it???

---

### Post by marl30 on 2010-08-23
The need to enable Virtualbox's access in Users and Groups.

Go to System/Administration - then scroll down to Users and Groups. Open Users and Groups, then click on Manage Groups. When the group settings menu pops up, scroll down to vboxusers. Highlight it, then click properties. Then check the box beside your user name below the part which says group members. Press ok. log off, then login. Load Virtualbox, and USB should be enabled.

---

### Post by gdonwallace on 2010-08-23
Also, You should check to make sure that Guest Editions is installed inside XP. That will open up some functionality that the base install does not have.

---

### Post by sofoxy on 2010-11-21
> **marl30 said:**
> The need to enable Virtualbox's access in Users and Groups.

Go to System/Administration - then scroll down to Users and Groups. Open Users and Groups, then click on Manage Groups. When the group settings menu pops up, scroll down to vboxusers. Highlight it, then click properties. Then check the box beside your user name below the part which says group members. Press ok. log off, then login. Load Virtualbox, and USB should be enabled.


The USB device found is grayed out.  Is there a way to enable the USB? BTW I'm using Ubuntu 10.10.

---

### Post by na5h on 2010-11-22
Also remember to check whether you are using the OSE or PUEL version of Virtualbox. The OSE-version does not have USB-support. Both versions are free of charge for personal use. You can download the PUEL-version from virtualbox.org

---

### Post by mdgeus on 2010-11-22
I had the same problem with virtualbox in 10.10 but I just installed vmware player. (it's free)

There is one remark, you can only run one vm at once in vmwareplayer.

---


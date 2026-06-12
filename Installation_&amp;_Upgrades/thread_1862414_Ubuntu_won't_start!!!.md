---
title: "Ubuntu won't start!!!"
date: 2011-10-16
forum: Installation &amp; Upgrades
---

### Post by demoniax on 2011-10-16
I ubuntu users, i recently had a big problem with my ubuntu , thé first Time i installed ubuntu everything was ok after i did Some updates and finally I restarted... Ubuntu dont Want to start a black screen appear with a flashing underscore, after30sec ubuntu loading page apper and thanatos it crash and There is Some black and purple lines and then it reboot .... What. Is thé matter UBUNTU

---

### Post by MAFoElffen on 2011-10-16
> **demoniax said:**
> I ubuntu users, i recently had a big problem with my ubuntu , thé first Time i installed ubuntu everything was ok after i did Some updates and finally I restarted... Ubuntu dont Want to start a black screen appear with a flashing underscore, after30sec ubuntu loading page apper and thanatos it crash and There is Some black and purple lines and then it reboot .... What. Is thé matter UBUNTU
Welcome to Ubuntu!

Sounds like you had a bad install.  Since it is a new install, it would probably be easier and less time for you to a fresh (new) reinstall.

Notes:  
- When it gets to the install options, select install over Ubuntu 11.10, use whole disk.
- When it gets to the install options, check the 2 radio buttons to install updates while installing and to download/install 3rd party software.

---

### Post by demoniax on 2011-10-16
Thanks a lot for your help i Will give you Some Come back, sorry for text error m'y iPhone correct so bad
Ok everything works. :D
But How do i install my drivers (Motherboard : GA-770t-usb3 , Graphic card : Radeon 6870)

---

### Post by MAFoElffen on 2011-10-17
> **demoniax said:**
> Thanks a lot for your help i Will give you Some Come back, sorry for text error m'y iPhone correct so bad
Ok everything works. :D
[COLOR=Red]But How do i install my drivers (Motherboard : GA-770t-usb3 , Graphic card : Radeon 6870)[/COLOR]
[COLOR=Black]On the first boot after your install, hold down the shift key.  When the grub  menu  comes up, press "e'.  That will put you into an edit mode.  Arrow  down  to the line that begins with "linux".  Arrow right to where is  says  "quiet splash" and before it says "vt.handoff=7"...  Insert "radeon.mode=0" Press <cntrl><x> and it will boot.

When it boots, login, continue into the GUI. At the desktop, click on the user_name in the upper-right-most  of the top bar > select System Settings > Select Additional  Drivers. > Install appropriate driver.

If that has no drivers to suggest, I have manual ways...
If it doesn't show any- try the instructions in this post...
[http://ubuntuforums.org/showpost.php?p=11358785&postcount=2](http://ubuntuforums.org/showpost.php?p=11358785&postcount=2)
[/COLOR]

---


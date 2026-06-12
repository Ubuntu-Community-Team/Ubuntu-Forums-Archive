---
title: "please read if you need to configure a 3g modem on 10.04"
date: 2010-08-13
forum: Installation &amp; Upgrades
---

### Post by RJB10 on 2010-08-13
Hi everybody!
If like me you are trying to get your huawei modem to be reconised as a modem instead of a storage device then follow these instructions for the work around.
I have been reading people have trouble getting it to work on ubuntu 9.10 but my modem worked once i correctly configured network manager and solved the permissions issue then on firefox under preferences chose to use auto detect proxy for this network.
So beashured it only needs to be configured correctly and it will work.
As for ubuntu 10.04 that is a totally different issue no matter what you try it would not work so ill tell you here the simpilest work around as for 3 days i followed many different peoples advice and got no where until i did this.
Which will take no longer than 5 minutes and is by far the easiest way to get it working.
1st using a working pc download to a floppy disk usb-modeswitch_1.1.3-1_i386.deb.
2nd again using a sepperate floppy download usb-modeswitch-data_20100127-1_all.deb.
These 2 will work together as others i tried said either missing dependences or the data one would break usb-modeswitch.
These worked for me using a amd k6-2 and this usb-modeswitch-data is for both 32-bit and 64-bit versions.
Download both to your home folder then using the right click menu install them.
Both should be accepted and then open a terminal window and individually type ls to list all your files and to make sure they are both their.
Then type sudo apt-get install usb-modeswitch_1.1.3-1_i386.deb and after the same for the other file.
Then with the modem plugged in while this has been going on type lsusb and hopefully you should see a change from the line if you typed lsusb before installing these files and if it is different you now know it is being detected as a modem
Do not worry if it says your dongle is a different model as mine says 12d1:1001 E620 usb modem even though it is a 1550 model.
If you have any problems with missing dependences when trying install any of the files you will just have to find the 2 what work for you as usb-modeswitch-data_20100701_1_all.deb said it would break the 1.1.3-1_i386.deb version so just find the 2 what work together and you will then be able to configure network manager to auto connect so everytime you plug in your dongle it will work.
This way has definetly by far been the easiest way i have found and the quickest.
Ok i hope this helps you and if you get stuck then let me know and ill let you know what to do. cheers!

---


---
title: "DCP-7040 scanner problem"
date: 2010-10-31
forum: Installation &amp; Upgrades
---

### Post by bedihardeep on 2010-10-31
i installed the drivers for brother dcp-7040 printer drivers but scanner is not working 

am using ubuntu 10.10 


i followed this thread 

<a href="http://ubuntuforums.org/showthread.php?t=1124867" target="_blank">
for scanner part 
i was unable to change the values in config file as file i opened  was blank 

Change some values in a config file
     Quote:
                                                  sudo gedit /etc/udev/rules.d/40-basic-permissions.rules                                 
    Edit "0664" to "0666" in "USB devices" section.

    Before the edit---------------------------------

    # USB devices (usbfs replacement)
    SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE="0664"
    SUBSYSTEM=="usb_device",                MODE="0664"

    After the edit----------------------------------

    # USB devices (usbfs replacement)
    SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE="0666"
    SUBSYSTEM=="usb_device",                MODE="0666"

---

### Post by plucky on 2010-11-01
For 10.10 a couple of things have changed.

Open a terminal and ```
sudo apt-get install sane-utils
```

Then from the [Brother Website](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1a.html)
```
Ubuntu 9.10, 10.04
    1. Open "/lib/udev/rules.d/40-libsane.rules" file.
    2.Add the following two lines to the end of the device list. (Before the line "# The following rule will disable ..."):


    The lines to be added--------------------------- 


    # Brother scanners
    ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"
     

    3. Restart the OS. 
```

This also works in 10.10 Maverick.

Reboot and you should now be able to scan.

To check the drivers are installed try ```
dpkg -l | grep Brother
```

Good Luck

---

### Post by bedihardeep on 2010-11-03
> **plucky said:**
> For 10.10 a couple of things have changed.

Open a terminal and ```
sudo apt-get install sane-utils
```Then from the [Brother Website]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1a.html")
```
Ubuntu 9.10, 10.04
    1. Open "/lib/udev/rules.d/40-libsane.rules" file.
    2.Add the following two lines to the end of the device list. (Before the line "# The following rule will disable ..."):


    The lines to be added--------------------------- 


    # Brother scanners
    ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"
     

    3. Restart the OS. 
```This also works in 10.10 Maverick.

Reboot and you should now be able to scan.

To check the drivers are installed try ```
dpkg -l | grep Brother
```Good Luck

i went to computer then file sys  then then lib then udev then rules.d then i opened the file u told me  and 
copied the  2 line u told me but when i try to paste the line into that file with right click paste command was not highlighted 

even i tried ctr+c  

how can paste those 2 line s 

thanks for your help

---

### Post by plucky on 2010-11-03
> i went to computer then file sys then then lib then udev then rules.d then i opened the file u told me and
copied the 2 line u told me but when i try to paste the line into that file with right click paste command was not highlighted


It is a system file so you need to use admin privilege ```
gksudo gedit /lib/udev/rules.d/40-libsane.rules
``` and then paste the two lines  (Before the line "# The following rule will disable ...")

Then reboot.

Good Luck

---

### Post by bedihardeep on 2010-11-07
> **plucky said:**
> It is a system file so you need to use admin privilege ```
gksudo gedit /lib/udev/rules.d/40-libsane.rules
``` and then paste the two lines  (Before the line "# The following rule will disable ...")

Then reboot.

Good Luck

Thanks  a lot 
You are great it works fine

---


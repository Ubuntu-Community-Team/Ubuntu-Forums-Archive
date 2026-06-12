---
title: "Blank screen on boot after install of 9.10 (wubi)"
date: 2010-02-05
forum: Installation &amp; Upgrades
---

### Post by Telescope_Nerd on 2010-02-05
This is a guide for how to solve the issue of a blank screen on boot, specifically the one which occurs with a fresh install of 9.10 on machines with and ati/amd graphics card.

Basically the solution is to access the command line and use that to install the ati graphics driver, here's how.

Step1. Using a working machine/partition go the the amd website and download the appropriate driver for your graphics card.

[http://support.amd.com/us/gpudownload/Pages/index.aspx]("http://support.amd.com/us/gpudownload/Pages/index.aspx")

Save the driver to an external hard drive or memory stick.

Step2. Make sure your machine has an Internet connection plugged in. Install 9.10 using wubi or the live cd. After the initial installation boot ubuntu for the first time. The important thing in this step is DO NOTHING. After booting ubuntu will finalise the install. Let the screen go blank and wait. After some time the machine will automatically reboot.

Step3. After the second boot the screen will go blank again, wait a minute or two and the press ctrl-alt-f1. This should call up the command line. Enter your user name and password as prompted to log in.

Step4. Enter in the command line
```
sudo nano /etc/apt/sources.list
```

This brings up a file showing the repositories where ubuntu looks for packages. The lines listing repositories begin deb..... a few of these lines are commented i.e. they start # deb... find these lines and delete the '#' symbols. 

When you've finished type ctrl-x to exit. Choose 'Y' when asked if you want to save the file then press return.

Step5. Enter in the command line 
```
sudo apt-get update
```
this makes ubuntu search the repositories for updated packages.

Step6. Enter the command
```
sudo apt-get upgrade
```
this installs the missing packages.

Step7. Reboot
```
sudo reboot
```

Step8. After reboot log in again by using ctrl-alt-f1 to get to the command line, then enter
```
sudo apt-get install libqtgui4
```

Step9. make a directory to mount the external drive containing the graphics driver.
```
sudo mkdir /media/Exdrive
```

Step10. Plug in the external drive containing the driver. The drive will be assigned a name in the directory called /dev/ (usually this is 'sdb1' but it may be something else e.g. 'sdc1') you will have to check. Assuming that it is sdb1 do.
```
sudo mount /dev/sdb1 /media/Exdrive
```

Step11. Make a folder in your home directory to hold the graphics driver
```
sudo mkdir ~/Graphics
```

Step12. Now copy the ati driver from the external drive
```
sudo cp /media/Exdrive/ati-driver-filename ~/Graphics
```

Step13. unmount the external drive
```
sudo umount /dev/sdb1
```
and unplug

Step14. navigate to the driver
```
cd ~/Graphics
```

Step15. Make the driver executable
```
sudo chmod +x ati-driver-filename
```

Step16 run the driver install
```
sudo ./ati-driver-filename
```
Then follow the instructions on screen selecting all the default options.

Step17 When the driver has finished installing enter
```
sudo aticonfig
```

Step18. Then finally....
```
sudo reboot
```

If all that worked after the reeboot the blank screen should be gone and you can see the lovely hi-res ubuntu gui!

Note:- some clever people can download files from the Internet using the command line which may mean you can do this without using an external hard drive. If one of them is out there please reply to this post adding that info!

---

### Post by Telescope_Nerd on 2010-02-06
Update: 

If you are using this guide to fix an updgrade or if you need to do a re-install of the graphics driver don't forget to delete the xconf.org file before installing the ati driver. i.e. between steps 13 and 14 do
```
sudo rm /etc/X11/xorg.conf
```

---

### Post by Taylor Franklyn on 2010-02-19
hey, I couldn't get past step 3... for som reason its not taking me to a command line, the screen just remains blank.... 

p.s im doing this for intel hd laptop graphics

---

### Post by Telescope_Nerd on 2010-02-21
Hi it's possible that the key combination is different on you laptop e.g. ctrl-alt-f2 ? but there is another way around this. During the second boot you should see the grub menu allowing you to choose kernel options. If you select the second option labelled (recovery mode) then this will automatically take you to the command line interface.

Let me know if this solves your problem.

---

### Post by Taylor Franklyn on 2010-02-24
safe graphics mode isnt working either...aghhh

---

### Post by Telescope_Nerd on 2010-02-25
Sounds like your problem is more serious than the one catered for by this guide. Sorry I couldn't be of more help. Have you tried installing the last long term support release (8.04)? You might find this more stable. While playing around I found that graphics worked in this version without having to resort to the fix described above.

---

### Post by texaswriter on 2010-02-25
Excellent guide guys!!! :popcorn::guitar:

---

### Post by t3h_pwnage on 2011-05-17
> **Telescope_Nerd said:**
> Sounds like your problem is more serious than the one catered for by this guide. Sorry I couldn't be of more help. Have you tried installing the last long term support release (8.04)? You might find this more stable. While playing around I found that graphics worked in this version without having to resort to the fix described above.

Do you think you could write a guide on how to install a linux ati driver from a Live CD? I think I have the same problem as the guy above. The screen is not completely black, it's just the backlight that is off. When I turn up the brightness I see a bunch of errors about the radeon graphics. I would gladly follow the steps in your guide (I even downloaded the driver) but since there is no way to access the command prompt I am stuck :(

---


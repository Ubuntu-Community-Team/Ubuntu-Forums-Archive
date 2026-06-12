---
title: "xserver not starting"
date: 2006-05-27
forum: Installation &amp; Upgrades
---

### Post by knewmocker on 2006-05-27
I just got done installing and xserver wont start up. I know its a common problem but im new to linux and not to good with comand line and it says to look at the /var/log/xorg.0.log to check for errors and set up and Im not to sure how to go about doing that

---

### Post by Sutekh on 2006-05-27
What sort of graphics card do you have?  NVIDIA or ATI?

Unfortunately NVIDIA and ATI are not very forthcoming on how their cards work.  The only way to get these cards working is to either use the manufacturers proprietry drivers or the community made free drivers.  Ubuntu has a commitment to free (as in freedom) software, so they only provide free software solutions.  Sadly they are often not completely up to the task, hence X server errors.


Anyhoo, this error should leave you at a command line where you can log in with your username and password.
  
Once logged in, you can use this command to change the video drivers temporarily to the **vesa** drivers, which seem to be a general fix-all driver.
```
sudo dpkg-reconfigure xserver-xorg
``` - when prompted for a password, use your users password. 

- this command will reconfigure the X server (the GUI), you will be asked a long string of questions regarding the input devices of your PC; your keyboard, mouse and monitor. If you don't know what you should answer to these questions go with the default/suggested ones.
 
  - the important step is when you are asked to choose the video card driver for the X server choose **vesa**
 
  - once you are done use this command
 ```
sudo /etc/init.d/gdm restart
```  - this will restart the GNOME Display Manager, and start the GUI.


 - If you use NVIDIA and all this works out then you can consider installing the proprietry NVIDIA drivers for your card. You can read all about it here

[Ubuntu Forums - HOWTO Latest NVIDIA Drivers]("http://www.ubuntuforums.org/showthread.php?t=75074")

 - Method 1 is by far the easiest method, and will install the Ubuntu repository NVIDIA drivers (v7667)

 - Method 2 is a little harder and can be used to install any version of the proprietry NVIDIA drivers.


 - If you use ATI and have got the graphical interface working with the **vesa** drivers, you could look into installing the Official ATI drivers, through one of these means.  
 
 You can try either this HOWTO
  
  [Ubuntu Document Storage Facility - Install ATI Driver]("http://doc.gwos.org/index.php/Install_ATI_driver")
  
 or look into installing EasyUbuntu (for GUI install of ATI drivers and loads of other stuff)
  
  [Ubuntu Forums - Easy Ubuntu v2.2]("http://ubuntuforums.org/showthread.php?t=64629")
 [URL="http://www.ubuntuforums.org/showthread.php?t=75074"]
[/URL]

---


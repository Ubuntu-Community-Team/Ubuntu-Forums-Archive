---
title: "X-server problems"
date: 2006-05-26
forum: Installation &amp; Upgrades
---

### Post by wp2 on 2006-05-26
Hi there... 

I´m new to the linux world and thereby not that good at it. I thaugt that ubuntu looked like a nice dist so i downloaded it and installed it.

My problem is before i can set a root password the install "aborts" because it cannot start the x-server. I read some guides howto install a  driver for my graphic card, but all have failed.

In most of the guieds i need to use sudo, and then it asks me for a password (root password?), but as i have not been able to set a password there i dont know what it is.

Just before the x-server error appears i have created me a account for my user, and it on that account im trying to install.


So what im asking is there a way to define a root password without the x-server, dosent seam to have installed any packages yet...

My hardware:
CPU....: AMD 64 3500+
GFX....: Asus ATI x850 xt pl (PIC-E)
MEM...: 1024Mb 

The Dist i try to install:
Ubuntu 5.10

---

### Post by pksings on 2006-05-26
First, the password it is asking for is not root, it is your user password, it is doing what is known as a "sudo" meaning run me as root. So it asks for a confirmation of your user password.

If you really want to set a password for root it can be done. At the prompt type "sudo(enter)", put in your password, the prompt should change from a "$" to a "#", that means you are root.  Then type "passwd(enter)", put in the desired root password twice and you are done. Note the shortened spelling, the designers of Unix were lazy and didn't like typing so most commands are shortened from their DOS equivalents.

That should allow you to set your display driver properly.

Hope this helps.

PK

---

### Post by Sutekh on 2006-05-26
Unfortunately ATI cards, often are the cause of video problems.   The installation should have completed successfully though.  What was the last step of the process that you completed?  Did you partition your discs, install GRUB, remove the CD and reboot?


If the install completed, then this error should leave you at a command line where you can log in with your username and password.
  

Once logged in, you can use this command to change the video drivers temporarily to the **vesa** drivers, which seem to be a general fix-all driver.
 ```
sudo dpkg-reconfigure xserver-xorg
``` - when prompted for a password, use your users password.  Don't worry about setting a root password, it isn't neccessary - [Ubuntu Wiki - Root and Sudo](wiki.ubuntu.com/RootSudo)
 
- this command will reconfigure the X server (the GUI), you will be asked a long string of questions regarding the input devices of your PC; your keyboard, mouse and monitor. If you don't know what you should answer to these questions go with the default/suggested ones.
 
  - the important step is when you are asked to choose the video card driver for the X server choose **vesa**
 
  - once you are done use this command
 ```
sudo /etc/init.d/gdm restart
```  - this will restart the GNOME Display Manager, and start the GUI.



  If you get the graphical interface working with the **vesa** drivers, you could look into installing the Official ATI drivers, through one of these means.  
 
 You can try either this HOWTO
  
  [Ubuntu Document Storage Facility - Install ATI Driver]("http://doc.gwos.org/index.php/Install_ATI_driver")
  
 or look into installing EasyUbuntu (for GUI install of ATI drivers and loads of other stuff)
  
  [Ubuntu Forums - Easy Ubuntu v2.2]("http://ubuntuforums.org/showthread.php?t=64629")
 [URL="http://www.ubuntuforums.org/showthread.php?t=75074"]
[/URL][ ]("http://www.ubuntuforums.org/showthread.php?t=75074")

---


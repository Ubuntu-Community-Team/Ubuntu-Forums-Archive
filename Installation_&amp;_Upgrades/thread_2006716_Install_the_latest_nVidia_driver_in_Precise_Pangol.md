---
title: "Install the latest nVidia driver in Precise Pangolin 12.04"
date: 2012-06-19
forum: Installation &amp; Upgrades
---

### Post by Cavsfan on 2012-06-19
I just installed the latest nVidia driver 295.59 which came out on 2012.6.11.

1) [[COLOR=blue]_Download the latest nVidia driver here._[/COLOR]]("http://www.nvidia.com/Download/index.aspx?lang=en-us")

2) Open Module blacklist by entering this in terminal **gksudo gedit /etc/modprobe.d/blacklist.conf**
Add these to the file and save it:
```
blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv
```3) Uninstall any previously installed Nvidia drivers: **sudo apt-get --purge remove nvidia-***

4) Reboot your computer and login via recovery mode.
I had to enter "login" and then my userid and password.

5) Navigate to where you downloaded the driver.

6) Enter **sudo chmod +x NVIDIA-Linux-x86_64-295.59.run** (or whatever your file name is, mine is 64 bit) to make it executable.

7) Enter **sudo sh NVIDIA-Linux-x86_64-295.59.run**
This should start the nVidia installer program.
It will give you a warning that you are running at runlevel 1 and to quit the installation and enter **telinit 3** but, ignore that and continue.
It will ask if you want to update the xserver config and answer Y to everything.
When it completes you can enter **telinit 3** and you will be looking at your normal login screen.
Entering **telinit 3** is probably not the perfect thing to do but, it worked for me.

Then once you have the driver installed, you **must** go through this How to from this forum so that subsequent kernels that get installed have this driver installed into them.
It is very simple and it provides a way for making a couple of minor changes for the next time you install a new driver.

[[COLOR=blue]_HOWTO: Automatically update manually installed NVidia drivers after kernel updates_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=835573")

I just copy the first 2 command to a text file (gedit) and modify them as needed.
Then copy and paste them one at a time into terminal.

Then after accomplishing the first 2 lines, I clear the gedit and copy the entire script and save it as update-nvidia in my home.

---

### Post by OrangeVixen on 2013-04-25
Just wanted to add that as of 2013 April 22, I was able to just go to settings and under Hardware -> Additional Drivers install the latest proprietery drivers and it worked.

I clicked on NVIDIA accelerated graphics driver (version current) [Recommended] and clicked on Activate. It asked me to install and then after a download it asked me to reboot.

Rebooted without any problems. So I believe NVidia has fixed most of the problems past encountered on Precise 12.04.


Just incase you come across any problems, such as a black screen, I found these commands to help.

Reboot in recover mode (hold SHIFT during Ubuntu boot) or if you can drop to a non-graphical terminal (CTRL + ALT + F1).

Log in and run:
```

sudo apt-get purge nvidia*
sudo dpkg-reconfigure -phigh xserver-xorg

```

This will remove all nvidia packages and try to go back to using the default X driver.

---


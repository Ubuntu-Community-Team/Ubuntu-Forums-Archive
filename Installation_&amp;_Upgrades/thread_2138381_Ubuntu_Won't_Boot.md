---
title: "Ubuntu Won't Boot"
date: 2013-04-23
forum: Installation &amp; Upgrades
---

### Post by thenewasbo on 2013-04-23
I just installed Ubuntu, and installed the recommended Nvidia drivers that popped up. Then, when I rebooted, I choose Ubuntu in Grub, then it shows me a black screen with a flashing small horizontal line, it stays that way for a few seconds, then it flashes some quick text I can't read. Then it goes back to just flashing that little line indefinitely. Any idea what I can do about this?


It's Ubuntu 12.04 64-bit.

SOLVED: I just deleted the partitions and reinstalled Ubuntu.

---

### Post by Randymanme on 2013-04-24
Hello thenewasbo,

I'm presently running 13.04, but I've used 12.04 recently enough to recall that happening to me.

Reboot and when you come to the grub menu, select "Advanced Options for Ubuntu."
Then select Recovery Mode.
After that, select "fsck Check all file systems - " (this will remount your file systems in read-write mode).
Next, select "root Drop to root shell prompt.)
At the root shell prompt, type apt-get purge nvidia.
At the next root shell prompt, type reboot.

You should be good.

---

### Post by thenewasbo on 2013-04-24
"ata_id[159]: HDIO_get_IDentity_ failed for 'dev/sdb' : invalid argument" is the error I get now. it says acpid: exiting and some text follows when I hit the power button to stop the flashing white line. Is there any way to reinstall it? Can I just delete the two partitions that Ubuntu is on?

---

### Post by Randymanme on 2013-04-25
I jsut happened to run across this, in [http://askubuntu.com/questions/202677/nvidia-driver-doesnt-work-in-12-10](http://askubuntu.com/questions/202677/nvidia-driver-doesnt-work-in-12-10).  I realize that you're using 12.04, but it may still help to restore the original desktop you had before installing the proprietary driver.

[I]For all of you in this situation (like I was) there is a easy solution:
1- After logged in the session (only wallpaper seems to appear and bad  resolution), right click and click on change wallpaper. Then click up in  the left in Show all configurations (my system is in Spanish so maybe  the label names are subtly different), then Software sources and finally  you just need to change back to X.Org Nouveau.
2- After applying the changes press Ctrl+Alt+T to open a terminal and  type "sudo reboot". After this the system should be working properly  again.
3- Now lets try lo install the NVIDIA drivers again. Open a new terminal  and type "sudo apt-get install linux-headers-generic" to install the  meta package, not a specific version which is a better approach.
[/I]*4- Go to system configuration panel and in the software sources select  the NVIDIA driver you prefer (I normally prefer to use the privative  tested one but it is only my preference).*

In the [I]same thread (response #29), regarding the installation of NVIDIA drivers:
 
Before switching to the nvidia drivers you need to install linux-source and linux-headers (see [bug 1068341]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-updates/+bug/1068341")).  After the source is installed, try switching to the nvidia drivers.
  Here is how:
  Before you start, install all updates (and reboot the computer, if you are told to).
  [/I]
[LIST=1]
[*]*Switch to a terminal (Ctrl-Alt-F1).* 
[*]*Login as your username.* 
[*]*Install linux source (sudo apt-get install linux-source) and headers (sudo apt-get install linux-headers-generic).* 
[*]*Uninstall nvidia driver - this depends on which version you installed (sudo apt-get remove nvidia-current or sudo apt-get remove nvidia-current-updates or sudo apt-get remove nvidia-experimental-304).* 
[*]*Reinstall nvidia driver (sudo apt-get install nvidia-current-updates).* 
[*]*If it successfully installs, restart the computer (sudo shutdown -r now).* 
[/LIST]
[I]  **More In-depth How-to**

  The following link gives a more in-depth overview on how to handle  the nvidia driver. It should be applicable to more cases, that are  similar, but not exactly the same as the one described here:  [/I][URL="https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia"][I][https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
[/I]
[/URL]

---


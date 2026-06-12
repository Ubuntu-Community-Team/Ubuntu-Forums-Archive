---
title: "After Update"
date: 2007-06-29
forum: Installation &amp; Upgrades
---

### Post by justtech on 2007-06-29
Still new to Ubuntu... got a new update today and when I restarted my computer about 5 hours later... it wouldn't boot into Graphical X.  What information do I need to post in order for someone to possibly help get back in.  I'm on the live cd now and I'm running 7.04 Fiesty Fawn.

---

### Post by limbourg31 on 2007-06-29
can you enter through safe graphics mode, and if not what about into command line? where does it hang on you or does it take you to a console?

---

### Post by justtech on 2007-06-29
It will not let me get anywhere but the "command promt".  Even if I try recovery.  But the error that I am getting is 

(EE) NVIDIA(0): Failed to Load the NVIDIA kernal module!
(EE) NVIDIA(0): ***ABORTING***

After reading another thread I have found out that it's because I was using a different version of the drivers then I was supposed to due to trying to get Dual Monitors set up.  So now how do I get the right drivers from the "Command Promt"

Thanks for your help.

---

### Post by orozcovision on 2007-06-29
I had this problem after updating to the recent Kernel. 

1). You'll have to re-download the latest drivers from [Nvidia]("http://www.nvidia.com")

Run the following at the Command Prompt:

2). sudo apt-get install build-essential
3). sudo apt-get install module-assistant nvidia-kernel-common
4). m-a prepare

Login as root and navigate to where ever you placed the nvidia drivers. (I just placed the driver in /home/myusername/Desktop and renamed it to "nvidia.run"

5). cd /home/<user>/Desktop
6) ./nvidia.run

After the install, Reboot.  Your X Server should now be working. If you continue to have problems, post your /etc/X11/xorg.conf file.

Best,
OrozcoVision

---

### Post by justtech on 2007-06-29
Not to sound stupid but I can't get to my desktop.  I am stuck at the command prompt.  When I run the commands that you put on there... I get "0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded."  Where to from now?

---

### Post by orozcovision on 2007-06-29
> I get "0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded." Where to from now?

This just means that the packages are already installed.  Start from #4.  Since you're posting here, I take it you have other means of being online.  Simply get the latest NVidia drivers and copy them into your affected Ubuntu machine. (For example, you can burn the drivers onto a CD. After inserting the CD into your Ubuntu machine, type "cd /cdrom" into your command prompt.  Then use "sudo cp <nvidia driver> /home/<user>)

You can still navigate to your Desktop via the Command Prompt.  As I had mentioned... that was just the directory where I placed my drivers.  You can copy (cp) your drivers to any dir you wish.

Then navigate to which ever dir. you placed your drivers. Type "./<nvidia driver.run>"

Once the install is complete, Reboot, and you should have your Desktop back.

---

### Post by justtech on 2007-06-29
thank you for your help

---

### Post by orozcovision on 2007-06-29
Here is a link I found. Hope this is also helpful for you:

[http://ubuntu-tutorials.com/2006/12/13/kernel-update-affects-some-nvidia-users-fix-included/](http://ubuntu-tutorials.com/2006/12/13/kernel-update-affects-some-nvidia-users-fix-included/)

Please let us know if any of these tips resolve your issue. Thanks in advance.

--
OrozcoVision.

---

### Post by justtech on 2007-06-29
Thank you for the link.  I have returned to the Ubuntu World.  Put away the Vista Laptop and now I am trying to get my dual monitors back.  I really appreciate your digging.  This is what FRAGOS had posted that had got me back in.

> There's more than one way to handle this but I'd do the following:

sudo nano ect/X11/xorg.conf

Find where the following section. Yours may differ from this one.

Section "Device"
Identifier "NVIDIA Corporation NV34 [GeForce FX 5200]"
Driver "nvidia"
BusID "PCI:1:0:0"
EndSection

change "nvidia" to "nv" and save the file.

When you reboot you shoild have X with the open source driver. Now I use synaptic to install the appropriate nvidia-glx package. This should get you in sync with the Ubuntu repositories. You may need to edit /etc/X11/xorg.conf again to say "nvidia".

Once again, I TRULEY Apreciate your help.  I love Ubuntu and hope that I start getting myself more familer with it.

---


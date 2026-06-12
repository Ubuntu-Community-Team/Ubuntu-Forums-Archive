---
title: "Upgrading difficulties with x server and nvidia 8800 GTS card"
date: 2008-04-04
forum: Installation &amp; Upgrades
---

### Post by JumbocactuarX27 on 2008-04-04
Today I logged onto my ubuntu to do some programming homework for the first time in a while. I noticed my system update icon was flashing at me. As it turned out, I was still on Fiesty Fawn and I decided that I may as well upgrade to Gutsy. Unfortunately for me, I forgot about the trial that was installing ubuntu in the first place. My GeForce 8800 GTS card instantly became a source of woe as I encountered problem after problem with x server. Now, I have Gutsy installed and running the gdm. Unfortunately, the restricted driver will not stay applied over restarts (I've tried three times now) and nothing else seems to be working. I'm stuck with a resolution of 800 x 600 which is only contributing to driving me insane. I've been at this for 4 hours now and I'm at the end of my rope. Any suggestions?

---

### Post by JumbocactuarX27 on 2008-04-04
It keeps starting in low-graphics mode if that helps. If I click continue then I get a blank screen, but if I click configure and choose VESA or nv drivers then I get to the conditions stated above.

---

### Post by Cresho on 2008-04-04
when ever I update and my 8800gt dies (drivers are not that wells supported yet), i follow my directions

1. sudo aptitude remove automake1.4
2. sudo apt-get install automake1.9 build-essential cvs libpango1.0-dev libgtk2.0-dev libgconf2-dev libglitz-glx-dev librsvg2-dev checkinstall libglade2-dev xserver-xorg-dev
3. grub into recovery mode and hit root.  cd into the directory where you downloaded the NVIDIA-Linux-x86-169.09-pkg1.run and sh NVIDIA-Linux-x86-169.09-pkg1.run in terminal.
4. ignore the question or say no to kernel download during instal and have nvidia xconfig update the x
5. is screen is not proper, continue and once booted, open synaptic package manager and remove nvidia kernel common.
6. add startup file to system->preference->sessions "nvidia-settings --load-config-only"
7. reboot and your good to go.

nvidia-xconfig if you have problems.

---

### Post by JumbocactuarX27 on 2008-04-04
I followed all your steps, and I'm still stuck with crappy resolution/low-graphics mode. Do I need to have that exact driver version? The one I downloaded was a newer one.

---

### Post by Cresho on 2008-04-04
did you try to uninstall nvidia-kernel common?  another thing you can do before this, try booting into the previous kernel.  you can see it in grub when you launch.  I do not use the nvidia kernel source, nore the new kernel.  THose nvidias are not needed.  If you remove them and reinstall the drivers, It should work.  I would remove those and do the process and then it boots fine.. First try to boot into your previous kernel from grub at bootup.

---

### Post by PmDematagoda on 2008-04-04
Just install the new driver through Recovery Mode and then start the X-Server soon after installation, then post here if the X-Server works properly, if it does then there is a way of making this permanent.

---

### Post by JumbocactuarX27 on 2008-04-04
First I did uninstall the nvidia kernel source along with all the drivers I could find. I had tried using the older kernel previously to no effect. When I went into recovery mode to reinstall the driver, it mentioned that it detected the driver had already been installed, not sure how to delete it then to install fresh. After reinstalling the driver (which popped up a few "directory/file not found" errors while trying to copy things) I started gdm to be greeted to 640 x 480 resolution and a lack of internet connection. I assumed these were because it was in recovery mode and went to restart into the kernel proper to see if the problem was fixed. That's when the GUI froze. I hit ctrl + alt + F1 and rebooted. Upon loading the kernel, I was again notified of low-graphics mode running, etc etc. 
Maybe I need to uninstall more stuff? I cleared out everything nvidia related that I could find in synaptic though.

---

### Post by Cresho on 2008-04-04
try reinstalling it again through the posted method.  IT has to work!  and let nvidia-xconfig fix it configure the x org.  I go through these problems myself and I usually end up getting the problem fixed.  It should be no different for you too!  the only thing i have in my synaptic that is nvidia is.........well none!  use the exact nvidia driver i posted!  the new ones put a pink halo around compiz windows.  I also have xserver-xorg-video-nv installed btw.  not sure exactly what this one does though but I havent had a problem with it.

here is an update.  uninstalled that xserver-xorg and it runs just fine without  it.  I know i can install that driver through grub recovery root menu with apt-get install so I really dont care if i screw my desktop.  This provides nvidia support and thats all it says.  maybee to run your low graphics?  but I figure this is vesa working here and not nvidia.

---

### Post by JumbocactuarX27 on 2008-04-04
Well, the problem is fixed I suppose. Since none of the above advice worked, I just reinstalled Fiesty Fawn and everything works fine like it used to before I tried upgrading yesterday. Since I'm not a power user or anything of ubuntu, I guess it doesn't matter that much if I upgrade or not. Thanks to everyone for the advice.

---


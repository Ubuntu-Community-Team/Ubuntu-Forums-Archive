---
title: "wireless problem"
date: 2010-04-28
forum: Installation &amp; Upgrades
---

### Post by dr_goose91 on 2010-04-28
Hey everyone, I installed ubuntu onto my laptop but the wireless isnt  working. I got the driver files from the realtek website but I dont know  how to install them :P

My card is the realtek RTL8191SE-VA2

and i got the drivers from here:  [http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PFid=48&Level=5&Conn=4&ProdID=226&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PFid=48&Level=5&Conn=4&ProdID=226&DownTypeID=3&GetDown=false&Downloads=true)

---

### Post by dstew on 2010-04-28
What you have downloaded is a tar.gz archive containing source code for the Realtek driver. You need to compile it and install it into your system if you want to use this driver. [This thread]("http://ubuntuforums.org/showthread.php?t=1425140") has some information on doing this. You need to install the build-essential and linux-headers packages for your kernel before you try to do it.

However, you might be able to use this wireless card without installing that driver. To see if the card is recognized by the generic Ubuntu driver, do **lspci** and **sudo lshw -C network** from a command line. Post the results to the forum.

---

### Post by dr_goose91 on 2010-04-28
> **dstew said:**
> What you have downloaded is a tar.gz archive containing source code for the Realtek driver. You need to compile it and install it into your system if you want to use this driver. [This thread]("http://ubuntuforums.org/showthread.php?t=1425140") has some information on doing this. You need to install the build-essential and linux-headers packages for your kernel before you try to do it.

However, you might be able to use this wireless card without installing that driver. To see if the card is recognized by the generic Ubuntu driver, do **lspci** and **sudo lshw -C network** from a command line. Post the results to the forum.

Thank you it sort of worked. The lspci and sudo lshw -c network didnt work. 

However I compiled the drivers using the instructions in the thread and they worked. 
However after I restarted there were no wireless networks again :(

Was I meant to do something else?

---

### Post by dstew on 2010-04-29
See if you can load the driver (kernel module) manually with the **modprobe** instruction as in the thread you followed. If that works, but it doesn't automatically load at boot time, you may need to do some additional configuration. You can modify the /etc/modules file to get it to load automatically at boot time.

---

### Post by dr_goose91 on 2010-04-29
> **dstew said:**
> See if you can load the driver (kernel module) manually with the **modprobe** instruction as in the thread you followed. If that works, but it doesn't automatically load at boot time, you may need to do some additional configuration. You can modify the /etc/modules file to get it to load automatically at boot time.
Ok, I'll give it a shot. I'll report back if it works

---

### Post by dstew on 2010-04-30
In thinking about it, after you created the module, you were in the Desktop/rt18 directory, if you followed the instructions on the thread. The module file, with the extension .ko, would be in this directory. Modprobe would work, since you issue the command while in the directory that contains the module file. However, at boot time, modprobe does not look in this directory for modules. It looks in the /lib/modules/"uname -r" directory. (The "uname -r" will return the current kernel version, which is the real directory name.) The kernel module file should be copied to the /lib/modules/"uname -r" directory.  After you copy the kernel file to the /lib/modules/"uname -r" directory, issue the command **depmod**. This updates the module dependencies file modules.dep, which modprobe needs to put the modules into the kernel at boot time.

After this, reboot and see if it works.

---


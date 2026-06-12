---
title: "After accepting updates, cannot log in as user or guest -- help!"
date: 2016-11-03
forum: Installation &amp; Upgrades
---

### Post by Paper Pusher on 2016-11-03
I am running 16.04 LTS.  I periodically check for SW updates and have always been able accept them without issues. Today I had Ubuntu install available updates and now I cannot get past the log-in screen.  Whether I put in my user password or attempt a guest log in, the screen goes dark after a few seconds, I get a little drum roll, and the log in screen comes back up.  Can anyone help me solve this problem?

---

### Post by scpatl4now on 2016-11-04
I am having the same issue.  I can log into a partition with 14.04, but I dont know what to do

---

### Post by scpatl4now on 2016-11-04
I was able to get in to 16.04.   There is some issue with Nvidia drivers.  I uninstalled them and was able to log in default resolution (everything too big).  I tried to reinstall via additional drivers and rebooted and same original log in error...so I'm still trying...but its definitely an Nvidia problem

---

### Post by k7gliderpilot on 2016-11-04
Same here on two independent machines. One is 16.04, the other 14.04. No network connections or USB contact between them. Both happened today.

Both are up to date. From the GRUB menu I chose the recovery menu item. And then tried to enable the network connection which failed. I cannot read the feedback because the recovery screen immediately returns. DPKG shows a number of packages it wants to update, apparently because they are damaged. They are mostly important ones like systemd.

Looks like something serious.

To be clear, one can login into Ubuntu, the username and password is verified and accepted. However the system then crashes and returns to the login screen.

Yes, NVIDIA here too. The screen appears nice and correct in the highest resolution, but the ssytem crashes.

---

### Post by ubfan1 on 2016-11-04
Try logging in with an older kernel (one which used to work), found under the grub "advanced" menu item.  See how nvidia is set up, and then duplicate it on the newer kernel, using "nomodeset" on the grub linux line if necessary to get in to do the fixes, or use a virtual terminal and the command line.

---

### Post by Paper Pusher on 2016-11-04
How do we access the grub? And how can we log into an old(working) Kernal?

---

### Post by ubfan1 on 2016-11-05
Hold down the shift or tab key at power on to force the grub menu to display.  Use the arrow keys to select the "advanced" choice, and then to select a kernel one number back from the latest one (or try "recovery" mode on the latest one, that might work too).

---

### Post by k7gliderpilot on 2016-11-05
Also featuring on:[URL="https://devtalk.nvidia.com/default/topic/974819/linux/cinnamon-crashes-after-updating-nvidia-driver-to-367-57-linux-mint-18-cinnamon-/"]

https://devtalk.nvidia.com/default/topic/974819/linux/cinnamon-crashes-after-updating-nvidia-driver-to-367-57-linux-mint-18-cinnamon-/[/URL]

Another forum:

[https://forums.geforce.com/default/topic/974910/geforce-drivers/newest-nvidia-driver-crashes-linux-reproducible-/](https://forums.geforce.com/default/topic/974910/geforce-drivers/newest-nvidia-driver-crashes-linux-reproducible-/)

---

### Post by FoxJT on 2016-11-07
I am having the same login looping problem on 16.04. I have tried all suggestions without success. It seems that the solution is very system dependent.
I have noticed that when booting into recovery mode, among all the OK messages there was one FAILED. This said "Failed to start Load Kernel Modules". This suggested checking "systemctl status systemd-modules-load.service". Drilling down I found the file /etc/modules-load.d/modules.conf. In the linked file /etc/modules were listed "lp, #ndiswrapper and rt3070sta", each on their own line. There was an empty line before "lp". Should this contain the call /boot/vmlinuz....? If so, why isn't it there? Unless rt3070sta calls it??

---

### Post by FoxJT on 2016-11-09
Why is nvidia suspected?
What are the commands to reinstall?

---

### Post by teprac on 2016-11-09
I cannot speak for everyone else, but I have the same problem and I have nvidia, and if you run the commands to purge and remove the nvidia drivers the problem goes away and you can login into ubuntu. But then linux crashes because it needs the nvidia drivers installed...

> **FoxJT said:**
> Why is nvidia suspected?
What are the commands to reinstall?

---

### Post by scpatl4now on 2016-11-10
The solution is here

[https://ubuntuforums.org/showthread.php?t=2342144&p=13568203&posted=1#post13568203](https://ubuntuforums.org/showthread.php?t=2342144&p=13568203&posted=1#post13568203)

You will need to downgrade to 304.131  The new driver is causing the problem.  The is also a bug report for this.

---

### Post by FoxJT on 2016-11-11
Solved my problem (I hope ) :/  which was "Booting up to login screen. Enter password .... returns to login screen (Ubuntu 16.04 )"

I have tried most options from trawling through the threads here and elsewhere, with no success.

Booting into recovery showed messages which said "Failed to load kernel modules".

I reloaded the kernel: 
   **sudo apt-get install --reinstall linux-image-4.4.0-45-generic**
then rebooted.  No change :(

The general consensus seemed to rotate around problems with the video drivers, so:
   **sudo ubuntu-drivers devices**
This shows the required drivers for my Video card (nVidia  G96 GeForce 9400 GT) as nvidia-340.
I ran:
   **sudo apt-get install nvidia-340**
The messages showed that nvidia-304 was being removed and replaced with nvidia-340.
After a reboot, I was able to finally login!!! Hooray!!!

Rebooting however had a "Internal Ububtu problem". [NO!!!].  The problem package was /usr/sbin/unity-greeter (?) and the problem was automatically reported.
After a reboot, it now boots up OK. However, the "Failed to load kernel modules" is still there?????

So, in my case, nvidia-304 is the wrong driver!!

Here's hoping it doesn't repeat!

Many thanks to all posters for all their help.

How do you make software totally hardware independent?
I assume that these problems are read about by developers and solutions incorporated into upgrades.

Incidentally, most of the above help came from help.ubuntu.com Community Help BinaryDriverHowto/Nvidia. Thanks.

---

### Post by Paper Pusher on 2016-11-17
We successfully restored Ubuntu 16.04.1 by creating a bootable DVD on a different computer and using it to boot up my machine. I then had to reformat my computer's boot drive (SSD) and reinstall the 16.04.1 operating system. I lost everything on the SSD, but there was nothing on it that I couldn't replace. 

The only thing that has not been restored is the scanner function of my Brother MFC-J870DW AIO. Have followed instructions for downloading and installing appropriate drives from the Brother website and although the printer now works fine, the scanner remains nonfunctional. Will create a separate post seeking guidance with the scanner.

---


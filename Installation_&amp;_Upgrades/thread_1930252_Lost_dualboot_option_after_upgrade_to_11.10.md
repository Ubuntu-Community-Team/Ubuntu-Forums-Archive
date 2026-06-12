---
title: "Lost dualboot option after upgrade to 11.10"
date: 2012-02-23
forum: Installation &amp; Upgrades
---

### Post by GijsWillem on 2012-02-23
Hello Forum,
Hope some-one can help me here. The situation is as follows. I have a HP desktop PC with 2 hard disks. One disk with a complete installation of Windows 7 and one with Ubuntu 10.04 plus installed dual boot option. Worked fine and was very pleased with it.
Installed an upgrade to Ubuntu 11.04 and I still had the option to select Windows 7 or Ubuntu. Then I went installing the upgrade to Ubuntu 11.10 and unfortunately I have lost the option to select an OS during boot up.
Note that nowhere during this upgrade installation I was asked if I wanted to keep anything or overwrite anything so I assumed that the choice at boot up would still be in place.
Any suggestions to help me out?
Many thanks for any help here.
Gijs

---

### Post by darkod on 2012-02-23
The first suggestion is to run the boot info script from the link in my signature. It has all the details there.
Post the results as explained. They will show more about the boot process.

---

### Post by GijsWillem on 2012-03-05
Hello darkod,

thanks for the instructions.
I did run run the boot info script file as per the instructions
Attached the results.txt file albeit compressed into tar format as the 19.5 k size limit was exceeded.

Hope that this file does contain the clues on how to get my Windows 7 OS back

Many thanks in advance.

Gijs

---

### Post by oldfred on 2012-03-05
Script shows two installs of Ubuntu. And a bug in the script with grub 1.99 does not show which install it is booting from in the MBR.

You have 11.10 in sda5 and 10.04 in sdb1.Which are you booting?

You have a lot of kernels in your sdb1 shows all the Ubuntu kernels before the Windows & Vista(recovery) boot choices. Grub's menu is in a box and you will get a (very) tiny arrow on the right bottom of the box to tell you that you have more entries. All you have to do is scroll down to find the Windows at the bottom.

You may want to houseclean old kernel. Just be sure not to delete current and usually we suggest keeping one older one in case of issues. You may want to boot into both systems to update.

Check current kernel:
lsb_release -a
Go to Synaptic Package Manager and search for linux-image.
More info in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)
HOWTO: Grub Customizer 
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)

---

### Post by GijsWillem on 2012-03-06
Hello Oldfred,
thanks for the help here. Highly appreciated. :D
I did follow your instructions and can confirm that I am booting and running 11.10
Checking my kernel gives following:
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 11.10
Release:        11.10
Codename:       oneiric


Installed the Grub customizer and in the menu I do see all the various OS and also Windows 7.
However here I am not totally sure what to do.
Through the preferences tab I could select to make Windows 7 (entry 5) the predefined choice. However when I boot there is simply no menu when the system booths so I am a little afraid if I do so I will loose the option to access Ubuntu and boot Ubuntu.
In the visibility section (of the preferences menu) both show menu and look for other menu boxes are ticked, but the system just does not shows me a menu during boot up.
In my case I just do not get the choice of any other OS and my machine boots into Ubuntu immediately.

Furthermore I also followed the link to remove old installations
I have added the txt file which shows the status after cleaning. 

Any help or suggestions as always highly appreciated.
Gijs

---

### Post by oldfred on 2012-03-06
Your other install still has lots of kernels.

If you hold shift key from BIOS until menu appears, do you get a menu?

Is system shutting down normally?

I also found that it sees key strokes from BIOS until menu, so you can often immediately hit down arrow to the menu item you want if you know how many down arrows to hit even before menu appears. You can try one to get to a recovery mode?

---

### Post by GijsWillem on 2012-03-07
I will try to remove the old kernels in order to clean it up a little.

With respect to the other remarks I can give you following information:
My hardware uses F2 to get into the BIOS set up. This works without any problem.
If I hold down the shift key the system just boots into Ubuntu 11.10
And the system shuts down perfectly normal.

I did also try to boot up pressing the arrow down key and finally got into a windows recovery set up.
This means that the choice during boot up how to boot up is still there but it's not shown on the monitor.
Running my previous Ubuntu installation I did not have this issue and just could see and consequently select the OS I wanted to boot. 
I did not change any hardware, only a new Ubuntu install.

Could I use another boot manager, and if so how do I install this? Any suggestions here?
Again many thanks for the help!
Gijs

---

### Post by GijsWillem on 2012-03-07
It looks like I found a solution.
I installed following software: StartUp-Manager
In this software I can change the display resolution. It was at standard DOS resolution being 640x480
Changing it to 800x600 did the trick. Now at boot up I do have a menu where I can select the OS.
Still wondering why with Ubuntu 11.10 my monitor refuses to display 640x480, as it was working fine in this resolution before.

But as for me the issue is solved the thread may be closed. Many thanks for the help here.
Gijs :p

---


---
title: "VMPlayer doesn't work after kernel upgrade"
date: 2007-06-19
forum: Installation &amp; Upgrades
---

### Post by forchessonly on 2007-06-19
A month or so ago Ubuntu Dapper did it's auto update thing and installed the new kernel (intrd.img-2.6.15-28-386 from intrd.img-2.6.15-27-386). I rebooted after install and immediately the xserver would not load. I quickly figured out that I could boot the old kernel from GRUB however, which I did, and I was back up and running. But now VMPlayer doesn't work when I boot the older, working kernel, 

I get the error:

Could not open /dev/vmmon:
No such file or directory.
Please make sure that the 
kernel module `vmmon' is 
loaded.

followed by:

Failed to initialize 
monitor device.

I would like to accomplish two things, get Ubuntu up and running with the new kernel and get vmplayer working again so I can run WindowsXP. Being very new to linux I really don't know how to accomplish this, and after quite a bit of searching I've failed to find a solution.

Any help would be much appreciated, thanks.

---

### Post by dayhawk4 on 2007-06-20
Okay, this one sounds like a bit of a challenge, this is the score,

     Different kernels have different drivers compiled in (more monolithic in nature), different drivers compiled for modules, and different configuration scripts for starting the modules.  Most likely if you are using a kernel which worked before, the it will be a start-up script which changed, or a device node has been removed.  Eitherway, the easiest approach would be to attempt to uninstall vmware player first, and then whether it successfully uninstalls or not, try reinstalling the package.  This should put back in all needed device modules and scripts for your older kernel.  Sometimes, the installation scripts also have a repair feature.  Most of the work that I have done with vmware is from windows with vmware in the virtual machine (makes dealing with devices without linux drivers easier to deal with .....) .  Let me know how it goes, and depending on the output, there might be a coupe of other things we can try....

dayhawk4

---

### Post by luvr on 2007-06-20
You will have to configure and compile the VMware modules for the new kernel.

To this end, run the **vmware-config.pl** script, which you will find in the [I]vmware-distrib/bin[//I] subdirectory of the folder from which you installed the VMware player--most likely, that will be a subdirectory of your home folder.

Thus, open a console window, and type something along the following lines:
```
cd ${wherever-you-installed-vmware-player-from}/vmware-distrib/bin
sudo vmware-config.pl
```

The script will ask you the VMware configuration questions that you got when you initially configured it. You can simply tell it to leave the configuration settings unchanged.

---


---
title: "Ubuntu 18.04 - Gigabyte Aero 15 Laptop - Crashes on setup and 'try' version"
date: 2018-05-06
forum: Installation &amp; Upgrades
---

### Post by lunarage on 2018-05-06
Ubuntu 18.04 - Gigabyte Aero 15 Laptop - Crashes on setup and 'try' version


I made a USB External HD bootable by using the Rufus application.


From laptop startup, I press F12 and then select the external USB HD. I am presented with a option of 'try','install'.


If I hit install, Ubuntu installer loads and I hear the sound and the splash screen show up. Then I am presented with a window asking me to select language, my mouse cursor moves but I cannot right or left click.


If I click, next, really quickly when the screen loads, it accepts the mouse click but then the cursor changes and then becomes un-responsive.


If I try the 'try' Ubuntu option, again the Ubuntu desktop loads but and my mouse cursor moves, but I cannot click anywhere?




Aero 15 has a 1060m GFX and im using a USB mouse (the same if I unplug and mouse and just use my laptops trackpad).


I looks for logs, and all I found where the F1-F12 text files which dont have any info to help.


Any known issues or fixes?

---

### Post by oldfred on 2018-05-06
If nVidia you need nomodeset. Both to boot installer & first boot or until you install nVidia proprietary driver from Ubuntu repository. You may need to add ppa to get very newest nVidia driver.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) 


 [https://ubuntuforums.org/showthread.php?t=2385770&p=13742959#post13742959](https://ubuntuforums.org/showthread.php?t=2385770&p=13742959#post13742959) by 1fallen
> EDIT: This seems to work for my card here, instead of using "nomodeset" I am using this "nogpumanager"
And I have to watch carefully any changes made to "/etc/X11/xorg.conf" 
   nVidia Must purge & install correct driver
[https://ubuntuforums.org/showthread.php?t=2380061](https://ubuntuforums.org/showthread.php?t=2380061)
[https://ubuntuforums.org/showthread.php?t=2362351](https://ubuntuforums.org/showthread.php?t=2362351) 

      
 # Shows standard repository versions, which is the same as
System Settings, Software & Updates icon, Additional drivers tab
ubuntu-drivers devices 
   [https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
sudo apt-add-repository ppa:graphics-drivers/ppa 
   # should show newest versions available in addition
ubuntu-drivers devices 

 You then can manually choose any in list.
sudo apt-get install nvidia-XXX

---


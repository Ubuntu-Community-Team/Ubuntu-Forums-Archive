---
title: "Boot failure after attempting to upgrade from 14.10 to 15.03, what to do next?"
date: 2015-07-12
forum: Installation &amp; Upgrades
---

### Post by Chris_Racey on 2015-07-12
My system was stable running 14.10 but every time I booted up I was prompted to ubgrade to 15.03. I finally gave in and attempted the upgrade. It gave several errors during the process, reported at the end that it had failed, and now when I restart the computer it doesn't load the GUI and only logs in to a command prompt with a virtual file system (unable to properly access files). The loading screen does now report version 15.03.

Although I've used it for a while now, I am not a particularly advanced Linux user, fixing this may be a little bit beyond my capabilities. Is anyone able to give me some advice on how to proceed? I'm not sure whether I should be trying to downgrade back to 14.10 or trying to get 15 working properly?

The main error I got during the install was:-

"Writing grub to boot device failed (failed to install to /dev/sda)"

Also from reading around I get the impression Ubuntu 15.03 has some issues with Nvidia drivers. The card in the machine is an Nvidia Quadro so this may be a factor.

Many thanks for any help or advice you can offer.

Chris

---

### Post by oldfred on 2015-07-12
Before doing an upgrade you really have to remove all proprietary drivers and anything installed by ppa. 
How did you install nVdia drivers. From repository, ppa, or directly from nVidia. Repository is always best choice.
Then after you upgrade you reinstall the nVidia driver.

Best to see details:
 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by Chris_Racey on 2015-07-20
Hi there,

I've created a bootinfo summary report and the url is below...
[http://paste.ubuntu.com/11909020/](http://paste.ubuntu.com/11909020/)

I'm sorry for the delay in replying, I've been out of the country, but I'm fully focused on this now so will be paying close attention to this thread.

As for your question about the nVidia drivers, I believe some version of them was installed when I originally set up the system with 14.10 and I then updated them with a package or repository from the nVidia site. I'm afraid it was a while ago so I cant really remember the details.

Since I have command line access, is there any way I can uninstall the drivers with the system as it is now and get it to boot normally again? Is it actually possible to get nVidia drivers working at all with version 15.03?

Many thanks,
Chris

---

### Post by Chris_Racey on 2015-07-20
Update: In order to generate the bootinfo summary I did a boot repair by booting off a usb stick (which attempted a repair as well as generating the report). It appears that this has made things worse and it now no longer boots to the command prompt at all. After the bios screens have finished I just get a black screen with a flashing cursor. I basically have no idea what to do from here (?).

---

### Post by oldfred on 2015-07-20
You have only gpt partitioned drives, but grub & install are on sdb.
Default install of grub is to sda, but your sda drive does not have a bios_grub partition so it can install grub to it.
But it should really be installing grub to sdb anyway. That can be reset.

If you installed nVidia drivers from nVidia directly then you in effect have to reinstall with every kernel update. If you install from repository or use a ppa to get newest nVidia driver the dpkg kernel install also re-integrates nVidia into the kernel automatically. So best not to use nVidia directly, but repository or ppa.

If you are booting from sdb in BIOS, and get black screen, then you may have gotten new kernel but do not have nVidia working. You should then be able to use nomodeset to get into gui system. But may be low quality video.
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

If you did install from nVidia, you must purge before installing from repository or ppa. Configurations somehow are slightly different and create major conflicts.
       
 But you have to totally purge before installing a different version or else you will have major conflicts
Shows various install methods for nVidia. 13.04 but still the same
[http://www.dedoimedo.com/computers/ubuntu-ringtail-nvidia.html](http://www.dedoimedo.com/computers/ubuntu-ringtail-nvidia.html)
Uninstall fixes
[http://choorucode.com/2013/02/07/how-to-fix-nvidia-driver-failure-on-ubuntu/](http://choorucode.com/2013/02/07/how-to-fix-nvidia-driver-failure-on-ubuntu/)

You show nVida GTX660, so you should only need the most current version in repository. If you really want newest driver you can add a ppa to get very newest. But most of updates in newest drivers are to support the newer cards/chips with newer features. A few things may improve if you really want the ppa's newest drivers.

Go to System Settings, Software & updates, and drivers tab.

Grub remembers drive.
 #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc # for BIOS with grub-pc 
It will show drive model & serial number
to see drive info
sudo lshw -C Disk -short 

    sudo grub-probe -t device /boot/grub

   #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc or dpkg-reconfigure grub-efi-amd64
#Enter thru first pages,tab to ok, spacebar to choose/unchoose drive, enter to accept, do not choose partitions
[http://ubuntuforums.org/showthread.php?t=2189643](http://ubuntuforums.org/showthread.php?t=2189643)

If you want grub to install to sda, you need to add a 1 or 2MB bios_grub unformatted partition anywhere on drive sda.

---

### Post by Chris_Racey on 2015-07-21
Many thanks for all your advice, it's been extremely useful and I think I'm making progress, I'm a little bit stuck about what to do next though...

First of all, I think the grub/boot issue is resolved. I swapped the boot order in the BIOS and it can clearly find grub on the other drive so it now boots up to a terminal command prompt again.

My plan was then to try to follow some instructions for removing and re-installing NVIDIA drivers. I was following some instructions which first told me to remount my hd (sudo mount -n -o remount,rw /). When I did this the screen flickered and it immediately tried to launch a GUI. The default desktop environment login screen appeared but failed with a black screen and some graphical errors as soon as I entered my password. If I ctrl+alt+f1 back to the console and type startx it immediately runs the mate desktop environment (which I keep installed for accessing the machine with remote-desktop/xrdp). This actually runs pretty well in full resolution and I'm typing this now from the largely function mate desktop environment. This are not perfect however as it's only running with a single monitor, upon reboot it goes back to a command prompt only, and several services aren't running properly.

I think what I'm going to do now is attempt to rip out the NVIDIA drivers and reinstall them based on the instructions on the page you linked ([http://choorucode.com/2013/02/07/how-to-fix-nvidia-driver-failure-on-ubuntu/](http://choorucode.com/2013/02/07/how-to-fix-nvidia-driver-failure-on-ubuntu/)). I'm unsure whether I installed from the NVIDIA site or from a repository so I'm going to try the purge method.

Fingers crossed :-)

---

### Post by Bucky Ball on 2015-07-21
Did you try this???

> **oldfred said:**
> 
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)



---

### Post by Chris_Racey on 2015-07-21
Hi Bucky,

Yes I did. It didn't seem to make any difference to the  way the desktop environment loaded, mate desktop worked, the default  one didn't (i dont know what the default one is called?). When I  rebooted the line had reverted back to 'quiet splash'.

I have now  gone through with the next step and got the nvidia drivers ripped out  and re-installed using the guides oldfred suggested. This has worked and  all desktop environments are up and running. I'm now in the process of  trying to recover some other smaller issues that are left over as a  result of the upgrade.

One problem I was having was my comp was starting up with a read only file system, and it ran normally once I remounted. The way I resolved this was by switching from systemd to upstart (the service manager used by ubuntu 14.10). This resolved this issue and a couple of others I was having. Hopefully that will be useful for others having problems after the upgrade.

Chris

---

### Post by Bucky Ball on 2015-07-21
Excellent news and well done all. Please mark the thread as solved. See the first link in my signature. Good luck. :)

---


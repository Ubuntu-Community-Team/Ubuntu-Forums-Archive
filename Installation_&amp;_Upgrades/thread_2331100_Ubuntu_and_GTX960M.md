---
title: "Ubuntu and GTX960M"
date: 2016-07-18
forum: Installation &amp; Upgrades
---

### Post by zelle-one on 2016-07-18
Hi

I have an Asus UX501V laptop with a GTX 960M graphics card and I am unable to get the Nvidia driver running. I know this topic has been discussed several times but none of the presented solutions worked for me. And after the third time of reloading my backup because I completely destroyed my system, I wanted to ask here, if someone could help me. Also in the past there where different solutions to get Optimus running with Ubuntu and I just don't know which solution is currently working and which driver I should use.

Currently I am running Ubuntu 14.04 but I also tried 16.04 with no luck. I have a single OS system, so just Ubuntu is installed on this machine. And I encrypted the system during Ubuntu installation.

Can anyone tell me how to install the Nvidia driver and also Cuda? Which driver version should I use? Which Ubuntu should I use, 14.04 or 16.04?

Thanks for the help,
ZO

---

### Post by grahammechanical on 2016-07-18
According to the Nvidia driver web site the GTX 960M is supported by driver 367.35 & driver 364.19. An earlier driver such as 340.96 does not support GTX 960M.

The newest version of Ubuntu is preferable. And if it is an LTS version then we should be installing the latest point release. With 14.04 that would be 14.04.2 with 14.04.3 being released at the end of August. And 16.04 should be getting its first point release (16.04.1) at the end of July. The purpose of these point releases is to keep the release up to date with hardware drivers for hardware that came out after the LTS was released.

How have you been going about installing the proprietary video driver? There are three methods. (1) When installing Ubuntu tick the box to install third party software. (2) After installation we go to System Settings>Software & Updates>Additional Drivers tab. (3) We use the terminal and run this command

```
sudo ubuntu-drivers autoinstall
```

That will install the recommended proprietary video driver. What method are you using? This command will list the officially available proprietary video drivers:

```
ubuntu-drivers list
```

Allow time for the command to work. A Nvidia settings utility will also be installed. Use that to switch from integrated graphics to Nvidia graphics.

Regards

---

### Post by zelle-one on 2016-07-18
Hi,

thanks for the help.

I tried these links:

[http://askubuntu.com/questions/658040/ubuntu-14-04-nvidia-drivers-for-geforce-gtx-960m](http://askubuntu.com/questions/658040/ubuntu-14-04-nvidia-drivers-for-geforce-gtx-960m)
[http://askubuntu.com/questions/768959/ubuntu-16-04-nvidia-drivers-for-geforce-gtx-960m](http://askubuntu.com/questions/768959/ubuntu-16-04-nvidia-drivers-for-geforce-gtx-960m)

And some other methods which I cannot find any more as I reloaded the backup and hence lost my browser history.

Till now I always used apt to install. I also tried to download and install the installer from the Nvidia site.

---

### Post by Bucky Ball on 2016-07-18
? Have you tried looking in 'Additional Drivers'? The driver for it should be there. Enable it.

You might want to go back to a fresh system, but it should be that simple. You can then configure the card with the NVidia config app that will be in you apps menu. There should be no reason to install from a third-party and hasn't been for many NVidia cards for a long time. There's nothing special about the 960m. I have a 940m and running a GTX970 in the desktop. All the same.

The driver from Additional Drivers should also bring in Cuda support if you card can do it.

---

### Post by zelle-one on 2016-07-18
Additional drivers tab shows me only version 352.63. Twice, one proprietary and one proprietary, tested. But only that version

---

### Post by zelle-one on 2016-07-18
```
$ ubuntu-drivers list
nvidia-352
nvidia-352-updates
$
```

I am on 14.04. Maybe I should update tu 16.04?

---

### Post by oldfred on 2016-07-18
Asus also often needs another boot parameter: pci=nomsi

If newer hardware 16.04 would be generally be better. Those with AMD have an issue with newer system  not working with current AMD proprietary driver, but nVidia works.

If you attempt to install more than one nVidia driver, you get conflicts. A new driver does not delete the old one. You must always purge before new driver install.
And do not install the .run file from nVidia as you have to manaully re-update with every kernel update. If new driver not in repository, you can add the ppa that has all the new drivers.

       # list drivers available, same list as system settings,  software updates,  additional drivers or last tab
ubuntu-drivers devices
# or
ubuntu-drivers devices | grep recommended  

If available driver is new enough for your nVidia card/chip:

 sudo apt-get remove --purge nvidia-*
sudo ubuntu-drivers devices
sudo ubuntu-drivers autoinstall 

Many need boot parameters to get into system, or use recovery mode, second line in grub to get to command line to install drivers.

 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) 

      
 Ubuntu Launches Its "Fresh" Proprietary Driver PPA - August 2015
[http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-Fresh-Driver-PPA](http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-Fresh-Driver-PPA)
Instructions are newest driver for newest cards, must load legacy driver if old nVidia card.
[http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action](http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action)
Details on why and future incorporation to Ubuntu installer
[https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html](https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html)
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa) 
   # Shows standard repository versions
ubuntu-drivers devices
sudo apt-add-repository ppa:graphics-drivers/ppa
# should show newest versions available in addition
ubuntu-drivers devices

 Problems Installing on ASUS F555U   needed boot option pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2303665](http://ubuntuforums.org/showthread.php?t=2303665)
Asus x555u w/o pci=nomsi - space issue on drive and runaway log files
[http://ubuntuforums.org/showthread.php?t=2327103&page=3](http://ubuntuforums.org/showthread.php?t=2327103&page=3)
[http://ubuntuforums.org/showthread.php?t=2327570](http://ubuntuforums.org/showthread.php?t=2327570) 
      
 Asus UX303UB hardware problems - a list  15.10
[http://ubuntuforums.org/showthread.php?t=2319066](http://ubuntuforums.org/showthread.php?t=2319066)

---

### Post by zelle-one on 2016-07-18
Thanks a lot for the detailed answer! I will look into this tomorrow morning. It was a long day today ...

---

### Post by Bucky Ball on 2016-07-18
352 is what I'm using on the desktop with the GTX970 and 16.04 LTS from memory and all is fine. Perhaps it has to do with oldfred's points if it is not working as it should for you.

I'll double check later, but if you are being offered the 352, pretty sure that is the one so shouldn't be a need to upgrade.

---

### Post by zelle-one on 2016-07-20
I did an upgrade from 14.04 to 16.04 and afterwards a ```
sudo ubuntu-drivers autoinstall
``` which resulted in my PC crashing after entering the encryption password.
So I added ```
acpi_osi= pci=nomsi
``` to my grub file and was able to boot Ubuntu and logging in but having my PC crashed again after about 10 seconds after logging in, without doing anything.
So I changed grub again to not boot ```
4.4.0-31
``` but ```
4.2.0-41
``` instead and now Ubuntu runs more or less stable.

To verify if my graphics card is working I tried ```
optirun glxgears
``` which leads to:

```

[ERROR]Cannot access secondary GPU - error: [XORG] (EE) Failed to load module "mouse" (module does not exist, 0)
[ERROR]Aborting because fallback start is disabled.

```

So I guess, the graphics card is not running?

---

### Post by zelle-one on 2016-07-20
Maybe this output is also important:
```
$ dpkg --get-selections | grep nvidia
nvidia-361                    install
nvidia-opencl-icd-361     install
nvidia-prime                  install
nvidia-settings               install
```

---

### Post by oldfred on 2016-07-20
This will show what is installed:
 #What is installed
dkms status 

      
 #To see video:
sudo lshw -c display
sudo lshw | grep -A 11 display
lspci | grep VGA

---

### Post by zelle-one on 2016-07-20
```
$ dkms status
bbswitch, 0.8, 4.2.0-42-generic, x86_64: installed
bbswitch, 0.8, 4.4.0-31-generic, x86_64: installed
nvidia-361, 361.42, 4.2.0-42-generic, x86_64: installed
nvidia-361, 361.42, 4.4.0-31-generic, x86_64: installed

```

```
$ sudo lshw -c display
  *-display UNCLAIMED     
       description: 3D controller
       product: GM107M [GeForce GTX 960M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:dc000000-dcffffff memory:b0000000-bfffffff memory:c0000000-c1ffffff ioport:e000(size=128) memory:dd000000-dd07ffff
  *-display
       description: VGA compatible controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:16 memory:db000000-dbffffff memory:70000000-7fffffff ioport:f000(size=64)

```
```
$ sudo lshw | grep -A 11 display
           *-display UNCLAIMED
                description: 3D controller
                product: GM107M [GeForce GTX 960M]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a2
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress cap_list
                configuration: latency=0
                resources: memory:dc000000-dcffffff memory:b0000000-bfffffff memory:c0000000-c1ffffff ioport:e000(size=128) memory:dd000000-dd07ffff
        *-display
             description: VGA compatible controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 06
             width: 64 bits
             clock: 33MHz
             capabilities: pciexpress msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:db000000-dbffffff memory:70000000-7fffffff ioport:f000(size=64)

```
```
$ lspci | grep VGA 
00:02.0 VGA compatible controller: Intel Corporation Skylake Integrated Graphics (rev 06)

```

---

### Post by oldfred on 2016-07-20
That says you have 361 installed.

You may want to check that you also have nvidia-prime and nvidia-settings installed.

---


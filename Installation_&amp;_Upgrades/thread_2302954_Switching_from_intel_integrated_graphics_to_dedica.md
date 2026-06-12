---
title: "Switching from intel integrated graphics to dedicated GPU"
date: 2015-11-15
forum: Installation &amp; Upgrades
---

### Post by snarkyCoder on 2015-11-15
I am very new to linux so please bear with me :)
I am running Ubuntu with an intel i7-4790 and using the integrated graphics but in a couple of days I will be getting a nvidia GeForce GTX 960
What should I do before installing the GPU? Is there a process I should do like uninstalling the intel graphics drivers?:confused:
Or should I just insert the card and boot the system up with the monitor connected to the GPU and then proceed with installation of the nvidia drivers?

---

### Post by grahammechanical on 2015-11-15
You may find that the machine is still using the integrated video adapter and that you need to enter the BIOS/UEFI to switch over to the discreet video card. If you load Ubuntu using the integrated video adapter you can then go to System Settings>Software & Updates>Additional Drivers tab and if you are connected to the internet and if you give the utility some time Additional Drivers may offer you some Nvida proprietary drivers to install. The utility will take care of disabling the Intel driver if it needs to.

Oh, by the way, At the boot menu there is an option called Advanced Options for Ubuntu. Open that sub-menu and we can select recovery mode. And then at the recovery menu we can select Resume. That can be a useful method of getting to a working desktop if there are problems with video drivers.

Regards

---

### Post by SeijiSensei on 2015-11-15
When I installed an NVIDIA 750 into my ASUS machine, both Windows and Ubuntu started using the device without any changes to the BIOS.  Ubuntu loaded the nouveau driver. It took a little work to install the proprietary driver, as the "Driver Manager" application in 14.04 couldn't find a match.  I ended up using the [xorg-edgers PPA]("http://askubuntu.com/questions/464354/update-nvidia-drivers-with-xorg-edgers-ppa") instead.

---

### Post by deadflowr on 2015-11-15
> **SeijiSensei said:**
> When I installed an NVIDIA 750 into my ASUS machine, both Windows and Ubuntu started using the device without any changes to the BIOS.  Ubuntu loaded the nouveau driver. It took a little work to install the proprietary driver, as the "Driver Manager" application in 14.04 couldn't find a match.  I ended up using the [xorg-edgers PPA]("http://askubuntu.com/questions/464354/update-nvidia-drivers-with-xorg-edgers-ppa") instead.

That's usually about right.
Newer machines tend to have the video card detector function set to automatically use any externally added card; external being a card used for a pcie or other pci-type connection, if that makes sense.

Only one way to see, and that's to simply pop that baby in and connect it to a monitor.

If it's blank, turn off  the machine, change the connection from the new card to the old card, then turn it on and go to the BIOS (or UEFI) screen.
(BIOS/UEFI screen access should be explained on the first screen when you turn on the machine; that first screen that usually tells you what to press to get the boot menu. it usually also shows how to access the settings option)
Then look for the video settings and change it.
Then follow how to save the setting. Shutdown, and change the connections once again.

When it works, you might look at what nvidia drivers are readily available in the drivers section.
(As explained already)

And you need not worry one bit about the intel drivers.
Whether or not they are on the system will have no effect on the nvidia card.
(And you might be better off keeping them in case the nvidia card goes belly up.)

---

### Post by snarkyCoder on 2015-11-15
> **grahammechanical said:**
> You may find that the machine is still using the integrated video adapter and that you need to enter the BIOS/UEFI to switch over to the discreet video card. If you load Ubuntu using the integrated video adapter you can then go to System Settings>Software & Updates>Additional Drivers tab and if you are connected to the internet and if you give the utility some time Additional Drivers may offer you some Nvida proprietary drivers to install. The utility will take care of disabling the Intel driver if it needs to.

Oh, by the way, At the boot menu there is an option called Advanced Options for Ubuntu. Open that sub-menu and we can select recovery mode. And then at the recovery menu we can select Resume. That can be a useful method of getting to a working desktop if there are problems with video drivers.

Regards

Thanks
I got a little confused about the last part. So I would go to the recovery menu for installing the nvidia drivers?

---

### Post by snarkyCoder on 2015-11-15
> **SeijiSensei said:**
> When I installed an NVIDIA 750 into my ASUS machine, both Windows and Ubuntu started using the device without any changes to the BIOS.  Ubuntu loaded the nouveau driver. It took a little work to install the proprietary driver, as the "Driver Manager" application in 14.04 couldn't find a match.  I ended up using the [xorg-edgers PPA]("http://askubuntu.com/questions/464354/update-nvidia-drivers-with-xorg-edgers-ppa") instead.

Have you tried the new ppa for nvidia?

 ```
sudo add-apt-repository ppa:graphics-drivers/ppa

sudo apt-get update && sudo apt-get install nvidia-355
```

---

### Post by snarkyCoder on 2015-11-15
> **deadflowr said:**
> That's usually about right.
Newer machines tend to have the video card detector function set to automatically use any externally added card; external being a card used for a pcie or other pci-type connection, if that makes sense.

Only one way to see, and that's to simply pop that baby in and connect it to a monitor.

If it's blank, turn off  the machine, change the connection from the new card to the old card, then turn it on and go to the BIOS (or UEFI) screen.
(BIOS/UEFI screen access should be explained on the first screen when you turn on the machine; that first screen that usually tells you what to press to get the boot menu. it usually also shows how to access the settings option)
Then look for the video settings and change it.
Then follow how to save the setting. Shutdown, and change the connections once again.

When it works, you might look at what nvidia drivers are readily available in the drivers section.
(As explained already)

And you need not worry one bit about the intel drivers.
Whether or not they are on the system will have no effect on the nvidia card.
(And you might be better off keeping them in case the nvidia card goes belly up.)

Thanks man! I will try it like that! 
Then report back :D

---

### Post by SeijiSensei on 2015-11-15
Actually I just reinstalled Kubuntu 14.04 on this machine and ran "apt-cache search nvidia".  There's now the nvidia-346 package in the repositories.  I just installed that with
```

sudo apt-get update
sudo apt-get install nvidia-346

```
and it is working fine with my 750 GTX. Some time back the 346 driver wasn't in the repository, and the 332 driver didn't work with this card.  I didn't need the xorg-edgers PPA this time around.

As always, I have to use a custom /etc/X11/xorg.conf file or else I get very tiny text fonts on my LG TV.  I imported the one I had before that I had created by first running "sudo nvidia-xconfig" and editing the file by adding
```

    Option         "DPI" "96x96"

```
to the "Monitor" section of xorg.conf. This problem seems endemic to NVIDIA on TVs.  I had it with my prior Sony model as well.  Using a regular monitor doesn't seem to have the same issues.

---

### Post by grahammechanical on 2015-11-16
@SnarkyCoder

Recovery mode is a little known feature that can be useful in fixing certain problems. In this case if the installation of a discrete video adapter and its driver does not go according to plan. The Recovery menu gives us these options
> 
resume - resume normal boot [that may be with a fall back open source video driver]
clean - try to create free space
dpkg - repair broken packages
failsafeX - run in failsafe graphic mode
grub - update grub boot loader
network - enable networking
root - drop to root shell prompt
system-summary

All useful stuff in certain situations. But not needed if we can get to a working desktop where we can open a terminal or a Linux console or Additional Drivers.

Regards.

---


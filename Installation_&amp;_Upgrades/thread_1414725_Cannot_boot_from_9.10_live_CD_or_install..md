---
title: "Cannot boot from 9.10 live CD or install."
date: 2010-02-23
forum: Installation &amp; Upgrades
---

### Post by Chris_cur on 2010-02-23
I have tried not to post my issue and find an answer myself but I have yet to get to a solution to my problem so I am giving in and making my own post.

I thank you all in advance.

I had issues installing Ubunut 9.10 on my Asus UX50 laptop but it installed perfectly on my tower. When installing 9.10 on my laptop I would get the live disc menu to try or install etc. Whenever I installed I got a big black screen for long lengths of time (each time varied from 15 minutes to 5+ hours), then on occasion I would get the glowy white Ubuntu logo, then if I was lucky, I would get scrolling code. It would scroll and scroll then stop. After the code stopped I would get the nice little blinking curser.  I can type all types of fun things at this black screen but nothing seems to work.

I have tried 4 different CDS to no avail, my tower had the OS installed by one of the same discs.

I am successfully running 9.04 on this laptop.

a command of :   lspci
gives me

> 00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation Device 06f1 (rev a1)
03:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
08:00.0 Ethernet controller: Attansic Technology Corp. Device 1063 (rev c0)From what I understand, my nVidia card may be the issue. So I have tried to boot in safe graphics mode and this also does not work. Safe mode directly delivers me to my black screen with my blinking curser.

I have also checked my drivers and I have no proprietary drivers installed.

Since I have 9.04 installed successfully does any one think that upgrading from Upgrade Manager would be successful?

---

### Post by byStanderone on 2010-02-24
...had googled a little bout this, and there seems to be some differences between mirrors, altho haven't find a guide as to where a particular mirror that would suit ones hardware spec. i guess some are lucky to pick a suitable one.

would say, why not try an upgrade, while having the option of downloading another mirror from another source...it is your choice of course.

---

### Post by davidryderuk on 2010-02-24
Hi,
I found the following thread written by someone with the same computer, which is probably relevant here.

[http://ubuntuforums.org/showthread.php?t=1308941](http://ubuntuforums.org/showthread.php?t=1308941)

In order to add the right option when booting from the livecd do the following:

1. When the livecd menu comes up click on F6.

2. Click on the Esc button (to get rid of the menu of boot options that appears).

3. You should be left with an editable list of boot options ending with "quiet splash --".

4. Add the option "i915.modeset=0" to the end of the list of boot options and hit return.

5. This should allow you to boot the live cd.

6. Once you have installed 9.10 you should reboot and take out the cd. 

7. Upon rebooting access the grub menu by holding down the shift key.

8. Hit the "e" key and then add the "i915.modeset=0" option to the end of the line.

9. Hit the "b" key to boot.

Once you have booted into your 9.10 install you can make the change to grub final by doing the following.

1. Open the grub file in gedit.

```
sudo gedit /etc/default/grub
```

2. Change the line

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```

to 

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i915.modeset=0"
```

3. Update grub

```
sudo update-grub
```

---

### Post by Chris_cur on 2010-02-24
Gah, I finally tried to update from Update Manager. Downloaded everything and now in the install I keep getting 

> process 23558: arguments to dbus_move_error() were incorrect, assertion "(dest)==NULL || !dbus_error_is_set ((dest))" faild in the file dbus-errors.c line 278

over and over and over again!!!

---

### Post by Chris_cur on 2010-02-24
Finished the upgrade, results.

Black screen and little blinking cursor in the top left corner again... GAH!!!

---

### Post by Chris_cur on 2010-02-24
> **davidryderuk said:**
> Hi,
I found the following thread written by someone with the same computer, which is probably relevant here.

[http://ubuntuforums.org/showthread.php?t=1308941](http://ubuntuforums.org/showthread.php?t=1308941)

You can follow these set of instructions to boot up karmic after having installed from the cd.



But if you want to have these settings permanently saved then your best off editing "/etc/default/grub"

i.e.

1. Open grub file in gedit.

```
sudo gedit /etc/default/grub
```2. Change the line

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```to 

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i915.modeset=0"
```3. Update grub

```
sudo update-grub
```

This fixed it!!! I have only tried it in low graphics mode though. :(  If I can boot in normal mode with this little fix.

---

### Post by Chris_cur on 2010-02-24
I have not found a way to change from low graphics mode. I even changed the nVidia drivers to version 185 this did not work.

On restart the grub change did not work. I still had to edit it in the boot menu.

???? This low res view is killing me!!!

any one?
anything?

---

### Post by Chris_cur on 2010-02-24
I still cannot up date the 
```
i.915.modeset=0
```I have tried to install the nvidia 195 driver and that did not install

When I restart I have to edit each time with the above code

I have to boot in low res mode and get the following
> 
(EE) Failed to load module "glx" (module does not exist, 0)
(EE) Failed to load module "nvidia" (module does not exist, 0)
(EE) No drivers available
Anything please??? I am starting to pull out my hair. I do not want to have to wipe my computer and do a new install of 9.04.

---

### Post by stephenmac7 on 2010-02-24
With the tower install the .iso to a usb using 'USB Startup Disk Creator', I think it is preinstalled on your computer. Then use that to install 9.10 to your laptop. Also you can do ```
sudo apt-get upgrade
``` on the laptop.

---

### Post by esclunatic on 2010-02-24
it may very well be a media/cd-rom problem,if one computer burns and reads the disc,where as the other does not.ive had a problem like this only after discovering
a dvd-rom drive in my closet,and hooking it up did i get a disc that was bootable,the other cdr`s i had on a recycled system failed to read,older perhaps..some older boot disc did work on the other cdr`s but for some reason(microsoft?multiread,outdated bios), they failed.until i tried the newer
dvd-rom drive.


its possible that this could be your  annoyance.

---

### Post by theozzlives on 2010-02-24
Try downloading the drivers from nVIDIA, boot to root prompt to install them. I had to do that with one of mine.

---

### Post by Chris_cur on 2010-02-24
9.10 is installed. That is not a problem any longer.

As I said earlier during the install I received numerous fails saying:
> process 23558: arguments to dbus_move_error() were incorrect, assertion "(dest)==NULL || !dbus_error_is_set ((dest))" faild in the file dbus-errors.c line 278

Every time I boot I still have to edit the boot and put:
```
i.915.modeset=0
```
 
as I was told to do earlier.

No version of the nVidia drivers have worked thus far. I either get:
> (EE) Failed to load module "glx" (module does not exist, 0)
(EE) Failed to load module "nvidia" (module does not exist, 0)
(EE) No drivers available
or 
> (EE) No device


@theozzlives
- How do i boot to root? I have only gotten to the command prompt line once and it was by completely stumble.

Thank you all!

---

### Post by davidryderuk on 2010-02-25
Sorry, I think this is a Grub versus Grub2 issue. On a fresh installation you run Grub2 (which is what is mentioned in my previous post) whereas on an upgraded system you run Grub.

In order to make any changes permanent on Grub you have to do the following:

1. Edit the menu.lst file.

```
sudo gedit /boot/grub/menu.lst
```

2. Find the following line.

```
# kopt=root=/dev/sda1 ro
```

and change it to

```
# kopt=root=/dev/sda1 ro i915.modeset=0
```

3. Update grub.

```
sudo update-grub
```

4. That should hopefully allow you to make the changes to grub permanent on an upgraded system.

I'm not quite sure about the low graphics mode problem. But one thing you could possibly try is the following.

1. Make sure that the propritory nvidia drivers are **not** activated.

2. Backup and remove the xorg.conf file. When you do this 9.10 should hopefully setup xorg with the default settings. 

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

Reboot and see if this solves your low graphics problem. If your graphics are worse than before you can reverse the changes by running the opposite of the command in 2.

```
sudo mv /etc/X11/xorg.conf.bak /etc/X11/xorg.conf
```

By the way you can run a command as root by simply adding sudo to the front of a command in terminal. It's not recommended unless you understand what the command does (that probably goes my instructions as well).

---

### Post by Chris_cur on 2010-02-25
@david

I do not have that line to replace
```
# kopt=root=/dev/sda1 ro
```This is the closest

```
## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=3549c2d6-d112-4b02-a1da-206e6ddac873 ro
```Is the above where I am supposed to change it? I will not mess with it yet. I will try out the low graphics solution you have presented though.

Thanks again!

---

### Post by Chris_cur on 2010-02-25
Messing with the xconfig does not work either...

---

### Post by Chris_cur on 2010-02-25
I am going to go back to 9.04. Thanks for all the help.

---

### Post by davidryderuk on 2010-02-25
Okay.
Hope you have better luck when the next version of Ubuntu comes out.

---

### Post by Chris_cur on 2010-02-25
Thanks everyone for all the help!

I am looking forward to trying out the new version later.

---


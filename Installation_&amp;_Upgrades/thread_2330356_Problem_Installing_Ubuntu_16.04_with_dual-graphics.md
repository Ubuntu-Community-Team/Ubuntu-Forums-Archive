---
title: "Problem Installing Ubuntu 16.04 with dual-graphics system (i7-4790K/GTX 960)"
date: 2016-07-10
forum: Installation &amp; Upgrades
---

### Post by cubdukat1968 on 2016-07-10
I recently attempted to install Ubuntu 16.04 on my system, but I have run into a problem that I have never faced before.

The computer is set up with two monitors: a 55" TV being driven via HDMI by a GTX 960, and a smaller 23" Samsung monitor being fed by the Intel graphics over DVI. I had to set the system up this way in order to be able to use QuickSync with several Windows video encoders.

Using both a USB stick and a live DVD, I was able to boot into the login screen, but the problems began right there. The Intel monitor had no image, and the 960-driven TV flashed on and off constantly, and was slow to respond to any inputs. I eventually had to physically uninstall the 960 and install Ubuntu with Intel graphics.

What steps do I need to take in order to install 16.04 so that the flashing problem is solved and I can have both displays working, or at the very least the primary one (the 960) working? I need to keep the 960 in the system so that I can use it with Blender.

---

### Post by MAFoElffen on 2016-07-11
XServer is simplified when you are using one type of driver at a time. But they will work, if you manually give it hints of where things are and what each uses as drivers.

Disconnect the monitor from your hdmi port going to your Intel GPU. On Boot, at the Grub Boot menu, <arrow-down><Arrow-up> to stop the timeout counter. 
Press <E> key to get into Edit Mode.
<Arrow-down> until you get to the line starting with the text "linux".
<Arrow-right> to the end of that line and append the text "nomodeset".
<Cntrl><X> to boot.

Go to settings > Software > Additional Drivers ... to install an appropriate driver for your NVidia Card.

Reboot. Start your "NVidia Control Center" to Configure anything you want, such as Preferred Resolultion. Have it create / write your /etc/X11/xorg.conf file.

After you have it create your xorg.conf file, start a terminal:
```

sudo lspci | grep -i VGA

```
Write down the output of the bus addresses of your two gpu's

Once you have that info
```

sudo gedit /etc/X11/xorg.conf

```
In the editor, copy / paste the Device section, to point your second device to the intel driver.
Ensure the original section points the nvidia driver to the bus address of the NVidia GPU.

In the second Device section that you pasted, change the device ID so that it is "different", like increment the number in it, so it is a unique ID. Change the driver name to "intel". Change the buss address to where it is located in the bus. Strip all the other lines of that section.

If you are not sure of what you are doing ... post the output of the bus address ... and your xorg.conf file ... both within Code Tags ... and I will show you what to edit where.

The gist of it, is that you show XServer where your GPU's are located and make the connection of which driver should be used for each. Once that is done, then they can coexist and play nice with each other. Then  you can tweak your settings for each.

---


---
title: "HOW-TO: Configure your PilotMouse bluetooth via DBT-120 USB dongle"
date: 2005-04-14
forum: Installation &amp; Upgrades
---

### Post by magicfab on 2005-04-14
This is a brief report about what worked for me. I have an Averatec 3250HX laptop to which I added a D-Link DBT120 USB bluetooth dongle and a Kensington bluetooth PilotMouse. This may work with other laptops / dongles / mice. Part of this is based on [this thread](http://ubuntuforums.org/showthread.php?t=21723) and [this one](http://ubuntuforums.org/showthread.php?t=22464) too.

You will need to activate the Universe repository and make sure you install the following packages:
- gnome-bluetooth (for a GUI to find out your mouse address)
- bluez-utils (for hcid)

Once gnome-bluetooth is installed, two new utilities will show up in the **Applications | System Tools** menu. Launch **Bluetooth manager**.

In the **Devices** menu, choose **Scan**. You should pay close attention to what will follow, as your mouse is "discovered" its address will be displayed in the status bar. The application froze some times before I could get detection of the mouse and actually write down the address. In my case the address was 00:0a:3a:02:1d:dc . This address will be used to connect to the mouse.

Open a root terminal window (**Applications | System Tools | Root Terminal**) and  execute the following commands **after making sure you' ve pressed the connect button under the mouse**:

```
modprobe hidp
hcid
hidd --connect aa:bb:cc:dd:ee:ff
```
Of course replace the "aa:bb..." string with your mouse address. At this point I had a cursor and could use my mouse. I also tested the scrolling wheel and it worked fine.

Apparently the mouse will be disconnected everytime you reboot and you would need to repeat the past commands. To have this setup permanently active, in the same root terminal window, edit the **/etc/default/bluez-utils** files so it contains the following lines, uncommented:

```
HIDD_ENABLED=1
HIDD_OPTIONS="-i 00:0A:3A:02:1D:DC --server"
```
With this mouse I noticed if I don' t use it for while the connection is lost, however if I press briefly on the left button, it will reconnect automatically.

Hope this saves other people time as much as the other combined posts did for me. Feel free to comment if I missed something!

---


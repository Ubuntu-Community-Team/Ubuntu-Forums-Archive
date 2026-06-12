---
title: "Lost X and ethernet after upgrade"
date: 2006-06-02
forum: Installation &amp; Upgrades
---

### Post by setdosa on 2006-06-02
Hi All,
   I just upgraded my hoary to drake and I lost my X server and ethernet capabilities. I upgraded by changing all the breezy to drake in /etc/apt/sources.lst. I was running the installation in runlevel 2.

    The X servers fails saying that nvidia module is not there, but when I do lsmod nvidia is listed.

    About the ethernet, I did ifup eth0 and it says failed to open state file /var/run/network/ifstate and ethtool eth0 says

      settings for eth0:
      cannot get device settings: No such device
     cannot get wake-on-lan-settings: No Such Device
    cannot get message level: No Such Device
     cannot get link status: : No Such Device
     No data available

     lspci gives :
           0000:00:04.0 Ethernet controller: nVidia corporation nForceEthernet Controller
          0000:02:00.0 VGA compatoble controller: nVidia Corporation NVCRsh11 ]GeForce2 M X Integrated Graphics] (rev b1)

       What are these 0000:02:00.0 numbers and what do they signify.

Thanks for your help.
Arun

---

### Post by GQed76 on 2006-06-02
The X server is most likely failing due to a driver with your video card

Try editing your xorg.conf

```
sudo gedit /etc/X11/xorg.conf
```


look for the area saying

Section "Device"
Identifier "NVIDIA ""
Driver "nvidia"
BusID "PCI:1:5:0"

And in the Driver area, replace nvidia (or whatever driver it is) with VESA. Save and try again


If you get into X then you can look into reinstalling the NVIDIA driver

---

### Post by heffo_j on 2006-06-02
I have the same problem, but my upgrade to Dapper is built upon hoary to breezy.

I too can't get the x to fire up (my laptop does not run the nvida card though). And I have the same eth0 problem. However my atheros wireless card is okay.

I'll give the steps listed above a go.

Thanks for the help.

ps thank goodness my Windows still works. (sorry).

---

### Post by heffo_j on 2006-06-02
It won't allow me to open gedit. Any other ways to edit the file?

Thanks you.

John

---

### Post by setdosa on 2006-06-03
I know what you are saying john, vi doesnt work either. Use /usr/bin/vim.basic instead. 

Arun

---

### Post by skelooth on 2006-06-03
personally i like to use nano for command line editing of conf files.... also when in doubt...

apt-get install lynx
apt-get install nano

that's all you need to get out of almost any hairy situation.

---

### Post by setdosa on 2006-06-03
Thanks GQed76 for responding. I did what you asked me to do the system hangs after startx.

/var/log/Xog.0.log ends abruptly with these 2 warnings
1. The directory /usr/share/X11/fonts/cyrillic doesnt exist. Entry deleted from font path.
2. The directory /usr/share/X11/fonts/CID doesnt exist. Entry deleted from font path.

also modprobe vesa says module not found.

Thanks again.

---


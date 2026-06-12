---
title: "Network issues with Ubuntu 64 bit"
date: 2010-02-14
forum: Installation &amp; Upgrades
---

### Post by YBYNTU on 2010-02-14
I've just installed 64 bit Ubuntu, install went seamless but I cant get a network connection, it shows as disconnected.
It was working fine with 32 bit Ubuntu, it just worked nothing to install.
 
Help please

---

### Post by efflandt on 2010-02-14
You have given no clue what type of network device (and output related to it from **sudo lspci -v** if built-in, or **sudo lsusb -v** if USB).

Are you sure the plugs are in tight?

Of course if it is wireless you have to configure a connection for it, and may need to set Auto eth0 to NOT connect automatically.

---

### Post by YBYNTU on 2010-02-15
I have and Asus motherboard with two integrated network ports - both Nvidia. Cables are all secure. 
I can't iunderstand why it worked straight away with 32Bit. I'm completely new to Linux, so sorry if I'm a bit vague.

---

### Post by darkod on 2010-02-15
> **YBYNTU said:**
> I have and Asus motherboard with two integrated network ports - both Nvidia. Cables are all secure. 
I can't iunderstand why it worked straight away with 32Bit. I'm completely new to Linux, so sorry if I'm a bit vague.

Most wired (ethernet) connection work straight away. Are you connecting it to a router? Cable modem? Does the light on the other device turn on to show you have a cable connection?
Are the lights on the network port on your PC on?

---

### Post by YBYNTU on 2010-02-16
Its connected to my router, I know the connection is working fine. If I boot to Windows 7 everything works.
 
I might put 32bit back on but I want to take advantage of my 8GB of RAM and I'd like to get to the bottom of the problem.

---

### Post by darkod on 2010-02-16
> **YBYNTU said:**
> Its connected to my router, I know the connection is working fine. If I boot to Windows 7 everything works.
 
I might put 32bit back on but I want to take advantage of my 8GB of RAM and I'd like to get to the bottom of the problem.

Do you get the Network Manager icon in the top right? If you right click on it and select Connection Information, does the IP information look OK?

Also, in firefox can you open your router web config, usually on 192.168.1.1?

---

### Post by YBYNTU on 2010-02-16
> **darkod said:**
> Do you get the Network Manager icon in the top right? If you right click on it and select Connection Information, does the IP information look OK?
 
Also, in firefox can you open your router web config, usually on 192.168.1.1?
 
The network manager is there, no IP shows it tells me that I'm disconnected but the cable is secure and LAN port LEDs are on.

---


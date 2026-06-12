---
title: "Installing 7.10 - 'failed to start X server' error"
date: 2007-10-28
forum: Installation &amp; Upgrades
---

### Post by davlaw2000 on 2007-10-28
Hi all I hope you can help. I have done a clean install of 7.10 on a spare PC. It has a PCI Express Nvidia GeForce 6200 in it and an AMD Sempron 3000+ cpu. The installation itself went fine, so then I went into the 'desktop effects' option and it told me I needed to enable the Nvidia Driver. So I ticked the 'enable' box and it told me I needed to re-start so I did. 
After the re-start, I went back into Desktop Effects and the driver still wasn't enabled, so I was in a bit of a loop. 
I decided to go into the 'Restricted Drivers' option, and sure enough there was an entry for an Nvidia driver but again it wasn't enabled. When I tried to enable it, something got downloaded and installed, then I was told a restart would be necessary so I did. 
Now when the computer starts up, I get to a blue screen with a white square in it. A message say 'Failed to start the X Server......it is likely that it is not set up correctly.....'
Please can anyone advise on how to resolve this? I did look through other posts before I posted this, but none seemed to match my situation.  
I did try the command to reconfigure X, and that went through quite a long series of screens, asking me all kinds of questions which I tried to answer as best I could, but at the end of it, after re-booting the pc, exactly the same error came back again. 

Any help would be much appreciated!

---

### Post by kiepmad on 2007-10-28
Hey!

When you get the message, press CTRL+ALT+F1. You then get into a terminal window. Login with your account. Next type, without quotes, 'sudo apt-get remove nvidia-glx-new'. After that you type 'sudo reboot'. 

You have now uninstalled the restricted driver you installed before. I hope you can get then back in your system and try again to install restricted drivers, by using the add/remove programm from your applications menu.

---

### Post by taurus on 2007-10-28
Or edit /etc/X11/xorg.conf

```
sudo nano -Bw /etc/X11/xorg.conf
```
and replace the "**nvidia**" with "**nv**".

Save it with <Ctrl>o and exit with <Ctrl>x.  Reboot and see what happens now.

```
sudo shutdown -r now
```

---


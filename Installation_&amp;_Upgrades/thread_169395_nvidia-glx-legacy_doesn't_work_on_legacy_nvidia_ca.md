---
title: "nvidia-glx-legacy doesn't work on legacy nvidia cards"
date: 2006-05-02
forum: Installation &amp; Upgrades
---

### Post by general_error on 2006-05-02
```
root@bonehead:/home/grishnoc# apt-get install linux-restricted-modules-2.6.12-9-386
Reading package lists... Done
Building dependency tree... Done
linux-restricted-modules-2.6.12-9-386 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 85 not upgraded.

root@bonehead:/home/grishnoc# apt-get install nvidia-glx-legacy 
Reading package lists... Done
Building dependency tree... Done
nvidia-glx-legacy is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 85 not upgraded.

root@bonehead:/home/grishnoc# apt-get remove nvidia-glx
Reading package lists... Done
Building dependency tree... Done
Package nvidia-glx is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 85 not upgraded.

```

So nvida-glx-legacy is install and nvidia-glx is not.  When I restart X I see this in dmesg:

```
[4306925.013000] NVRM: The NVIDIA GeForce2 Ti GPU installed in this system is
[4306925.013000] NVRM:  supported through the NVIDIA Legacy drivers. Please
[4306925.013000] NVRM:  visit http://www.nvidia.com/object/unix.html for more
[4306925.013000] NVRM:  information.  The 1.0-7667 NVIDIA driver will ignore
[4306925.013000] NVRM: No NVIDIA graphics adapter found!
```


I have a 
```
root@bonehead:/home/grishnoc# lspci |grep VGA
0000:01:00.0 VGA compatible controller: nVidia Corporation NV15DDR [GeForce2 Ti] (rev a4)
```

---

### Post by general_error on 2006-05-02
I rebooted and have no nvidia messages in dmesg now... but i didn't get the nvdia splash screen and when I try to run glxinfo I get the following message:

```
grishnoc@bonehead:~$ glxinfo |grep -i direct
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
```

---

### Post by tonyr on 2006-05-02
Look at this:
[URL="http://doc.gwos.org/index.php/Latest_Nvidia_Dapper"]
http://doc.gwos.org/index.php/Latest_Nvidia_Dapper[/URL]

I think that the part you are missing is the part about **nvidia-xconfig**.
Make a backup copy of /etc/X11/xorg.conf, then
```

sudo apt-get install nvidia-xconfig
sudo nvidia-xconfig

```

Are you using a really early version of Dapper (6.02)?  If so, you should really
get the Dapper Beta and install that.

---


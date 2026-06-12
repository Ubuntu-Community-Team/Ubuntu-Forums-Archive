---
title: "Out range scale at installating ubuntu server"
date: 2022-11-21
forum: Installation &amp; Upgrades
---

### Post by sourc32 on 2022-11-21
Hi everyone!
It's my first time posting here, sorry for my english or inexperience.
Im trying to revive an old server to use as wiki-repository for our job, in the first try I got a error with Ubuntu server (that was my first distro option because there is a lot info on internet) ``Out range scale´´  after the installation. I tried all I saw on internet and I didnt got nothing. After that I tested with Opensuse and for now is the only distro without this problem (I supposed is for VGA and old connections). 
That's for now.
Then I tried to install dokuwiki, ssh, xampp etc and that's the point i got mad, all the tutorials and info is for ubuntu or debian distribution and Im very very noob to repair something for myself.
I had broke all, the DNS (I thought is for dnsmasq), the file manager on dokuwiki, the log system, etc. And all the problems (sendmail, network manager, etc), all is for ubuntu, I got very mad so I want to try the ubuntu server installation again.
But first I need to know If you know how to resolve this, I had read about boot-repair, and I have other PC to make a ssh if the resolution is other time out range(I dont know if the distro come with ssh activated)
You are my last oportunity, thanks in advance!

---

### Post by grahammechanical on 2022-11-21
The out of range error means that the operating system is outputting video at a resolution and frequency that is outside the range of settings that the monitor uses. What are the video settings that the monitor can use? What video adapter does this machine have? What ranges can it output? I assume that you are using a VGA connection between machine and monitor.

The Ubuntu Server edition is a command line operating system. It does not have a Graphical User Interface (GUI) or Desktop Environment (DE). It does not need to output high resolution video to the monitor. Here are the instructions for installing Ubuntu Server edition.

[https://ubuntu.com/server/docs/install/step-by-step](https://ubuntu.com/server/docs/install/step-by-step)

Connecting the server installation via ssh

[https://ubuntu.com/server/docs/install/general#connect-via-ssh](https://ubuntu.com/server/docs/install/general#connect-via-ssh)

[https://ubuntu.com/server/docs/installation](https://ubuntu.com/server/docs/installation)

Regards

---

### Post by sourc32 on 2022-11-22
Thanks in advance! I will test to install and connect via ssh, I dont need to use the monitor if SSH works. I dont know the graphic card or the monitor resolution..best regards!

---

### Post by MAFoElffen on 2022-11-22
It is still susceptible to an "Out of range error". if connected to a display that does not return the EDID. Because even though it looks like it is in a text mode, it adds enriched pseudo vga graphics "Rich Text Mode"...No problem...

On boot of the Live Installer media, and the first boot, delete "quiet splash" from the boot line (that begins with 'linux", and at the end of that same line, append:
```

-- 3

```
On that first boot, after the install, edit the /etc/default/grub file (with sudo privileges) and add those options to 
```

GRUB_CMDLINE_LINUX_DEFAULT="-- 3"

```
and uncomment the line
```

GRUB_TERMINAL=console

```
After saving, then do
```

sudo update-grub

```
Alternately, you could set a framebuffer KMS mode of the resolution you know that display has... refer to the 1st post of my graphics resolution sticky in my signature line, and the server graphics links in the second post of that sticky. If you run the UbuntuForums 'system-info" script, also in my signature line, I'll recommend a boot parameter for you for that...

---


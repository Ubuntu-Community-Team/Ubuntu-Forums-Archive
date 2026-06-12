---
title: "After Login I can't use Kubuntu anymore"
date: 2012-05-03
forum: Installation &amp; Upgrades
---

### Post by SoggyCornflake on 2012-05-03
My wife likes the default Ubuntu desktop (Gnome?) while I perfer the kubuntu desktop (KDE).  For years I've been able to use the default installation and then add KDE and we're both happy.  After the latest upgrade, I find that KDE is non-responsive after logging into it.  I have to reboot and then log in using the Ubuntu choice.  By the way, the Ubuntu 3D login fails too - in a slightly different way.  It generates a text box with lots of errors and then conpriz (or whatever it's called) crashes.

Does anybody know what to do to get Kubuntu running happily again?

---

### Post by carl4926 on 2012-05-04
Sounds like a graphics issue
Look and see if you need to install/upgrade your graphics driver

---

### Post by SoggyCornflake on 2012-05-06
I'm feeling a. It like the Sorceror's Apprentence right now.   Thinking that I needed to upgrade my NVidia driver, I went straight to NVidia and downloaded what I thought was the correct driver script from thier site.  I rebooted and selected the recovery mode option where I dropped  into a command shell.  I ran the script which created the driver module and the new configuration.  after rebooting and not seeing anything come up, I returned to the recovery mode and went back to the command shell.  When I ran startx, I got the following message:  API mismatch:  the NVIDIA kernel module has version 295.40,  but this NVIDIA driver component has version 295.49.   So can you tell me how to undo the damage I've done?

---

### Post by carl4926 on 2012-05-06
You can't really start installing the blob manually if you had already used synaptic.

You could chroot in to your system, run synaptic to repair the nvidia driver

---

### Post by SoggyCornflake on 2012-05-06
I can't really use Synaptic because from the command line I get can not open display.

---

### Post by carl4926 on 2012-05-07
If you use a live CD and boot it to a working Live desktop, it must be either 32 or 64 bit to match your actual installed system.

Now, just to be sure, run
```
sudo fdisk -l
```
And make a note of your installation partition (root), I'm going to assume your install is all in one partition, but some of us separate / (root) and /home.

So let's say your / is /dev/sda1 (change the following as to your findings)

Now we need to mount the filesystem to /mnt

```
sudo mount /dev/sda1 /mnt
```

    * Now mount the rest of your devices

```
sudo mount --bind /dev /mnt/dev
```

    * Now chroot into your system

```
sudo chroot /mnt
```

Now you can use synaptic or apt-get to manage your installation

---

### Post by SeijiSensei on 2012-05-07
Let's try a simpler approach first since you're able to boot into recovery mode.  After you drop into the root shell, try running these commands

```

apt-get purge nvidia-*
apt-get install nvidia-current
nvidia-xconfig

```

The purge command may come up empty; if so, that's fine.  Now reboot and see how things work out. I'm hoping that this will overwrite the driver module that you tried to install from NVIDIA with the ones from the repository.  If this doesn't fix the problem, we might have to root out the stuff you installed from the NVIDIA site.

I don't know how you're connected to the network, but if you don't have network connectivity when you're in the shell, the easiest solution is to use a wired connection.  If you have a spare Ethernet cable, plug it in to your router.  If you know your local subnet address, say 192.168.1.0/24 which is a common default, then you can set up networking manually like this:

```

ifconfig eth0 192.168.1.100 netmask 255.255.255.0 broadcast 192.168.1.255
ip route add default via 192.168.1.1

```

where 192.168.1.1 is the router's LAN address.  Once you've done this you should be able to ping the router; if that works try pinging the Google DNS server at 8.8.8.8.  If you still cannot connect to the Internet, then you should fall back on Carl's suggestion above and use the Ubuntu CD.

For the NVIDIA driver, I've found it's always safest simply to run the Additional Drivers application in the Ubuntu menus, or just install nvidia-current from the repositories with apt-get.  It's a very rare circumstance where you would need to install anything that's not in the repositories.  The only times I've done so is when I wanted to use some features in a cutting-edge version of a program in rapid development like mplayer.  In those cases I've compiled the binary from source.  In the case of the NVIDIA driver, though, I've never used anything other than what's available in the repositories.  This method also ensures that the driver will be updated automatically whenever necessary.

---


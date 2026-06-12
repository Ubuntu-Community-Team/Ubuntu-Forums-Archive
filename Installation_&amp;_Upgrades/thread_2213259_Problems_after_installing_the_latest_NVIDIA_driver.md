---
title: "Problems after installing the latest NVIDIA driver for Ubuntu 13.10 and rebooting"
date: 2014-03-25
forum: Installation &amp; Upgrades
---

### Post by abraham4 on 2014-03-25
I installed the NVIDIA driver version 331 through the terminal and decided to reboot. When I came back to check if it did I was surprised by a window saying that there is a problem with the graphics card and gave me the option to configure it, to use a generic one, or to troubleshoot and none of those options worked. I have no idea what to do or if this can be fixed...

This is exactly what the it said:
[B]
The system is running in low-graphics mode [/B]
Your screen, graphics card, and input device settings could not be detected correctly. You will need to configure these yourself.

---

### Post by kc1di on 2014-03-25
First of all what Nvidia card are you using?  not all cards will work with the 331 driver.

boot to a root terminal and type the following:
```
lspci 
``` and list the output here.

you can remove the nvidia-331 from the terminal by typing :
```
sudo apt-get remove nvidia-331
```

Then install nvidia current with the command :

```
sudo apt-get install nvidia-current
```

---

### Post by abraham4 on 2014-03-25
It's GeForce 8600 GT

---

### Post by abraham4 on 2014-03-25
how do I get to the root terminal?

---

### Post by kc1di on 2014-03-25
you can get to a root shell when the grub boot list comes up select ubuntu advanced then recovery mode. you'll be presented a list of options one of which will be root shell choose that one it will drop you to a root terminal line. you can preform the commands there.

---

### Post by abraham4 on 2014-03-25
i don't think it worked. 
Output: 
W: Not using locking for read only lock file /var/lib/dpkg/lock 
E: Unable to write to /var/cache/apt/
E: The package lists or status file could not be parsed or opened.

---

### Post by ajgreeny on 2014-03-25
In recent versions of Ubuntu, in recovery mode the filesystem is mounted as read-only, so  you need to enter the following command to get it to remount as  read-write, which will allow you to make changes: 
```
mount -o rw,remount /
``` and you also need to choose to boot to commandline with network access enabled
then continue with the commands shown by kc1di to remove the nvidia driver and reinstall a different version.

---

### Post by hamishmb on 2014-03-25
Ah, you aren't in read-write mode. The best way to fix this is boot to the recovery menu as described above and then select 'FSCK' or 'Check Filesystems' and then follow out the instructions given above.

Hamish

---

### Post by abraham4 on 2014-03-25
Still encountering the same problem

---

### Post by kc1di on 2014-03-26
Ok try this command after you've got it in Read Write as mentioned above. 
```
 rm -f  /var/lib/apt/lists/lock
 rm -f /var/lib/dpkg/lock
```
Then 
```
apt-get update
``` **(note you do not need the sudo at the front because you are already in a root shell.**)
Then run the commands to remove and reinstall Nvidia-current.

---

### Post by abraham4 on 2014-03-26
I'm sorry but it still doesn't work.

---

### Post by codenine75a on 2014-03-26
Just a question?  Did you use ubuntu's video drivers or nvidia's drivers.  When I had that video card I used to download nvidia's video drivers and install it in single console mode.

---

### Post by manishbhoola on 2014-03-26
If you are using the xorg edgers PPA, the problem is with the bumblebee package which blacklists the current nvidia drivers causing this issue. I had the same issues on my geforce 610 and followewed the instructions to uninstall and purge the bumblebee package after which everything works just fine. [http://askubuntu.com/questions/379504/problem-with-nvidia-driver-331-20-on-ubuntu-13-10-64bit](http://askubuntu.com/questions/379504/problem-with-nvidia-driver-331-20-on-ubuntu-13-10-64bit)

regards

---

### Post by abraham4 on 2014-03-27
Thanks manishbhoola! I followed the steps in your link and they worked. 

Codenine75a, before installing the nvidia drivers I was using an Ubuntu Gallium driver.

It appears the OS is running slower than before (it takes about 10 seconds for Firefox to open up and also when I'm downloading a program everything else become incredibly slow), I don't know if video drivers have anything to do with that or it's just my crappy computer.

---

### Post by manishbhoola on 2014-03-29
Do the upgrade to the latest ubuntu 14.04 beta. However before you do that, dont forget to use ppa-purge xorg-edgers and remove the extra ppa without which the upgrade fails. it has the latest NVIDA drivers too !

---


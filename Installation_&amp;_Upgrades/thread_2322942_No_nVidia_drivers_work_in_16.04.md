---
title: "No nVidia drivers work in 16.04"
date: 2016-05-01
forum: Installation &amp; Upgrades
---

### Post by stepheny on 2016-05-01
Using any nVidia driver results in a black screen on boot. In my opinion this is a very important issue that is being ignored. I am using a nVidia Optimus laptop and have been using Bumblebee since 9.04 (it had another name back then, I forget what it was), to switch between the intel and nVidia GPUs. Since "upgrading" to 16.04 not only does Bumblebee no longer work but if any nVidia driver is installed the GUI and Unity fail completely. Below is a solution if you find yourself locked out of your system because of this problem but a solution to the nVidia driver problem is needed urgently.

If you find yourself locked out of your system this is the solution that worked for me:

*) In the grub menu select the partition you want to boot and the press "e" and then replace 
```
....ro    quiet splash .....
```
with
```
....ro    nomodeset quiet splash .....
```
*) If that boots to the login screen, but keeps returning to the login screen press Crtl + Alt + F2, login, and then run 
```
sudo apt-get purge nvidia.* bumblebee
```
*) Reboot.

---

### Post by mc4man on 2016-05-01
I filed a hardware specific bug on no nvidia not working about a month ago, reasonably similar to what you see. Maybe take a read thru to see if the same.
[https://bugs.launchpad.net/ubuntu/+source/ubuntu-drivers-common/+bug/1565516](https://bugs.launchpad.net/ubuntu/+source/ubuntu-drivers-common/+bug/1565516)

If so try the 358 drivers which did work in a fashion, they're [still in the ppa]("https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa")
By 'in a fashion' is described in report - [https://bugs.launchpad.net/ubuntu/+source/ubuntu-drivers-common/+bug/1565516/comments/8](https://bugs.launchpad.net/ubuntu/+source/ubuntu-drivers-common/+bug/1565516/comments/8)

Edit: just to note I only was testing /trying with the default of  nvidia-prime

---

### Post by stepheny on 2016-05-02
Yes, you describe the problem very well. 

Whilst trying all possible drivers I installed 361-updates and after purging because it didn't work I booted into a GUi without a Unity sidebar ot topbar. No shortcuts worked so Ctrl-Alt-T didn't bring up a terminal but right clicking on the deskstop did, but without the usual close button etc. I tried restarting Unity and other solutions I found online but nothing worked. Eventually I had to restore via Clonezilla. I don't feel much like messing with this any more until Ubuntu announce a fix.

Also the 16.04 software app cannot handle third party software such as Chrome or Skype. [Bug report here.]("https://bugs.launchpad.net/ubuntu/+source/gnome-software/+bug/1573206")

How a LTS can be so broken weeks after release is very sad indeed.

---

### Post by rickrobs on 2016-05-02
I had the same problem.  Couldn't boot with NVidia Drivers enabled.  

Ctrl + Alt + F1 to F7 would bring you down to the respective TTY, but you coudln't do anything because it would throw the error "a start job is running for hold until boot process finishes up"

tty8 worked, though.  

It turns out it was a bug in GDM-- 

if you want to continue to use the NVidia driver, try switching to LightDMenabled me to boot with the NVidia Driver enabled.  

```

sudo dpkg-reconfigure lightdm

```

---

### Post by stepheny on 2016-05-03
I think Ubuntu 16.04 uses LightDM as default.
Running
```
cat /etc/X11/default-display-manager
```
on my install gives
```
/usr/sbin/lightdm
```

---

### Post by stepheny on 2016-05-06
I have finally got Bumblebee working with a nVidia driver on 16.04. The only driver I've managed to get to work is the nvidia-364, from ubuntu graphics ppa. Here is what I did:

First get purge all existing nVidia drivers and Bumblebee with
```
sudo apt-get purge nvidia* bumblebee
```
and the reboot the system.

Then install nvidia-364 from the repository ubuntu graphics ppa
```
sudo add-apt-repository ppa:graphics-drivers/ppa

sudo apt-get update

sudo apt-get install nvidia-364

sudo apt-get install bumblebee bumblebee-nvidia primus linux-headers-generic

sudo systemctl enable bumblebeed
```

Add the follwing two lines to /etc/modules:
```
i915
bbswitch
```

Then run
```
sudo prime-select intel
```

Finally edit /etc/bumblebee/bumblebee.conf

In line 22 change Driver= to Driver=nvidia and on lines 55, 58 and 61 change nvidia-current to nvidia-364.

Then reboot and run 

```
optirun glxgears
``` 

to see if everything is working.

---

### Post by jag-f on 2016-05-28
@stepheny

You're the only one who has hit the nail on the head out of tons of false advice on the net.

Thanks.

Jag

---

### Post by vbdanl-yahoo on 2016-07-11
I have been having problems trying to get nvidia to working with 16.04.  followed your instructions.
my Display shows "built-in display" and resolution is 1280x1024 which is not good for 24" dell monitor.
the optirun glxgears command returns "the bumblebee daemon has not been started yet or the socket path was incorrect"
could not connect to bumblebee daemon.. is it running?
should i remove the xorg.conf file ?  think i ran something earlier that populated it.. before running your post commands.  thanks for your help !

---

### Post by ac2334 on 2016-12-21
having same issue as vbdanl-yahoo

---

### Post by ac2334 on 2016-12-29
Has anyone gotten any further with this extremely frustrating issue? If lightdm is causing the issue, could there be any workaround?

---

### Post by LordOfRuin on 2017-06-17
Removed as solution found.

---

### Post by LordOfRuin on 2017-06-21
Removed due to Mods Advice

---


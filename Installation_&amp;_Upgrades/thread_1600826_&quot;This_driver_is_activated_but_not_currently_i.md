---
title: "&quot;This driver is activated but not currently in use&quot;"
date: 2010-10-19
forum: Installation &amp; Upgrades
---

### Post by Qvark on 2010-10-19
Hi! After installing 10.10 I get this error in the Additional Driver application. At the same time compiz has revertet to using the "no effects" setting which is very annoying. I have tried a complete reinstall of the NVIDIA drivers, both the nvidia-current and the latest one from nvidias homepage. Nothing works.

---

### Post by sikander3786 on 2010-10-19
Did you install all the updates from update manager?

See this bug post if it helps.

[https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/539997](https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/539997)

Also, post the output of

```
sudo lshw -C display
```

---

### Post by Qvark on 2010-10-19
Thanks for the fast answer!

Yes, everything is updated. 

Sorry, I'm nor really sure have to interpret that bugreport. 

  *-display               
       description: VGA compatible controller
       product: G92 [GeForce 8800 GT]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:fd000000-fdffffff memory:d0000000-dfffffff memory:fa000000-fbffffff ioport:cc00(size=128) memory:fe9e0000-fe9fffff

---

### Post by sikander3786 on 2010-10-19
The problem might be that your system as 2 nvidia drivers installed at the same time. Can you remove both of them, the one's from Additional Drivers and also the one's that you installed from the manufacturer's website. Reboot and then install the recommended ones from Additional Drivers?

The open source nvidia driver might also be causing problems but before getting there, if the above one didn't work, try this.

From terminal try to backup your xorg.conf and then reconfigure your graphics.

```
cd /etc/X11
```

```
sudo cp xorg.conf xorg.conf.old
```

```
sudo rm xorg.conf
```

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by Qvark on 2010-10-19
The only drivers I found in additional drivers where the nvidia current. When I uninstalled them and used the "NVIDIA-Linux-x86_64-260.19.12.run --uninstall". When I restarted I booted into the commandline instead of a GUI. I had to start in recoverymode and install nvidia-current from there (from the commandline because the "additional drivers" was empty) but the problems persists. When I installed the drivers I got some error messages though.

warning, in file '/var/lib/dpkg/status' near line 41821 package 'virtualbox-3.0':
 error in Version string '3.0.12-54655_Ubuntu_karmic': invalid character in revision number
warning, in file '/var/lib/dpkg/available' near line 46766 package 'virtualbox-3.0':
 error in Version string '3.0.12-54655_Ubuntu_karmic': invalid character in revision number
Selecting previously deselected package nvidia-current.
(Reading database ... 213282 files and directories currently installed.)
Unpacking nvidia-current (from .../nvidia-current_260.19.12-0ubuntu1~xup1_amd64.deb) ...
Processing triggers for man-db ...
warning, in file '/var/lib/dpkg/status' near line 41821 package 'virtualbox-3.0':
 error in Version string '3.0.12-54655_Ubuntu_karmic': invalid character in revision number
warning, in file '/var/lib/dpkg/available' near line 46766 package 'virtualbox-3.0':
 error in Version string '3.0.12-54655_Ubuntu_karmic': invalid character in revision number
Setting up nvidia-current (260.19.12-0ubuntu1~xup1) ...
warning, in file '/var/lib/dpkg/status' near line 41821 package 'virtualbox-3.0':
 error in Version string '3.0.12-54655_Ubuntu_karmic': invalid character in revision number
warning, in file '/var/lib/dpkg/available' near line 46766 package 'virtualbox-3.0':
 error in Version string '3.0.12-54655_Ubuntu_karmic': invalid character in revision number

Edit: I tried the second solution as well, no dice I'm afraid.

---

### Post by sikander3786 on 2010-10-19
Were you able to update the repository information with all those errors? Did you install any package successfully previously with those errors?

You've got some non-existing lines in /var/lib/dpkg/

Try

```
sudo dpkg --clear-avail
```

to clear them and then,

```
sudo apt-get update
```

```
sudo apt-get upgrade
```

Now remove the .run drivers package and reinstall the same or the one from Additional Drivers. It should be listed now.

Hope it helps this time.

---

### Post by efflandt on 2010-10-19
Did you notice that all those errors seem to refer to **package 'virtualbox-3.0'** not nvidia drivers.  Deja vu.  I have seen that in another post awhile back, but would have to search for it.

---


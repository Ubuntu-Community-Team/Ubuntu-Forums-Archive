---
title: "No Graphics after reconfigure xserver"
date: 2014-10-26
forum: Installation &amp; Upgrades
---

### Post by nasim3 on 2014-10-26
Hi dear users

after enter two command:

sudo dpkg-reconfigure xserver-xorg

and

sudo apt-get upgrade ATI

my ubuntu no start and only apear one black screen.
can you help me that solve this problem?
thanks a lot.

ubuntu:12.04.05
my graphics: ATI radeon.
laptop:HP-Pavilion dv6

---

### Post by nasim3 on 2014-10-27
can you help me? :(

---

### Post by grahammechanical on 2014-10-27
Why did you use the command?

```
apt-get upgrade ATI
```

I am not aware that apt-get upgrade can be used to upgrade individual packages. There is much that I do not know but after reading the Ubuntu wiki about apt-get and the apt-get man pages I am sure the command that you used is not a valid apt-get command.

> **upgrade**
           upgrade is used to install the newest versions of all packages currently installed on the system from the sources enumerated in  /etc/apt/sources.list. Packages currently installed with new versions available are retrieved and upgraded; under no circumstances are currently installed packages removed, or packages not already installed retrieved and installed. New versions of currently installed packages that cannot be upgraded without changing the install status of another package will be left at their current version. An update must be performed first so that  apt-get knows that new versions of packages are available.


From the man apt-get command.

[https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)

If you wish to install a proprietary video driver then try these commands

```
 ubuntu-drivers list
```

that should list all the drivers available for your system.

```
ubuntu-drivers devices
```

that will tell what graphic adapter you have and what drivers are available for it.

```
ubuntu-drivers autoinstall
```

that will install a proprietary video driver for your system. I know this works on 14.04 because I experimented with these commands myself but I have not tried with 12.04.5.

Regards.

---

### Post by nasim3 on 2014-10-27
thank you [**[COLOR=#000000]grahammechanical[/COLOR]**]("http://ubuntuforums.org/member.php?u=1087323")

these codes no work on 12.04 ubuntu.

---

### Post by Bashing-om on 2014-10-27
nasim3; Hello;

If you wish to install a proprietary video driver in release 12.04 there is a utility to do this.

[color=red]IF[/color] there is currently no driver installed from a PPA, try ->
Left side of screen is the launcher ->ubuntu Software Center ->Software Sources(edit menu option on top task bar) ->Additional Drivers (tab in Software Sources) [must have 'net connectivity ]//assumes that 3rd party software sources have been enabled in the Software Sources ! // Install the recommended driver.

[INDENT][INDENT]there is a way unto man that seems right, but
[/INDENT][/INDENT]

---

### Post by nasim3 on 2014-10-28
thanks bashing-om for reply.

i access only to terminal. 

how i can do your answer?

---

### Post by Bashing-om on 2014-10-28
nasim3; Good day ;

One may install the proprietary driver from terminal.
1st, however, if there exists any other driver, it must be removed prior to attempting to install another;

Show the results of terminal command:
```

dpkg -l | grep fglrx

```
and we will proceed to remove these and next install the driver.

[INDENT][INDENT]no step for a stepper
[/INDENT][/INDENT]

---

### Post by nasim3 on 2014-10-28
after enter this command:
dpkg -l | grep fglrx

nothing shows.

What command do I install my drivers?

thanks a lot ^_^

---

### Post by Bashing-om on 2014-10-28
nasim3l OK;


This code is ONLY good IF your ATI card is a later release than the 4X series  !! Else there is no Proprietary driver available for the card, and trying to install a driver for the legacy card will NOT work.
```

lspci -nnk | grep -iA3 vga

```
IF you have the later cards, then to install the proprietary driver, do terminal commands:
```

sudo apt-get install linux-headers-generic
sudo apt-get install dkms
sudo apt-get install fglrx fglrx-amdcccle fglrx-modaliases
sudo amdconfig --initial

```
Reboot for the change to take effect.

Are you now up and running with better graphics ?

[INDENT][INDENT][INDENT]it could happen
[/INDENT][/INDENT][/INDENT]

---

### Post by nasim3 on 2014-10-29
these packages : linux-headers-generic  fglrx fglrx-amdcccle, are already installed.
after enter
sudo apt-get install fglrx-modaliases
This message comes: is not available.
and after enter
sudo amdconfig --initial This message comes: uninitialised file found, configuring.
using /etc/X11/xorg.conf.





   I still  have not any graphics :)





   I do not know what happened ^_^

thank you very much.

---

### Post by Bashing-om on 2014-10-29
nasim3; yuk;

You say:
> 
after enter this command:
dpkg -l | grep fglrx

nothing shows.

SO, this output makes no sense to happen:
> 
these packages : linux-headers-generic fglrx fglrx-amdcccle, are already installed.
after enter
sudo apt-get install fglrx-modaliases


What is the truth, and what has been going on to alter my conception of what is true ?

I do not know what we are working with.
Post back the outputs of terminal commands:
```

dpkg -l | grep fglrx
lspci -nnk | grep -iA3 vga
sudo lshw -C display

```
Which will show us the hardware and if/what driver is loaded .

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by nasim3 on 2014-11-01
Dear Bashing-om
I'm sorry for the delayed reply.

[COLOR=#ff0000]dpkg -l | grep fglrx[/COLOR]

```

ii fglrx               2:13.350.1-0ubuntu 0.0.1
ii fglrx-amdcccle      2:13.350.1-0ubuntu 0.0.1  
```

[COLOR=#ff0000]lspci -nnk | grep -iA3 vga[/COLOR]

```

00:02.0 VGA compatible controller [0300]: Intel corporation 2nd generation core processor family integrated graphics controller [8086:0116] (rev 09)
Subsystem:Hewlett-Packard company device [103C:1657]
Kernel driver in use:i915
kernel modules:i915

[COLOR=#0000ff]--[/COLOR]

01:00.0 VGA compatible controller [0300]:Advanced micro devices, Inc.[AMD/ATI] whistler [Radeon HD  673OM/677OM/769OM XT] [1002:6740]
Subsystem:Hewlett-Packard company device [103C:1657]
Kernel driver in use:fglrx_pci
kernel modules:fglrx,radeon


```

[COLOR=#ff0000]sudo lshw -C display[/COLOR]

```


*display 
description: VGA compatible controller
product:whistler [Radeon HD 673OM/677OM/769OM XT]
vendor:Hynix semicinductor (Hyundai Electronics)
physical id: 0
bus info: pci@0000:01:00.0
version:00
width:64 bits
clock:33 MHZ
capabilities: pm  pciexpress msi vga_controller bus_master cap_list rom
configuration:driver=fglrx_pci latency=0
resources: irq:54 memory:a0000000-affffff memory:c650000-c651ffff ioport:5000(size=256) memory:c6520000-c653ffff

*display 
description: VGA compatible controller
product:2nd generation core processor family integrated graphics controller
vendor:Intel corporation
physical id: 2
bus info: pci@0000.00:02.0
version:09
width:64 bits
clock:33 MHZ
capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
configuration:driver=i915 latency=0
resources: irq:54 memory:c0000000-c03ffff memory:b0000000-bfffffff ioport:600(size=67)

```

---

### Post by Bashing-om on 2014-11-01
nasim3; Well !

Now we know what we are dealing with - Hybrid graphics !

Unfortunately, AMD - nor Intel  provide support for linux in this situation.
We must look else where. There are a number of alternatives, but, I can not advise on which is the better solution for your use case.
1) [https://help.ubuntu.com/community/BinaryDriverHowto/AMD](https://help.ubuntu.com/community/BinaryDriverHowto/AMD) 
 Manually installing Catalyst 13.4, special case for Intel/AMD hybrid graphics .

2) [https://github.com/beidl/amd-indicator](https://github.com/beidl/amd-indicator)
This indicator applet allows owners of laptops with AMD/Intel hybrid graphics capabilities to easily switch between the graphics cards without the need of running CCC or terminal commands.

3) [https://wiki.ubuntu.com/X/Config/HybridGraphics](https://wiki.ubuntu.com/X/Config/HybridGraphics)
open source: " we have worked to officially support Hybrid graphics "
[https://help.ubuntu.com/community/HybridGraphics](https://help.ubuntu.com/community/HybridGraphics)
[https://launchpad.net/~hybrid-graphics-linux](https://launchpad.net/~hybrid-graphics-linux)

4) [http://rudrageek.com/linux-now-supports-hybrid-graphics-systems-ubuntu-13-10/](http://rudrageek.com/linux-now-supports-hybrid-graphics-systems-ubuntu-13-10/)
Linux now supports Hybrid Graphics Systems with Ubuntu 13.10

5) [http://askubuntu.com/questions/205112/how-do-i-get-amd-intel-hybrid-graphics-drivers-to-work/288355#288355](http://askubuntu.com/questions/205112/how-do-i-get-amd-intel-hybrid-graphics-drivers-to-work/288355#288355)
Solutions offered in respect to switchable graphics.
[http://ubuntuforums.org/showthread.php?t=1927317](http://ubuntuforums.org/showthread.php?t=1927317)

6) [http://planetoss.com/articles/how-to-disable-the-discrete-amd-graphics-card-in-linux/](http://planetoss.com/articles/how-to-disable-the-discrete-amd-graphics-card-in-linux/)
Using the swircheroo tool to switch chip sets.

You will have to do your homework, and make a choice on the direction to take. We will support your decision, and help to implement it.

[INDENT][INDENT]it is not great,
[INDENT][INDENT]just the way it is
[/INDENT][/INDENT][/INDENT][/INDENT]

---


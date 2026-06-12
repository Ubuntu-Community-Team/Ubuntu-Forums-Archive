---
title: "The &quot;Ubuntu Software&quot; application no longer sees that I'm online in Ubuntu 21.04"
date: 2021-06-12
forum: Installation &amp; Upgrades
---

### Post by cdysthe on 2021-06-12
Hi,

I can update my system using apt and the Software Updater application on my Ubuntu 21.04 laptop. But I can not longer use the Ubuntu Software application. It keeps telling me "Go online to check for updates" and the update button top left is grayed out. I can install applications with Ubuntu Software. It's only checking for updates that doesn't work. I have checked repositories, even switched to another mirror, but Ubuntu Software still claims I am not online. No other applications have problems with internet connection either.

What can I do to convince Ubuntu Software that I am online so I can use it for update checks? It also checks for firmware updates so I would like to have it working. See screenshot for the error I am getting The Network Settings button does nothing: If I knew how to reset this application I'm sure this problem would be solved but since it's a snap I do not know where it's configuration is stored.

[ATTACH=CONFIG]288650[/ATTACH]

---

### Post by MAFoElffen on 2021-06-13
Is your system using Netplan or Network Manager for network management? And do you have DCHP or have a static IP address set?

---

### Post by MAFoElffen on 2021-06-13
Before your answer to the above, I am seeing more of this type of error lately. I suspect it's a disconnect between a new updated version of software-updater, netplan, and network-manager. I think is related to these two Bugs (but really needs to be reported as it own bug in software-updater, so that it can be corrected in Main as a priority).
    [https://bugs.launchpad.net/ubuntu/+source/netplan.io/+bug/1789130](https://bugs.launchpad.net/ubuntu/+source/netplan.io/+bug/1789130)
    [https://bugs.launchpad.net/ubuntu/+source/open-iscsi/+bug/1713803](https://bugs.launchpad.net/ubuntu/+source/open-iscsi/+bug/1713803)


They are still working on integration of systemd and systemd-networkd. I believe that the last update of software-updater might have had some pointer problems on some systems, which causes a disconnect on pointing to an incorrect network manager renderer. (pointing to a Network Manager that is not defined as being currently in use.

That would explain why it fails seeing a connected network, when it does have a network... And that pressing the "Network Settings" button does "Nothing." It's just confused on what to use as the network manager, and doesn't see correctly that it is really connected.

Netplan started being used in Ubuntu back in 18.04. The Desktops still use Network Manager to add the GUI for network management. If nothing was ever manually configured, when it dynamically renders the network config, the settings in those files may be empty or not. And there seems to be a pointer problem on which network manager is in control as the default network manager renderer.

The above is my assumption based on the fixes that we have been coming up with as work-arounds that seem to solve this problem.

For fixes, it seems if the renderer is manually set to "reestablish" that pointer... It doesn't matter whether that is to NetPlan or to the Network Manager... Then this fixes that problem. Below is the instruction for either:

NetPlan as renderer:
```
sudo systemctl stop NetworkManager
sudo systemctl disable NetworkManager
sudo systemctl mask NetworkManager

# Next, start and enable the systemd-networkd service:
sudo systemctl unmask systemd-networkd.service
sudo systemctl enable systemd-networkd.service
sudo systemctl start systemd-networkd.service

# Add the interface configuration to the netplan config file (in the /etc/netplan directory):
#Make a copy of the file
cp /etc/netplan/01-netcfg.yaml ~/Documents/O1-netcfg_old.yaml

# Edit the file with admin privilege's

#### File Contents ###
[COLOR=#000000]# This file describes the network interfaces available on your system
# For more information, see netplan(5).[/COLOR]network:
  version: 2
  renderer: networkd
  ethernets:
    enp0s3:
      dhcp4: yes
### End Contents ###

# Apply the changes by running the following command:
sudo netplan apply

```

Network Manager as renderer:
```
sudo systemctl stop NetworkManager

#Make a copy of the file
cp /etc/netplan/01-netcfg.yaml ~/Documents/O1-netcfg_old.yaml

# Edit the file with admin privilege's

#### File Contents ###
# This file describes the network interfaces available on your system
# For more information, see netplan(5).
# Set and change netplan renderer to NetworkManager GUI tool 
network:
  version: 2
  renderer: NetworkManager

### End contents ###

# start the service back up and apply
sudo systemctl start NetworkManager
sudo netplan apply

```
Note that after doing that to explicitly use the Network Manager as the renderer, that it's easiest to use the GUI Network Manager > Settings to set the settings in the GUI and save to generate the new network settings files.

There's 100's of ways to do similar things, but those two fixes seem to work.

---

### Post by fizyk on 2021-06-14
Hmmm... 
I've got two systems, one is upgraded from 20.10 the other is fresh 21.04 install and got this issue on the new system. What was the difference? 
It was the fact that the old system used gnome-software, while new system had just the ubuntu software that could not connect to network. 

Could this be the fact, that the ubuntu-software was installed from snap? Anyway, I installed the gnome-software from apt, and it works like on the old system.

---

### Post by ActionParsnip on 2021-06-14
Do you use a proxy for web access?

---

### Post by MAFoElffen on 2021-06-14
I'm not sure how to replicate this problem... Because it doesn't happen to everyone. Nor people who have a certain pattern of actions. The people reporting it are versions 20.04 through 21.04, and there doesn't seem to be a consistent pattern there yet either. So I don't know if what it is caused by is from a specific package update or from a script that sees a certain condition...

But remapping the network manager renderer seems to fix it.

---

### Post by cdysthe on 2021-06-14
> **MAFoElffen said:**
> Is your system using Netplan or Network Manager for network management? And do you have DCHP or have a static IP address set?

My system is totally vanilla Ubuntu 21.04 so I guess it's using Network Manager. Everything else connecting to the Internet works like it has been. It's only Ubuntu Software that won't update.

---

### Post by cdysthe on 2021-06-14
> **ActionParsnip said:**
> Do you use a proxy for web access?

No, no proxy.

---

### Post by MAFoElffen on 2021-06-14
So did you try to reconnect Network Manager as the default renderer?

---

### Post by cdysthe on 2021-06-15
This turns out to be a bug in Snap and Ubuntu Software. I reported it here: 

 [https://forum.snapcraft.io/t/the-ubuntu-software-application-refuses-to-see-that-i-am-online/24981]("https://forum.snapcraft.io/t/the-ubuntu-software-application-refuses-to-see-that-i-am-online/24981")

I am sure it will be fixed soon.  Regardless, thank you for help and suggestions.

---


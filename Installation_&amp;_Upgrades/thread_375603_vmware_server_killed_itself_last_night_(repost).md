---
title: "vmware server killed itself last night (repost)"
date: 2007-03-03
forum: Installation &amp; Upgrades
---

### Post by gollybegully on 2007-03-03
Downloaded, setup, installed windows, installed vmware tools everything's running fine.

I restart my computer and today vmware would not start. I type vmware in a terminal and get

vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.


when I run that command I get:

Making sure services for VMware Server are stopped.

Stopping VMware services:
Virtual machine monitor done
Bridged networking on /dev/vmnet0 done
DHCP server on /dev/vmnet1 done
Host-only networking on /dev/vmnet1 done
DHCP server on /dev/vmnet8 done
NAT service on /dev/vmnet8 done
Host-only networking on /dev/vmnet8 done
Virtual ethernet failed
Unable to stop services for VMware Server

Execution aborted.





the part that drives me crazy is that everything was running perfect and i didnt change anything all i did was reboot and somehow it magically ****** itself overnight.

---

### Post by ffxr on 2007-03-03
if its happening after each reboot, i guess must be something to do with your init scripts.. have look through your syslogs and see if if there is any errors corresponding to the vmware virtual network drivers & post back..

& how did you install virtual server?

& have you done sudo vmware-config.pl ?

---

### Post by gollybegully on 2007-03-04
> **ffxr said:**
> if its happening after each reboot, i guess must be something to do with your init scripts.. have look through your syslogs and see if if there is any errors corresponding to the vmware virtual network drivers & post back..

& how did you install virtual server?

& have you done sudo vmware-config.pl ?

well I installed is yesterday and only had one reboot since.  Im sorry I dont know where to find syslogs.

I installed it pretty much following this wiki to a tee [https://help.ubuntu.com/community/VMware/Server?action=show&redirect=VmwareServer](https://help.ubuntu.com/community/VMware/Server?action=show&redirect=VmwareServer)

yes and when I run sudo vmware-config.pl

it says that Virtual ethernet failed to be stopped so I cant configure it.




should I just uninstall and reinstall?  I just would like to have some idea of what went wrong cause Ive used this before with no problem.

---

### Post by zvacet on 2007-03-04
Is it  kernel(do you have diferent version now)?If you want to uninstall it go to usr/bin and you will find file named somrthing like vmware-unistall.pl
Become root
```
sudo -i
```
```
cd /usr/bin
```
```
root@localhost#./vmware-uninstall
```
ofcourse you will put correct filename
Just to be sure chek etc,etc/init.d,home(hidden folder too),tmp to see is any of vmware files left.If it is all clean install it again.

---

### Post by veejoe on 2007-11-01
I have this problem too.  Successful install of VMWare Server, then after each reboot it prompts that vmware-config.pl has to be re-run.

I've seen this on other distros where the install process doesn't complete properly and leaves behind one or more files that cause the VMware programs to think the configure hasn't been run.  However I can't find these files this time.  And the "Virtual Ethernet" service failing to shut down is a new symptom too.

I will try a re-install as well and see what happens.

gollybegully, when you did the vmware-install did you receive a bunch of compiler warnings in the build of one of the modules?  Don't know if it's significant but I wonder if one of the modules is bad causing services to fail or not function properly.

---


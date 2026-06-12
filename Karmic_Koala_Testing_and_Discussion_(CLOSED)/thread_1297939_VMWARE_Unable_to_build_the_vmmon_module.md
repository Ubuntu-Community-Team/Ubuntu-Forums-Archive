---
title: "VMWARE Unable to build the vmmon module"
date: 2009-10-22
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by sdowney717 on 2009-10-22
does anyone know the solution?
thanks

> /tmp/vmware-config0/vmmon-only/linux/driver.c:1990: error: ‘struct task_struct’ has no member named ‘gid’
/tmp/vmware-config0/vmmon-only/linux/driver.c:2007: error: too many arguments to function ‘smp_call_function’
make[2]: *** [/tmp/vmware-config0/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config0/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-11-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config0/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/go/unsup-linux-products" and 
"http://www.vmware.com/go/unsup-linux-tools".

Execution aborted.


---

### Post by dabl on 2009-10-22
You need the patch from here:

[http://communities.vmware.com/thread/221724;jsessionid=A7863D95C6E99E7D0AB10C6AEA079403?start=0&tstart=0](http://communities.vmware.com/thread/221724;jsessionid=A7863D95C6E99E7D0AB10C6AEA079403?start=0&tstart=0)

You actually want the script file from post #6.

Follow the instructions and it should build correctly on the 2.6.31 kernel.

The other problem you may have is a mouse/keyboard focus issue.

[http://communities.vmware.com/thread/228636;jsessionid=AEDA87CADB5450C331299CF099B8A059?tstart=105](http://communities.vmware.com/thread/228636;jsessionid=AEDA87CADB5450C331299CF099B8A059?tstart=105)

The solution is to edit /etc/vmware/bootstrap and add one of these lines (per post by fredsey, p.2 of the thread):

export VMWARE_USE_SHIPPED_GTK=yes

or

export VMWARE_USE_SHIPPED_GTK=force


Finally, this one seems to help some folks -- I didn't have the problem:

[http://communities.vmware.com/thread/228949](http://communities.vmware.com/thread/228949)

---

### Post by sdowney717 on 2009-10-22
i tried it but it is not working. server is different from workstation
is this the issue?

scott@scott-desktop:~$ cd vmware-server-distrib
scott@scott-desktop:~/vmware-server-distrib$ sudo ./vmware-6.5.2-newkernmods.sh
md5sum: /usr/lib/vmware/modules/source/vmblock.tar: No such file or directory
Sorry, installed file content does not match what was expected
for VMware Workstation 6.5.2 /usr/lib/vmware/modules/source/vmblock.tar file.
             Your checksum: 
Expected checksum (64-bit): 08894c1edd8c7c1c45846768102f3700
Expected checksum (32-bit): 111725518eb37a65e5ad6bc6bd16774b
scott@scott-desktop:~/vmware-server-distrib$

---

### Post by sdowney717 on 2009-10-22
[http://blog.mymediasystem.net/uncategorized/vmware-server-2-0-1-installation-howto-for-karmic-koala-x86_64/](http://blog.mymediasystem.net/uncategorized/vmware-server-2-0-1-installation-howto-for-karmic-koala-x86_64/)

I may have solved it by following this, now how do you start the web interface?
[http://localhost:8222/ui/#](http://localhost:8222/ui/#)

but i cant login, no permission to access it. what is my user and password??

Starting VMware services:
   Virtual machine monitor                                             done
   Virtual machine communication interface                             done
   Virtual ethernet                                                    done
   Bridged networking on /dev/vmnet0                                   done
   Host-only networking on /dev/vmnet1 (background)                    done
   DHCP server on /dev/vmnet1                                          done
   Host-only networking on /dev/vmnet8 (background)                    done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done
   VMware Server Authentication Daemon (background)                    done
   Shared Memory Available                                             done
Starting VMware management services:
   VMware Server Host Agent (background)                               done
   VMware Virtual Infrastructure Web Access
Starting VMware autostart virtual machines:
   Virtual machines                                                    done

The configuration of VMware Server 2.0.1 build-156745 for Linux for this 
running kernel completed successfully.

scott@scott-desktop:/usr/lib/vmware/modules/binary$

ok, i solved it by following  this

I m using a Ubuntu distrib and I dont have a root password, so I found another solution to log with my user &#8220;will&#8221;.

Edit the file
/etc/vmware/hostd/authorization.xml
and edit the line :
root

so it becomes :
will

then restart vmware :
sudo service vmware restart

OK, you can log into user &#8220;will&#8221; !

---

### Post by dabl on 2009-10-22
Heh -- you're way ahead of me on the server interface thing -- I'm just a VMware Player user, running a Win XP guest, so I can run a Win app that has no Linux counterpart.

AFAIK, for the patching and module-building issues, workstation=server=player.  So one solution fixes all versions.  :)

---

### Post by sdowney717 on 2009-10-23
Just incase that page ever goes down. here are the instructions on how to get it going

> 
VMware-server 2.0.1 Installation HOWTO for Karmic Koala (x86_64)
October 10th, 2009 by acmelab68

I was trying to install the VMware server 2.0.1 x86_64 on my new Karmic Koala (Ubuntu 9.10, kernel 2.6.31-13) server, but I’ve got a bunch of errors. Looking for an any-any patch haven’t been successful, but I’ve found an discussion thread, where the problem was solved. Unfortunately it sucks a bit going through the links and threads. That’s why here is a short and clear HOWTO with an already fixed patch:

First time installation

    * Download or get VMware-server-2.0.1-156745.x86_64.tar.gz and unpack it.
    * go into vmware-server-distrib and run vmware-install.pl.
    * the process stops with an error. (... wait.h:78: error: conflicting types ... ).
      Download and unpack this vmware-server.2.0.1_x64-modules-2.6.30.4-fix.tgz into the vmware-server-distrib directory.
      Invoke vmware-server.2.0.1_x64-modules-2.6.30.4-fix.sh
    * remove this directory: /usr/lib/vmware/modules/binary
    * start vmware-config.pl
    * This should leave you with a working VMware installation. Go now with your browser to [https://localhost:8333](https://localhost:8333) and enter your Serial Number under “Applications->Enter Serial Number“.

Reinstallation
If anything goes wrong, you can do the installation again. In order to do so, you need to do some steps manually on your console.

    * first, delete the vmware modules

          rm -rf /usr/lib/vmware/modules/

      and if necessary (you’ll be told, if so):

          rm -rf /lib/modules/2.6.31-13-server/misc/vm*

    * If the vmware-config.pl aborts, because it can’t accomplish to shut down all vmware processes, kill all vmware processes manually.

          kill -9 $( grep -i vm | awk '{ print $2 }' )

    * rerun vmware-config.pl
    * if somewhere in the installation process you should be asked:

          “/usr/bin/vmware-config.pl“. Do you want this
          program to invoke the command for you now? [yes]

      you should answer: no
      then run the patch vmware-server.2.0.1_x64-modules-2.6.30.4-fix.sh.
      After this you run /usr/bin/vmware-config.pl 

Empty Browser Remote Console Problem

Sometime it happens, my Firefox 3.5.3 doesn’t show anything, if I try to start [https://localhost:8333](https://localhost:8333). If I should take a wild *** guess, this is all due to my multiple installation attempts of the VMware server itself. Or is it just buggy?
I noticed, that actually three different approaches (sometimes in combination) lead to a relief.

    * Don’t use hostnames, but IPs only in your browser. E.g: [https://127.0.0.1:8333/ui](https://127.0.0.1:8333/ui) instead of [https://localhost:8333/ui](https://localhost:8333/ui)
    * Restart the vmware-hostd (your running VM’s won’t be affected <- bold statement, don’t you think?).

          /etc/initd.d/vmware-mgmt restart

      If the process number stays unchanged, and a log entry in /var/log/vmware/hostd-x.log indicates an already running vmware-hostd, kill the process manually, because it seams to hang:

          killall -9 vmware-hostd

    * Uninstall the VMware remote console Plug-in:

          Menu: Tools -> Add-ons -> Tag:Extentions -> “VMware remote console Plug-in” -> Button:Uninstall

      and reinstall it again. Perform the first step.

    * Remove the VMware’s SSL-Certificate:

          Menu: Edit -> Preferences -> Section:Advanced -> Tab:Security ->Tab:Encryption -> Button:View Cerfiticates -> Authorities.

      Scroll down, until VMware shows up. Select and delete all entries. Perform the first step
    * Or follow a completely different approach described here

You can read a more complete error log of the failed VMWare server installation here.

make[1]: Entering directory `/usr/src/linux-headers-2.6.31-13-server'
  CC [M]  /tmp/vmware-config1/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config1/vmmon-only/linux/driver.c:31:
/tmp/vmware-config1/vmmon-only/./include/compat_wait.h:78: error: conflicting types for ‘poll_initwait’
include/linux/poll.h:70: note: previous declaration of ‘poll_initwait’ was here
In file included from /tmp/vmware-config1/vmmon-only/./include/vmware.h:38,

use a social bookmark, e-mail or print this story

    * Digg
    * del.icio.us
    * MisterWong
    * StumbleUpon
    * Google Bookmarks
    * Technorati
    * Facebook
    * MySpace
    * Live
    * email
    * Print

Tags: 9.10, error, HOWTO, istallation, karmic, koala, problem, server, ubuntu, vmware, x86_64.
1 Response to “VMware-server 2.0.1 Installation HOWTO for Karmic Koala (x86_64)”

   1. Daniele

      Works perfectly, thanks a ton!!


---

### Post by zackiv31 on 2009-10-27
This is all well and good, but is there a version for 2.02?  It got released yesterday and I only see that blog linking to 2.01.

Don't know where the original files are from either...

---

### Post by benjamimgois on 2009-10-27
same problem here, i think that i'll wait for an update.

---

### Post by zackiv31 on 2009-10-27
I actually just tried that 2.01 update... and it seemed to have installed correctly, but when trying to power on my VM from the web admin tool, it seems to have hung and crashed.

Is this an update to vmware we're waiting for, or an update to ubuntu that is preventing it working from out of the box?

---

### Post by sdowney717 on 2009-10-28
you may have kvm modules loaded which does keep vmware machines from starting. remove them and see if it starts

to stop kvm modules from loading and interfering with vmware
vmware just will not run with these loaded.
follow these steps to temporarily unload the KVM module


sudo /etc/init.d/libvirt-bin stop

look in  /proc/modules and search for kvm... I have an Intel chip so I had two hits: kvm-intel and kvm .. next, simply remove them in order:


sudo modprobe -r kvm_intel
sudo modprobe -r kvm

These modules will return after a reboot or by running the modprobe commands again to load the modules:

sudo modprobe kvm_intel
sudo modprobe kvm
sudo /etc/init.d/libvirt-bin start

---

### Post by sdowney717 on 2009-10-28
this file when run will power up the vmware server machine with the mouse working correctly.
you can run it like this without having to load the web interface. 
a screen will be presented to you with a choice of vm's to start.
i made a file called launchvm.sh and made it executable.
the first 3 lines simply unload the offending kvm modules.

i did not have to unload any kvm stuff until i installed kvm and made some VM's. so i suppose the first 3 lines are not needed
if you never installed kvm.

> gksudo /etc/init.d/libvirt-bin stop
gksudo modprobe -r kvm_intel
gksudo modprobe -r kvm
#!/bin/bash
################################################################################
# Call VMWare Server's Remote Console in a clean GTK setup.
################################################################################

# Clean GTK setup for VMWare
export VMWARE_USE_SHIPPED_GTK=yes

# Find console executable in Firefox plugins.
vmrc="$(find "$HOME/.mozilla/firefox" -name vmware-vmrc -type f -perm -111 | tail -1)"
[ -x "$vmrc" ] || exit 1

set -x
cd "$(dirname "$vmrc")" && "$vmrc" -h 127.0.0.1:8333

---


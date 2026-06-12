---
title: "vmware server install errors and grumbles"
date: 2010-06-22
forum: Installation &amp; Upgrades
---

### Post by rannable on 2010-06-22
Hey everyone.

Im Rob and I have Ubuntu 10.04 x64 running on a Dell Studio 17 and I just cant seem to play nicely with vmware server. 

I have downloaded the setup tar file to my desktop and unpacked everything throughout several install attempts to a folder on my desktop called vmware-server-distrib.

I first followed this install [http://www.howtoforge.com/how-to-install-vmware-server-2-on-ubuntu-9.04](http://www.howtoforge.com/how-to-install-vmware-server-2-on-ubuntu-9.04).

During part of the install some of the services failed to be stopped:

Stopping VMware autostart virtual machines:
   Virtual machines                                                   failed
Stopping VMware management services:
   VMware Virtual Infrastructure Web Access
   VMware Server Host Agent                                           failed
Stopping VMware services:
   VMware Authentication Daemon                                        done
   Virtual machine monitor                                             done

However I plodded on, accepted the licence agreement and the next prompt was:

None of the pre-built vmmon modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes]

So I said yes to this and it returned this:

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.32-22-generic/build/include] 

It then returns loads of info and at the end it advises the installation has been aborted. I can show you the data it returns if you like but its a lot so didnt want to clog up the page any more than i already had ;)

As that failed i tried following these instructions: [http://www.ubuntugeek.com/how-to-install-vmware-server-2-0-x-in-ubuntu-9-10-karmic.html](http://www.ubuntugeek.com/how-to-install-vmware-server-2-0-x-in-ubuntu-9-10-karmic.html) but that didnt work with the same problem.

I found these instructions [http://www.bauer-power.net/2009/03/how-to-install-vmware-server-2-on.html](http://www.bauer-power.net/2009/03/how-to-install-vmware-server-2-on.html) and its a similar story. When I get to here it starts to go wrong:

None of the pre-built vmmon modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes]  

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.32-22-generic/build/include] 

I just keep getting execution aborted, can someone please help :confused:

---

### Post by Azazel on 2010-06-23
I am having the exact same problem, I followed the instructions from the vmserver2 user guide. 

if you made it this far then you have installed vmware server, but you are having problems configuring it.

If you have never successfully configured before then don't worry about it failing to stop those services, because they haven't been started therefor they cant be stopped.

as for building the kernel module, I'm doing some research to figure out what is going on, if i figure anything out i will post my results.

good luck!

---


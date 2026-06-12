---
title: "Parallels Work Station purchased thru Cannocial Store"
date: 2008-02-24
forum: Installation &amp; Upgrades
---

### Post by LarryJ2 on 2008-02-24
I purchased Parallels workstation thru the Cannonical Store.  I  installed the three parallels packages using Adept Manager.   I then entered my product key apparently successfully and then created a virtual machine hosted on Ubuntu 7.10.   When I try to power on the vm,  I get the error message below.    I haven't found anything on the Parallels site or here that addresses this... am I the only one?  


----------------------------------
Parallels Workstation
Error occurred while trying to interact with Parallels driver! Parallels Workstation is either not installed or/and configured or has integrity problems, which prevent it from operating properly. Please reinstall the Parallels Workstation.

---

### Post by Hesi on 2008-02-24
Hi LarryJ2

I've got the same error after i've updated my parallels version in Ubuntu 7.10 over synaptic.
Also i've report this error to parallels.

But you can use a workaround meanwhile.

you must completle remove the three parallels packages over synaptic and install the Version from Paralells website directly. 

this helped me out.

But after install do not download and install the update then. If i get answer from Parallels i will let you now.

regards
Frank

---

### Post by LarryJ2 on 2008-02-24
Thank you Frank.  I'll give that a try.

Form Admin:  This thread really should be in the virtualization area.   Please move it there if possible.   Thanks.

Larry

---

### Post by iamfuzz on 2008-02-26
Hi,

My name is Brian Thomason and I head up the engineering side of the Canonical Partner Repository.  First off, let me apologize for the issues you are experiencing with your Parallels install.  

We have a bug open on the issue and are working together with Parallels to resolve it:

[https://bugs.edge.launchpad.net/ubuntu/+source/parallels/+bug/194798](https://bugs.edge.launchpad.net/ubuntu/+source/parallels/+bug/194798)

You can track progress there, and I will also update this thread when it is resolved.

Again, I apologize for the inconvenience.

-Brian

---

### Post by LarryJ2 on 2008-02-29
Brian,
I removed  the partner repository packages using Adept_Manger (as suggested by Frank above)  then I downloaded the parallels  .deb file directly from the parallels web site and followed the install instructions in the parallels .pdf which went roughly
> $sudo dpkg -i Parallels-2.2.2222-lin.deb
$sudo parallels-config
$ ....Accept License Agreement  Y

     Compiling Parallels Workstation 2.2 drivers...
     Drivers have been compiled successfully.
     Installing drivers...
     Starting drivers...
Loading Parallels Workstation 2.2 hypervisor ...
 Parallels Workstation  hypervisor already loaded.
Loading Parallels Workstation 2.2 vm-main ...
Loading Parallels Workstation 2.2 vm-bridge ...
 Parallels Workstation  vm-bridge already loaded.
Loading Parallels Workstation 2.2 vmvirtualnic ...
 Parallels Workstation  vmvirtualnic already loaded.
Parallels Workstation has been successfully configured

Now you can run Parallels Workstation 2.2
    Issue parallels command.

I was able to bring up the parallels control panel but

1.  The adept_updater is prompting me that "parallels is upgradeable, and that  parallels-modules, parallels-modules-2.6 need to be installed."   Will I break the installation if I allow adept_manger to run?

2.  I was able to successfully register my copy purchased from the Canonical site but now after issuing the "parallels" command,  I am now getting an error
> Parallels Workstation experience problem when trying to allocate physical memory in PAE mode. The current version of Parallels Workstation supports up to 4 GB of physical memory. To fix the problem you have to change the auto detected memory size to 4096MB. Add to your boot loader the following option "mem=4096M"
Since I have only 4096MB (4 sticks of 1024) memory,  I don't know why  they are complaining  exactly,    maybe just an entry  in the grub file?

Update:  Parallels is now running.  I added mem=4096M to the /boot/menu.lst line  as shown below.   No more error "experience problme when...".  Don't honestly know if this was the cure or not.
 kernel		/vmlinuz-2.6.22-14-generic root=UUID=56b6988f-1311-44fd-95e2-9dcacb05086b ***mem=4096M*** ro 
Larry

---

### Post by Hesi on 2008-03-07
Since last Night updated packages over synaptic installed, and it's working again. :-)

THX to IAMFuzz and the other bug trackers :-)

Great Service, Great Help

---


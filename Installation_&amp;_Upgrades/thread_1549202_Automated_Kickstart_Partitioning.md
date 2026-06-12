---
title: "Automated Kickstart Partitioning"
date: 2010-08-09
forum: Installation &amp; Upgrades
---

### Post by mxl9499 on 2010-08-09
First off my apologies if this has been asked before, however in my searches over the past few weeks I have not found any clear answer to this.

I am trying to put together a customized automatic installation of Ubuntu 9.10 Desktop for a set of computers I manage at work. Since there are other servers in my department that are Red Hat based, I was introduced to Kickstart so I have been using that exclusively. 

I have almost my entire installation automated using Kickstart with the exception of the partitioning, which is as follows:

#force full install, wipe everything
install
bootloader --location=mbr
zerombr yes
clearpart --all --initlabel
autopart

My problem that I am asking for help on is that the Kickstart automates everything until the clearpart, where it then asks 2 questions which I would like to figure out how to automate the answers to (preferably within my Kickstart script)

The first question is the install process telling me about my currently configured partitions and mount points. Asking me if i want to "Undo changes to partitions" or "Finish Partitioning and write changes to disk" which I of course want to finish partitioning.

The second question is telling me if I continue the changes listed will be written to the disks, and asks if I want to "Write changes to disks?" which I want to select Yes for automatically.


Like I mentioned before I have searched the web and this forum for any potential way of doing this, but so far have come up with nothing, so I figured I would ask the experts out here and see what suggestions come up. I realize the Kickstart is not completely implemented in Ubuntu, however since I have everything written in Kickstart already I would prefer to stay within the Kickstart script to fix this. 

Thank you in advance!
mxl9499

---

### Post by TSJason on 2010-10-29
Hey mxl9499,

I was looking for this same solution. I'm using PXE boot for unattended installs. The solution comes in the form of a "preseed" file that works with the debian installer. 

I define this preseed file in the APPEND line with my kickstart and initrd arguments. So for example:

```
LABEL Ubuntu Lucid
        MENU LABEL Uubuntu Lucid i386 Workstation Install
        KERNEL images/ubuntu/ubuntu-installer/i386/linux
        APPEND ks=http://10.50.20.20/deploy-data/kickstarts/kubuntu-ldap-i386.cfg url=http://10.50.20.20/deploy-data/kickstarts/kubuntu-ldap-i386.preseed initrd=images/ubuntu/ubuntu-installer/i386/initrd.gz
```

The preseed file itself only contains a few lines to achieve exactly what you are looking for (works for me flawlessly), but there are a ton of other options that can be used as well.

```

d-i partman/confirm_write_new_label boolean true
d-i partman/choose_partition \
select Finish partitioning and write changes to disk
d-i partman/confirm boolean true

```

For more info on preseeding, I found a pretty useful article here:
[http://www.debuntu.org/how-to-unattended-ubuntu-network-install-preseed-p5](http://www.debuntu.org/how-to-unattended-ubuntu-network-install-preseed-p5)

---


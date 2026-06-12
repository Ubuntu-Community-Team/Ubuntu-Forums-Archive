---
title: "Successfully installed JeOS but failed to start..."
date: 2007-11-16
forum: Installation &amp; Upgrades
---

### Post by xellzhang on 2007-11-16
Hello guys! I tried to install Ubuntu 7.10 JeOS on VMware workstation 6.0.2. The installation is ok. But when the first boot the progress bar (orange one) stayed at very beginning and nothing went on.

Please see attachment.

I don't know why...

---

### Post by xellzhang on 2007-11-17
Did anyone meet the same problem?

---

### Post by arijarot on 2007-11-17
Same problem: installed fine, fails to boot(stuck at one orange bar). The md5 sum checked out (341ca65a187c71643079a2f9ee5523b5 *ubuntu-7.10-jeos-i386.iso), but when I did a disc integrity check, it failed. > "The ./isolinux/boot.cat file failed the md5 sum verification. Your cd-rom or this file may have been corrupted." 

---

### Post by arijarot on 2007-11-17
Has anyone successfully booted JeOS?

---

### Post by Ausbilder on 2007-11-17
Hy.

I got the same problem.

The problem is the LSI Scsi driver. When you install the VM, you must choose the Buslogic SCSI driver, and the system will boot correctly.

Ausbilder

---

### Post by arijarot on 2007-11-17
OK. **Successfully** boots when changing hard drive from SCSI to** IDE **under vmware fusion. 


But, what about the failed integrity test (i.e., "./isolinux/boot.cat file failed the md5 sum verification")? Shouldn't this be reported as a bug?

---

### Post by pacostudio on 2007-11-19
The problem is that when Ubuntu Linux is selected when creating a new Virtual Machine under VMware Fusion, it automatically creates a virtual disk with SCSI geometries.

Except for manually editing config files, I haven't been able to easily convert the virtual disk type once the virtual machine has been created.

---

### Post by Solow on 2007-11-19
I'm installed it under VMWare but got that message. When I changed the HD to IDE it installed fine.
Do anyone now if the problem accoure under a real SCSI disk?

What do I do now on the command promt? How can I run a viritual machine?

---

### Post by jasonfiset on 2007-11-20
This is concerning.  I wonder how this will impact ISVs trying to develop VMs for use on the ESX platform?  ESX only allows SCSI based VMs - IDE disks will not work on ESX.

-Jason

---

### Post by jasonfiset on 2007-11-20
Apparently the buslogic controller works - not sure if ESX supports Buslogic or not.  If the init kernel does not support LSIlogic, the installer should not be able to install to this type of virtual disk.  I think it would be better to integrate the LSI driver into the initrd image so users don't have to hack the vmx file to get it to boot.  The LSIlogic interface will also perform much better than the buslogic interface on ESX.

-Jason

---

### Post by AndrewShugg on 2007-11-21
JeOS works in ESX Server 3.x, as long as you change the SCSI controller to BusLogic rather than LSI as other people have mentioned.

If you have already created the VM and have this problem, the simplest thing to do is to shut it down and edit its settings.  (VM -> Edit Settings)[LIST]
[*]Click on "Hard Disk 1", click "Remove", and click "Remove from virtual machine and delete files from disk".
[*]Then click "OK".
[*]Now go into Edit Settings again and click "Add....", select "Hard Disk", click "Next", change size and location if desired, click "Next", change Advanced Options if desired, click "Next", and click "Finish".
[*]Then in the Hardware list select the "New SCSI Controller (adding)" line and click the "Change Type" button.
[*]Select "BusLogic" and click "OK".
[*]Click "OK" to complete the hardware config change.
[*]Then boot off the JeOS ISO again and install afresh.[/LIST]Another problem I found was that if I selected 'Guided with LVM' during the partition setup then the base system would fail to install - syslog complained that the installer hadn't been able to find the lvm2 package.  (It is on the ISO though.)

If you want the VMware Tools installed - which you will, in ESX, here's one way that you can do it:
```

$ sudo apt-get -y install alien fakeroot
[ watch stuff install ]
[ click on VM -> Install VMware Tools ]
$ mount /media/cdrom
$ fakeroot alien -cv /media/cdrom/*rpm
[ watch stuff happen ]
$ sudo dpkg -i vmwaretools*deb
[ stuff installs ]
$ sudo vmware-config-tools.pl
[ answer 'n' to all questions about building modules ]

```Once complete, shut down the VM, then go to VM -> Edit Settings, click Options, click Advanced, click Configuration Parameters, and change the value of the tools.syncTime row to TRUE.  Then OK, OK, and power up the VM again.

To build the modules you'll need to 'sudo apt-get install gcc linux-headers-virtual' and then rerun 'sudo vmware-config-tools.pl' and answer yes to the questions about building modules.

Now you will have a very bloated VM but you can now remove all the cruft that was installed since the 'apt-get -y install alien fakeroot'... I have done that by looking in /var/log/apt/term.log and identifying which line number corresponded to the start of the alien and fakeroot install (in this case it was 844).  Then I ran the following (all one line, here the lines are broken for clarity):

```

$ sudo sed -n '844,$p' /var/log/apt/term.log | 
perl -n -e 'if (/^Selecting.*package/) { chomp; ($pkg = (split())[4]; 
$pkg =~ s/\.$//; print "$pkg\n"; }' | xargs sudo apt-get dpkg -P

```There might be an easier way to do it though.  =)

Cheers

Andrew S.

---

### Post by arjanhs on 2007-11-23
I have followed the instructions, but got an message about remove modules before running the vmware-configure.pl:

The following VMware kernel modules have been found on your system that were
not installed by the VMware Installer.  Please remove them then run this
installer again.

vmhgfs
vmblock
vmmemctl
vmxnet

Execution aborted.

---

### Post by autumnlover on 2007-11-26
Hey! It was one of the most bizzare bugs I ever encounter... I even run memtest to see if memory chips at my PC are broken, but also checked checksums and was really confused trying to run JeOS under VMWare Server in Windows.

---

### Post by steffen on 2008-02-20
Here is a bug report for it to track in Launchpad: [https://answers.launchpad.net/ubuntu-jeos/+question/17744](https://answers.launchpad.net/ubuntu-jeos/+question/17744)

---


---
title: "Experiences with vmware workstation or server on feisty 7.04 for use in howto?"
date: 2007-09-04
forum: Installation &amp; Upgrades
---

### Post by Krijk on 2007-09-04
A few months ago I decided to go all linux and get rid of my Windows workstation.

Vmware on linux however keeps giving me problems. ](*,) SInce I use it extensively as a test environment it is the primary reason why I sometimes want to go back to Windows.  At least vmware was one of the things that usually worked without problems.

**Remaining issues:**
[LIST]
[*]bridged networking (with Windows/BSD) with GB NIC
[*]poor performance of guest WIndows OS
[/LIST]

**Installation:**
[LIST]
[*]install from tar.gz
[*]vmware-any-any patch
[*]headerfiles
[*]host-only (don't remember how I fixed this)
[*]very slow bridged networking ->partially solved with tx/sg/tso off on eth on host, but sometimes still gives problems with some guests
[*]graphics in guest OS with new graph-cards -> change linux display drivers
[/LIST]

**Specifications:**
[LIST]
[*]Ubuntu 7.04 32bit  2.6.20-16-server
[*]4 GB RAM
[*]AMD Athlon 64X2 4600+
[*]VMware Workstation 5.5.0
[/LIST]

I would like to get some feedback from other users and write an extensive howto  with a troubleshooting and solutions part in it.  There are a lot of individual postings here and on the internet, but it will benefit the community more to have a good howto.

Personally I prefer Workstation because of the snapshot functionality, but maybe server runs better. Also it might be better to go back to 6.06? Please share your experiences. Also with issues with specific guest OS. Preferably with URL's where useful info can be found.

---

### Post by x-point on 2007-09-04
Please check this [post]("http://www.linuxscrew.com/2007/08/21/vmware-server-ubuntu-feisty-fawn-704-linux/").  It may be useful.

---

### Post by Krijk on 2007-09-04
> **x-point said:**
> Please check this [post]("http://www.linuxscrew.com/2007/08/21/vmware-server-ubuntu-feisty-fawn-704-linux/").  It may be useful.

Done that, but that doesn't solve a lot of issues. The purpose is making an extended version of something like this:
 [http://ubuntuforums.org/showthread.php?t=539990&highlight=vmware]("http://ubuntuforums.org/showthread.php?t=539990&highlight=vmware")

```
This is a doc that i prepared for my own reference. See if this helps. I have done this on both Intel 64 and AMD64.

Build Environment
Make sure you have the needed build environment and tools to compile the vmware modules for the kernel.

**
aptitude install linux-headers-`uname -r` build-essential
aptitude install xinetd
**

for server
**
sudo aptitude install libxtst6 libxt6 libxrender1
**

for 64-bit
**
sudo apt-get install ia32-libs libc6-i386
**

Downloading VMware Server
Vmware Server can be downloaded from:
http://www.vmware.com/download/server/
After accepting the EULA grab the vmware server .tgz file (around 102MB).
Note: As of right now VMware Server won't compile correctly on Feisty without patching the vmmon file.

Patch information can be found here:

http://www.vmware.com/community/thre...76957&tstart=0

The patch can be downloaded here: http://ftp.cvut.cz/vmware/vmware-any...date109.tar.gz

Installing VMware Server

Untar the VMware Server package:
**
tar -xzf /Path/To/VMware-server-1.0.3-xxx.tar.gz
**

Change into the install directory:
**
cd vmware-server-distrib
**

Run the installer:
**
sudo vmware-install.pl
**

Choose defaults to questions until it asks:

"Before running VMware Server for the first time, you need to configure it by invoking the following command: "/usr/bin/vmware-config.pl". Do you want this program to invoke the command for you now? [yes]"

Enter NO and quit the install. To install the patch cd back to your start directory:
cd ..

Untar the patch:
**
tar xvzf /Path/To/vmware-any-any-update109.tar.gz
**

Enter the directory:
**
cd vmware-any-any-update109
**

Run the patch script:
**
sudo ./runme.pl
**

It should prompt you to run vmware-config.pl, Choose YES at this time. If it doesn't you can always run the config script manually:
**
sudo vmware-config.pl
**

Again you can hit enter to choose the defaults to all the questions, though you will probably want to manually choose which networking features you want. To access the server run
**
vmware
**
for the VMware Server Console.


To get the remote Mangegment Interface:

Download Mangement Inteface from VMWare Download Site

**
tar zxvf VMware-mui-<xxx>.tar.gz
sudo ./vmware-install.pl
**

If you receive a "starting httpd.vmware:-ne failed" error at the end of running vmware-config-mui.pl you will need to run the following command.
**
sudo ln -s -f /bin/bash /bin/sh
sudo vmware-config-mui.pl
**

If you want to administer VMware from the server itself with a minimal set of GUI

KDE Environment
**
sudo apt-get install kdebase kdm x-window-system-core
**
```

---

### Post by dmonty on 2007-09-21
> If you receive a "starting httpd.vmware:-ne failed" error at the end of running vmware-config-mui.pl you will need to run the following command.
**
sudo ln -s -f /bin/bash /bin/sh
sudo vmware-config-mui.pl
**


You don't have to replace sh (dash) with (bash)....

Here is a one liner that will fix the vmware-mui webserver init script:
```

sed -i 's/bin\/sh/bin\/bash/g' /etc/init.d/httpd.vmware
/etc/init.d/httpd.vmware start

```

---


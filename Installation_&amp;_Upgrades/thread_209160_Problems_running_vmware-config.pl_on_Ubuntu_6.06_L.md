---
title: "Problems running vmware-config.pl on Ubuntu 6.06 LTS"
date: 2006-07-04
forum: Installation &amp; Upgrades
---

### Post by hikmat on 2006-07-04
Hello,

I hope someone out there will have an answer or a link to an answer. I did all the apt-get, install, etc., commands. Things fail at the following point:

****************************

In which directory do you want to install the mime type icons?
[/usr/share/icons]

In which directory do you want to install the application's icon?
[/usr/share/pixmaps]

Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Workstation is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for
your system (you need to have a C compiler installed on your system)? [yes]

Using compiler "/usr/bin/gcc-3.4". Use environment variable CC to override.

Your kernel was built with "gcc" version "4.0.3", while you are trying to use
"/usr/bin/gcc-3.4" version "3.4.6". This configuration is not supported and
VMware Workstation cannot work in such configuration. Please either recompile
your kernel with "/usr/bin/gcc-3.4" version "3.4.6", or restart
/usr/bin/vmware-config.pl with CC environment variable pointing to the "gcc"
version "4.0.3".

For more information on how to troubleshoot module-related problems, please
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

**********************************

The version of workstation is : VMware-workstation-5.0.0-13124

Thanks in advance.

---

### Post by scxtt on 2006-07-04
seems like you're using a version of gcc that VMware doesn't like ... i can't remember exactly, but i think i had that problem installing VMware Server ... so it looks like you'll want to install gcc using a version like **"/usr/bin/gcc-3.4" version "3.4.6"** as the install requests ... i'm not sure if you can just install that version via synaptic (and have them both) or uninstall version 4, then install version 3.4 ...

also, take a look @ your /usr/bin/vmware-config.pl and see if there's a line that creates the "CC environment variable" and see if you can set it to where your current version of gcc is located ... maybe that's what i did, can't remember ...

---

### Post by lordelph on 2006-07-05
I managed to get VMWare working on a new Dapper installation, I made some [notes on my blog.]("http://blog.dixo.net/2006/06/05/installing-vmware-server-beta-on-ubuntu-606-dapper-drake/")

---


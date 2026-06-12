---
title: "Feisty Server and VMWare-Tools"
date: 2007-09-11
forum: Installation &amp; Upgrades
---

### Post by Zack McCool on 2007-09-11
I'm running Ubuntu 7.04 Feisty Server in a VMWare ESX 3.0 Virtual Machine.  It is running all current updates, including the latest kernel (2.6.20-16-server).

I have installed the correct headers, and build-essentials.

When I run vmware-config-tools.pl, I enter the correct path for the source, 
/usr/src/linux-headers-2.6.20-16-server/include

And the response from the install script is:
The directory of kernel headers (version @@VMWARE@@ UTS_RELEASE) does not match your running kernel (version 2.6.20-16-server).  Even if the module were to compile successfully, it would not load into the running kernel.

So, what am I to do to correct this.  I am getting quite frustrated.

Any help would be appreciated.

Joe

---

### Post by Mach1US on 2007-09-15
My vwware tools installation failed and i need to reinstall vmware tools , how to do it or how to remove previous installation ?
Trying to run installation script only produces message " Previous installation detected - aborting "

---

### Post by Pumalite on 2007-09-15
[http://www.howtoforge.com/ubuntu_feisty_fawn_vmware_server_howto](http://www.howtoforge.com/ubuntu_feisty_fawn_vmware_server_howto)

[https://help.ubuntu.com/community/VMware/Server](https://help.ubuntu.com/community/VMware/Server)

[http://www.ubuntugeek.com/how-to-install-vmware-server-from-canonical-commercial-repository-in-ubuntu-feisty.html](http://www.ubuntugeek.com/how-to-install-vmware-server-from-canonical-commercial-repository-in-ubuntu-feisty.html)

[http://ubuntuforums.org/showthread.php?t=534004](http://ubuntuforums.org/showthread.php?t=534004)

[http://ubuntuforums.org/showthread.php?t=421904](http://ubuntuforums.org/showthread.php?t=421904)

---

### Post by Mach1US on 2007-09-15
I'm trying to install feisty in xp-pro.
Thanks for the reply , unfortunately none of them has anything on reinstalling vmware tools in ubuntu .
One of them has how to on installation of them but says nothing ab  out what to do when install fails or how to reinstall them .
If you have any thing else will be greatly appreciated.THX

---

### Post by Zack McCool on 2007-09-18
> **Pumalite said:**
> [http://www.howtoforge.com/ubuntu_feisty_fawn_vmware_server_howto](http://www.howtoforge.com/ubuntu_feisty_fawn_vmware_server_howto)

[https://help.ubuntu.com/community/VMware/Server](https://help.ubuntu.com/community/VMware/Server)

[http://www.ubuntugeek.com/how-to-install-vmware-server-from-canonical-commercial-repository-in-ubuntu-feisty.html](http://www.ubuntugeek.com/how-to-install-vmware-server-from-canonical-commercial-repository-in-ubuntu-feisty.html)

[http://ubuntuforums.org/showthread.php?t=534004](http://ubuntuforums.org/showthread.php?t=534004)

[http://ubuntuforums.org/showthread.php?t=421904](http://ubuntuforums.org/showthread.php?t=421904)

That's all great, and I appreciate the attempt, but none of those addressed my question.  

I have a Feisty Server Installed under VMWare, with the latest kernel and matching headers, but cannot get the VMWare tools to install...

---

### Post by duvidel on 2007-09-21
I run Feisty Fawn 7.04 in a virtual machine on a Vista host. It wants me to install the Vmware tools package, but the .rpm doesn't open and when I try to use the .tgz, it throws an error about requiring Perl. I couldn't really care if Vmware Server is in Feisty, and in fact would rather not have the entire Vmware Server. I just want Vmware Tools so that the virtual machine itself functions more effectively. Is there a way to install just that through Apt-Get or some other method? 

Thanks for any help.

---

### Post by Pumalite on 2007-09-21
> **Zack McCool said:**
> That's all great, and I appreciate the attempt, but none of those addressed my question.  

I have a Feisty Server Installed under VMWare, with the latest kernel and matching headers, but cannot get the VMWare tools to install...

[http://www.daveshuck.com/blog/index.cfm/2007/1/4/Problem-installing-V](http://www.daveshuck.com/blog/index.cfm/2007/1/4/Problem-installing-V)

---

### Post by Zack McCool on 2007-10-05
> **Pumalite said:**
> [http://www.daveshuck.com/blog/index.cfm/2007/1/4/Problem-installing-V](http://www.daveshuck.com/blog/index.cfm/2007/1/4/Problem-installing-V)

" Sorry
There are no blog entries available that match your criteria. "

Hmmm...

---

### Post by britrb on 2007-10-09
Is there a distro of Ubuntu that will easily accept the vmware tools install, like a build of vista inside virtual pc accepts its equivilant?

---


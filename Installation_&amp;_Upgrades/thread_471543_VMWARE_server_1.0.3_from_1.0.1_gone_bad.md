---
title: "VMWARE server 1.0.3 from 1.0.1 gone bad"
date: 2007-06-12
forum: Installation &amp; Upgrades
---

### Post by rjn456 on 2007-06-12
Newbie looking for any kind of help or direction.  I tried to upgrade vmware server from 1.0.1 to 1.0.3 but received several lines of the following:

'Deep recursion on subroutine "main::installer_dir" at /home/user/vmware/vmware-1.0.3/VMware-server-1.0.3-44356/vmware-server-distrib/vmware-install.pl line 1269'.

Had to Ctrl-Z out of the script.  

To add more detail, I'm running Kubuntu 6.06 server edition on a AMD64 PC.  Before I attempted the upgrade, I updated my kernal image, headers, and restricted-modules from 2.6.15-28.51-amd64-generic to 2.6.15-28.55

I rebooted, uninstalled vmware 1.0.1, and attempted the install of vmware 1.0.3...After the first failed attempt, I tried a couple of more times.  I didn't get the error above but I also didn't see any signs of progress so I Ctrl-Z'd out.  However I did notice that my root folder kept increasing in size.  I did a file/folder search on '*vmware*' and found a ridiculous about of 'vmware' subfolders in /etc.  I deleted /etc/vmware but I wonder what other files or folders were installed or created multiple times.  

I tried to go back to vmware server 1.0.1, which had been running fine for almost a year, but get the same problem.  
As an FYI, I installed vmware server 1.0.1 based on the following guide:
[http://howtoforge.com/ubuntu_vmware_server](http://howtoforge.com/ubuntu_vmware_server)

---

### Post by rjn456 on 2007-06-13
I figured out what I did wrong but don't understand the difference.
My mistake was running the install script this way (from the root directory):
root:/#/home/user/vmware/vmware-1.0.3/VMware-server-1.0.3-44356/vmware-server-distrib/vmware-install.pl

I looked back at the howto guide and ran the script from the directory where the files where extracted:
root:/home/user/vmware/vmware-1.0.3/VMware-server-1.0.3-44356/vmware-server-distrib#./vmware-install.pl

Oh well. Live and learn.

---


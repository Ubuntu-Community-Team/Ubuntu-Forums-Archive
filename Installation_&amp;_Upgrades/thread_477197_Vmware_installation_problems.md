---
title: "Vmware installation problems"
date: 2007-06-18
forum: Installation &amp; Upgrades
---

### Post by dcalvani on 2007-06-18
hi, after trying to install Vmare server through Automatix (it didn't work) I did the following:

1) (to edit the /etc/apt/sources.list file) sudo vi /etc/apt/sources.list (and add) 
    deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main
2) (to update Ubuntu Source List) sudo apt-get update
3) (to Install Vmware Server in Ubuntu Feisty) 
sudo apt-get install vmware-server vmware-tools-kernel-modules

As a result, I got the following message:
"A previous installation of a Vmware product has been detected.
If installed it from the Vmware website, please remove it by running vmware-uninstall-pl before proceeding.
If it was installed through Ubuntu, you must purge (completely remove) the old package."

I don't know how to run vmware-uninstall.pl. I tried 'sudo apt-get autoremove vmware' 
but it didn't work: I got the following message: 'E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied) E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?'

I then pressed enter on the first message, and I got the following:

'The following packages were automatically installed and are no longer required:
  libtext-glob-perl libdate-calc-perl libcarp-clan-perl libfile-find-rule-perl
  libnumber-compare-perl libbit-vector-perl
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed
  vmware-server
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
Need to get 0B/79.4MB of archives.
After unpacking 131MB of additional disk space will be used.
Preconfiguring packages ...
(Reading database ... 185835 files and directories currently installed.)
Unpacking vmware-server (from .../vmware-server_1.0.3-1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/vmware-server_1.0.3-1_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/vmware-server_1.0.3-1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)'

Can anyone help me? Many thanks.

---

### Post by Gannin on 2007-06-18
From a terminal, try running "sudo vmware-uninstall.pl" and see if that does anything for you.

If not, go to System > Administration > Synaptic, then do a search for "vmware" and remove any components that are installed.

---

### Post by beatbros on 2007-06-18
Hi,
after a succesfull uninstall you can follow this guide that worked here in my system. (7.04)

[http://www.howtoforge.com/ubuntu_feisty_fawn_vmware_server_howto](http://www.howtoforge.com/ubuntu_feisty_fawn_vmware_server_howto)

Probably you miss to install the patch.

Bye

---

### Post by luvr on 2007-06-18
Also, once you're sure that VMware was uninstalled, and you subsequently try to reinstall, you may still get the message that *"A previous installation of a Vmware product has been detected"* (I once had that happen to me.)

In that case, look into your **/etc** directory, and see if contains a **vmware** subdirectory. If it does, then delete the subdirectory--it will be a left-over from the previous installation.

---

### Post by dcalvani on 2007-06-18
Thank you all!

I run "sudo vmware-uninstall.pl" but the Terminal says "command not found". After that I tried the synaptic package manager, searched Vmware, found one file (VM Ware-server), marked it for complete removal, and got the following (incomplete) message:

"E: vmware-server: Package is in a very bad inconsistent state - you should"

I'll try to re-download the the whole thing from [http://www.howtoforge.com/ubuntu_fei...e_server_howto](http://www.howtoforge.com/ubuntu_fei...e_server_howto). 

One question: how do you see your /etc directory ?

---

### Post by luvr on 2007-06-18
> **dcalvani said:**
> One question: how do you see your /etc directory ?

Select *"Places"* --> *"Computer"* from the GNOME menu, then open *"File System."* That will open your top-level directory (i.e., *"/"*) in a File Browser window. One of the folders in that window will be *"etc"*; open that, and you can see the contents of your *"/etc"* directory.

If you uninstalled VMware, you shouldn't see a *"vmware"* folder in *"/etc,"* or you won't be able to reinstall VMware. To remove the *"vmware"* folder, you will have to open a command-line terminal (since you will have to do the removal under the root account)--i.e., *"Applications"* --> *"Accessories"* --> *"Terminal"*--and enter the following command:
```
sudo rm -R /etc/vmware
```You will then have to enter your password in order to actually execute the command.

---

### Post by watermark on 2007-06-25
I had the same problem, and removing the /etc/vmware directory fixed that problem.  Now install fails because I don't have an eth0 interface.   That seems kinda stupid default installing to an interface someone may not have.

I gave up and  installed from the package on their website.   Stupid automatix...

---


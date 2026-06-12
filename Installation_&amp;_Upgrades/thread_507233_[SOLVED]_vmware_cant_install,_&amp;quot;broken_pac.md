---
title: "[SOLVED] vmware cant install, &amp;quot;broken packages&amp;quot;."
date: 2007-07-22
forum: Installation &amp; Upgrades
---

### Post by upthelum on 2007-07-22
Trying to install vmware server, got as far as downloading the tar but that didnt work. Found the commands to do it in terminal, ran:

apt-get install vmware-server vmware-tools-kernel-modules

Got this output:

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package vmware-tools-kernel-modules
root@ubuntu-desktop:/etc/apt# apt-get install vmware-server
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  vmware-server: Depends: update-inetd but it is not installable
                 Depends: vmware-server-kernel-modules but it is not installable
E: Broken packages
root@ubuntu-desktop:/etc/apt#

Before this i installed the build environment and tools needed for the install:

aptitude install linux-headers-`uname -r` build-essential

and

aptitude install xinetd

Does this mean i cannot install vmware?
I saw this: [http://www.howtoforge.com/ubuntu_feisty_fawn_vmware_server_howto?]("http://www.howtoforge.com/ubuntu_feisty_fawn_vmware_server_howto?")

But the sudo vmware-install.pl wouldnt work and another post said i must report a bug in feisty because of the broken packages message above.

So i then ran apt-get update and now get this:

apt-get install vmware-server vmware-tools-kernel-modules
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package vmware-tools-kernel-modules

I also added deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main to sources.list and then an update again. Yet another post said try:
sudo bash vmware-installer.pl but there's no such file.

Has anyone had this trouble before and can i possibly resolve it?
Thanks all...

---

### Post by upthelum on 2007-07-22
Started getting somewhere with this:

./vmware-install.pl

and it started to install until i got this message:

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] 

Is this the default location for these files and why are they not there. Can anyone help i'm getting closer to installation.

---

### Post by upthelum on 2007-07-23
Thought i would bring this up again as i got it to work. Ran this code:
sudo apt-get install linux-headers-**`uname -r`** build-essential 
Those aren't apostrophes!!!
This took me a while to sort out and i'm not a novice so to a total noob it could potentially take much longer.
Is there some way this can be noted for future reference somewhere on the boards outwith this thread?

---


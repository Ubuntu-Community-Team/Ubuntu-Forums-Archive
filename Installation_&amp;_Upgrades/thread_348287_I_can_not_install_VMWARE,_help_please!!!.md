---
title: "I can not install VMWARE, help please!!!"
date: 2007-01-28
forum: Installation &amp; Upgrades
---

### Post by hsalgado on 2007-01-28
Hi friends, I am having a real problem trying to install vmware.  When I go trough the process, it tell me:

Unable to find any instance of the super-server "inetd" or "xinetd".  It is 
possible that you do not have one of these packages installed on this machine. 
Please install "inetd" or "xinetd".

[I]If you do have "inetd" or "xinetd" installed, make sure that /etc/inetd.conf or
/etc/xinetd.d exists.
The configuration will continue, but you should re-run 
/usr/bin/vmware-config.pl after you fix the super-server.[/I]

Well, I download xinetd, but when I try to compile it, it gave me the following message:

[I] checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
[/I]

In thel config.log there is the following:

[I] configure: failed program was:
| /* confdefs.h.  */
[/I]

Any help????

---

### Post by gh0st on 2007-01-28
The easiest way to install xined is with apt-get rather than downloading the source and compiling it. Thats what I did when I installed VMWare server. Try this command:

sudo apt-get install xined

That worked for me. Let me know if you need anything else.

Hope that helps :D

---

### Post by hsalgado on 2007-01-28
That worked with xinetd!  I will try vmware now.

Thanks a lot!
pd:  If there is something I really like about Ubuntu... IS THIS FORUM AND THE HELP YOU PROVIDE!  You make ubuntu and Linux the best OS!

---

### Post by hsalgado on 2007-01-28
Still having problems.  It seems that xinetd is now installed, but I am still getting error messages when trying to install vmware.  This is what I got now.
[I]
Building the VMware VmPerl Scripting API.

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

Unable to compile the VMware VmPerl Scripting API.

********
The VMware VmPerl Scripting API was not installed.  Errors encountered during 
compilation and installation of the module can be found here: 
/tmp/vmware-config0

You will not be able to use the "vmware-cmd" program.

Errors can be found in the log file: 
'/tmp/vmware-config0/control-only/make.log'
********
[/I]

Please, help!!!!

---

### Post by hsalgado on 2007-01-28
I just ignored the last message and the installation worked anyway...  I guess something is not going to work, I don't know what yet.  I am installing winxp now.  Thanks a lot!

---

### Post by gh0st on 2007-01-29
> **hsalgado said:**
> Still having problems.  It seems that xinetd is now installed, but I am still getting error messages when trying to install vmware.  This is what I got now.
[I]
Building the VMware VmPerl Scripting API.

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

Unable to compile the VMware VmPerl Scripting API.

********
The VMware VmPerl Scripting API was not installed.  Errors encountered during 
compilation and installation of the module can be found here: 
/tmp/vmware-config0

You will not be able to use the "vmware-cmd" program.

Errors can be found in the log file: 
'/tmp/vmware-config0/control-only/make.log'
********
[/I]

Please, help!!!!

I haven't seen this message before and I'm not sure what VMPerl is sorry. It seems to be a Perl API that the installer can't find on your system. I don't know how this will affect VMWare when you run it. 

It seems to say you can't use vmware-cmd but I don't know what that is. Going off the name I assume it's a command line part of the VMware interface.

Have you installed WinXP anyway? If so, does it work? If it works and you can use if fine then I wouldn't worry too much about this message.

---

### Post by hsalgado on 2007-01-30
Yes, I installed winxp and it works, but very slow (I don't know if that is always the case with vmware).  I have allocated 512 ram to the winxp virtual machine and 1 or 2 processors but it is still very slow.  Thanks for your help.

---

### Post by gh0st on 2007-01-31
> **hsalgado said:**
> Yes, I installed winxp and it works, but very slow (I don't know if that is always the case with vmware).  I have allocated 512 ram to the winxp virtual machine and 1 or 2 processors but it is still very slow.  Thanks for your help.

Good news, I don't think that missing package when you installed will be affecting the speed of Windows XP. I find my WinXP virtual machine runs ok, it's not fast though. I allocated 512mb RAM to it and it does seem to be a bit slow. No slower than windows normally is on a real machine though :D

---

### Post by johnmarkschofield on 2008-06-11
Regarding the "Unable to compile the VMware VmPerl Scripting API." problem: I covered this on my blog at [http://blog.sudosu.net/2008/installing-vmware-server-106-on-ubuntu-hardy/](http://blog.sudosu.net/2008/installing-vmware-server-106-on-ubuntu-hardy/)

Short answer: apt-get install libc6-dev

---


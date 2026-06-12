---
title: "VirtualBox starting problem"
date: 2008-10-04
forum: Installation &amp; Upgrades
---

### Post by bhowmicksamrat on 2008-10-04
I am trying to install VirtualBox, but it is showing some error like

[B]VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).[/B]

What should I do now?

---

### Post by Rocket2DMn on 2008-10-04
This tends to happen after kernel upgrades, which means you need to get the latest modules packages.  Have you tried running
```
sudo apt-get install virtualbox-ose-modules-generic
```
If you have the -proposed or -backports repositories enabled, there is often a delay between the release of a new kernel and the release of compatible virtualbox-ose-modules to match that kernel.

If this is the first time you are trying to install vbox, here is a nice and easy guide that I like (since it sounds like you are trying to install windows in the VM) - [http://lifehacker.com/367714/run-windows-apps-seamlessly-inside-linux](http://lifehacker.com/367714/run-windows-apps-seamlessly-inside-linux)

If you are still having problems, please post the output of
```
uname -a
```
along with the output from the install command above.

---

### Post by NewNerd99 on 2008-10-04
Hi Rocket,
I get the same. This is the reply from the first cmd:

chris@chris-laptop:~$ sudo apt-get install virtualbox-ose-modules-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  virtualbox-ose-modules-generic: Depends: virtualbox-ose-modules-2.6.24-20-generic but it is not going to be installed
E: Broken packages
chris@chris-laptop:~$ 


....and from the second

chris@chris-laptop:~$ uname -a
Linux chris-laptop 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686 GNU/Linux
chris@chris-laptop:~$

Chris

---

### Post by Rocket2DMn on 2008-10-04
Do you have the Universe repositories enabled?  Make sure you do.

It says you are running the -19 kernel, but that the ose-modules packages depends on the -20 kernel.  I'm not sure why it's saying it depends on virtualbox-ose-modules-2.6.24-20-generic since the -20 kernel is in the -proposed repositories.  Try installing the ose modules specifically for your kernel (available in the universe repo)
```
sudo apt-get install virtualbox-ose-modules-2.6.24-19-generic
```

---

### Post by NewNerd99 on 2008-10-04
no good :(

chris@chris-laptop:~$ sudo apt-get install virtualbox-ose-modules-2.6.24-19-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  virtualbox-ose-modules-2.6.24-19-generic
0 upgraded, 1 newly installed, 0 to remove and 87 not upgraded.
1 not fully installed or removed.
Need to get 327kB of archives.
After this operation, 918kB of additional disk space will be used.
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/universe virtualbox-ose-modules-2.6.24-19-generic 24.0.4
  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/universe/v/virtualbox-ose-modules/virtualbox-ose-modules-2.6.24-19-generic_24.0.4_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/universe/v/virtualbox-ose-modules/virtualbox-ose-modules-2.6.24-19-generic_24.0.4_i386.deb)  404 Not Found [IP: 91.189.88.46 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
chris@chris-laptop:~$

---

### Post by Rocket2DMn on 2008-10-04
Try another mirror from System->Administration->Software Sources?  It looks like your mirror just doesn't have it.
Post back and I'll check up on this thread in the morning.  Good luck.

---

### Post by NewNerd99 on 2008-10-04
Thanks rocket...this is from the main server.

Really would like o get this fixed as I'm unable to get anything outside of synaptics and add/remove

chris@chris-laptop:~$ sudo apt-get install virtualbox-ose-modules-2.6.24-19-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  virtualbox-ose-modules-2.6.24-19-generic
0 upgraded, 1 newly installed, 0 to remove and 87 not upgraded.
1 not fully installed or removed.
Need to get 327kB of archives.
After this operation, 918kB of additional disk space will be used.
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe virtualbox-ose-modules-2.6.24-19-generic 24.0.4
  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/v/virtualbox-ose-modules/virtualbox-ose-modules-2.6.24-19-generic_24.0.4_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/v/virtualbox-ose-modules/virtualbox-ose-modules-2.6.24-19-generic_24.0.4_i386.deb)  404 Not Found [IP: 91.189.88.46 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
chris@chris-laptop:~$

---

### Post by Rocket2DMn on 2008-10-05
NewNerd, make sure your system is fully up to date, and please be sure that under System->Administration->Software Sources that the Universe repository is enabled, and that under the Updates tab, hardy-updates is enabled.  Typically, you should not have the -proposed repo enabled, and most certainly should not have the -backports repo enabled unless you know what you are doing.

---

### Post by jayson.rowe on 2008-10-05
Did you install Virtualbox-OSE from the Ubuntu repo's or Virtualbox-2.0 from the Sun VirtualBox Ubuntu repo?

---

### Post by bhowmicksamrat on 2008-10-05
Thanks Rocket.

At first **sudo apt-get install virtualbox-ose-modules-generic** did not work for me, but then I tried **sudo apt-get install virtualbox-ose-modules-2.6.24-19-generic** It worked out fine and fixed the problem.

---

### Post by NewNerd99 on 2008-10-06
Rocket,
Due to download constraints I'm gradually getting updates done. Will finish ALL the updates before I post back. On all your other points, they are set as you described.

Jayson,
I have put a few things on over the last few days, but am nearly 100% certain I just would have done it from the 'add/remove programs' its the easiest for me at this stage.....and sudo apt get is NOT getting!!

Thanks guys
Chris

---

### Post by NewNerd99 on 2008-10-07
Thanks for your patience guys.

All updates done and same results as the initial posts.

Chris

---

### Post by NewNerd99 on 2008-10-21
Still no joy with VirtualBox

Linux chris-laptop 2.6.24-21-generic #1 SMP Mon Aug 25 17:32:09 UTC 2008 i686 GNU/Linux
chris@chris-laptop:~$

---


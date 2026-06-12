---
title: "Lost Power... Bad things happened"
date: 2008-09-13
forum: Installation &amp; Upgrades
---

### Post by jtholt on 2008-09-13
Today I wanted to upgrade my Ubuntu installation form 7.04 (I think) to the most current release. The update process was about half done (or more), somewhere in the install stage, and the electricity in my house blinked off. Due to my lack of UPS my computer was forcefully shutdown. the power came back just a second later. So with my fingers crossed I started my computer. I was excited when I got to the login page, which looked just as it had before. So I logged in. I was presented with a blank blue screen with a black courser in the middle of it. Is there anything I can do to fix my computer short of a new install, since one of the Linux ideas is, fix the problem, don't just re-install. 

Thanks in advance for your help.

John

---

### Post by 1/0 on 2008-09-13
How far does it boot? Can you go out of X (*ctrl + alt + F2*)?

If you can't then boot from the live cd or try get in to rescue mode in GRUB (I think by pressing escape). (If from live cd chroot in to the distro.)

Now its time to try to repair the damage. Try this:

```
sudo dpkg --configure -a
```

Post error messages aso. 

I'm going out for beer in a while, just so you know. Its Saturday after all :)

---

### Post by lukjad on 2008-09-13
I hope you backed up your files. I think you may just have to bight the bullet and reinstall. There is a possibility that there is a was to get the system up and running. Wait around and see if anyone has any better suggestions. The best I can give you is this. Go to a live CD and copy your files that you can see (only from your /home folder) to an external media (USB drive, CD-R(W), DVD, floppy...) Next, wipe and reinstall. You may be able to get your system back but it is a matter of how badly it was damaged. The most important thing to do is to back up your data NOW before it may get lost.

---

### Post by cariboo on 2008-09-13
Start up in recovery mode and try:

```
sudo apt-get install -f
```

This may finishing installing the missing files.

Jim

---

### Post by jtholt on 2008-09-14
So some good news..

I got my system up and running by some combo of the above commands 

But there is one other problem

when I install anything it installs but I get errors,,

Today I installed samba and dhcpd   this is what happened when I clicked apply 

```
E: acpid: subprocess post-installation script returned error exit status 1
E: acpi-support: dependency problems - leaving unconfigured
E: powermanagement-interface: dependency problems - leaving unconfigured
E: ubuntu-desktop: dependency problems - leaving unconfigured
```

I cannot seem to copy what is in the Terminal Drop down 


Any Ideas,

Thanks for your help,

John

EDIT: If I run apt-get install -f it says

```
 :~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up acpid (1.0.4-5ubuntu8) ...
 * Loading ACPI modules...                                               [ OK ] 
 * Starting ACPI services...                                                    invoke-rc.d: initscript acpid, action "start" failed.
dpkg: error processing acpid (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of acpi-support:
 acpi-support depends on acpid (>= 1.0.4-1ubuntu4); however:
  Package acpid is not configured yet.
dpkg: error processing acpi-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of powermanagement-interface:
 powermanagement-interface depends on acpi-support (>= 0.17); however:
  Package acpi-support is not configured yet.
dpkg: error processing powermanagement-interface (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on acpi-support; however:
  Package acpi-support is not configured yet.
 ubuntu-desktop depends on acpid; however:
  Package acpid is not configured yet.
 ubuntu-desktop depends on powermanagement-interface; however:
  Package powermanagement-interface is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 acpid
 acpi-support
 powermanagement-interface
 ubuntu-desktop
E: Sub-process /usr/bin/dpkg returned an error code (1)

```


EDIT2:
wait this is pretty Much what it said in the window that I couldn't copy


Thanks, John

---

### Post by lukjad on 2008-09-14
Go to Applications->Accessories->Terminal and right click and select copy? Sometimes I make the mistake and try to do Ctrl+C too. ;) That doesn't work.

---


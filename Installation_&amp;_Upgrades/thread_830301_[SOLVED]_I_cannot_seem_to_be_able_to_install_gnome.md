---
title: "[SOLVED] I cannot seem to be able to install gnome..."
date: 2008-06-15
forum: Installation &amp; Upgrades
---

### Post by marshall.robert on 2008-06-15
Hi,

im having trouble installing gnome on ubuntu server 8.04.

'apt-get install gnome' kicks out this:

The following packages have unmet dependencies.
  gnome: Depends: gnome-desktop-environment (= 1:2.20.2.2) but it is not going to be installed
E: Broken packages


'apt-get install gnome-desktop-environment' kicks out this:

The following packages have unmet dependencies.
  gnome-desktop-environment: Depends: gnome-keyring-manager (>= 2.20.0) but it is not installable
E: Broken packages


'apt-get install gnome-keyring-manager' kicks out:

Package gnome-keyring-manager is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package gnome-keyring-manager has no installation candidate

thus i am now stuck.

i have managed to install X and synaptic and gdm, i have also checked over my sources.list several times and i am pretty sure every repo line is not commented out, i have also done apt-get update after every time i have opened it, change or not, just to make sure. also apt-get upgrade tells me its holding back packages, not sure why.

can someone please help me with this? im trying to build an environment that i can use for a live cd, and possibly install too.

thanks

-rob

---

### Post by Partyboi2 on 2008-06-16
Could you use ubuntu-desktop instead?
```
sudo apt-get -f install
``` will fix broken packages

---

### Post by marshall.robert on 2008-06-16
apt-get -f install didnt do anything, and doesnt ubuntu desktop install everything? all the games, and stuff? the command to install ubuntu-desktop works, but i didnt said no after it checked dependancies.

edit: i also just tried to install gnome-panel, which doesnt complain...

---

### Post by Partyboi2 on 2008-06-16
I did abit of searching around and found out that gnome-keyring-manager has been removed from ubuntu repo's as it has deprecated. You can download the deb package from [[COLOR=Blue]here[/COLOR]]("https://launchpad.net/ubuntu/hardy/i386/gnome-keyring-manager/2.20.0-1ubuntu1") then proceed to install gnome.

---

### Post by marshall.robert on 2008-06-16
thanks, but its still throwing an error, i have got all the dependencies installed too...

it appears to get stuck on liblaunchpad-integration0, says that liblaunchpad-integration1 replaces it, so i install, still no avail...

---

### Post by Partyboi2 on 2008-06-16
What version do you currently have installed?
```
dpkg -l liblaunchpad-integration*
```
I was able to install it by installing  liblaunchpad-integration0  which you can manually install from [[COLOR=Blue]here[/COLOR]]("http://packages.ubuntu.com/gutsy/liblaunchpad-integration0")

---

### Post by marshall.robert on 2008-06-17
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                              Version                           Description
+++-=================================-=================================-==================================================================================
un  liblaunchpad-integration0         <none>                            (no description available)
ii  liblaunchpad-integration1         0.1.19                            library for launchpad integration


im guessing that its liblaunchpad-integration1.

---

### Post by Partyboi2 on 2008-06-17
Yes that is liblaunchpad-integration1 that you have installed. Have you tried manually installing liblaunchpad-integration0 and then installing gnome? The link I provided in my last post is where you can download it from.

---

### Post by marshall.robert on 2008-06-17
well, it first didnt want to be installed, so it told me to apt-get -f install here is the terminal, should explain it better:

```
root@rubuntu:~# dpkg -i liblaunchpad-integration0_0.1.15_i386.deb 
Selecting previously deselected package liblaunchpad-integration0.
(Reading database ... 21272 files and directories currently installed.)
Unpacking liblaunchpad-integration0 (from liblaunchpad-integration0_0.1.15_i386.deb) ...
Replaced by files in installed package liblaunchpad-integration1 ...
dpkg: dependency problems prevent configuration of liblaunchpad-integration0:
 liblaunchpad-integration0 depends on launchpad-integration; however:
  Package launchpad-integration is not installed.
dpkg: error processing liblaunchpad-integration0 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 liblaunchpad-integration0
root@rubuntu:~# apt-get remove liblaunchpad-integration0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run &#8216;apt-get -f install&#8217; to correct these:
The following packages have unmet dependencies.
  gnome-keyring-manager: Depends: liblaunchpad-integration0 (>= 0.0patch26) but it is not going to be installed
E: Unmet dependencies. Try &#8216;apt-get -f install&#8217; with no packages (or specify a solution).
root@rubuntu:~# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies...Done
The following extra packages will be installed:
  launchpad-integration
The following NEW packages will be installed
  launchpad-integration
0 upgraded, 1 newly installed, 0 to remove and 4 not upgraded.
2 not fully installed or removed.
Need to get 11.6kB of archives.
After this operation, 90.1kB of additional disk space will be used.
Do you want to continue [Y/n]?  
Get: 1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/main launchpad-integration 0.1.19 [11.6kB]
Fetched 11.6kB in 0s (26.4kB/s)            
Selecting previously deselected package launchpad-integration.
(Reading database ... 21277 files and directories currently installed.)
Unpacking launchpad-integration (from .../launchpad-integration_0.1.19_all.deb) ...
Setting up launchpad-integration (0.1.19) ...

Setting up liblaunchpad-integration0 (0.1.15) ...

Setting up gnome-keyring-manager (2.20.0-1ubuntu1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place

```

then i went to install gnome and it wanted to work, but im going to wait till i get home, faster connection there.

also:
```

root@rubuntu:/# dpkg -l liblaunchpad-integration*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  liblaunchpad-i 0.1.15         library for launchpad integration
ii  liblaunchpad-i 0.1.19         library for launchpad integration

```
so im guessing, that the thing that how to solve this problem would be to install liblaunchpad-integration0 first then try to install gnome-keyringmanager, both manually, and if that fails then use dpkg -i to sort if out and you should be away!

thanks for all your help.

-rob


edit: i have found that i have to install gnome-applets seperately! it chucks a 404 error.

---

### Post by EdGato on 2008-06-19
Marked as Solved, but in case someone happens to come across this same problem, use tasksel. Type:

```
sudo tasksel
```

then select Ubuntu Desktop

[Here]("https://bugs.launchpad.net/ubuntu/+source/gnome-keyring-manager/+bug/190950")'s the source I used as reference.[]("https://bugs.launchpad.net/ubuntu/+source/gnome-keyring-manager/+bug/190950")

hth

---


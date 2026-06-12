---
title: "Vmware wont install"
date: 2008-02-03
forum: Installation &amp; Upgrades
---

### Post by Deep fried ice-cream on 2008-02-03
(I'm a noob) Ive been try to install vmware sever for some time now an the thing never seems to work. if somebody could give me terminal instructions that would be great ( Ill copy & paste how I go).
BTW I don't have a internet connection. the installer & Gusty patch are tar balls at /home/richy/Desktop/ubuntu/

---

### Post by Partyboi2 on 2008-02-04
Download [VMware-server]("http://vmware.com/download/server/") (If you have not already done so)
make sure you have xinetd, build-essential  and the linux headers installed.
You can download them from here: 
[ xinetd]("http://packages.ubuntu.com/gutsy/net/xinetd") 
[ build-essential]("http://packages.ubuntu.com/gutsy/devel/build-essential") 
[linux headers]("http://packages.ubuntu.com/gutsy/devel/linux-headers-2.6.22-14-generic") 
Note: You may need to install extra dependencies to get these packages installed which you can look for them from [Ubuntu packages]("http://packages.ubuntu.com/")
 Another way to get these all installed is to use something like [nonetdebs]("http://nonetdebs.homeip.net/") to install all the packages.
Once you have those packages installed. Open a terminal (Applications>Accessories>Terminal) change to where the vmware package is that you downloaded, in your case```
cd /home/richy/Desktop/ubuntu
```then unpack the package if you have not already done so
```
tar xvzf VMware-server-1.03-44356.tar.gz
```then change into the VMware directory
```
cd vmware-server-distrib
``` then
```
sudo ./vmware-install.pl
```You will be asked some questions, just use the default choices, **[COLOR=Red]But[/COLOR]** when you get to this part:
> Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes]choose **[COLOR=Blue]No[/COLOR]**
Then download the [patch]("http://knihovny.cvut.cz/ftp/pub/vmware/vmware-any-any-update115.tar.gz")
(If you have not already done so)
Change to the Desktop
```
cd Desktop
```Then move it to your ubuntu folder
```
mv vmware-any-any-update115 /home/richy/Desktop/ubuntu
```then enter the patch directory
```
cd /home/richy/Desktop/ubuntu/vmware-any-any-update115
```then apply the patch
```
sudo ./runme.pl
```answer the questions again, but this time when you get to
> Trying to find a suitable vmmon module for your running kernel.
Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes]choose **[COLOR=Blue]Yes[/COLOR]**, and finish answering the questions all going well afterwards it should be installed and launched from Applications>Other>VMware server console

---

### Post by Deep fried ice-cream on 2008-02-04
Isnt there a patch you need to install to install vmware on gusty?

---

### Post by Partyboi2 on 2008-02-05
have updated my previous post to include the patching.

---


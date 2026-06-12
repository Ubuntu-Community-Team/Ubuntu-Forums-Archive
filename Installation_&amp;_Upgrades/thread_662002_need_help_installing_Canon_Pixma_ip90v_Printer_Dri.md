---
title: "need help installing Canon Pixma ip90v Printer Driver"
date: 2008-01-08
forum: Installation &amp; Upgrades
---

### Post by anyo409 on 2008-01-08
Hi,
	I have a Canon Pixma ip90v Printer. I am running Gutsy & the printer gets detected by Ubuntu but when I click on test print, nothing happens. How would I go about installing a printer driver for this ? 

Thanks

---

### Post by anyo409 on 2008-01-08
anyone out there ?

---

### Post by Partyboi2 on 2008-01-08
Download the driver from the cannon website 
[http://software.canon-europe.com/products/0010457.asp](http://software.canon-europe.com/products/0010457.asp)
This will be a rpm package which needs to be converted to .deb To do that
Install alien if you have not already done so.
```
sudo apt-get install alien
```Then Cd to where the downloaded driver is. If its downloaded to your Desktop you would use
```
cd Desktop
```To get the name of the package
```
ls
```Then to convert the package
```
sudo alien -d <name of package>
```eg.
```
 sudo alien -d cnijfilter-common-2.70-2.src.rpm
```After it has converted it to a deb
get the name of the deb package
```
ls
```then install it
```
sudo dpkg -i <name of package>
```eg.
```
sudo dpkg -i cnijfilter-common_2.70-3_i386.deb
```All going well package should be installed.

---

### Post by anyo409 on 2008-01-09
I have AMD 64bit. I get wrong architecture error:  is there anyways I can use 32bit drivers with AMD 64bit?


sudo alien -d cnijfilter-common-2.70-2.src.rpm
Package build failed. Here's the log:
dh_testdir
dh_testdir
dh_testroot
dh_clean -k -d
dh_installdirs
dh_installdocs
dh_installchangelogs
find . -maxdepth 1 -mindepth 1 -not -name debian -print0 | \
                xargs -0 -r -i cp -a {} debian/cnijfilter-common
dh_compress
dh_makeshlibs
dh_installdeb
dh_shlibdeps
dh_gencontrol
dpkg-gencontrol: error: current build architecture amd64 does not appear in package's list (i386)
dh_gencontrol: command returned error code 65280
make: *** [binary-arch] Error 1
find: cnijfilter-common-2.70: No such file or directory

---

### Post by Partyboi2 on 2008-01-09
Sorry, I forgot to check if you were using 32 or 64 bit machine.
You could try turboprint. If not maybe someone else will be able to point you in the right direction for 64 bit drivers.
[http://www.linuxprinting.org/show_printer.cgi?recnum=Canon-PIXMA_iP90](http://www.linuxprinting.org/show_printer.cgi?recnum=Canon-PIXMA_iP90)

---

### Post by brytanix on 2008-03-27
Hi

I have a problem with my Canon PIXMA iP90v. I followed Partyboi2's instructions and I did installed cnijfilter-ip90_2.70-2_i386.deb successfully but nothing happens when I try to print something. In Printer Configuration window I can see the driver installed. 

Can you help me to solve the problem, please? I am a new user of Ubuntu and I am very happy with it. I tested Mandriva, Suse, Kubuntu but this is the best. No problem with installation at all but I can't go through with my printer. Please help me if you can. 

I use the newest Ubuntu 7.10.

Thank you.

---

### Post by ellalan on 2008-03-29
Try uninstalling "gnome-cups manager" in Synaptic package manager, then reinstall "gnome-cups manager". I hope this helps.

---

### Post by moondogx on 2008-05-19
Hi , I installed Hardy Heron, on a Travelmate 800, but I can't print on a Canon IP90v.

I tried all of the aforementioned methods, but I still can't print:(
I kept having the 'pstocanonij missing' problem, then I found here ([http://forums.linux-foundation.org/read.php?25,3367,3456,quote=1](http://forums.linux-foundation.org/read.php?25,3367,3456,quote=1)) a deb containing pstocanonij, which I copied in /usr/lib/cups/filter/. This removed the error, everything seems ok, but the printer just sits idle and no idle jobs are to be seen in the queue.

Any help would be most appreciated!

---


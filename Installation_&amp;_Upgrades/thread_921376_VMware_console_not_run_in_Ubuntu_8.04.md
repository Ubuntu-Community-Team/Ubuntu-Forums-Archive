---
title: "VMware console not run in Ubuntu 8.04"
date: 2008-09-16
forum: Installation &amp; Upgrades
---

### Post by Faria on 2008-09-16
Hello,

I have been installed Ubuntu 8.04.1

Then I installed the VMware server, is ok, but the vmware-server-console show some errors:

rodrigo@rodrigo-laptop:~$ vmware-server-console 
/usr/lib/vmware-server-console/bin/vmware-server-console: /usr/lib/vmware-server-console/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware-server-console/bin/vmware-server-console: /usr/lib/vmware-server-console/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
/usr/lib/vmware-server-console/bin/vmware-server-console: /usr/lib/vmware-server-console/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware-server-console/bin/vmware-server-console: /usr/lib/vmware-server-console/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
/usr/lib/vmware-server-console/bin/vmware-server-console: /usr/lib/vmware-server-console/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware-server-console/bin/vmware-server-console: /usr/lib/vmware-server-console/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)

My version gcc:

rodrigo@rodrigo-laptop:~$ gcc --version
gcc (GCC) 4.2.3 (Ubuntu 4.2.3-2ubuntu7)

All files are installed.

rodrigo@rodrigo-laptop:~$ whereis libgcc_s.so.1
libgcc_s.so: /lib/libgcc_s.so.1

rodrigo@rodrigo-laptop:~$ whereis  libcairo.so.2
libcairo.so: /usr/lib/libcairo.so.2

rodrigo@rodrigo-laptop:~$ whereis libstdc++.so.6
libstdc++.so: /usr/lib/libstdc++.so.6

Any idea ?

Best regards,

Faria

---

### Post by capnjack on 2008-09-17
I was having this issue with the VMware Server Console on Ubuntu 8.04 64-bit (Linux cmccabe-ubuntu 2.6.24-19-generic #1 SMP Wed Aug 20 17:53:40 UTC 2008 x86_64 GNU/Linux):
cmccabe@cmccabe-ubuntu:~$ vmware-server-console
/usr/lib/vmware-server-console/bin/vmware-server-console: /usr/lib/vmware-server-console/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib32/libcairo.so.2)
/usr/lib/vmware-server-console/bin/vmware-server-console: /usr/lib/vmware-server-console/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib32/libstdc++.so.6)
/usr/lib/vmware-server-console/bin/vmware-server-console: /usr/lib/vmware-server-console/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib32/libcairo.so.2)
/usr/lib/vmware-server-console/bin/vmware-server-console: /usr/lib/vmware-server-console/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib32/libstdc++.so.6)
/usr/lib/vmware-server-console/bin/vmware-server-console: /usr/lib/vmware-server-console/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib32/libcairo.so.2)
/usr/lib/vmware-server-console/bin/vmware-server-console: /usr/lib/vmware-server-console/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib32/libstdc++.so.6)

Renaming the library did the trick:

cmccabe@cmccabe-ubuntu:~$ cd /usr/lib/vmware-server-console/lib/libgcc_s.so.1
[email]cmccabe@cmccabe-ubuntu:/usr/lib/vmware-server-console/lib/libgcc_s.so[/email].1$ sudo mv libgcc_s.so.1 libgcc_s.so.1.orig

Thanks,
Chaz

---

### Post by cdmdotnet on 2008-09-22
what you&#314;l need to do is run the following commands in a terminal window

sudo cp /lib/libgcc_s.so.1 /usr/lib/vmware/lib/libgcc_s.so.1
sudo cp /usr/lib/libpng12.so.0 /usr/lib/vmware/lib/libpng12.so.0

if you are running x64 version of ubuntu you&#314;l need to run the following as well

sudo ln -s /usr/lib32 /usr/l32
sudo sed -i -e 's:usr/lib/:usr/l32/:g'  /usr/lib32/gtk-2.0/2.10.0/loader-files.d/libgtk2.0-0.loaders
sudo sed -i -e 's:usr/lib/:usr/l32/:g' /usr/lib32/libgdk_pixbuf-2.0.so.0.1200.9

the full instructions for installing vmware on hardy are located at : [http://ubuntuforums.org/showthread.php?t=779934](http://ubuntuforums.org/showthread.php?t=779934)

---

### Post by slimx3m on 2008-09-24
thnx for this.  i reinstalled my ubuntu and i forgot to do that too :D:)

---

### Post by pirato on 2008-10-23
> **cdmdotnet said:**
> what you&#314;l need to do is run the following commands in a terminal window

sudo cp /lib/libgcc_s.so.1 /usr/lib/vmware/lib/libgcc_s.so.1
sudo cp /usr/lib/libpng12.so.0 /usr/lib/vmware/lib/libpng12.so.0

if you are running x64 version of ubuntu you&#314;l need to run the following as well

sudo ln -s /usr/lib32 /usr/l32
sudo sed -i -e 's:usr/lib/:usr/l32/:g'  /usr/lib32/gtk-2.0/2.10.0/loader-files.d/libgtk2.0-0.loaders
sudo sed -i -e 's:usr/lib/:usr/l32/:g' /usr/lib32/libgdk_pixbuf-2.0.so.0.1200.9

the full instructions for installing vmware on hardy are located at : [http://ubuntuforums.org/showthread.php?t=779934](http://ubuntuforums.org/showthread.php?t=779934)
thanks this works on Kubuntu 8.04.1. VM-ware server console 1.0.4 however creates a folder for each of the libriary file e.g /usr/lib/vmware-server-console/lib/libgcc_s.so.1/libgcc_s.so.1 I simply deleted the folder and copied from the /lib dir

---


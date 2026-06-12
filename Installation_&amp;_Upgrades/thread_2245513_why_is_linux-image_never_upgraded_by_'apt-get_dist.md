---
title: "why is linux-image never upgraded by 'apt-get dist-upgrade' ?"
date: 2014-09-24
forum: Installation &amp; Upgrades
---

### Post by jason-vas-dias on 2014-09-24
Good day - sorry if this question has been answered somewhere before, but I couldn't find it -
I'd like to understand why my Ubuntu "14.04.1 LTS, Trusty Tahr" x86_64 (Haswell) system 
never upgrades the kernel automatically as part of the 'apt-get dist-upgrade' process.
The updated kernel is not even shown in 'dpkg-query -l 'linux-image*' , and I have 
to specifically request it , as happened again this morning :
```

$ apt-get dist-upgrade   
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  libssh2-1 libtar0 libx265-27 libx265-30 linux-headers-3.13.0-34
  linux-headers-3.13.0-34-generic linux-tools-3.13.0-30
  linux-tools-3.13.0-30-generic linux-tools-3.13.0-32
  linux-tools-3.13.0-32-generic linux-tools-3.13.0-34
  linux-tools-3.13.0-34-generic vlc-plugin-pulse
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  linux-headers-3.13.0-36 linux-headers-3.13.0-36-generic
  linux-tools-3.13.0-36 linux-tools-3.13.0-36-generic
The following packages will be upgraded:
  apt apt-transport-https apt-utils chromium-browser chromium-browser-l10n
  chromium-codecs-ffmpeg-extra dbus dbus-x11 libapt-inst1.5 libapt-pkg4.12
  libdbus-1-3 libdbus-1-3:i386 libdbus-1-dev linux-doc linux-headers-generic
  linux-libc-dev linux-tools-common linux-tools-generic linux-tools-virtual
19 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 72.0 MB of archives.
After this operation, 70.7 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
...

```
This upgrade completed OK, but did NOT install the new kernel.

Now I could see there were new 'linux-headers' and 'linux-tools' packages available,
(but not for the 3.13.0-36 version!)
so I had to guess 'Aha! there must be a new kernel ..' and specifically request it - it
wasn't even listed in available packages:

```

$ dpkg-query -l 'linux-image*'
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                                  Version                         Architecture                    Description
+++-=====================================================-===============================-===============================-===============================================================================================================
un  linux-image                                           <none>                          <none>                          (no description available)
un  linux-image-3.0                                       <none>                          <none>                          (no description available)
rc  linux-image-3.13.0-24-generic                         3.13.0-24.47                    amd64                           Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-30-generic                         3.13.0-30.55                    amd64                           Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-32-generic                         3.13.0-32.57                    amd64                           Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-32-lowlatency                      3.13.0-32.57                    amd64                           Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-35-generic                         3.13.0-35.62                    amd64                           Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-35-lowlatency                      3.13.0-35.62                    amd64                           Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-24-generic                   3.13.0-24.47                    amd64                           Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-30-generic                   3.13.0-30.55                    amd64                           Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-35-generic                   3.13.0-35.62                    amd64                           Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP

```

But if I actually ask for the latest kernel, it magically appears :
```

$ apt-get install linux-image-3.13.0-36-lowlatency linux-headers-3.13.0-36-lowlatency
...
The following NEW packages will be installed:
  linux-image-3.13.0-36-lowlatency
  linux-headers-3.13.0-36-lowlatency
...
done

```

ie. the last upgrade succeeded in installing the  linux-image-3.13.0-36-lowlatency and linux-headers-3.13.0-36-lowlatency packages,  which 
were not even listed in 'dpkg-query -l linux-*' .
So the questions arise:

1.  How can I ensure that 'dpkg-query -l' is showing me ALL available packages ? ( it evidently isn't wrt linux-image /linux-header packages ).
2.  How can I ensure that the kernel is automatically upgraded along with other packages ?  (it isn't unless I specifically request a particular new kernel package, whose name I have to guess because it is not listed).

Any answers would be greatly appreciated.
Thanks & Regards,
Jason

---

### Post by matt_symes on 2014-09-24
Hi

I have to be honest, i have only read the very first part of your post, however..

You don't have the linux-image-generic package installed.

Other kernels are a dependency of this so installing this will allow you to update the kernel using dist upgrade.

```
sudo apt-get install linux-image-generic
```

Kind regards

---

### Post by matt_symes on 2014-09-24
Hi

If i understand you other question correctly, dpkg shows you what you have installed and not what is available

To see what is available then use apt-cache search but remember to use apt-get update first.

Here's an example from my system. BTW, I use many aliases that i will show first.

This is what i have installed on my system.
```

matthew-laptop:/home/matthew:5 % fa ^dli
dli='dpkg -l | grep -i'
matthew-laptop:/home/matthew:5 % dli linux-image
rc  linux-image-3.13.0-32-generic                               3.13.0-32.57                           amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-34-generic                               3.13.0-34.60                           amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-35-generic                               3.13.0-35.62                           amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-36-generic                               3.13.0-36.63                           amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-32-generic                         3.13.0-32.57                           amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-34-generic                         3.13.0-34.60                           amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-35-generic                         3.13.0-35.62                           amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-36-generic                         3.13.0-36.63                           amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-generic                                         3.13.0.36.43                           amd64        Generic Linux kernel image
matthew-laptop:/home/matthew:5 %
```

This is what is available.

```

matthew-laptop:/home/matthew:5 % fa acse                     
acse='apt-cache search'
matthew-laptop:/home/matthew:5 % acse linux-image | head -n10
linux-image-3.13.0-24-generic - Linux kernel image for version 3.13.0 on 64 bit x86 SMP
linux-image-3.13.0-24-lowlatency - Linux kernel image for version 3.13.0 on 64 bit x86 SMP
linux-image-extra-3.13.0-24-generic - Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
linux-image-extra-virtual - Transitional package.
linux-image-generic - Generic Linux kernel image
linux-image-generic-lts-quantal - Generic Linux kernel image
linux-image-generic-lts-raring - Generic Linux kernel image
linux-image-generic-lts-saucy - Generic Linux kernel image
linux-image-generic-lts-trusty - Generic Linux kernel image
linux-image-lowlatency - lowlatency Linux kernel image
matthew-laptop:/home/matthew:5 % acse linux-image | wc -l    
41
matthew-laptop:/home/matthew:5 % 
```

I have only shown the first 10 of 41 available kernels.

Kind regards

---

### Post by matt_symes on 2014-09-24
Hi

Just to clarify my first post, here the linux-image-generic package description.

```

matthew-laptop:/home/matthew:5 % fa acsh                                           
acsh='apt-cache show'
matthew-laptop:/home/matthew:5 % acsh linux-image-generic | grep -A2 Description-en
Description-en: Generic Linux kernel image
 This package will always depend on the latest generic kernel image
 available.
--
Description-en: Generic Linux kernel image
 This package will always depend on the latest generic kernel image
 available.
matthew-laptop:/home/matthew:5 % 

```

Kind regards

---

### Post by jason-vas-dias on 2014-09-24
Thanks for the prompt reply , Matt - 
But I don't think that can be the issue, since 'linux-image-3.13.0-35-generic' WAS installed before I did either 'apt-get dist-upgrade' OR 'dpkg-query -l "linux-image*"' .
Here are the kernels I now have installed :
<code>
$ dpkg-query -l 'linux-image*'   
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                                  Version                         Architecture                    Description
+++-=====================================================-===============================-===============================-===============================================================================================================
un  linux-image                                           <none>                          <none>                          (no description available)
un  linux-image-3.0                                       <none>                          <none>                          (no description available)
rc  linux-image-3.13.0-24-generic                         3.13.0-24.47                    amd64                           Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-30-generic                         3.13.0-30.55                    amd64                           Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-32-generic                         3.13.0-32.57                    amd64                           Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-32-lowlatency                      3.13.0-32.57                    amd64                           Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-35-generic                         3.13.0-35.62                    amd64                           Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-35-lowlatency                      3.13.0-35.62                    amd64                           Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-36-generic                         3.13.0-36.63                    amd64                           Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-36-lowlatency                      3.13.0-36.63                    amd64                           Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-24-generic                   3.13.0-24.47                    amd64                           Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-30-generic                   3.13.0-30.55                    amd64                           Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-35-generic                   3.13.0-35.62                    amd64                           Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-36-generic                   3.13.0-36.63                    amd64                           Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
</code>

In any case,  my query is really how to make 'dpkg-query -l' report on ALL AVAILABLE PACKAGES , which it evidently is not doing .
Or is there some other command I should be using to list available packages ?

---

### Post by matt_symes on 2014-09-24
Hi

You don't have linux-image-generic package installed.

Open up a terminal and type

```
sudo apt-get install linux-image-generic
```

This will pull in new kernels using a dist-upgrade.

BTW: You use code tags like this.

[noparse]```
text
```[/noparse]

Kind regards

---

### Post by jason-vas-dias on 2014-09-24
OK, I installed the linux-image-generic package .  But how was I meant to know that it was available ?
It was not listed in 'dpkg-query -l linux-image*' until I installed it with 'apt-get install linux-image-generic' .
If dpkg-query -l is NOT meant to be listing available but uninstalled packages, it has a bug - it lists MANY uninstalled packages.
If it is meant to be listing available packages, it has a bug, because it does not list available kernel packages.
Is there any command I can use to get a listing of ALL available packages,  like 'dpkg-query -l', with one entry
per line, showing the package name, version, and a brief description  ?
Incidentally, 'apt-cache show' seems to be unusable for this purpose - it dumps the long multi-line entries for each
package,  and does not honor its documented '--names-only' option , and seems to have no 'names + version only' option.
So one is meant to write scripts to parse apt-cache long output to get a list of available packages ?   
Is there no equivalent to 'yum list available' ?

---

### Post by matt_symes on 2014-09-24
Hi

> In any case,  my query is really how to make 'dpkg-query -l' report on  ALL AVAILABLE PACKAGES , which it evidently is not doing .

To answer your other question - sorry i was bidding on a new gigabit switch on ebay; didn't get it :

Do you do want to list all the packages installed on your system ?

If so, use this command.

```
dpkg -l
```

Do you want to list all the packages available in all the repositories and PPAs you have listed in /etc/apt/sources.list{,.d/*} . ie. all available packages ?

If so, try this command.

```
apt-cache search ^
```

If you want to use dpkg-query to list all available installed and not installed packages on your system that dpkg sees, try this command.

```
dpkg-query -l "*"
```

Maybe i'm not really understanding what you want and that's most probably because i have not had my requisite number of cups of coffee yet today :)

Kind regards

---


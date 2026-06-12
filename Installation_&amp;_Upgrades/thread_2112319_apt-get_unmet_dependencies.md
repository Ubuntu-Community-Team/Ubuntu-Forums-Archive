---
title: "apt-get unmet dependencies"
date: 2013-02-04
forum: Installation &amp; Upgrades
---

### Post by TnTSCS on 2013-02-04
it appears my ubuntu 12.04 LTS, currently on 3.2.0-36-generic, is having issues upgrading to -37... I think it's stuck half way or something.

See attached screenshot for the error I get when I try to do anything with apt-get.  

When the server starts, I get a warning about /boot only having 2.5mb space left.  I tried removing old kernels, but am greeted with the error depicted in the screenshot.

I tried to install ubuntu-tweak and synaptic, but am greeted with the same error message.

The server still runs w/o issue, just the warning about low space on /boot and I can't complete the kernel update to -37.

I've tried sudo apt-get autoremove as well, but still same error.

---

### Post by ibjsb4 on 2013-02-04
There are several ways to remove old kernels, one way:

[https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels#Manual](https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels#Manual)

Last post:

[http://ubuntuforums.org/showthread.php?t=2098490&page=2](http://ubuntuforums.org/showthread.php?t=2098490&page=2)

Other ways:

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=remove+old+kernels+command+line+terminal&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=remove+old+kernels+command+line+terminal&as_qdr=all&sa=Google+Search&lang=en)

---

### Post by TnTSCS on 2013-02-04
Thanks ibjsb4, however, those links outline all the things I've tried.  I'm at a point where I can't install or remove anything because Ubuntu is stuck in lala land trying/waiting to update from 3.2.0.37.44 to 3.2.0.37.45 or something.

See attached photo of my attempt at ```
sudo apt-get purge $(dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | head -n -1)
```

Also, when I try to sudo apt-get -f install, I get the following:
```

mylogon:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.2.0-34 linux-headers-3.2.0-34-generic fwbuilder-doc
  fwbuilder-common
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-image-server linux-server
The following packages will be upgraded:
  linux-image-server linux-server
2 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
4 not fully installed or removed.
Need to get 0 B/4,458 B of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Setting up initramfs-tools (0.99ubuntu13.1) ...
update-initramfs: deferring update (trigger activated)
Setting up linux-image-3.2.0-37-generic (3.2.0-37.58) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
The link /initrd.img is a dangling linkto /boot/initrd.img-3.2.0-37-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-37-generic /boot/vmlinuz-3.2.0-37-generic
update-initramfs: Generating /boot/initrd.img-3.2.0-37-generic

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-3.2.0-37-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-37-generic.postinst line 1010.
dpkg: error processing linux-image-3.2.0-37-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-server:
 linux-image-server depends on linux-image-3.2.0-37-generic; however:
  Package linux-image-3.2.0-37-generic is not configured yet.
dpkg: error processing linux-image-server (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-server:
 linux-server depends on linux-image-server (= 3.2.0.37.44); however:
  Package linux-image-server is not configured yet.
 linux-server depends on linux-headers-server (= 3.2.0.37.44); however:
  Version of linux-headers-server on system is 3.2.0.37.45.
dpkg: error processing linux-server (--configure):
 dependency problems - leaving unconfigured
Processing triggers for initramfs-tools ...
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    update-initramfs: Generating /boot/initrd.img-3.2.0-36-generic

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-3.2.0-36-generic with 1.
dpkg: error processing initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-image-3.2.0-37-generic
 linux-image-server
 linux-server
 initramfs-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)

```[/spoiler]

---

### Post by jodpcc on 2013-02-05
I think I am having the same problem, seemingly caused by an upgrade that failed due to insufficient space on boot drive.
Having alleviated the space problem, I am unable to to fix the upgrade:


xxxxxx@server1:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.2.0-31-generic linux-headers-3.2.0-31 linux-headers-3.2.0-32 linux-headers-3.2.0-34 linux-headers-3.2.0-29
  linux-headers-3.2.0-35 linux-headers-3.2.0-36 linux-headers-3.2.0-34-generic linux-headers-3.2.0-29-generic libutouch-evemu1
  libutouch-geis1 libutouch-frame1 linux-headers-3.2.0-32-generic linux-headers-3.2.0-35-generic libutouch-grail1
  linux-headers-3.2.0-36-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-server
The following packages will be upgraded:
  linux-server
1 upgraded, 0 newly installed, 0 to remove and 143 not upgraded.
1 not fully installed or removed.
Need to get 0 B/1,734 B of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: dependency problems prevent configuration of linux-server:
 linux-server depends on linux-image-server (= 3.2.0.37.44); however:
  Version of linux-image-server on system is 3.2.0.37.45.
 linux-server depends on linux-headers-server (= 3.2.0.37.44); however:
  Version of linux-headers-server on system is 3.2.0.37.45.
dpkg: error processing linux-server (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Errors were encountered while processing:
 linux-server
E: Sub-process /usr/bin/dpkg returned an error code (1)
xxxxxx@server1:~$

---

### Post by ibjsb4 on 2013-02-05
And did you try

```
sudo apt-get autoremove
```

---

### Post by furything on 2013-02-05
TnTSCS
Your log file is complaining about disk space. You must be running out.

Have a look at what archived log files you can get rid of.

More importantly using package manager, how many kernel images have you got?

If more than 2 start there and 'completely remove' (purge) them in the package manager. You want headers and matching image
e.g. linux-headers-3.5.0-17
linux-headers-3.5.0-17-generic
linux-image-3.5.0-17-generic
linux-image-extra-3.5.0-17-generic

Use disk utility to check your hard disk is not failing - check SMART data should be green

---

### Post by furything on 2013-02-05
jodpcc
as asked by ibjsb4 have you tried the ```
sudo apt-get automremove
```

If fails also try ```
sudo apt-get dist-upgrade
```
last one fixed very similar for me

---

### Post by jodpcc on 2013-02-05
Thanks for the advice.  I had already tried autoremove and just gave dist-upgrade a go .... Unfortunately both issue same error:

E: Unmet dpenendencies. Try using -f

I also tried the advised apt-get -f install but to no avail :-(

Appreciate your help :-)

---

### Post by iponeverything on 2013-02-05
find and download the debs for:

 linux-image-server 3.2.0.37.44 
and
 linux-headers-server 3.2.0.37.44

and install them using "sudo dpkg -i <package>"

---

### Post by jodpcc on 2013-02-05
> **iponeverything said:**
> find and download the debs for:

 linux-image-server 3.2.0.37.44 
and
 linux-headers-server 3.2.0.37.44

and install them using "sudo dpkg -i <package>"


Sorry, would you be able to to detail the steps involved a little more; I'm afraid you've lost me :oops:
(Pretend you're talking to an idiot, you won't be far wrong .... :) )

---

### Post by TnTSCS on 2013-02-05
I also tried autoremove and dist-upgrade, but still get the error about 3.2.0.37.44 is needed but 3.2.0.37.45 is installed... and I can't use anything apt-get without that error popping up.

I tried searching for linux-image-server-3.2.0.37.44 and headers, but could not find it - found tons of links for 37.45

---

### Post by dino99 on 2013-02-06
To those with deprecated configs:

Note: Since 12.04, there is no difference in kernel between Ubuntu Desktop and Ubuntu Server since linux-image-server is merged into linux-image-generic. 

[https://help.ubuntu.com/community/ServerFaq](https://help.ubuntu.com/community/ServerFaq)

So check your /etc/apt/sources.list, and update; then upgrade packages that exist  ):P

---

### Post by furything on 2013-02-06
TntSCS
Did you check your hard drive using the disk utility as suggested?
What about cleaning up some space

try
```
sudo apt-get clean
```To clean up package cache
This should give you room

The auto remove dist upgrade comments were just for jodpcc

your log states no disk space - you have to sort this out first

Have a look here encase this is your exact same problem

[http://ubuntuforums.org/showthread.php?t=889368](http://ubuntuforums.org/showthread.php?t=889368)

---

### Post by joma on 2013-02-06
I've had the same problem. Here is how I solved it:

```

# dpkg -l | grep linux-server
iU  linux-server                       3.2.0.37.44                         Complete Linux kernel on Server Equipment.
# dpkg --configure linux-server
dpkg: dependency problems prevent configuration of linux-server:
 linux-server depends on linux-image-server (= 3.2.0.37.44); however:
  Version of linux-image-server on system is 3.2.0.37.45.
 linux-server depends on linux-headers-server (= 3.2.0.37.44); however:
  Version of linux-headers-server on system is 3.2.0.37.45.
dpkg: error processing linux-server (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-server

```

First locate the 3.2.0.37.44 packages

```

# locate 3.2.0.37.44 
/var/cache/apt/archives/linux-headers-server_3.2.0.37.44_amd64.deb
/var/cache/apt/archives/linux-image-server_3.2.0.37.44_amd64.deb
/var/cache/apt/archives/linux-server_3.2.0.37.44_amd64.deb

```

If you look at the installed packages you see that headers-server and image-server are ahead of linux-server
```

# dpkg -l | grep 3.2.0.37.4
ii  linux-headers-server               3.2.0.37.45                         Linux kernel headers on Server Equipment.
ii  linux-image-server                 3.2.0.37.45                         Linux kernel image on Server Equipment.
iU  linux-server                       3.2.0.37.44                         Complete Linux kernel on Server Equipment.

```

Remove linux-headers-server and linux-image-server. It seems to be safe
```

# dpkg -r linux-headers-server linux-image-server
(Reading database ... 132581 files and directories currently installed.)
Removing linux-headers-server ...
Removing linux-image-server ...

# dpkg -l linux-headers-server linux-image-server
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
un  linux-headers- <none>         (no description available)
un  linux-image-se <none>         (no description available)

```

Now intall the linux 3.2.0.37.44 headers and image:
```

# dpkg -i /var/cache/apt/archives/linux-headers-server_3.2.0.37.44_amd64.deb /var/cache/apt/archives/linux-image-server_3.2.0.37.44_amd64.debSelecting previously unselected package linux-headers-server.

```

Configure and serve... ;)
```

# dpkg --configure linux-server
Setting up linux-server (3.2.0.37.44) ...

```

Last. Write 20 times 
> 
I shall not dpkg -r the running kernel...

;) That's what I deed.

Cheers

---

### Post by jodpcc on 2013-02-07
Thanks a million for your help peeps :D

I followed Joma's advice and that cleared it up nicely.  apt-get is now working like a dream again.

Just one more thing to do now:

I shall not dpkg -r the running kernel... 
I shall not dpkg -r the running kernel... 
I shall not dpkg -r the running kernel... ....... ):P

---

### Post by TnTSCS on 2013-02-07
I'm going to try booting to gparted live and grow my /boot partition - it came setup with only 90MBs :(

Increasing it to 500MBs... will take an hour or more.

---

### Post by TnTSCS on 2013-02-07
Solved for me anyways...

What I ended up doing was:

1) boot with gparted and resized my /boot from 80MB to 500MB
2) found out I didn't have the following two files in /var/cache/apt/archives
 a) linux-server_3.2.0.37.45_amd64.deb
 b) linux-headers-server_3.2.0.37.45_amd64.deb

With the above two (and probably trying all of the suggestions in this thread) my problem has been solved.

---


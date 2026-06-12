---
title: "trouble with apt-get upgrade"
date: 2013-11-13
forum: Installation &amp; Upgrades
---

### Post by slgtheindividual on 2013-11-13
Hi, I'm having problems when trying to run apt-get upgrade

```


$sudo apt-get upgrade;


Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  gir1.2-gtk-3.0 google-chrome-stable hud indicator-appmenu initramfs-tools initramfs-tools-bin kdelibs-bin kdelibs5-data kdelibs5-plugins kdoctools libavcodec53
  libavformat53 libavutil51 libgail-3-0 libgnome-media-profiles-3.0-0 libgtk-3-0 libgtk-3-bin libgtk-3-common libhud-client2 libido3-0.1-0 libkcmutils4
  libkde3support4 libkdeclarative5 libkdecore5 libkdesu5 libkdeui5 libkdewebkit5 libkdnssd4 libkemoticons4 libkfile4 libkhtml5 libkidletime4 libkio5 libkjsapi4
  libkjsembed4 libkmediaplayer4 libknewstuff2-4 libknewstuff3-4 libknotifyconfig4 libkntlm4 libkparts4 libkprintutils4 libkpty4 libkrosscore4 libktexteditor4
  libkunitconversion4 liblxc0 libnepomuk4 libnepomukquery4a libnepomukutils4 libplasma3 libpostproc52 libsolid4 libswscale2 libthreadweaver4 lxc lxc-templates
  python3-lxc shim-signed
59 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 67.6 MB of archives.
After this operation, 9,352 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://dl.google.com/linux/chrome/deb/ stable/main google-chrome-stable amd64 31.0.1650.48-1 [48.7 MB]
Get:2 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libavutil51 amd64 6:0.8.9-0ubuntu0.13.10.1 [56.3 kB]
Get:3 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libavcodec53 amd64 6:0.8.9-0ubuntu0.13.10.1 [2,321 kB]
Get:4 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libavformat53 amd64 6:0.8.9-0ubuntu0.13.10.1 [434 kB]
Get:5 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libgtk-3-common all 3.8.6-0ubuntu2 [155 kB]
Get:6 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libgail-3-0 amd64 3.8.6-0ubuntu2 [20.2 kB]
Get:7 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libgtk-3-0 amd64 3.8.6-0ubuntu2 [1,850 kB]
Get:8 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libhud-client2 amd64 13.10.1+13.10.20131031-0ubuntu1 [34.7 kB]
Get:9 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libido3-0.1-0 amd64 13.10.0+13.10.20131031-0ubuntu1 [58.3 kB]
Get:10 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main lxc-templates all 1.0.0~alpha1-0ubuntu13 [41.6 kB]
Get:11 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main python3-lxc amd64 1.0.0~alpha1-0ubuntu13 [18.2 kB]
Get:12 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main liblxc0 amd64 1.0.0~alpha1-0ubuntu13 [137 kB]
Get:13 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main lxc amd64 1.0.0~alpha1-0ubuntu13 [140 kB]
Get:14 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libpostproc52 amd64 6:0.8.9-0ubuntu0.13.10.1 [35.9 kB]
Get:15 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libswscale2 amd64 6:0.8.9-0ubuntu0.13.10.1 [76.6 kB]
Get:16 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main initramfs-tools-bin amd64 0.103ubuntu1.1 [9,872 B]
Get:17 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main initramfs-tools all 0.103ubuntu1.1 [49.1 kB]
Get:18 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main gir1.2-gtk-3.0 amd64 3.8.6-0ubuntu2 [169 kB]
Get:19 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main hud amd64 13.10.1+13.10.20131031-0ubuntu1 [166 kB]
Get:20 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main indicator-appmenu amd64 13.01.0+13.10.20131031-0ubuntu1 [29.5 kB]
Get:21 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libknotifyconfig4 amd64 4:4.11.2-0ubuntu2.1 [39.4 kB]
Get:22 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libplasma3 amd64 4:4.11.2-0ubuntu2.1 [885 kB]
Get:23 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libknewstuff3-4 amd64 4:4.11.2-0ubuntu2.1 [151 kB]
Get:24 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libknewstuff2-4 amd64 4:4.11.2-0ubuntu2.1 [132 kB]
Get:25 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libkunitconversion4 amd64 4:4.11.2-0ubuntu2.1 [81.5 kB]
Get:26 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/universe kdelibs5-plugins amd64 4:4.11.2-0ubuntu2.1 [925 kB]
Get:27 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libkhtml5 amd64 4:4.11.2-0ubuntu2.1 [1,918 kB]
Get:28 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libktexteditor4 amd64 4:4.11.2-0ubuntu2.1 [96.2 kB]
Get:29 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libkprintutils4 amd64 4:4.11.2-0ubuntu2.1 [27.9 kB]
Get:30 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libkmediaplayer4 amd64 4:4.11.2-0ubuntu2.1 [29.2 kB]
Get:31 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libkdewebkit5 amd64 4:4.11.2-0ubuntu2.1 [61.8 kB]
Get:32 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libkde3support4 amd64 4:4.11.2-0ubuntu2.1 [295 kB]
Get:33 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libkparts4 amd64 4:4.11.2-0ubuntu2.1 [118 kB]
Get:34 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libkfile4 amd64 4:4.11.2-0ubuntu2.1 [215 kB]                                                            
Get:35 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libkemoticons4 amd64 4:4.11.2-0ubuntu2.1 [41.4 kB]                                                      
Get:36 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main kdoctools amd64 4:4.11.2-0ubuntu2.1 [172 kB]                                                            
Get:37 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main kdelibs-bin amd64 4:4.11.2-0ubuntu2.1 [199 kB]                                                          
Get:38 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libkio5 amd64 4:4.11.2-0ubuntu2.1 [826 kB]                                                              
Get:39 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libsolid4 amd64 4:4.11.2-0ubuntu2.1 [265 kB]                                                            
Get:40 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libnepomukutils4 amd64 4:4.11.2-0ubuntu2.1 [85.4 kB]                                                    
Get:41 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libnepomukquery4a amd64 4:4.11.2-0ubuntu2.1 [107 kB]                                                    
Get:42 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libnepomuk4 amd64 4:4.11.2-0ubuntu2.1 [203 kB]                                                          
Get:43 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libkjsembed4 amd64 4:4.11.2-0ubuntu2.1 [303 kB]                                                         
Get:44 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libkjsapi4 amd64 4:4.11.2-0ubuntu2.1 [257 kB]                                                           
Get:45 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libkrosscore4 amd64 4:4.11.2-0ubuntu2.1 [55.7 kB]                                                       
Get:46 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libkidletime4 amd64 4:4.11.2-0ubuntu2.1 [37.4 kB]                                                       
Get:47 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libkdnssd4 amd64 4:4.11.2-0ubuntu2.1 [66.1 kB]                                                          
Get:48 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libkdeclarative5 amd64 4:4.11.2-0ubuntu2.1 [38.5 kB]                                                    
Get:49 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libkcmutils4 amd64 4:4.11.2-0ubuntu2.1 [92.0 kB]                                                        
Get:50 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libkdeui5 amd64 4:4.11.2-0ubuntu2.1 [1,261 kB]                                                          
Get:51 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libthreadweaver4 amd64 4:4.11.2-0ubuntu2.1 [46.7 kB]                                                    
Get:52 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libkdesu5 amd64 4:4.11.2-0ubuntu2.1 [50.9 kB]                                                           
Get:53 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libkpty4 amd64 4:4.11.2-0ubuntu2.1 [32.7 kB]                                                            
Get:54 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libkntlm4 amd64 4:4.11.2-0ubuntu2.1 [28.5 kB]                                                           
Get:55 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libkdecore5 amd64 4:4.11.2-0ubuntu2.1 [899 kB]                                                          
Get:56 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main kdelibs5-data all 4:4.11.2-0ubuntu2.1 [2,579 kB]                                                        
Get:57 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/universe libgnome-media-profiles-3.0-0 amd64 3.0.0-1ubuntu2 [54.3 kB]                                        
Get:58 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libgtk-3-bin amd64 3.8.6-0ubuntu2 [18.2 kB]                                                             
Get:59 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main shim-signed amd64 1.5~13.10.1+0.4-0ubuntu4 [432 kB]                                                     
Fetched 67.6 MB in 18s (3,636 kB/s)                                                                                                                                    
Extract templates from packages: 100%
Setting up procps (1:3.3.4-2) ...
update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults
insserv: Service mountkernfs has to be enabled to start service procps
insserv: exiting now!
update-rc.d: error: insserv rejected the script header
dpkg: error processing procps (--configure):
 subprocess installed post-installation script returned error exit status 1
configured to not write apport reports
                                      dpkg: dependency problems prevent configuration of udev:
 udev depends on procps; however:
  Package procps is not configured yet.


dpkg: error processing udev (--configure):
 dependency problems - leaving unconfigured
configured to not write apport reports
                                      Errors were encountered while processing:
 procps
 udev
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

also

```

$ sudo dpkg --configure -a

Setting up procps (1:3.3.4-2) ...
update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults
insserv: Service mountkernfs has to be enabled to start service procps
insserv: exiting now!
update-rc.d: error: insserv rejected the script header
dpkg: error processing procps (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of udev:
 udev depends on procps; however:
  Package procps is not configured yet.


dpkg: error processing udev (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 procps
 udev



```

```

~$ sudo apt-get -f install


Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 59 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up procps (1:3.3.4-2) ...
update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults
insserv: Service mountkernfs has to be enabled to start service procps
insserv: exiting now!
update-rc.d: error: insserv rejected the script header
dpkg: error processing procps (--configure):
 subprocess installed post-installation script returned error exit status 1
configured to not write apport reports
                                      dpkg: dependency problems prevent configuration of udev:
 udev depends on procps; however:
  Package procps is not configured yet.


dpkg: error processing udev (--configure):
 dependency problems - leaving unconfigured
configured to not write apport reports
                                      Errors were encountered while processing:
 procps
 udev
E: Sub-process /usr/bin/dpkg returned an error code (1)



```

```
~$ sudo apt-get dist-upgrade

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  gir1.2-gtk-3.0 google-chrome-stable hud indicator-appmenu initramfs-tools initramfs-tools-bin kdelibs-bin kdelibs5-data kdelibs5-plugins kdoctools libavcodec53
  libavformat53 libavutil51 libgail-3-0 libgnome-media-profiles-3.0-0 libgtk-3-0 libgtk-3-bin libgtk-3-common libhud-client2 libido3-0.1-0 libkcmutils4
  libkde3support4 libkdeclarative5 libkdecore5 libkdesu5 libkdeui5 libkdewebkit5 libkdnssd4 libkemoticons4 libkfile4 libkhtml5 libkidletime4 libkio5 libkjsapi4
  libkjsembed4 libkmediaplayer4 libknewstuff2-4 libknewstuff3-4 libknotifyconfig4 libkntlm4 libkparts4 libkprintutils4 libkpty4 libkrosscore4 libktexteditor4
  libkunitconversion4 liblxc0 libnepomuk4 libnepomukquery4a libnepomukutils4 libplasma3 libpostproc52 libsolid4 libswscale2 libthreadweaver4 lxc lxc-templates
  python3-lxc shim-signed
59 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0 B/67.6 MB of archives.
After this operation, 9,352 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Extract templates from packages: 100%
Setting up procps (1:3.3.4-2) ...
update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults
insserv: Service mountkernfs has to be enabled to start service procps
insserv: exiting now!
update-rc.d: error: insserv rejected the script header
dpkg: error processing procps (--configure):
 subprocess installed post-installation script returned error exit status 1
configured to not write apport reports
                                      dpkg: dependency problems prevent configuration of udev:
 udev depends on procps; however:
  Package procps is not configured yet.


dpkg: error processing udev (--configure):
 dependency problems - leaving unconfigured
configured to not write apport reports
                                      Errors were encountered while processing:
 procps
 udev
E: Sub-process /usr/bin/dpkg returned an error code (1)



```

I have no idea what the error codes mean, any help would be greatly appreciated

---

### Post by Bashing-om on 2013-11-13
slgtheindividual; Hi !

All the errors point back to "procps" not configured .
Let's see what results when it is (re-)configured, and maybe get some more information.
Post back - between code tags - the out put of Terminal codes:
```

dpkg -l procps
sudo dpkg-reconfigure procps

```
Maybe get an idea of what is not going on.

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by Bucky Ball on 2013-11-13
Just a note. ALWAYS run 'sudo apt-get update' prior to 'sudo apt-get upgrade'. Just in case you don't. ;)

---

### Post by slgtheindividual on 2013-11-13
Thank you for the reply. 
Here is what I got for both:

```

~$ dpkg -l procps

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
iF  procps         1:3.3.4-2    amd64        /proc file system utilities



``` 

```

~$ sudo dpkg-reconfigure procps

/usr/sbin/dpkg-reconfigure: procps is broken or not fully installed.

```


Ok, I always do, but thank you for the info, why is it that it should be that way? Thank you for any help you can give

---

### Post by Bashing-om on 2013-11-13
slgtheindividual; Hey .

due to this notice:
> 
procps is broken or not fully installed.

let's see what results when we do install it:
```

sudo apt-get install procps

```
Looking to get additional information as to what is missing.

As to why run "update" ..The package management system relies on numerous index and control files, amongst which are data bases on what is actually installed. In the "update" process these databases are compared with the databases residing on the mirror, and the databases on your system are updated to correspond to what is available and installable from that mirror.

[INDENT][INDENT]where there is cause there is effect
[/INDENT][/INDENT]

---

### Post by slgtheindividual on 2013-11-13
ok I did that and got the following

```

~$ sudo apt-get install procps

Reading package lists... Done
Building dependency tree       
Reading state information... Done
procps is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 61 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up procps (1:3.3.4-2) ...
update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults
insserv: Service mountkernfs has to be enabled to start service procps
insserv: exiting now!
update-rc.d: error: insserv rejected the script header
dpkg: error processing procps (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of udev:
 udev depends on procps; however:
  Package procps is not configured yet.


dpkg: error processing udev (--configure):
 dependency problems - leaving unconfigured
configured to not write apport reports
                                      configured to not write apport reports
                                                                            Errors were encountered while processing:
 procps
 udev
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

ok cool thanx

---

### Post by Bashing-om on 2013-11-13
slgtheindividual; Well !

That was an exercise in futility . Did not tell us anything we did not know, and no closer to what is wrong. 
Punting: 
what returns from :
```

dpkg -l initscripts

```
because we see:
> 
update-rc.d: error: insserv rejected the script header


[INDENT][INDENT]we be look'n
[/INDENT][/INDENT]

---

### Post by slgtheindividual on 2013-11-13
that gives me the following:

```

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  initscripts    2.88dsf-41ub amd64        scripts for initializing and shut

```

also just to note, I don't know what any of this means, I'm not exactly an advanced user, but I really appreciate all of the help, thank you all

---

### Post by Bashing-om on 2013-11-13
slgtheindividual; Hey,

Presently I am a bit confused:
> 
<launchpad>
Steve Langasek (vorlon) wrote on 2011-09-19:	 #3
As discussed on IRC, all Ubuntu systems are supposed to have a /etc/init.d/.legacy-bootordering flag file telling update-rc.d (and /etc/init.d/rc) not to use insserv/startpar, which will fail terribly on Ubuntu.

Is the file in question existent ?
```

ls -la /etc/init.d/.legacy-bootordering

```
and what returns from this check:
```

/usr/share/insserv/check-initd-order

```
In the process of fault isolation ->
[INDENT][INDENT]do not know where this leads
[/INDENT][/INDENT]

---

### Post by slgtheindividual on 2013-11-14
ok so this is what I get:

```

~$ ls -la /etc/init.d/.legacy-bootordering

-rw-r--r-- 1 root root 0 Oct 16 19:59 /etc/init.d/.legacy-bootordering

```

the second command returns nothing:
```
~$ /usr/share/insserv/check-initd-order

~$
```

---

### Post by slgtheindividual on 2013-11-14
I don't know if it's relevant but if it's something to do with booting I'm currently dual booting windows 8 with EFI

---

### Post by Bashing-om on 2013-11-14
slgtheindividual;

That last is all to the good, no error there. I am back to the drawing board. I am stumped presently on how to identify that script that "insserv" is having the problem with.

Let's try this shotgun approach and see what results, I can see no harm in trying.
```

sudo apt-get install --reinstall insserv sysv-rc

```

[INDENT][INDENT]worth a shot
[/INDENT][/INDENT]

---

### Post by slgtheindividual on 2013-11-14
well that's good. 

Unfortunately this doesn't seem to help:

```

~$ sudo apt-get install --reinstall insserv sysv-rc

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reinstallation of sysv-rc is not possible, it cannot be downloaded.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 61 not upgraded.
2 not fully installed or removed.
Need to get 43.3 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://gb.archive.ubuntu.com/ubuntu/ saucy/main insserv amd64 1.14.0-5ubuntu2 [43.3 kB]
Fetched 43.3 kB in 0s (67.2 kB/s)  
Setting up procps (1:3.3.4-2) ...
update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults
insserv: Service mountkernfs has to be enabled to start service procps
insserv: exiting now!
update-rc.d: error: insserv rejected the script header
dpkg: error processing procps (--configure):
 subprocess installed post-installation script returned error exit status 1
configured to not write apport reports
                                      dpkg: dependency problems prevent configuration of udev:
 udev depends on procps; however:
  Package procps is not configured yet.


dpkg: error processing udev (--configure):
 dependency problems - leaving unconfigured
configured to not write apport reports
                                      Errors were encountered while processing:
 procps
 udev
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by Bashing-om on 2013-11-14
slgtheindividual; Yuk !

Well, Let's take the package managers hint - Service mountkernfs  - as the possible malfunction.

Lemme see what I can find out about that service.

[INDENT][INDENT]I'll be Baaacck
[/INDENT][/INDENT]

---

### Post by slgtheindividual on 2013-11-14
Ok, thank you very much, I really appreciate all the time and effort

---

### Post by Bashing-om on 2013-11-14
slgtheindividual; Hey,

I am not making much headway in an attempt to comprehend.

Let's see if "mountkernfs" is running; post back the out put of terminal command:
```

initctl list | grep mountkernfs.sh

```

and is the control file corrupt ? show me :
```

cat /etc/init/mountkernfs.sh.conf

```

I keep running into "mountkernfs" in conjunction with virtual machines.
Are you in fact running in a VM ? Or trying to start a VM ??

[INDENT][INDENT][INDENT]sometimes I wonder othertimes I just do not know
[/INDENT][/INDENT][/INDENT]

---

### Post by slgtheindividual on 2013-11-14
That's ok, I appreciate you trying.

Ok well the first command returned nothing
```
~$ initctl list | grep mountkernfs.sh

~$
```

the second gave me:

```

~$ cat /etc/init/mountkernfs.sh.conf
# mountkernfs.sh - compatibility job for sysvinit dependencies
#
# This job runs once virtual filesystems are mounted, to signal startpar
# that other rcS jobs relying on the historic mountkernfs.sh interface can
# continue.


description	"Signal sysvinit that virtual filesystems are mounted"


start on virtual-filesystems

```

no, I'm not running a VM or doing anything VM related, just a normal ubuntu desktop 13.10 on my laptop (acer aspire e1-571) dual booting with windows 8 efi, had no problems since I got it until now.

---

### Post by Bashing-om on 2013-11-14
slgtheindividual; Well, that is some progress;

"initctl list | grep mountkernfs.sh" should have returned:
> 
sysop@1304mini:~$ initctl list | grep mountkernfs.sh
mountkernfs.sh start/running
sysop@1304mini:~$

The file that I had half-way expected to be corrupted looks good !

So, the question now is why is it not running ? The process is failing  - some where.
I will have to do a heap of pondering on that and get back at ya .

[INDENT][INDENT]indeed a process of learning[/INDENT][/INDENT]

---

### Post by slgtheindividual on 2013-11-14
ok, thank you

---

### Post by slgtheindividual on 2013-11-16
any new ideas, I'm still having the exact same errors

---

### Post by Bashing-om on 2013-11-16
slgtheindividual; Hi !

In this case, no news is bad news. I have not given up, but I have not found a way to proceed.

[INDENT][INDENT]this is a process in learning
[/INDENT][/INDENT]

---

### Post by ian-weisser on 2013-11-16
> **slgtheindividual said:**
> ```

~$ cat /etc/init/mountkernfs.sh.conf
# mountkernfs.sh - compatibility job for sysvinit dependencies
#
# This job runs once virtual filesystems are mounted, to signal startpar
# that other rcS jobs relying on the historic mountkernfs.sh interface can
# continue.


description    "Signal sysvinit that virtual filesystems are mounted"


start on virtual-filesystems

```

no, I'm not running a VM or doing anything VM related, just a normal ubuntu desktop 13.10 on my laptop (acer aspire e1-571) dual booting with windows 8 efi, had no problems since I got it until now.

"Virtual" in this case doesn't mean a VM - it means the "virtual" local filesystem interface.
And it's no surprise you can't find the running service - there isn't one.

This particular script is a compatibility tail. Older processes like procps depend on mountkernfs running before they can start. All this file does is emit a signal at the right point in boot that those sysvinit scripts are listening for.

You can emit the same signal two ways:
1) by rebooting
2) with the command [B]sudo initctl emit mountkernfs
[/B]3) or you can ignore mountkernfs completely and start procps directly with **sudo service procps start**

 So, if you're willing, try
```
sudo initctl emit mountkernfs
sudo apt-get --configure -a
```

or

```
sudo service procps start
sudo apt-get --configure -a
```
 and see if one of those kickstarts the process.

---

### Post by Bashing-om on 2013-11-16
@ ian-weisser; Thanks !

See it is a process of learning... I learned something here !
Interesting to see what does result .

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by slgtheindividual on 2013-11-17
> **ian-weisser said:**
> 
```
sudo initctl emit mountkernfs
sudo apt-get --configure -a
```

or

```
sudo service procps start
sudo apt-get --configure -a
```
 and see if one of those kickstarts the process.

Ok thank you for these suggestions, I tried these but to no avail, my output is beow:

```

~$ sudo initctl emit mountkernfs
~$ sudo apt-get --configure -a
E: Command line option --configure is not understood

```

and 

```

~$ sudo service procps start
procps stop/waiting
~$ sudo apt-get --configure -a
E: Command line option --configure is not understood

```

---

### Post by Bashing-om on 2013-11-17
slgtheindividual; Hey:

Try that command as :
```

sudo dpkg --configure -a

```

see what results, and carry forth.

[INDENT][INDENT]we be try'n
[/INDENT][/INDENT]

---

### Post by slgtheindividual on 2013-11-17
Ok still no luck I'm afraid:

```

~$ sudo initctl emit mountkernfs
~$ sudo dpkg --configure -a
Setting up procps (1:3.3.4-2) ...
update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults
insserv: Service mountkernfs has to be enabled to start service procps
insserv: exiting now!
update-rc.d: error: insserv rejected the script header
dpkg: error processing procps (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of udev:
 udev depends on procps; however:
  Package procps is not configured yet.


dpkg: error processing udev (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 procps
 udev

```

and

```

~$ sudo service procps start
procps stop/waiting
~$ sudo dpkg --configure -a
Setting up procps (1:3.3.4-2) ...
update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults
insserv: Service mountkernfs has to be enabled to start service procps
insserv: exiting now!
update-rc.d: error: insserv rejected the script header
dpkg: error processing procps (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of udev:
 udev depends on procps; however:
  Package procps is not configured yet.


dpkg: error processing udev (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 procps
 udev

```

---

### Post by Bashing-om on 2013-11-17
slgtheindividual; & ian-weisser --

I am still stuck on this. I see it as a corrupted header file - some where.
> 
update-rc.d: warning:


//

Looking for a good reason why mountkernfs is not set by default...seeking a means to determine the initiating script, and once more I am not making much headway. A failure on my part to understand what is going on with upstart (??).

[INDENT][INDENT]what we have here is a failure to communicate !
[/INDENT][/INDENT]

---

### Post by ian-weisser on 2013-11-17
Hmmm.
Does the same error occur after a reboot?

---

### Post by Bashing-om on 2013-11-17
Ian, Hello;

I am still mystified that "mountkernfs" will not start, even manually:
> 
~$ sudo initctl emit mountkernfs
~$ sudo dpkg --configure -a
Setting up procps (1:3.3.4-2) ...
update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults
insserv: Service mountkernfs has to be enabled to start service procps

 Now from "cat /etc/init/mountkernfs.sh.conf" -which appears to be valid
there is:
> 
start on virtual-filesystems

Can we imply that "mountkernfs will not start so long as "virtual-filesystems" is not started ?

and what is this relationship ?
> 
update-rc.d: error: insserv rejected the script header


Which brings me back to the original question ... "What script header" ?? As it does not appear to be "mountkernfs.sh.conf" -> "/etc/insserv.conf" and I do not see a relationship there to either "mountkernfs" or "procps".

[INDENT][INDENT]as around and round I go
[/INDENT][/INDENT]

---

### Post by ian-weisser on 2013-11-17
> start on virtual-filesystems
When init hears the virtual-filesystems signal (offhand, I don't know which .conf sends it),
then it starts the mountkernfs service. Your assumption that A must run for B to run is usually correct.

> Setting up procps (1:3.3.4-2) ...
Hang on, that's a not-current version of procps.
Consider deleting it from the package cache ( **sudo apt-get clean procps** ) and redownloading ( **sudo apt-get update && sudo apt-get upgrade** )

```
$ rmadison -u ubuntu procps
[...]
    procps | 1:3.3.3-2ubuntu9 | saucy-updates | source, amd64, arm64, armhf, i386, powerpc
[...]

```

---

### Post by Bashing-om on 2013-11-17
Wow !

This from "packages.ubuntu.com"
> 
You have searched for packages that names contain procps in suite(s) saucy-updates, all sections, and all architectures. Found 3 matching packages.

Exact hits

Package procps

saucy-updates (admin): /proc file system utilities 
1:3.3.3-2ubuntu9: amd64 i386


Was I ever on the wrong trail.

---

### Post by ian-weisser on 2013-11-18
Looking at a couple other threads and bug reports for procps, fail-to-configure has happened before recently, some resolved successfully...however, none with this specific error message. Nevertheless, not alone! 
[http://ubuntuforums.org/showthread.php?t=1965734](http://ubuntuforums.org/showthread.php?t=1965734)
[https://bugs.launchpad.net/ubuntu/+source/procps/+bug/1157643](https://bugs.launchpad.net/ubuntu/+source/procps/+bug/1157643)

---

### Post by slgtheindividual on 2013-11-18
> **ian-weisser said:**
> When init hears the virtual-filesystems signal (offhand, I don't know which .conf sends it),
then it starts the mountkernfs service. Your assumption that A must run for B to run is usually correct.


Hang on, that's a not-current version of procps.
Consider deleting it from the package cache ( **sudo apt-get clean procps** ) and redownloading ( **sudo apt-get update && sudo apt-get upgrade** )

```
$ rmadison -u ubuntu procps
[...]
    procps | 1:3.3.3-2ubuntu9 | saucy-updates | source, amd64, arm64, armhf, i386, powerpc
[...]

```

Ok so first of all yes, I still get the same error after reboot. 

next I tried the following but no good:

```
~$ sudo apt-get clean procps 
~$ sudo apt-get update && sudo apt-get upgrade
Ign http://archive.canonical.com saucy InRelease
Ign http://dl.google.com stable InRelease                                      
Hit http://archive.canonical.com saucy Release.gpg                             
Ign http://extras.ubuntu.com saucy InRelease                                   
Ign http://ppa.launchpad.net saucy InRelease                                   
Hit http://archive.canonical.com saucy Release                                 
Ign http://gb.archive.ubuntu.com saucy InRelease                               
Get:1 http://extras.ubuntu.com saucy Release.gpg [72 B]                        
Hit http://dl.google.com stable Release.gpg                                    
Hit http://ppa.launchpad.net saucy Release.gpg                                 
Ign http://gb.archive.ubuntu.com saucy-updates InRelease                       
Hit http://extras.ubuntu.com saucy Release                                     
Hit http://ppa.launchpad.net saucy Release                                     
Hit http://dl.google.com stable Release                                        
Ign http://gb.archive.ubuntu.com saucy-backports InRelease                     
Ign http://security.ubuntu.com saucy-security InRelease                        
Hit http://archive.canonical.com saucy/partner amd64 Packages                  
Hit http://gb.archive.ubuntu.com saucy Release.gpg                             
Hit http://archive.canonical.com saucy/partner i386 Packages                   
Hit http://extras.ubuntu.com saucy/main Sources                                
Hit http://gb.archive.ubuntu.com saucy-updates Release.gpg                     
Hit http://extras.ubuntu.com saucy/main amd64 Packages                         
Hit http://ppa.launchpad.net saucy/main amd64 Packages                         
Hit http://gb.archive.ubuntu.com saucy-backports Release.gpg                   
Hit http://extras.ubuntu.com saucy/main i386 Packages                          
Hit http://security.ubuntu.com saucy-security Release.gpg                      
Hit http://dl.google.com stable/main amd64 Packages                            
Hit http://ppa.launchpad.net saucy/main i386 Packages                          
Hit http://gb.archive.ubuntu.com saucy Release                                 
Hit http://dl.google.com stable/main i386 Packages                             
Hit http://repo.steampowered.com precise InRelease                             
Get:2 https://private-ppa.launchpad.net saucy InRelease [356 B]                
Hit http://gb.archive.ubuntu.com saucy-updates Release                         
Ign https://private-ppa.launchpad.net saucy InRelease                          
Ign http://archive.canonical.com saucy/partner Translation-en_GB               
Hit http://security.ubuntu.com saucy-security Release                          
Ign https://private-ppa.launchpad.net saucy InRelease                          
Ign http://archive.canonical.com saucy/partner Translation-en                  
Hit http://gb.archive.ubuntu.com saucy-backports Release                       
Ign https://private-ppa.launchpad.net saucy InRelease                          
Hit http://gb.archive.ubuntu.com saucy/main Sources                            
Hit https://private-ppa.launchpad.net saucy Release.gpg                        
Hit http://gb.archive.ubuntu.com saucy/restricted Sources                      
Hit http://security.ubuntu.com saucy-security/main Sources                     
Hit https://private-ppa.launchpad.net saucy Release.gpg                        
Hit http://gb.archive.ubuntu.com saucy/universe Sources                        
Hit http://repo.steampowered.com precise/steam Sources                         
Ign http://extras.ubuntu.com saucy/main Translation-en_GB                      
Hit https://private-ppa.launchpad.net saucy Release.gpg                        
Hit http://gb.archive.ubuntu.com saucy/multiverse Sources                      
Ign http://extras.ubuntu.com saucy/main Translation-en                         
Ign http://ppa.launchpad.net saucy/main Translation-en_GB                      
Hit https://private-ppa.launchpad.net saucy Release                            
Hit http://gb.archive.ubuntu.com saucy/main amd64 Packages                     
Ign http://ppa.launchpad.net saucy/main Translation-en                         
Hit http://security.ubuntu.com saucy-security/restricted Sources               
Hit https://private-ppa.launchpad.net saucy Release                            
Hit http://gb.archive.ubuntu.com saucy/restricted amd64 Packages               
Hit https://private-ppa.launchpad.net saucy Release                            
Hit http://gb.archive.ubuntu.com saucy/universe amd64 Packages                 
Ign http://dl.google.com stable/main Translation-en_GB                         
Hit https://private-ppa.launchpad.net saucy/main amd64 Packages                
Hit http://security.ubuntu.com saucy-security/universe Sources                 
Hit http://gb.archive.ubuntu.com saucy/multiverse amd64 Packages               
Ign http://dl.google.com stable/main Translation-en                  
Hit https://private-ppa.launchpad.net saucy/main i386 Packages       
Get:3 https://private-ppa.launchpad.net saucy/main Translation-en_GB [378 B]
Hit http://security.ubuntu.com saucy-security/multiverse Sources               
Hit http://gb.archive.ubuntu.com saucy/main i386 Packages                      
Hit https://private-ppa.launchpad.net saucy/main amd64 Packages
Hit http://gb.archive.ubuntu.com saucy/restricted i386 Packages      
Hit http://repo.steampowered.com precise/steam amd64 Packages        
Hit https://private-ppa.launchpad.net saucy/main i386 Packages
Hit http://gb.archive.ubuntu.com saucy/universe i386 Packages                  
Hit http://security.ubuntu.com saucy-security/main amd64 Packages              
Get:4 https://private-ppa.launchpad.net saucy/main Translation-en_GB [371 B]   
Hit http://gb.archive.ubuntu.com saucy/multiverse i386 Packages                
Hit https://private-ppa.launchpad.net saucy/main amd64 Packages                
Hit http://gb.archive.ubuntu.com saucy/main Translation-en_GB                  
Hit http://security.ubuntu.com saucy-security/restricted amd64 Packages        
Hit https://private-ppa.launchpad.net saucy/main i386 Packages                 
Hit http://gb.archive.ubuntu.com saucy/main Translation-en                     
Get:5 https://private-ppa.launchpad.net saucy/main Translation-en_GB [371 B]   
Hit http://gb.archive.ubuntu.com saucy/multiverse Translation-en_GB            
Hit http://gb.archive.ubuntu.com saucy/multiverse Translation-en               
Hit http://security.ubuntu.com saucy-security/universe amd64 Packages
Hit http://gb.archive.ubuntu.com saucy/restricted Translation-en_GB
Hit http://gb.archive.ubuntu.com saucy/restricted Translation-en
Hit http://security.ubuntu.com saucy-security/multiverse amd64 Packages
Hit http://gb.archive.ubuntu.com saucy/universe Translation-en_GB
Hit http://repo.steampowered.com precise/steam i386 Packages
Hit http://gb.archive.ubuntu.com saucy/universe Translation-en
Hit http://gb.archive.ubuntu.com saucy-updates/main Sources                    
Hit http://security.ubuntu.com saucy-security/main i386 Packages               
Hit http://gb.archive.ubuntu.com saucy-updates/restricted Sources              
Hit http://gb.archive.ubuntu.com saucy-updates/universe Sources                
Hit http://security.ubuntu.com saucy-security/restricted i386 Packages         
Hit http://gb.archive.ubuntu.com saucy-updates/multiverse Sources              
Hit http://security.ubuntu.com saucy-security/universe i386 Packages
Hit http://gb.archive.ubuntu.com saucy-updates/main amd64 Packages
Hit http://gb.archive.ubuntu.com saucy-updates/restricted amd64 Packages
Hit http://security.ubuntu.com saucy-security/multiverse i386 Packages
Hit http://gb.archive.ubuntu.com saucy-updates/universe amd64 Packages
Hit http://gb.archive.ubuntu.com saucy-updates/multiverse amd64 Packages
Hit http://gb.archive.ubuntu.com saucy-updates/main i386 Packages
Hit http://gb.archive.ubuntu.com saucy-updates/restricted i386 Packages
Ign https://private-ppa.launchpad.net saucy/main Translation-en_GB
Hit http://gb.archive.ubuntu.com saucy-updates/universe i386 Packages
Ign https://private-ppa.launchpad.net saucy/main Translation-en      
Hit http://gb.archive.ubuntu.com saucy-updates/multiverse i386 Packages
Ign https://private-ppa.launchpad.net saucy/main Translation-en_GB   
Ign https://private-ppa.launchpad.net saucy/main Translation-en      
Ign https://private-ppa.launchpad.net saucy/main Translation-en_GB   
Hit http://gb.archive.ubuntu.com saucy-updates/main Translation-en   
Ign https://private-ppa.launchpad.net saucy/main Translation-en      
Hit http://security.ubuntu.com saucy-security/main Translation-en
Hit http://gb.archive.ubuntu.com saucy-updates/multiverse Translation-en
Hit http://gb.archive.ubuntu.com saucy-updates/restricted Translation-en
Hit http://security.ubuntu.com saucy-security/multiverse Translation-en
Hit http://gb.archive.ubuntu.com saucy-updates/universe Translation-en
Hit http://gb.archive.ubuntu.com saucy-backports/main Sources
Hit http://gb.archive.ubuntu.com saucy-backports/restricted Sources
Hit http://security.ubuntu.com saucy-security/restricted Translation-en
Hit http://gb.archive.ubuntu.com saucy-backports/universe Sources
Hit http://gb.archive.ubuntu.com saucy-backports/multiverse Sources
Hit http://gb.archive.ubuntu.com saucy-backports/main amd64 Packages
Hit http://gb.archive.ubuntu.com saucy-backports/restricted amd64 Packages
Hit http://gb.archive.ubuntu.com saucy-backports/universe amd64 Packages
Hit http://security.ubuntu.com saucy-security/universe Translation-en
Hit http://gb.archive.ubuntu.com saucy-backports/multiverse amd64 Packages
Hit http://gb.archive.ubuntu.com saucy-backports/main i386 Packages
Hit http://gb.archive.ubuntu.com saucy-backports/restricted i386 Packages
Hit http://gb.archive.ubuntu.com saucy-backports/universe i386 Packages
Hit http://gb.archive.ubuntu.com saucy-backports/multiverse i386 Packages
Hit http://gb.archive.ubuntu.com saucy-backports/main Translation-en
Hit http://gb.archive.ubuntu.com saucy-backports/multiverse Translation-en
Hit http://gb.archive.ubuntu.com saucy-backports/restricted Translation-en
Hit http://gb.archive.ubuntu.com saucy-backports/universe Translation-en
Ign http://security.ubuntu.com saucy-security/main Translation-en_GB
Ign http://repo.steampowered.com precise/steam Translation-en_GB
Ign http://security.ubuntu.com saucy-security/multiverse Translation-en_GB
Ign http://repo.steampowered.com precise/steam Translation-en
Ign http://security.ubuntu.com saucy-security/restricted Translation-en_GB
Ign http://gb.archive.ubuntu.com saucy-updates/main Translation-en_GB
Ign http://gb.archive.ubuntu.com saucy-updates/multiverse Translation-en_GB
Ign http://gb.archive.ubuntu.com saucy-updates/restricted Translation-en_GB
Ign http://security.ubuntu.com saucy-security/universe Translation-en_GB
Ign http://gb.archive.ubuntu.com saucy-updates/universe Translation-en_GB
Ign http://gb.archive.ubuntu.com saucy-backports/main Translation-en_GB
Ign http://gb.archive.ubuntu.com saucy-backports/multiverse Translation-en_GB
Ign http://gb.archive.ubuntu.com saucy-backports/restricted Translation-en_GB
Ign http://gb.archive.ubuntu.com saucy-backports/universe Translation-en_GB
Fetched 72 B in 4s (15 B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  flashplugin-installer gir1.2-gtk-3.0 google-chrome-stable hud
  indicator-appmenu initramfs-tools initramfs-tools-bin kdelibs-bin
  kdelibs5-data kdelibs5-plugins kdoctools libavcodec53 libavformat53
  libavutil51 libgail-3-0 libgnome-media-profiles-3.0-0 libgtk-3-0
  libgtk-3-bin libgtk-3-common libhud-client2 libido3-0.1-0 libkcmutils4
  libkde3support4 libkdeclarative5 libkdecore5 libkdesu5 libkdeui5
  libkdewebkit5 libkdnssd4 libkemoticons4 libkfile4 libkhtml5 libkidletime4
  libkio5 libkjsapi4 libkjsembed4 libkmediaplayer4 libknewstuff2-4
  libknewstuff3-4 libknotifyconfig4 libkntlm4 libkparts4 libkprintutils4
  libkpty4 libkrosscore4 libktexteditor4 libkunitconversion4 liblxc0
  libnepomuk4 libnepomukquery4a libnepomukutils4 libplasma3 libpostproc52
  libsolid4 libswscale2 libthreadweaver4 lxc lxc-templates python3-lxc
  shim-signed steam-launcher
61 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 69.7 MB of archives.
After this operation, 9,353 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://dl.google.com/linux/chrome/deb/ stable/main google-chrome-stable amd64 31.0.1650.57-1 [48.7 MB]
Get:2 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libavutil51 amd64 6:0.8.9-0ubuntu0.13.10.1 [56.3 kB]
Get:3 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libavcodec53 amd64 6:0.8.9-0ubuntu0.13.10.1 [2,321 kB]
Get:4 http://repo.steampowered.com/steam/ precise/steam steam-launcher all 1.0.0.44 [2,058 kB]
Get:5 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libavformat53 amd64 6:0.8.9-0ubuntu0.13.10.1 [434 kB]
Get:6 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libgtk-3-common all 3.8.6-0ubuntu2 [155 kB]
Get:7 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libgail-3-0 amd64 3.8.6-0ubuntu2 [20.2 kB]
Get:8 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libgtk-3-0 amd64 3.8.6-0ubuntu2 [1,850 kB]
Get:9 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libhud-client2 amd64 13.10.1+13.10.20131031-0ubuntu1 [34.7 kB]
Get:10 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libido3-0.1-0 amd64 13.10.0+13.10.20131031-0ubuntu1 [58.3 kB]
Get:11 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main lxc-templates all 1.0.0~alpha1-0ubuntu13 [41.6 kB]
Get:12 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main python3-lxc amd64 1.0.0~alpha1-0ubuntu13 [18.2 kB]
Get:13 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main liblxc0 amd64 1.0.0~alpha1-0ubuntu13 [137 kB]
Get:14 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main lxc amd64 1.0.0~alpha1-0ubuntu13 [140 kB]
Get:15 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libpostproc52 amd64 6:0.8.9-0ubuntu0.13.10.1 [35.9 kB]
Get:16 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libswscale2 amd64 6:0.8.9-0ubuntu0.13.10.1 [76.6 kB]
Get:17 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main initramfs-tools-bin amd64 0.103ubuntu1.1 [9,872 B]
Get:18 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main initramfs-tools all 0.103ubuntu1.1 [49.1 kB]
Get:19 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/multiverse flashplugin-installer amd64 11.2.202.327ubuntu0.13.10.1 [7,010 B]
Get:20 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main gir1.2-gtk-3.0 amd64 3.8.6-0ubuntu2 [169 kB]
Get:21 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main hud amd64 13.10.1+13.10.20131031-0ubuntu1 [166 kB]
Get:22 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main indicator-appmenu amd64 13.01.0+13.10.20131031-0ubuntu1 [29.5 kB]
Get:23 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libknotifyconfig4 amd64 4:4.11.2-0ubuntu2.1 [39.4 kB]
Get:24 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libplasma3 amd64 4:4.11.2-0ubuntu2.1 [885 kB]
Get:25 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libknewstuff3-4 amd64 4:4.11.2-0ubuntu2.1 [151 kB]
Get:26 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libknewstuff2-4 amd64 4:4.11.2-0ubuntu2.1 [132 kB]
Get:27 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libkunitconversion4 amd64 4:4.11.2-0ubuntu2.1 [81.5 kB]
Get:28 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/universe kdelibs5-plugins amd64 4:4.11.2-0ubuntu2.1 [925 kB]
Get:29 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libkhtml5 amd64 4:4.11.2-0ubuntu2.1 [1,918 kB]
Get:30 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libktexteditor4 amd64 4:4.11.2-0ubuntu2.1 [96.2 kB]
Get:31 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libkprintutils4 amd64 4:4.11.2-0ubuntu2.1 [27.9 kB]
Get:32 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libkmediaplayer4 amd64 4:4.11.2-0ubuntu2.1 [29.2 kB]
Get:33 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libkdewebkit5 amd64 4:4.11.2-0ubuntu2.1 [61.8 kB]
Get:34 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libkde3support4 amd64 4:4.11.2-0ubuntu2.1 [295 kB]
Get:35 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libkparts4 amd64 4:4.11.2-0ubuntu2.1 [118 kB]
Get:36 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libkfile4 amd64 4:4.11.2-0ubuntu2.1 [215 kB]
Get:37 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libkemoticons4 amd64 4:4.11.2-0ubuntu2.1 [41.4 kB]
Get:38 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main kdoctools amd64 4:4.11.2-0ubuntu2.1 [172 kB]
Get:39 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main kdelibs-bin amd64 4:4.11.2-0ubuntu2.1 [199 kB]
Get:40 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libkio5 amd64 4:4.11.2-0ubuntu2.1 [826 kB]
Get:41 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libsolid4 amd64 4:4.11.2-0ubuntu2.1 [265 kB]
Get:42 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libnepomukutils4 amd64 4:4.11.2-0ubuntu2.1 [85.4 kB]
Get:43 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libnepomukquery4a amd64 4:4.11.2-0ubuntu2.1 [107 kB]
Get:44 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libnepomuk4 amd64 4:4.11.2-0ubuntu2.1 [203 kB]
Get:45 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libkjsembed4 amd64 4:4.11.2-0ubuntu2.1 [303 kB]
Get:46 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libkjsapi4 amd64 4:4.11.2-0ubuntu2.1 [257 kB]
Get:47 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libkrosscore4 amd64 4:4.11.2-0ubuntu2.1 [55.7 kB]
Get:48 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libkidletime4 amd64 4:4.11.2-0ubuntu2.1 [37.4 kB]
Get:49 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libkdnssd4 amd64 4:4.11.2-0ubuntu2.1 [66.1 kB]
Get:50 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libkdeclarative5 amd64 4:4.11.2-0ubuntu2.1 [38.5 kB]
Get:51 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libkcmutils4 amd64 4:4.11.2-0ubuntu2.1 [92.0 kB]
Get:52 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libkdeui5 amd64 4:4.11.2-0ubuntu2.1 [1,261 kB]
Get:53 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libthreadweaver4 amd64 4:4.11.2-0ubuntu2.1 [46.7 kB]
Get:54 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libkdesu5 amd64 4:4.11.2-0ubuntu2.1 [50.9 kB]
Get:55 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libkpty4 amd64 4:4.11.2-0ubuntu2.1 [32.7 kB]
Get:56 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libkntlm4 amd64 4:4.11.2-0ubuntu2.1 [28.5 kB]
Get:57 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libkdecore5 amd64 4:4.11.2-0ubuntu2.1 [899 kB]
Get:58 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main kdelibs5-data all 4:4.11.2-0ubuntu2.1 [2,579 kB]
Get:59 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/universe libgnome-media-profiles-3.0-0 amd64 3.0.0-1ubuntu2 [54.3 kB]
Get:60 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libgtk-3-bin amd64 3.8.6-0ubuntu2 [18.2 kB]
Get:61 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main shim-signed amd64 1.5~13.10.1+0.4-0ubuntu4 [432 kB]
Fetched 69.7 MB in 19s (3,588 kB/s)                                            
Extract templates from packages: 100%
Preconfiguring packages ...
Setting up procps (1:3.3.4-2) ...
update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults
insserv: Service mountkernfs has to be enabled to start service procps
insserv: exiting now!
update-rc.d: error: insserv rejected the script header
dpkg: error processing procps (--configure):
 subprocess installed post-installation script returned error exit status 1
configured to not write apport reports
                                      dpkg: dependency problems prevent configuration of udev:
 udev depends on procps; however:
  Package procps is not configured yet.


dpkg: error processing udev (--configure):
 dependency problems - leaving unconfigured
configured to not write apport reports
                                      Errors were encountered while processing:
 procps
 udev
E: Sub-process /usr/bin/dpkg returned an error code (1)
~$ 

```

---

### Post by slgtheindividual on 2013-11-18
Is there something in particular I should do next? Sorry, I don't really understand a lot of technical stuff you guys are saying, but I really appreciate the help =]

---

### Post by slgtheindividual on 2013-11-18
Ok so I ran this from one of the links you posted ( I don't know if this info helps at all but here it is):

```
:~$ cat /etc/sysctl.d/*.conf /etc/sysctl.conf | sudo sysctl -p -

kernel.printk = 4 4 1 7
net.ipv6.conf.all.use_tempaddr = 2
net.ipv6.conf.default.use_tempaddr = 2
kernel.kptr_restrict = 1
fs.protected_hardlinks = 1
fs.protected_symlinks = 1
kernel.sysrq = 176
net.ipv4.conf.default.rp_filter = 1
net.ipv4.conf.all.rp_filter = 1
net.ipv4.tcp_syncookies = 1
kernel.yama.ptrace_scope = 1
vm.mmap_min_addr = 65536
fs.inotify.max_user_watches = 524288
```

---

### Post by Bashing-om on 2013-11-18
slgtheindividual, & Ian;

Here is my present thoughts.
The out put of "cat /etc/sysctl.d/*.conf /etc/sysctl.conf | sudo sysctl -p -" indicates no errors,
The Launchpad bugs all appear to be squashed by procps version "procps/1:3.3.3-2ubuntu8"

Currently  slgtheindividual, your system is attempting in install a later version of procps:
> 
~$ sudo dpkg --configure -a
Setting up procps (1:3.3.4-2) ...

And what is called for is procps version "1:3.3.3-2ubuntu9: amd64 i386".

This mismatch in versions may well and likely to be the source of the "update-rc.d: error: insserv rejected the script header" error message. [what a wonderful catch on Ian's part]

Let us focus our attention on getting the proper version of procps installed.

Let's try this less intrusive method once more to see if the proper version will install;
```

sudo apt-get clean procps
sudo apt-get update
sudo apt-get install --reinstall procps
sudo apt-get upgrade

```
else will consider editing the control files and try try again (??)

//
of topic: I have chores I must get done so will be absent from the keyboard for several hours. I will return asap.

I think I see
[INDENT][INDENT]light at the end of the tunnel
[/INDENT][/INDENT]

---

### Post by slgtheindividual on 2013-11-18
> **Bashing-om said:**
> slgtheindividual, & Ian;

```

sudo apt-get clean procps
sudo apt-get update
sudo apt-get install --reinstall procps
sudo apt-get upgrade

```[INDENT][INDENT]
[/INDENT]
[/INDENT]


Ok well unfortunately this didn't work (the reinstall step gave me an error) output below:

```

~$ sudo apt-get clean procps
 
~$ sudo apt-get update
Ign http://archive.canonical.com saucy InRelease
Ign http://dl.google.com stable InRelease                                      
Ign http://ppa.launchpad.net saucy InRelease                                   
Ign http://extras.ubuntu.com saucy InRelease                                   
Hit http://archive.canonical.com saucy Release.gpg                             
Hit http://dl.google.com stable Release.gpg                                    
Hit http://archive.canonical.com saucy Release                                 
Ign http://gb.archive.ubuntu.com saucy InRelease                               
Ign http://security.ubuntu.com saucy-security InRelease                        
Get:1 http://extras.ubuntu.com saucy Release.gpg [72 B]                        
Hit http://dl.google.com stable Release                                        
Hit http://ppa.launchpad.net saucy Release.gpg                                 
Ign http://gb.archive.ubuntu.com saucy-updates InRelease                       
Hit http://extras.ubuntu.com saucy Release                                     
Hit http://ppa.launchpad.net saucy Release                                     
Get:2 http://security.ubuntu.com saucy-security Release.gpg [933 B]            
Ign http://gb.archive.ubuntu.com saucy-backports InRelease                     
Get:3 http://security.ubuntu.com saucy-security Release [49.6 kB]     
Hit http://gb.archive.ubuntu.com saucy Release.gpg                             
Get:4 http://gb.archive.ubuntu.com saucy-updates Release.gpg [933 B]           
Hit http://archive.canonical.com saucy/partner amd64 Packages                  
Hit http://gb.archive.ubuntu.com saucy-backports Release.gpg                   
Hit http://archive.canonical.com saucy/partner i386 Packages                   
Hit http://gb.archive.ubuntu.com saucy Release                                 
Hit http://repo.steampowered.com precise InRelease                             
Hit http://dl.google.com stable/main amd64 Packages                            
Get:5 http://gb.archive.ubuntu.com saucy-updates Release [49.6 kB]             
Hit http://extras.ubuntu.com saucy/main Sources                                
Hit http://dl.google.com stable/main i386 Packages                             
Hit http://extras.ubuntu.com saucy/main amd64 Packages                         
Hit http://ppa.launchpad.net saucy/main amd64 Packages                         
Hit http://extras.ubuntu.com saucy/main i386 Packages                          
Hit http://ppa.launchpad.net saucy/main i386 Packages                          
Get:6 http://security.ubuntu.com saucy-security/main Sources [10.8 kB]         
Get:7 https://private-ppa.launchpad.net saucy InRelease [356 B]                
Ign https://private-ppa.launchpad.net saucy InRelease                          
Hit http://gb.archive.ubuntu.com saucy-backports Release                       
Get:8 http://security.ubuntu.com saucy-security/restricted Sources [14 B]      
Ign http://archive.canonical.com saucy/partner Translation-en_GB               
Ign https://private-ppa.launchpad.net saucy InRelease                          
Hit http://gb.archive.ubuntu.com saucy/main Sources                            
Get:9 http://security.ubuntu.com saucy-security/universe Sources [5,271 B]     
Ign http://archive.canonical.com saucy/partner Translation-en                  
Ign https://private-ppa.launchpad.net saucy InRelease                          
Hit http://gb.archive.ubuntu.com saucy/restricted Sources                      
Get:10 http://security.ubuntu.com saucy-security/multiverse Sources [688 B]    
Hit https://private-ppa.launchpad.net saucy Release.gpg                        
Hit http://repo.steampowered.com precise/steam Sources                         
Hit http://gb.archive.ubuntu.com saucy/universe Sources                        
Get:11 http://security.ubuntu.com saucy-security/main amd64 Packages [36.8 kB] 
Hit https://private-ppa.launchpad.net saucy Release.gpg                        
Hit http://gb.archive.ubuntu.com saucy/multiverse Sources                      
Ign http://dl.google.com stable/main Translation-en_GB                         
Hit https://private-ppa.launchpad.net saucy Release.gpg                        
Ign http://dl.google.com stable/main Translation-en                            
Hit http://gb.archive.ubuntu.com saucy/main amd64 Packages                     
Ign http://extras.ubuntu.com saucy/main Translation-en_GB                      
Hit https://private-ppa.launchpad.net saucy Release                            
Ign http://ppa.launchpad.net saucy/main Translation-en_GB                      
Get:12 http://security.ubuntu.com saucy-security/restricted amd64 Packages [14 B]
Ign http://extras.ubuntu.com saucy/main Translation-en                         
Hit http://gb.archive.ubuntu.com saucy/restricted amd64 Packages               
Hit https://private-ppa.launchpad.net saucy Release                            
Ign http://ppa.launchpad.net saucy/main Translation-en                         
Get:13 http://security.ubuntu.com saucy-security/universe amd64 Packages [11.4 kB]
Hit http://gb.archive.ubuntu.com saucy/universe amd64 Packages                 
Hit https://private-ppa.launchpad.net saucy Release                            
Get:14 http://security.ubuntu.com saucy-security/multiverse amd64 Packages [1,155 B]
Hit http://gb.archive.ubuntu.com saucy/multiverse amd64 Packages               
Hit https://private-ppa.launchpad.net saucy/main amd64 Packages       
Get:15 http://security.ubuntu.com saucy-security/main i386 Packages [36.8 kB]
Hit https://private-ppa.launchpad.net saucy/main i386 Packages                 
Get:16 https://private-ppa.launchpad.net saucy/main Translation-en_GB [378 B]  
Hit http://gb.archive.ubuntu.com saucy/main i386 Packages                      
Get:17 http://security.ubuntu.com saucy-security/restricted i386 Packages [14 B]
Hit https://private-ppa.launchpad.net saucy/main amd64 Packages                
Hit http://repo.steampowered.com precise/steam amd64 Packages         
Hit http://gb.archive.ubuntu.com saucy/restricted i386 Packages       
Get:18 http://security.ubuntu.com saucy-security/universe i386 Packages [11.8 kB]
Hit https://private-ppa.launchpad.net saucy/main i386 Packages                 
Hit http://gb.archive.ubuntu.com saucy/universe i386 Packages                  
Get:19 http://security.ubuntu.com saucy-security/multiverse i386 Packages [1,389 B]
Get:20 https://private-ppa.launchpad.net saucy/main Translation-en_GB [371 B]  
Hit http://gb.archive.ubuntu.com saucy/multiverse i386 Packages                
Hit http://gb.archive.ubuntu.com saucy/main Translation-en_GB                  
Hit https://private-ppa.launchpad.net saucy/main amd64 Packages                
Hit http://gb.archive.ubuntu.com saucy/main Translation-en                     
Hit https://private-ppa.launchpad.net saucy/main i386 Packages                 
Hit http://gb.archive.ubuntu.com saucy/multiverse Translation-en_GB            
Get:21 https://private-ppa.launchpad.net saucy/main Translation-en_GB [371 B]  
Get:22 http://security.ubuntu.com saucy-security/main Translation-en [15.4 kB] 
Hit http://gb.archive.ubuntu.com saucy/multiverse Translation-en               
Hit http://gb.archive.ubuntu.com saucy/restricted Translation-en_GB  
Hit http://security.ubuntu.com saucy-security/multiverse Translation-en
Hit http://gb.archive.ubuntu.com saucy/restricted Translation-en
Hit http://repo.steampowered.com precise/steam i386 Packages
Hit http://gb.archive.ubuntu.com saucy/universe Translation-en_GB
Hit http://security.ubuntu.com saucy-security/restricted Translation-en        
Hit http://gb.archive.ubuntu.com saucy/universe Translation-en                 
Get:23 http://gb.archive.ubuntu.com saucy-updates/main Sources [34.8 kB]       
Hit http://security.ubuntu.com saucy-security/universe Translation-en          
Get:24 http://gb.archive.ubuntu.com saucy-updates/restricted Sources [14 B]    
Get:25 http://gb.archive.ubuntu.com saucy-updates/universe Sources [13.5 kB]   
Get:26 http://gb.archive.ubuntu.com saucy-updates/multiverse Sources [688 B]   
Get:27 http://gb.archive.ubuntu.com saucy-updates/main amd64 Packages [84.9 kB]
Ign https://private-ppa.launchpad.net saucy/main Translation-en_GB      
Get:28 http://gb.archive.ubuntu.com saucy-updates/restricted amd64 Packages [14 B]
Ign https://private-ppa.launchpad.net saucy/main Translation-en              
Get:29 http://gb.archive.ubuntu.com saucy-updates/universe amd64 Packages [37.2 kB]
Ign https://private-ppa.launchpad.net saucy/main Translation-en_GB             
Ign https://private-ppa.launchpad.net saucy/main Translation-en                
Get:30 http://gb.archive.ubuntu.com saucy-updates/multiverse amd64 Packages [1,155 B]
Ign https://private-ppa.launchpad.net saucy/main Translation-en_GB             
Get:31 http://gb.archive.ubuntu.com saucy-updates/main i386 Packages [84.4 kB]
Ign http://security.ubuntu.com saucy-security/main Translation-en_GB           
Ign https://private-ppa.launchpad.net saucy/main Translation-en                
Ign http://security.ubuntu.com saucy-security/multiverse Translation-en_GB
Get:32 http://gb.archive.ubuntu.com saucy-updates/restricted i386 Packages [14 B]
Ign http://security.ubuntu.com saucy-security/restricted Translation-en_GB
Get:33 http://gb.archive.ubuntu.com saucy-updates/universe i386 Packages [37.6 kB]
Ign http://security.ubuntu.com saucy-security/universe Translation-en_GB
Get:34 http://gb.archive.ubuntu.com saucy-updates/multiverse i386 Packages [1,389 B]
Get:35 http://gb.archive.ubuntu.com saucy-updates/main Translation-en [38.0 kB]
Hit http://gb.archive.ubuntu.com saucy-updates/multiverse Translation-en      
Hit http://gb.archive.ubuntu.com saucy-updates/restricted Translation-en
Get:36 http://gb.archive.ubuntu.com saucy-updates/universe Translation-en [20.6 kB]
Hit http://gb.archive.ubuntu.com saucy-backports/main Sources                 
Hit http://gb.archive.ubuntu.com saucy-backports/restricted Sources
Hit http://gb.archive.ubuntu.com saucy-backports/universe Sources
Hit http://gb.archive.ubuntu.com saucy-backports/multiverse Sources
Hit http://gb.archive.ubuntu.com saucy-backports/main amd64 Packages
Hit http://gb.archive.ubuntu.com saucy-backports/restricted amd64 Packages
Hit http://gb.archive.ubuntu.com saucy-backports/universe amd64 Packages
Hit http://gb.archive.ubuntu.com saucy-backports/multiverse amd64 Packages
Hit http://gb.archive.ubuntu.com saucy-backports/main i386 Packages
Hit http://gb.archive.ubuntu.com saucy-backports/restricted i386 Packages
Hit http://gb.archive.ubuntu.com saucy-backports/universe i386 Packages
Hit http://gb.archive.ubuntu.com saucy-backports/multiverse i386 Packages
Hit http://gb.archive.ubuntu.com saucy-backports/main Translation-en
Hit http://gb.archive.ubuntu.com saucy-backports/multiverse Translation-en
Hit http://gb.archive.ubuntu.com saucy-backports/restricted Translation-en
Hit http://gb.archive.ubuntu.com saucy-backports/universe Translation-en
Ign http://repo.steampowered.com precise/steam Translation-en_GB
Ign http://repo.steampowered.com precise/steam Translation-en
Ign http://gb.archive.ubuntu.com saucy-updates/main Translation-en_GB
Ign http://gb.archive.ubuntu.com saucy-updates/multiverse Translation-en_GB
Ign http://gb.archive.ubuntu.com saucy-updates/restricted Translation-en_GB
Ign http://gb.archive.ubuntu.com saucy-updates/universe Translation-en_GB
Ign http://gb.archive.ubuntu.com saucy-backports/main Translation-en_GB
Ign http://gb.archive.ubuntu.com saucy-backports/multiverse Translation-en_GB
Ign http://gb.archive.ubuntu.com saucy-backports/restricted Translation-en_GB
Ign http://gb.archive.ubuntu.com saucy-backports/universe Translation-en_GB
Fetched 587 kB in 4s (119 kB/s)
Reading package lists... Done
~$ sudo apt-get install --reinstall procps
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reinstallation of procps is not possible, it cannot be downloaded.
0 upgraded, 0 newly installed, 0 to remove and 69 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up procps (1:3.3.4-2) ...
update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults
insserv: Service mountkernfs has to be enabled to start service procps
insserv: exiting now!
update-rc.d: error: insserv rejected the script header
dpkg: error processing procps (--configure):
 subprocess installed post-installation script returned error exit status 1
configured to not write apport reports
                                      dpkg: dependency problems prevent configuration of udev:
 udev depends on procps; however:
  Package procps is not configured yet.


dpkg: error processing udev (--configure):
 dependency problems - leaving unconfigured
configured to not write apport reports
                                      Errors were encountered while processing:
 procps
 udev
E: Sub-process /usr/bin/dpkg returned an error code (1)
~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  desktop-file-utils flashplugin-installer gir1.2-gtk-3.0 gnome-keyring
  gnome-screensaver google-chrome-stable hud indicator-appmenu initramfs-tools
  initramfs-tools-bin kdelibs-bin kdelibs5-data kdelibs5-plugins kdoctools
  libavcodec53 libavformat53 libavutil51 libgail-3-0
  libgnome-media-profiles-3.0-0 libgtk-3-0 libgtk-3-bin libgtk-3-common
  libhud-client2 libido3-0.1-0 libkcmutils4 libkde3support4 libkdeclarative5
  libkdecore5 libkdesu5 libkdeui5 libkdewebkit5 libkdnssd4 libkemoticons4
  libkfile4 libkhtml5 libkidletime4 libkio5 libkjsapi4 libkjsembed4
  libkmediaplayer4 libknewstuff2-4 libknewstuff3-4 libknotifyconfig4 libkntlm4
  libkparts4 libkprintutils4 libkpty4 libkrosscore4 libktexteditor4
  libkunitconversion4 liblxc0 libnepomuk4 libnepomukquery4a libnepomukutils4
  libnss3 libnss3-1d libp11-kit-gnome-keyring libp11-kit-gnome-keyring:i386
  libpam-gnome-keyring libplasma3 libpostproc52 libsolid4 libswscale2
  libthreadweaver4 lxc lxc-templates python3-lxc shim-signed steam-launcher
69 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 71.6 MB of archives.
After this operation, 9,385 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://dl.google.com/linux/chrome/deb/ stable/main google-chrome-stable amd64 31.0.1650.57-1 [48.7 MB]
Get:2 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libp11-kit-gnome-keyring amd64 3.8.2-0ubuntu3.1 [40.6 kB]
Get:3 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libp11-kit-gnome-keyring i386 3.8.2-0ubuntu3.1 [38.2 kB]
Get:4 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libgtk-3-common all 3.8.6-0ubuntu2 [155 kB]
Get:5 http://repo.steampowered.com/steam/ precise/steam steam-launcher all 1.0.0.44 [2,058 kB]
Get:6 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libgail-3-0 amd64 3.8.6-0ubuntu2 [20.2 kB]
Get:7 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libgtk-3-0 amd64 3.8.6-0ubuntu2 [1,850 kB]
Get:8 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main gnome-keyring amd64 3.8.2-0ubuntu3.1 [562 kB]
Get:9 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libnss3-1d amd64 2:3.15.3-0ubuntu0.13.10.1 [12.4 kB]
Get:10 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libnss3 amd64 2:3.15.3-0ubuntu0.13.10.1 [1,078 kB]
Get:11 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libavutil51 amd64 6:0.8.9-0ubuntu0.13.10.1 [56.3 kB]
Get:12 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libavcodec53 amd64 6:0.8.9-0ubuntu0.13.10.1 [2,321 kB]
Get:13 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libavformat53 amd64 6:0.8.9-0ubuntu0.13.10.1 [434 kB]
Get:14 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libhud-client2 amd64 13.10.1+13.10.20131031-0ubuntu1 [34.7 kB]
Get:15 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libido3-0.1-0 amd64 13.10.0+13.10.20131031-0ubuntu1 [58.3 kB]
Get:16 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main lxc-templates all 1.0.0~alpha1-0ubuntu13 [41.6 kB]
Get:17 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main python3-lxc amd64 1.0.0~alpha1-0ubuntu13 [18.2 kB]
Get:18 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main liblxc0 amd64 1.0.0~alpha1-0ubuntu13 [137 kB]
Get:19 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main lxc amd64 1.0.0~alpha1-0ubuntu13 [140 kB]
Get:20 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libpam-gnome-keyring amd64 3.8.2-0ubuntu3.1 [35.6 kB]
Get:21 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libpostproc52 amd64 6:0.8.9-0ubuntu0.13.10.1 [35.9 kB]
Get:22 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libswscale2 amd64 6:0.8.9-0ubuntu0.13.10.1 [76.6 kB]
Get:23 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main initramfs-tools-bin amd64 0.103ubuntu1.1 [9,872 B]
Get:24 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main initramfs-tools all 0.103ubuntu1.1 [49.1 kB]
Get:25 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main desktop-file-utils amd64 0.21-1ubuntu3 [43.1 kB]
Get:26 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/multiverse flashplugin-installer amd64 11.2.202.327ubuntu0.13.10.1 [7,010 B]
Get:27 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main gir1.2-gtk-3.0 amd64 3.8.6-0ubuntu2 [169 kB]
Get:28 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main gnome-screensaver amd64 3.6.1-0ubuntu7 [86.0 kB]
Get:29 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main hud amd64 13.10.1+13.10.20131031-0ubuntu1 [166 kB]
Get:30 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main indicator-appmenu amd64 13.01.0+13.10.20131031-0ubuntu1 [29.5 kB]
Get:31 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libknotifyconfig4 amd64 4:4.11.2-0ubuntu2.1 [39.4 kB]
Get:32 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libplasma3 amd64 4:4.11.2-0ubuntu2.1 [885 kB]
Get:33 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libknewstuff3-4 amd64 4:4.11.2-0ubuntu2.1 [151 kB]
Get:34 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libknewstuff2-4 amd64 4:4.11.2-0ubuntu2.1 [132 kB]
Get:35 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libkunitconversion4 amd64 4:4.11.2-0ubuntu2.1 [81.5 kB]
Get:36 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/universe kdelibs5-plugins amd64 4:4.11.2-0ubuntu2.1 [925 kB]
Get:37 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libkhtml5 amd64 4:4.11.2-0ubuntu2.1 [1,918 kB]
Get:38 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libktexteditor4 amd64 4:4.11.2-0ubuntu2.1 [96.2 kB]
Get:39 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libkprintutils4 amd64 4:4.11.2-0ubuntu2.1 [27.9 kB]
Get:40 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libkmediaplayer4 amd64 4:4.11.2-0ubuntu2.1 [29.2 kB]
Get:41 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libkdewebkit5 amd64 4:4.11.2-0ubuntu2.1 [61.8 kB]
Get:42 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libkde3support4 amd64 4:4.11.2-0ubuntu2.1 [295 kB]
Get:43 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libkparts4 amd64 4:4.11.2-0ubuntu2.1 [118 kB]
Get:44 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libkfile4 amd64 4:4.11.2-0ubuntu2.1 [215 kB]
Get:45 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libkemoticons4 amd64 4:4.11.2-0ubuntu2.1 [41.4 kB]
Get:46 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main kdoctools amd64 4:4.11.2-0ubuntu2.1 [172 kB]
Get:47 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main kdelibs-bin amd64 4:4.11.2-0ubuntu2.1 [199 kB]
Get:48 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libkio5 amd64 4:4.11.2-0ubuntu2.1 [826 kB]
Get:49 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libsolid4 amd64 4:4.11.2-0ubuntu2.1 [265 kB]
Get:50 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libnepomukutils4 amd64 4:4.11.2-0ubuntu2.1 [85.4 kB]
Get:51 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libnepomukquery4a amd64 4:4.11.2-0ubuntu2.1 [107 kB]
Get:52 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libnepomuk4 amd64 4:4.11.2-0ubuntu2.1 [203 kB]
Get:53 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libkjsembed4 amd64 4:4.11.2-0ubuntu2.1 [303 kB]
Get:54 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libkjsapi4 amd64 4:4.11.2-0ubuntu2.1 [257 kB]
Get:55 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libkrosscore4 amd64 4:4.11.2-0ubuntu2.1 [55.7 kB]
Get:56 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libkidletime4 amd64 4:4.11.2-0ubuntu2.1 [37.4 kB]
Get:57 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libkdnssd4 amd64 4:4.11.2-0ubuntu2.1 [66.1 kB]
Get:58 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libkdeclarative5 amd64 4:4.11.2-0ubuntu2.1 [38.5 kB]
Get:59 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libkcmutils4 amd64 4:4.11.2-0ubuntu2.1 [92.0 kB]
Get:60 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libkdeui5 amd64 4:4.11.2-0ubuntu2.1 [1,261 kB]
Get:61 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libthreadweaver4 amd64 4:4.11.2-0ubuntu2.1 [46.7 kB]
Get:62 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libkdesu5 amd64 4:4.11.2-0ubuntu2.1 [50.9 kB]
Get:63 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libkpty4 amd64 4:4.11.2-0ubuntu2.1 [32.7 kB]
Get:64 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libkntlm4 amd64 4:4.11.2-0ubuntu2.1 [28.5 kB]
Get:65 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libkdecore5 amd64 4:4.11.2-0ubuntu2.1 [899 kB]
Get:66 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main kdelibs5-data all 4:4.11.2-0ubuntu2.1 [2,579 kB]
Get:67 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/universe libgnome-media-profiles-3.0-0 amd64 3.0.0-1ubuntu2 [54.3 kB]
Get:68 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libgtk-3-bin amd64 3.8.6-0ubuntu2 [18.2 kB]
Get:69 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main shim-signed amd64 1.5~13.10.1+0.4-0ubuntu4 [432 kB]
Fetched 71.6 MB in 19s (3,627 kB/s)                                            
Extract templates from packages: 100%
Preconfiguring packages ...
Setting up procps (1:3.3.4-2) ...
update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults
insserv: Service mountkernfs has to be enabled to start service procps
insserv: exiting now!
update-rc.d: error: insserv rejected the script header
dpkg: error processing procps (--configure):
 subprocess installed post-installation script returned error exit status 1
configured to not write apport reports
                                      dpkg: dependency problems prevent configuration of udev:
 udev depends on procps; however:
  Package procps is not configured yet.


dpkg: error processing udev (--configure):
 dependency problems - leaving unconfigured
configured to not write apport reports
                                      Errors were encountered while processing:
 procps
 udev
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by Bashing-om on 2013-11-18
slgtheindividual; Well,

Let's do surgery !
Put the cat outside, the children to bed, check the skies for storms -> in this procedure a mishap will be fatal (only so in the event of a loss of power), and if we must resort to manually removing "procps" and (re-)installing.
terminal codes:
```

sudo cp /var/lib/dpkg/status /var/lib/dpkg/status-orig

```
load the file into the text editor "gedit" (in my case my preferred editor)

Search for the term "procps" and
Then edit the file to remove the reference to procps;
```

gksudo gedit /var/lib/dpkg/status

```
Removing the entire stanza from this point:
> 
Package: procps

all the way to and inclusive of this:
> 
Homepage: [http://gitorious.org/procps](http://gitorious.org/procps)
Original-Maintainer: Craig Small <csmall@debian.org>

leaving one blank line between the remaining stanzas as the delimiter,
save and exit the text editor;
and next in terminal do:
```

sudo rm /var/lib/dpkg/info/procps.list
sudo apt-get update
sudo apt-get install --reinstall procps

```
I am not 100% sure of this "install --reinstall" but rather try this as to "remove" procps" - leaving your system naked and alone in the event that a loss of power were to occur - while "installing" the repository version of "procps".

If the package manager says no can do, then will resort to removing "procps" prior to "installing" !! - Will in all likely hood have to repeat the surgery in "/var/lib/dpkg/status" and "rm /var/lib/dpkg/info/procps.list".

[INDENT][INDENT]where there is a will there is a way[/INDENT][/INDENT]

---

### Post by slgtheindividual on 2013-11-19
Ok so I did everything up until the update and there were no problems, after that there were:

```

~$ sudo cp /var/lib/dpkg/status /var/lib/dpkg/status-orig

~$ gksudo gedit /var/lib/dpkg/status


(gedit:3649): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files


(gedit:3649): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
~$ sudo rm /var/lib/dpkg/info/procps.list
~$ sudo apt-get update
Ign http://archive.canonical.com saucy InRelease
Ign http://dl.google.com stable InRelease                                      
Hit http://archive.canonical.com saucy Release.gpg                             
Ign http://ppa.launchpad.net saucy InRelease                                   
Ign http://extras.ubuntu.com saucy InRelease                                   
Hit http://archive.canonical.com saucy Release                                 
Ign http://gb.archive.ubuntu.com saucy InRelease                               
Ign http://security.ubuntu.com saucy-security InRelease                        
Get:1 http://extras.ubuntu.com saucy Release.gpg [72 B]                        
Get:2 http://dl.google.com stable Release.gpg [198 B]                          
Hit http://ppa.launchpad.net saucy Release.gpg                                 
Ign http://gb.archive.ubuntu.com saucy-updates InRelease                       
Hit http://extras.ubuntu.com saucy Release                                     
Hit http://ppa.launchpad.net saucy Release                                     
Get:3 http://security.ubuntu.com saucy-security Release.gpg [933 B]            
Ign http://gb.archive.ubuntu.com saucy-backports InRelease                     
Get:4 http://dl.google.com stable Release [1,347 B]                            
Get:5 http://security.ubuntu.com saucy-security Release [49.6 kB]              
Hit http://gb.archive.ubuntu.com saucy Release.gpg                             
Get:6 http://gb.archive.ubuntu.com saucy-updates Release.gpg [933 B]           
Hit http://gb.archive.ubuntu.com saucy-backports Release.gpg                   
Hit http://gb.archive.ubuntu.com saucy Release                                 
Get:7 http://gb.archive.ubuntu.com saucy-updates Release [49.6 kB]             
Hit http://archive.canonical.com saucy/partner amd64 Packages                  
Hit http://archive.canonical.com saucy/partner i386 Packages                   
Hit http://extras.ubuntu.com saucy/main Sources                                
Hit http://repo.steampowered.com precise InRelease                             
Hit http://gb.archive.ubuntu.com saucy-backports Release                       
Hit http://extras.ubuntu.com saucy/main amd64 Packages                         
Get:8 https://private-ppa.launchpad.net saucy InRelease [356 B]                
Ign https://private-ppa.launchpad.net saucy InRelease                          
Hit http://ppa.launchpad.net saucy/main amd64 Packages                         
Hit http://extras.ubuntu.com saucy/main i386 Packages                          
Hit http://ppa.launchpad.net saucy/main i386 Packages                          
Ign https://private-ppa.launchpad.net saucy InRelease                          
Get:9 http://dl.google.com stable/main amd64 Packages [1,216 B]                
Hit http://gb.archive.ubuntu.com saucy/main Sources                            
Ign https://private-ppa.launchpad.net saucy InRelease                          
Get:10 http://dl.google.com stable/main i386 Packages [1,205 B]                
Get:11 http://security.ubuntu.com saucy-security/main Sources [10.8 kB]        
Hit https://private-ppa.launchpad.net saucy Release.gpg                        
Hit http://gb.archive.ubuntu.com saucy/restricted Sources                      
Get:12 http://security.ubuntu.com saucy-security/restricted Sources [14 B]     
Hit https://private-ppa.launchpad.net saucy Release.gpg                        
Ign http://archive.canonical.com saucy/partner Translation-en_GB               
Hit http://gb.archive.ubuntu.com saucy/universe Sources                        
Get:13 http://security.ubuntu.com saucy-security/universe Sources [5,271 B]    
Ign http://archive.canonical.com saucy/partner Translation-en                  
Hit https://private-ppa.launchpad.net saucy Release.gpg                        
Hit http://gb.archive.ubuntu.com saucy/multiverse Sources                      
Hit https://private-ppa.launchpad.net saucy Release                            
Get:14 http://security.ubuntu.com saucy-security/multiverse Sources [688 B]    
Hit http://repo.steampowered.com precise/steam Sources                         
Hit https://private-ppa.launchpad.net saucy Release                            
Hit http://gb.archive.ubuntu.com saucy/main amd64 Packages                     
Get:15 http://security.ubuntu.com saucy-security/main amd64 Packages [36.8 kB] 
Hit https://private-ppa.launchpad.net saucy Release                            
Hit http://gb.archive.ubuntu.com saucy/restricted amd64 Packages               
Ign http://extras.ubuntu.com saucy/main Translation-en_GB                      
Ign http://ppa.launchpad.net saucy/main Translation-en_GB                      
Hit https://private-ppa.launchpad.net saucy/main amd64 Packages                
Hit http://gb.archive.ubuntu.com saucy/universe amd64 Packages                 
Ign http://extras.ubuntu.com saucy/main Translation-en                         
Get:16 http://security.ubuntu.com saucy-security/restricted amd64 Packages [14 B]
Ign http://ppa.launchpad.net saucy/main Translation-en                         
Hit https://private-ppa.launchpad.net saucy/main i386 Packages                 
Hit http://gb.archive.ubuntu.com saucy/multiverse amd64 Packages               
Get:17 http://security.ubuntu.com saucy-security/universe amd64 Packages [11.4 kB]
Get:18 https://private-ppa.launchpad.net saucy/main Translation-en_GB [378 B]  
Get:19 http://security.ubuntu.com saucy-security/multiverse amd64 Packages [1,155 B]
Ign http://dl.google.com stable/main Translation-en_GB                         
Get:20 http://security.ubuntu.com saucy-security/main i386 Packages [36.8 kB]  
Hit https://private-ppa.launchpad.net saucy/main amd64 Packages                
Hit http://gb.archive.ubuntu.com saucy/main i386 Packages                      
Hit https://private-ppa.launchpad.net saucy/main i386 Packages                 
Ign http://dl.google.com stable/main Translation-en                            
Hit http://gb.archive.ubuntu.com saucy/restricted i386 Packages                
Get:21 https://private-ppa.launchpad.net saucy/main Translation-en_GB [371 B]
Get:22 http://security.ubuntu.com saucy-security/restricted i386 Packages [14 B]
Hit http://gb.archive.ubuntu.com saucy/universe i386 Packages                  
Get:23 http://security.ubuntu.com saucy-security/universe i386 Packages [11.8 kB]
Hit http://repo.steampowered.com precise/steam amd64 Packages                  
Hit https://private-ppa.launchpad.net saucy/main amd64 Packages                
Hit http://gb.archive.ubuntu.com saucy/multiverse i386 Packages                
Get:24 http://security.ubuntu.com saucy-security/multiverse i386 Packages [1,389 B]
Hit https://private-ppa.launchpad.net saucy/main i386 Packages                 
Hit http://gb.archive.ubuntu.com saucy/main Translation-en_GB                  
Get:25 https://private-ppa.launchpad.net saucy/main Translation-en_GB [371 B]  
Hit http://gb.archive.ubuntu.com saucy/main Translation-en                     
Hit http://gb.archive.ubuntu.com saucy/multiverse Translation-en_GB            
Hit http://gb.archive.ubuntu.com saucy/multiverse Translation-en               
Hit http://security.ubuntu.com saucy-security/main Translation-en              
Hit http://gb.archive.ubuntu.com saucy/restricted Translation-en_GB
Hit http://gb.archive.ubuntu.com saucy/restricted Translation-en
Hit http://security.ubuntu.com saucy-security/multiverse Translation-en
Hit http://gb.archive.ubuntu.com saucy/universe Translation-en_GB
Hit http://gb.archive.ubuntu.com saucy/universe Translation-en
Hit http://repo.steampowered.com precise/steam i386 Packages
Hit http://security.ubuntu.com saucy-security/restricted Translation-en
Get:26 http://gb.archive.ubuntu.com saucy-updates/main Sources [37.1 kB]       
Hit http://security.ubuntu.com saucy-security/universe Translation-en          
Get:27 http://gb.archive.ubuntu.com saucy-updates/restricted Sources [14 B]    
Get:28 http://gb.archive.ubuntu.com saucy-updates/universe Sources [13.9 kB]   
Get:29 http://gb.archive.ubuntu.com saucy-updates/multiverse Sources [1,351 B] 
Get:30 http://gb.archive.ubuntu.com saucy-updates/main amd64 Packages [90.7 kB]
Ign https://private-ppa.launchpad.net saucy/main Translation-en_GB             
Ign https://private-ppa.launchpad.net saucy/main Translation-en                
Get:31 http://gb.archive.ubuntu.com saucy-updates/restricted amd64 Packages [14 B]
Ign https://private-ppa.launchpad.net saucy/main Translation-en_GB      
Get:32 http://gb.archive.ubuntu.com saucy-updates/universe amd64 Packages [37.5 kB]
Ign https://private-ppa.launchpad.net saucy/main Translation-en
Ign https://private-ppa.launchpad.net saucy/main Translation-en_GB             
Get:33 http://gb.archive.ubuntu.com saucy-updates/multiverse amd64 Packages [1,578 B]
Ign https://private-ppa.launchpad.net saucy/main Translation-en                
Get:34 http://gb.archive.ubuntu.com saucy-updates/main i386 Packages [90.2 kB]
Ign http://security.ubuntu.com saucy-security/main Translation-en_GB           
Ign http://security.ubuntu.com saucy-security/multiverse Translation-en_GB     
Get:35 http://gb.archive.ubuntu.com saucy-updates/restricted i386 Packages [14 B]
Ign http://security.ubuntu.com saucy-security/restricted Translation-en_GB
Get:36 http://gb.archive.ubuntu.com saucy-updates/universe i386 Packages [37.8 kB]
Ign http://security.ubuntu.com saucy-security/universe Translation-en_GB
Get:37 http://gb.archive.ubuntu.com saucy-updates/multiverse i386 Packages [1,806 B]
Get:38 http://gb.archive.ubuntu.com saucy-updates/main Translation-en [41.0 kB]
Get:39 http://gb.archive.ubuntu.com saucy-updates/multiverse Translation-en [717 B]
Hit http://gb.archive.ubuntu.com saucy-updates/restricted Translation-en      
Get:40 http://gb.archive.ubuntu.com saucy-updates/universe Translation-en [20.9 kB]
Hit http://gb.archive.ubuntu.com saucy-backports/main Sources                 
Hit http://gb.archive.ubuntu.com saucy-backports/restricted Sources
Hit http://gb.archive.ubuntu.com saucy-backports/universe Sources
Hit http://gb.archive.ubuntu.com saucy-backports/multiverse Sources
Hit http://gb.archive.ubuntu.com saucy-backports/main amd64 Packages
Hit http://gb.archive.ubuntu.com saucy-backports/restricted amd64 Packages
Hit http://gb.archive.ubuntu.com saucy-backports/universe amd64 Packages
Hit http://gb.archive.ubuntu.com saucy-backports/multiverse amd64 Packages
Hit http://gb.archive.ubuntu.com saucy-backports/main i386 Packages
Hit http://gb.archive.ubuntu.com saucy-backports/restricted i386 Packages
Hit http://gb.archive.ubuntu.com saucy-backports/universe i386 Packages
Hit http://gb.archive.ubuntu.com saucy-backports/multiverse i386 Packages
Hit http://gb.archive.ubuntu.com saucy-backports/main Translation-en
Hit http://gb.archive.ubuntu.com saucy-backports/multiverse Translation-en
Hit http://gb.archive.ubuntu.com saucy-backports/restricted Translation-en
Hit http://gb.archive.ubuntu.com saucy-backports/universe Translation-en
Ign http://repo.steampowered.com precise/steam Translation-en_GB
Ign http://repo.steampowered.com precise/steam Translation-en
Ign http://gb.archive.ubuntu.com saucy-updates/main Translation-en_GB
Ign http://gb.archive.ubuntu.com saucy-updates/multiverse Translation-en_GB
Ign http://gb.archive.ubuntu.com saucy-updates/restricted Translation-en_GB
Ign http://gb.archive.ubuntu.com saucy-updates/universe Translation-en_GB
Ign http://gb.archive.ubuntu.com saucy-backports/main Translation-en_GB
Ign http://gb.archive.ubuntu.com saucy-backports/multiverse Translation-en_GB
Ign http://gb.archive.ubuntu.com saucy-backports/restricted Translation-en_GB
Ign http://gb.archive.ubuntu.com saucy-backports/universe Translation-en_GB
Fetched 596 kB in 5s (118 kB/s)
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
~$ sudo apt-get install --reinstall procps
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.

```

---

### Post by Bashing-om on 2013-11-19
slgtheindividual;Well !

Not what I had expected !

OK ... make sure that what was cut from the "status file" was not replaced, (as the update may have replaced them)
and the procps.list file also not replaced,
ok the biggy let's do in terminal:
```

sudo apt-get remove procps
sudo apt-get install procps

```
Naked and alone .. if nothing interrupts, no problem !

[INDENT][INDENT]here we go again
[/INDENT][/INDENT]

---

### Post by slgtheindividual on 2013-11-19
So I checked the status file and it hadn't changed and then this happened:

```

~$ gksudo gedit /var/lib/dpkg/status
~$ sudo apt-get remove procps
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
~$ sudo apt-get install procps
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
~$ 

```

---

### Post by Bashing-om on 2013-11-19
slgtheindividual; That is a first for me !

Ok .. let's fix the list files and see what we can do:
```

sudo rm -fr /var/lib/apt/lists
sudo mkdir -pv /var/lib/apt/lists/partial
sudo apt-get update

```

now see of we can remove "procps"
```

sudo dpkg --remove procps

```
and reinstall :
```

sudo apt-get install procps

```

[INDENT][INDENT]fingers crossed
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2013-11-20
slgtheindividual;;

I hope no news is good news !
In the event that you are in trouble, do not reboot or shut the system down.

I am calling it an end to this session . I will check your status in my AM.

[INDENT][INDENT]cheers
[/INDENT][/INDENT]

---

### Post by slgtheindividual on 2013-11-20
> **Bashing-om said:**
> slgtheindividual; That is a first for me !

Ok .. let's fix the list files and see what we can do:
```

sudo rm -fr /var/lib/apt/lists
sudo mkdir -pv /var/lib/apt/lists/partial
sudo apt-get update

```

now see of we can remove "procps"
```

sudo dpkg --remove procps

```
and reinstall :
```

sudo apt-get install procps

```
[INDENT][INDENT]fingers crossed
[/INDENT]
[/INDENT]



Ok I did this and it unfortunately gave me errors from the update step onwards:

```

~$ sudo rm -fr /var/lib/apt/lists
 
~$ sudo mkdir -pv /var/lib/apt/lists/partial
mkdir: created directory ‘/var/lib/apt/lists’
mkdir: created directory ‘/var/lib/apt/lists/partial’
slg@slg-Aspire-E1-571:~$ sudo apt-get update
Ign http://dl.google.com stable InRelease
Ign http://archive.canonical.com saucy InRelease                               
Get:1 http://archive.canonical.com saucy Release.gpg [933 B]                   
Ign http://extras.ubuntu.com saucy InRelease                                   
Get:2 http://dl.google.com stable Release.gpg [198 B]                          
Ign http://ppa.launchpad.net saucy InRelease                                   
Get:3 http://archive.canonical.com saucy Release [7,072 B]                     
Ign http://security.ubuntu.com saucy-security InRelease                        
Ign http://gb.archive.ubuntu.com saucy InRelease                               
Get:4 http://dl.google.com stable Release [1,347 B]                            
Get:5 http://extras.ubuntu.com saucy Release.gpg [72 B]                        
Get:6 http://ppa.launchpad.net saucy Release.gpg [316 B]                       
Get:7 http://security.ubuntu.com saucy-security Release.gpg [933 B]            
Get:8 http://extras.ubuntu.com saucy Release [9,753 B]                         
Get:9 http://archive.canonical.com saucy/partner amd64 Packages [2,196 B]      
Ign http://gb.archive.ubuntu.com saucy-updates InRelease                       
Get:10 http://dl.google.com stable/main amd64 Packages [1,216 B]               
Get:11 http://ppa.launchpad.net saucy Release [11.8 kB]                        
Get:12 http://security.ubuntu.com saucy-security Release [49.6 kB]             
Get:13 http://archive.canonical.com saucy/partner i386 Packages [3,150 B]      
Get:14 http://extras.ubuntu.com saucy/main Sources [14 B]                      
Ign http://gb.archive.ubuntu.com saucy-backports InRelease                     
Get:15 http://dl.google.com stable/main i386 Packages [1,205 B]                
Get:16 http://extras.ubuntu.com saucy/main amd64 Packages [14 B]               
Get:17 http://gb.archive.ubuntu.com saucy Release.gpg [933 B]                  
Get:18 http://extras.ubuntu.com saucy/main i386 Packages [14 B]                
Get:19 http://ppa.launchpad.net saucy/main amd64 Packages [1,025 B]            
Get:20 http://gb.archive.ubuntu.com saucy-updates Release.gpg [933 B]          
Get:21 http://ppa.launchpad.net saucy/main i386 Packages [1,043 B]             
Get:22 http://gb.archive.ubuntu.com saucy-backports Release.gpg [933 B]        
Get:23 http://repo.steampowered.com precise InRelease [2,840 B]                
Get:24 http://security.ubuntu.com saucy-security/main Sources [10.8 kB]        
Get:25 http://gb.archive.ubuntu.com saucy Release [49.6 kB]                    
Get:26 http://security.ubuntu.com saucy-security/restricted Sources [14 B]     
Get:27 https://private-ppa.launchpad.net saucy InRelease [356 B]               
Ign https://private-ppa.launchpad.net saucy InRelease                          
Ign http://archive.canonical.com saucy/partner Translation-en_GB               
Get:28 http://security.ubuntu.com saucy-security/universe Sources [5,271 B]    
Ign https://private-ppa.launchpad.net saucy InRelease                          
Ign http://archive.canonical.com saucy/partner Translation-en                  
Ign https://private-ppa.launchpad.net saucy InRelease                          
Get:29 http://security.ubuntu.com saucy-security/multiverse Sources [688 B]    
Ign http://dl.google.com stable/main Translation-en_GB                         
Get:30 http://gb.archive.ubuntu.com saucy-updates Release [49.6 kB]            
Ign http://dl.google.com stable/main Translation-en                            
Ign http://extras.ubuntu.com saucy/main Translation-en_GB                      
Get:31 http://security.ubuntu.com saucy-security/main amd64 Packages [36.8 kB] 
Get:32 http://repo.steampowered.com precise/steam Sources [549 B]              
Ign http://extras.ubuntu.com saucy/main Translation-en                         
Get:33 https://private-ppa.launchpad.net saucy Release.gpg [316 B]             
Ign http://ppa.launchpad.net saucy/main Translation-en_GB                      
Get:34 https://private-ppa.launchpad.net saucy Release.gpg [316 B]             
Get:35 http://security.ubuntu.com saucy-security/restricted amd64 Packages [14 B]
Get:36 http://gb.archive.ubuntu.com saucy-backports Release [49.6 kB]          
Ign http://ppa.launchpad.net saucy/main Translation-en                         
Get:37 https://private-ppa.launchpad.net saucy Release [11.9 kB]               
Get:38 http://security.ubuntu.com saucy-security/universe amd64 Packages [11.4 kB]
Get:39 http://gb.archive.ubuntu.com saucy/main Sources [1,009 kB]              
Get:40 http://security.ubuntu.com saucy-security/multiverse amd64 Packages [1,155 B]
Get:41 http://repo.steampowered.com precise/steam amd64 Packages [606 B]       
Get:42 https://private-ppa.launchpad.net saucy Release [11.9 kB]               
Get:43 http://security.ubuntu.com saucy-security/main i386 Packages [36.8 kB]  
Get:44 https://private-ppa.launchpad.net saucy Release [11.9 kB]               
Get:45 https://private-ppa.launchpad.net saucy/main amd64 Packages [1,138 B]   
Get:46 http://security.ubuntu.com saucy-security/restricted i386 Packages [14 B]
Get:47 https://private-ppa.launchpad.net saucy/main i386 Packages [1,131 B]    
Get:48 http://repo.steampowered.com precise/steam i386 Packages [806 B]        
Get:49 https://private-ppa.launchpad.net saucy/main Translation-en_GB [378 B]  
Get:50 http://security.ubuntu.com saucy-security/universe i386 Packages [11.8 kB]
Get:51 http://security.ubuntu.com saucy-security/multiverse i386 Packages [1,389 B]
Get:52 https://private-ppa.launchpad.net saucy/main i386 Packages [826 B]      
Get:53 http://security.ubuntu.com saucy-security/main Translation-en [15.4 kB] 
Get:54 https://private-ppa.launchpad.net saucy/main Translation-en_GB [371 B]  
Get:55 http://security.ubuntu.com saucy-security/multiverse Translation-en [587 B]
Get:56 http://gb.archive.ubuntu.com saucy/restricted Sources [4,759 B]         
Get:57 https://private-ppa.launchpad.net saucy/main i386 Packages [880 B]      
Get:58 http://gb.archive.ubuntu.com saucy/universe Sources [6,108 kB]          
Get:59 https://private-ppa.launchpad.net saucy/main Translation-en_GB [371 B]  
Get:60 http://security.ubuntu.com saucy-security/restricted Translation-en [14 B]
Get:61 http://security.ubuntu.com saucy-security/universe Translation-en [7,089 B]
Ign http://repo.steampowered.com precise/steam Translation-en_GB               
Ign http://repo.steampowered.com precise/steam Translation-en                  
Get:62 http://gb.archive.ubuntu.com saucy/multiverse Sources [175 kB]          
Ign http://security.ubuntu.com saucy-security/main Translation-en_GB           
Ign https://private-ppa.launchpad.net saucy/main Translation-en_GB             
Ign http://security.ubuntu.com saucy-security/multiverse Translation-en_GB     
Ign https://private-ppa.launchpad.net saucy/main Translation-en                
Ign http://security.ubuntu.com saucy-security/restricted Translation-en_GB     
Ign https://private-ppa.launchpad.net saucy/main Translation-en_GB             
Ign http://security.ubuntu.com saucy-security/universe Translation-en_GB       
Ign https://private-ppa.launchpad.net saucy/main Translation-en                
Ign https://private-ppa.launchpad.net saucy/main Translation-en_GB             
Get:63 http://gb.archive.ubuntu.com saucy/main amd64 Packages [1,239 kB]       
Ign https://private-ppa.launchpad.net saucy/main Translation-en                
Get:64 http://gb.archive.ubuntu.com saucy/restricted amd64 Packages [9,348 B]  
Get:65 http://gb.archive.ubuntu.com saucy/universe amd64 Packages [5,643 kB]   
Get:66 http://gb.archive.ubuntu.com saucy/multiverse amd64 Packages [131 kB]   
Get:67 http://gb.archive.ubuntu.com saucy/main i386 Packages [1,238 kB]        
Get:68 http://gb.archive.ubuntu.com saucy/restricted i386 Packages [9,688 B]   
Get:69 http://gb.archive.ubuntu.com saucy/universe i386 Packages [5,652 kB]    
Get:70 http://gb.archive.ubuntu.com saucy/multiverse i386 Packages [133 kB]    
Get:71 http://gb.archive.ubuntu.com saucy/main Translation-en_GB [570 kB]      
Get:72 http://gb.archive.ubuntu.com saucy/main Translation-en [711 kB]         
Get:73 http://gb.archive.ubuntu.com saucy/multiverse Translation-en_GB [65.1 kB]
Get:74 http://gb.archive.ubuntu.com saucy/multiverse Translation-en [101 kB]   
Get:75 http://gb.archive.ubuntu.com saucy/restricted Translation-en_GB [2,264 B]
Get:76 http://gb.archive.ubuntu.com saucy/restricted Translation-en [2,686 B]  
Get:77 http://gb.archive.ubuntu.com saucy/universe Translation-en_GB [3,468 kB]
Get:78 http://gb.archive.ubuntu.com saucy/universe Translation-en [3,886 kB]   
Get:79 http://gb.archive.ubuntu.com saucy-updates/main Sources [37.1 kB]       
Get:80 http://gb.archive.ubuntu.com saucy-updates/restricted Sources [14 B]    
Get:81 http://gb.archive.ubuntu.com saucy-updates/universe Sources [13.9 kB]   
Get:82 http://gb.archive.ubuntu.com saucy-updates/multiverse Sources [1,351 B] 
Get:83 http://gb.archive.ubuntu.com saucy-updates/main amd64 Packages [90.7 kB]
Get:84 http://gb.archive.ubuntu.com saucy-updates/restricted amd64 Packages [14 B]
Get:85 http://gb.archive.ubuntu.com saucy-updates/universe amd64 Packages [37.5 kB]
Get:86 http://gb.archive.ubuntu.com saucy-updates/multiverse amd64 Packages [1,579 B]
Get:87 http://gb.archive.ubuntu.com saucy-updates/main i386 Packages [90.2 kB] 
Get:88 http://gb.archive.ubuntu.com saucy-updates/restricted i386 Packages [14 B]
Get:89 http://gb.archive.ubuntu.com saucy-updates/universe i386 Packages [37.8 kB]
Get:90 http://gb.archive.ubuntu.com saucy-updates/multiverse i386 Packages [1,807 B]
Get:91 http://gb.archive.ubuntu.com saucy-updates/main Translation-en [41.0 kB]
Get:92 http://gb.archive.ubuntu.com saucy-updates/multiverse Translation-en [717 B]
Get:93 http://gb.archive.ubuntu.com saucy-updates/restricted Translation-en [14 B]
Get:94 http://gb.archive.ubuntu.com saucy-updates/universe Translation-en [20.9 kB]
Get:95 http://gb.archive.ubuntu.com saucy-backports/main Sources [14 B]        
Get:96 http://gb.archive.ubuntu.com saucy-backports/restricted Sources [14 B]  
Get:97 http://gb.archive.ubuntu.com saucy-backports/universe Sources [795 B]   
Get:98 http://gb.archive.ubuntu.com saucy-backports/multiverse Sources [834 B] 
Get:99 http://gb.archive.ubuntu.com saucy-backports/main amd64 Packages [14 B] 
Get:100 http://gb.archive.ubuntu.com saucy-backports/restricted amd64 Packages [14 B]
Get:101 http://gb.archive.ubuntu.com saucy-backports/universe amd64 Packages [604 B]
Get:102 http://gb.archive.ubuntu.com saucy-backports/multiverse amd64 Packages [14 B]
Get:103 http://gb.archive.ubuntu.com saucy-backports/main i386 Packages [14 B] 
Get:104 http://gb.archive.ubuntu.com saucy-backports/restricted i386 Packages [14 B]
Get:105 http://gb.archive.ubuntu.com saucy-backports/universe i386 Packages [602 B]
Get:106 http://gb.archive.ubuntu.com saucy-backports/multiverse i386 Packages [709 B]
Get:107 http://gb.archive.ubuntu.com saucy-backports/main Translation-en [14 B]
Get:108 http://gb.archive.ubuntu.com saucy-backports/multiverse Translation-en [525 B]
Get:109 http://gb.archive.ubuntu.com saucy-backports/restricted Translation-en [14 B]
Get:110 http://gb.archive.ubuntu.com saucy-backports/universe Translation-en [617 B]
Ign http://gb.archive.ubuntu.com saucy-updates/main Translation-en_GB          
Ign http://gb.archive.ubuntu.com saucy-updates/multiverse Translation-en_GB    
Ign http://gb.archive.ubuntu.com saucy-updates/restricted Translation-en_GB    
Ign http://gb.archive.ubuntu.com saucy-updates/universe Translation-en_GB      
Ign http://gb.archive.ubuntu.com saucy-backports/main Translation-en_GB        
Ign http://gb.archive.ubuntu.com saucy-backports/multiverse Translation-en_GB  
Ign http://gb.archive.ubuntu.com saucy-backports/restricted Translation-en_GB  
Ign http://gb.archive.ubuntu.com saucy-backports/universe Translation-en_GB    
Fetched 31.0 MB in 1min 29s (344 kB/s)                                         
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
~$ sudo dpkg --remove procps
dpkg: error: parsing file '/var/lib/dpkg/status' near line 6849:
 missing package name
~$ sudo apt-get install procps
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.

```

sorry I took a while to reply, it was night time here and I fell asleep at my computer. It's ok, I haven't logged off or switched off since we started.

---

### Post by Bashing-om on 2013-11-20
slgtheindividual; Yikes !

I have conducted this process several times, and have never encountered the situation where these errors are generated when that stanza is removed for (re-)installing a package !...Maybe because it is a system package (??). Looks like I too am in a learning mode.

There is no doubt that we must get the proper version of "procps" installed onto the system ... How ?

I am of a mind to read over this thread, see what all we have tried that has not worked, and download the package direct from the source and try and install with "dpkg -i". I will Take a look at the 3rd party sources - perhaps one of them is holding "procps" at that higher version !

For now let's put the package management system back to a stable condition, then back up and regroup and learn why this process is failing.

```

sudo cp /var/lib/dpkg/status-orig /var/lib/dpkg/status
sudo apt-get update

```

//

I have chores I must get done and off my mind before I can properly focus on this sloppyation. I will be back unless a catastrophe prevents.

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by slgtheindividual on 2013-11-20
Ok thanks, I did that and restored the original file. Thanks! :)

---

### Post by Bashing-om on 2013-11-20
slgtheindividual; Roger that !

I'll get back to this soonest !
[INDENT][INDENT]we will, we will
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2013-11-20
slgtheindividual; Hello,

Is it possible that there are two stanza for "procps" in /var/lib/dpkg/status ?
One for version procps (1:3.3.4-2) as well as for an earlier version .
Please search and advise.

Else;

Airing my ignorance; How about the thought that "procps" is so deeply embedded and innertwinned and entwined into the operating system that it can not be removed ?
 
Others' thoughts are welcome !

@ slgtheindividual; To see my reasoning do:
```

dpkg --listfiles procps

```
You will see many files installed into the operating system. Then,
load "/var/lib/dpkg/available" into the text editor and search on "procps". See "procps" has it's fingers in many applications;
and
same for "/var/lib/dpkg/status" .
-A quicker way -
```

grep -B3 -A10 procps /var/lib/dpkg/status

```

It is enlightening to see what all is dependent on "procps" .

Meanwhile; I am back to looking-to-see-what-I-can-find in that respect !

hey ->
[INDENT][INDENT]sometimes I wonder, other times I just do not know
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2013-11-20
slgtheindividual; Hi !

Here is another thought - that I actually like better than removing and (RE-)installing;
How bout we try reverting "procps" to the proper version ?
```

sudo apt-get install procps=1:3.3.3-2ubuntu9

```

That too is ->
[INDENT][INDENT]worth a shot
[/INDENT][/INDENT]

---

### Post by slgtheindividual on 2013-11-20
ok so I checked /var/lib/dpkg/status[COLOR=#000000] and there is only procps and libprocps0, no duplicates.

I think your idea to revert procps (partially) worked, it definitely made some progress:

```
[/COLOR]$ sudo apt-get install procps=1:3.3.3-2ubuntu9


Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be DOWNGRADED:
  procps
0 upgraded, 0 newly installed, 1 downgraded, 0 to remove and 91 not upgraded.
2 not fully installed or removed.
Need to get 231 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main procps amd64 1:3.3.3-2ubuntu9 [231 kB]
Fetched 231 kB in 0s (574 kB/s)
dpkg: warning: downgrading procps from 1:3.3.4-2 to 1:3.3.3-2ubuntu9
dpkg: warning: files list file for package 'procps' missing; assuming package has no files currently installed
(Reading database ... 331574 files and directories currently installed.)
Preparing to replace procps 1:3.3.4-2 (using .../procps_1%3a3.3.3-2ubuntu9_amd64.deb) ...
Unpacking replacement procps ...
Processing triggers for menu ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Setting up procps (1:3.3.3-2ubuntu9) ...


Configuration file `/etc/init.d/procps'
 ==> File on system created by you or by a script.
 ==> File also in package provided by package maintainer.
   What would you like to do about it ?  Your options are:
    Y or I  : install the package maintainer's version
    N or O  : keep your currently-installed version
      D     : show the differences between the versions
      Z     : start a shell to examine the situation
 The default action is to keep your current version.
*** procps (Y/I/N/O/D/Z) [default=N] ? y
Installing new version of config file /etc/init.d/procps ...


Configuration file `/etc/sysctl.conf'
 ==> File on system created by you or by a script.
 ==> File also in package provided by package maintainer.
   What would you like to do about it ?  Your options are:
    Y or I  : install the package maintainer's version
    N or O  : keep your currently-installed version
      D     : show the differences between the versions
      Z     : start a shell to examine the situation
 The default action is to keep your current version.
*** sysctl.conf (Y/I/N/O/D/Z) [default=N] ? y
Installing new version of config file /etc/sysctl.conf ...
procps stop/waiting
insserv: warning: script 'bluetooth' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `bluetooth'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `bluetooth'
insserv: warning: script 'console-setup' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `console-setup'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `console-setup'
insserv: warning: script 'setvtrgb' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `setvtrgb'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `setvtrgb'
insserv: warning: script 'rfkill-store' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `rfkill-store'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `rfkill-store'
insserv: warning: script 'anacron' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `anacron'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `anacron'
insserv: warning: script 'cgroup-lite' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `cgroup-lite'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `cgroup-lite'
insserv: warning: script 'friendly-recovery' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `friendly-recovery'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `friendly-recovery'
insserv: warning: script 'console-font' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `console-font'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `console-font'
insserv: warning: script 'cron' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `cron'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `cron'
insserv: warning: script 'rfkill-restore' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `rfkill-restore'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `rfkill-restore'
insserv: warning: script 'resolvconf' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `resolvconf'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `resolvconf'
insserv: warning: script 'kmod' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `kmod'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `kmod'
Processing triggers for ureadahead ...
Setting up udev (204-5) ...
Installing new version of config file /etc/init.d/udev ...
Installing new version of config file /etc/udev/udev.conf ...
Installing new version of config file /etc/init/udev-finish.conf ...
Installing new version of config file /etc/init/udev.conf ...
Installing new version of config file /etc/init/udevmonitor.conf ...
insserv: warning: script 'bluetooth' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `bluetooth'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `bluetooth'
insserv: warning: script 'console-setup' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `console-setup'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `console-setup'
insserv: warning: script 'setvtrgb' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `setvtrgb'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `setvtrgb'
insserv: warning: script 'rfkill-store' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `rfkill-store'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `rfkill-store'
insserv: warning: script 'anacron' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `anacron'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `anacron'
insserv: warning: script 'cgroup-lite' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `cgroup-lite'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `cgroup-lite'
insserv: warning: script 'friendly-recovery' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `friendly-recovery'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `friendly-recovery'
insserv: warning: script 'console-font' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `console-font'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `console-font'
insserv: warning: script 'cron' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `cron'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `cron'
insserv: warning: script 'rfkill-restore' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `rfkill-restore'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `rfkill-restore'
insserv: warning: script 'resolvconf' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `resolvconf'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `resolvconf'
insserv: warning: script 'kmod' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `kmod'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `kmod'
udev stop/waiting
udev start/running, process 10383
update-initramfs: deferring update (trigger activated)
insserv: Service mountkernfs has to be enabled to start service udev
insserv: exiting now!
update-rc.d: error: insserv rejected the script header
dpkg: error processing udev (--configure):
 subprocess installed post-installation script returned error exit status 1
configured to not write apport reports
                                      Processing triggers for menu ...
Processing triggers for ureadahead ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.11.0-13-generic
Errors were encountered while processing:
 udev
E: Sub-process /usr/bin/dpkg returned an error code (1)[COLOR=#000000]

```[/COLOR][COLOR=#000000]

Seems it's only listing a problem with udev now.

Then when I tried updating:

[/COLOR]```
~$ sudo apt-get update; sudo apt-get upgrade

Ign http://archive.canonical.com saucy InRelease
Ign http://extras.ubuntu.com saucy InRelease
Ign http://dl.google.com stable InRelease                                      
Hit http://archive.canonical.com saucy Release.gpg                             
Get:1 http://extras.ubuntu.com saucy Release.gpg [72 B]                        
Ign http://gb.archive.ubuntu.com saucy InRelease                               
Ign http://ppa.launchpad.net saucy InRelease                                   
Hit http://dl.google.com stable Release.gpg                                    
Hit http://archive.canonical.com saucy Release                                 
Hit http://extras.ubuntu.com saucy Release                                     
Hit http://ppa.launchpad.net saucy Release.gpg                                 
Ign http://gb.archive.ubuntu.com saucy-updates InRelease                       
Hit http://dl.google.com stable Release                                        
Hit http://archive.canonical.com saucy/partner amd64 Packages                  
Hit http://ppa.launchpad.net saucy Release                                     
Hit http://extras.ubuntu.com saucy/main Sources                                
Hit http://archive.canonical.com saucy/partner i386 Packages                   
Ign http://gb.archive.ubuntu.com saucy-backports InRelease                     
Ign http://security.ubuntu.com saucy-security InRelease                        
Hit http://dl.google.com stable/main amd64 Packages                            
Hit http://extras.ubuntu.com saucy/main amd64 Packages                         
Hit http://ppa.launchpad.net saucy/main amd64 Packages                         
Hit http://gb.archive.ubuntu.com saucy Release.gpg                             
Hit http://extras.ubuntu.com saucy/main i386 Packages                          
Hit http://dl.google.com stable/main i386 Packages                             
Hit http://ppa.launchpad.net saucy/main i386 Packages                          
Get:2 http://gb.archive.ubuntu.com saucy-updates Release.gpg [933 B]           
Get:3 http://security.ubuntu.com saucy-security Release.gpg [933 B]            
Hit http://gb.archive.ubuntu.com saucy-backports Release.gpg                   
Hit http://gb.archive.ubuntu.com saucy Release                                 
Hit http://repo.steampowered.com precise InRelease                             
Get:4 http://security.ubuntu.com saucy-security Release [49.6 kB]              
Ign http://archive.canonical.com saucy/partner Translation-en_GB               
Get:5 http://gb.archive.ubuntu.com saucy-updates Release [49.6 kB]             
Ign http://archive.canonical.com saucy/partner Translation-en                  
Get:6 https://private-ppa.launchpad.net saucy InRelease [356 B]                
Ign https://private-ppa.launchpad.net saucy InRelease                          
Ign https://private-ppa.launchpad.net saucy InRelease                          
Ign http://extras.ubuntu.com saucy/main Translation-en_GB                      
Ign https://private-ppa.launchpad.net saucy InRelease                          
Hit http://gb.archive.ubuntu.com saucy-backports Release                       
Ign http://extras.ubuntu.com saucy/main Translation-en                         
Hit http://repo.steampowered.com precise/steam Sources                         
Ign http://ppa.launchpad.net saucy/main Translation-en_GB                      
Hit https://private-ppa.launchpad.net saucy Release.gpg                        
Hit http://gb.archive.ubuntu.com saucy/main Sources                            
Ign http://ppa.launchpad.net saucy/main Translation-en                         
Hit https://private-ppa.launchpad.net saucy Release.gpg                        
Hit http://gb.archive.ubuntu.com saucy/restricted Sources                      
Ign http://dl.google.com stable/main Translation-en_GB                         
Hit https://private-ppa.launchpad.net saucy Release.gpg                        
Hit http://gb.archive.ubuntu.com saucy/universe Sources                        
Ign http://dl.google.com stable/main Translation-en                            
Get:7 http://security.ubuntu.com saucy-security/main Sources [10.8 kB]         
Hit https://private-ppa.launchpad.net saucy Release                            
Hit http://gb.archive.ubuntu.com saucy/multiverse Sources                      
Hit https://private-ppa.launchpad.net saucy Release                            
Hit http://gb.archive.ubuntu.com saucy/main amd64 Packages                     
Hit https://private-ppa.launchpad.net saucy Release                            
Hit http://gb.archive.ubuntu.com saucy/restricted amd64 Packages               
Get:8 http://security.ubuntu.com saucy-security/restricted Sources [14 B]
Hit https://private-ppa.launchpad.net saucy/main amd64 Packages            
Hit http://gb.archive.ubuntu.com saucy/universe amd64 Packages        
Hit https://private-ppa.launchpad.net saucy/main i386 Packages        
Get:9 https://private-ppa.launchpad.net saucy/main Translation-en_GB [378 B]
Hit http://gb.archive.ubuntu.com saucy/multiverse amd64 Packages               
Get:10 http://security.ubuntu.com saucy-security/universe Sources [5,271 B]    
Hit http://repo.steampowered.com precise/steam amd64 Packages                  
Hit https://private-ppa.launchpad.net saucy/main amd64 Packages      
Hit https://private-ppa.launchpad.net saucy/main i386 Packages                 
Get:11 http://security.ubuntu.com saucy-security/multiverse Sources [688 B]    
Hit http://gb.archive.ubuntu.com saucy/main i386 Packages                      
Get:12 https://private-ppa.launchpad.net saucy/main Translation-en_GB [371 B]  
Hit http://gb.archive.ubuntu.com saucy/restricted i386 Packages                
Hit https://private-ppa.launchpad.net saucy/main amd64 Packages                
Hit http://gb.archive.ubuntu.com saucy/universe i386 Packages                  
Get:13 http://security.ubuntu.com saucy-security/main amd64 Packages [36.8 kB] 
Hit https://private-ppa.launchpad.net saucy/main i386 Packages                 
Hit http://gb.archive.ubuntu.com saucy/multiverse i386 Packages                
Get:14 https://private-ppa.launchpad.net saucy/main Translation-en_GB [371 B]  
Hit http://gb.archive.ubuntu.com saucy/main Translation-en_GB                  
Hit http://gb.archive.ubuntu.com saucy/main Translation-en                     
Hit http://gb.archive.ubuntu.com saucy/multiverse Translation-en_GB  
Get:15 http://security.ubuntu.com saucy-security/restricted amd64 Packages [14 B]
Hit http://gb.archive.ubuntu.com saucy/multiverse Translation-en               
Hit http://repo.steampowered.com precise/steam i386 Packages         
Hit http://gb.archive.ubuntu.com saucy/restricted Translation-en_GB
Get:16 http://security.ubuntu.com saucy-security/universe amd64 Packages [11.4 kB]
Hit http://gb.archive.ubuntu.com saucy/restricted Translation-en               
Hit http://gb.archive.ubuntu.com saucy/universe Translation-en_GB              
Hit http://gb.archive.ubuntu.com saucy/universe Translation-en                 
Get:17 http://security.ubuntu.com saucy-security/multiverse amd64 Packages [1,155 B]
Get:18 http://gb.archive.ubuntu.com saucy-updates/main Sources [38.3 kB]       
Get:19 http://security.ubuntu.com saucy-security/main i386 Packages [36.7 kB]  
Get:20 http://gb.archive.ubuntu.com saucy-updates/restricted Sources [14 B]    
Get:21 http://gb.archive.ubuntu.com saucy-updates/universe Sources [13.9 kB]   
Get:22 http://gb.archive.ubuntu.com saucy-updates/multiverse Sources [1,351 B] 
Get:23 http://security.ubuntu.com saucy-security/restricted i386 Packages [14 B]
Get:24 http://gb.archive.ubuntu.com saucy-updates/main amd64 Packages [94.0 kB]
Ign https://private-ppa.launchpad.net saucy/main Translation-en_GB
Get:25 http://security.ubuntu.com saucy-security/universe i386 Packages [11.8 kB]
Ign https://private-ppa.launchpad.net saucy/main Translation-en                
Ign https://private-ppa.launchpad.net saucy/main Translation-en_GB             
Get:26 http://security.ubuntu.com saucy-security/multiverse i386 Packages [1,389 B]
Ign https://private-ppa.launchpad.net saucy/main Translation-en                
Get:27 http://gb.archive.ubuntu.com saucy-updates/restricted amd64 Packages [14 B]
Ign https://private-ppa.launchpad.net saucy/main Translation-en_GB             
Get:28 http://gb.archive.ubuntu.com saucy-updates/universe amd64 Packages [37.6 kB]
Ign https://private-ppa.launchpad.net saucy/main Translation-en                
Get:29 http://gb.archive.ubuntu.com saucy-updates/multiverse amd64 Packages [1,572 B]
Get:30 http://gb.archive.ubuntu.com saucy-updates/main i386 Packages [93.6 kB]
Get:31 http://gb.archive.ubuntu.com saucy-updates/restricted i386 Packages [14 B]
Hit http://security.ubuntu.com saucy-security/main Translation-en              
Get:32 http://gb.archive.ubuntu.com saucy-updates/universe i386 Packages [38.0 kB]
Get:33 http://gb.archive.ubuntu.com saucy-updates/multiverse i386 Packages [1,800 B]
Get:34 http://gb.archive.ubuntu.com saucy-updates/main Translation-en [42.4 kB]
Hit http://security.ubuntu.com saucy-security/multiverse Translation-en        
Hit http://gb.archive.ubuntu.com saucy-updates/multiverse Translation-en       
Hit http://gb.archive.ubuntu.com saucy-updates/restricted Translation-en
Hit http://security.ubuntu.com saucy-security/restricted Translation-en
Get:35 http://gb.archive.ubuntu.com saucy-updates/universe Translation-en [20.9 kB]
Hit http://gb.archive.ubuntu.com saucy-backports/main Sources                 
Hit http://security.ubuntu.com saucy-security/universe Translation-en
Hit http://gb.archive.ubuntu.com saucy-backports/restricted Sources
Hit http://gb.archive.ubuntu.com saucy-backports/universe Sources
Hit http://gb.archive.ubuntu.com saucy-backports/multiverse Sources
Hit http://gb.archive.ubuntu.com saucy-backports/main amd64 Packages
Hit http://gb.archive.ubuntu.com saucy-backports/restricted amd64 Packages
Hit http://gb.archive.ubuntu.com saucy-backports/universe amd64 Packages
Hit http://gb.archive.ubuntu.com saucy-backports/multiverse amd64 Packages
Hit http://gb.archive.ubuntu.com saucy-backports/main i386 Packages
Hit http://gb.archive.ubuntu.com saucy-backports/restricted i386 Packages
Hit http://gb.archive.ubuntu.com saucy-backports/universe i386 Packages
Hit http://gb.archive.ubuntu.com saucy-backports/multiverse i386 Packages
Hit http://gb.archive.ubuntu.com saucy-backports/main Translation-en
Hit http://gb.archive.ubuntu.com saucy-backports/multiverse Translation-en
Hit http://gb.archive.ubuntu.com saucy-backports/restricted Translation-en
Hit http://gb.archive.ubuntu.com saucy-backports/universe Translation-en
Ign http://repo.steampowered.com precise/steam Translation-en_GB
Ign http://security.ubuntu.com saucy-security/main Translation-en_GB
Ign http://security.ubuntu.com saucy-security/multiverse Translation-en_GB
Ign http://repo.steampowered.com precise/steam Translation-en
Ign http://security.ubuntu.com saucy-security/restricted Translation-en_GB
Ign http://security.ubuntu.com saucy-security/universe Translation-en_GB
Ign http://gb.archive.ubuntu.com saucy-updates/main Translation-en_GB
Ign http://gb.archive.ubuntu.com saucy-updates/multiverse Translation-en_GB
Ign http://gb.archive.ubuntu.com saucy-updates/restricted Translation-en_GB
Ign http://gb.archive.ubuntu.com saucy-updates/universe Translation-en_GB
Ign http://gb.archive.ubuntu.com saucy-backports/main Translation-en_GB
Ign http://gb.archive.ubuntu.com saucy-backports/multiverse Translation-en_GB
Ign http://gb.archive.ubuntu.com saucy-backports/restricted Translation-en_GB
Ign http://gb.archive.ubuntu.com saucy-backports/universe Translation-en_GB
Fetched 601 kB in 5s (120 kB/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  apparmor cups cups-bsd cups-client cups-common cups-daemon cups-ppdc
  cups-server-common desktop-file-utils firefox firefox-locale-en
  flashplugin-installer gir1.2-dbusmenu-glib-0.4 gir1.2-gtk-3.0 gnome-keyring
  gnome-screensaver google-chrome-stable hud indicator-application
  indicator-appmenu initramfs-tools initramfs-tools-bin kdelibs-bin
  kdelibs5-data kdelibs5-plugins kdoctools libapparmor-perl libapparmor1
  libavcodec53 libavformat53 libavutil51 libcups2 libcups2:i386 libcupscgi1
  libcupsimage2 libcupsmime1 libcupsppdc1 libdbusmenu-glib4 libdbusmenu-gtk3-4
  libdbusmenu-gtk4 libdrm-intel1 libdrm-intel1:i386 libdrm-nouveau2
  libdrm-nouveau2:i386 libdrm-radeon1 libdrm-radeon1:i386 libdrm2 libdrm2:i386
  libgail-3-0 libglamor0 libgnome-media-profiles-3.0-0 libgtk-3-0 libgtk-3-bin
  libgtk-3-common libhud-client2 libido3-0.1-0 libkcmutils4 libkde3support4
  libkdeclarative5 libkdecore5 libkdesu5 libkdeui5 libkdewebkit5 libkdnssd4
  libkemoticons4 libkfile4 libkhtml5 libkidletime4 libkio5 libkjsapi4
  libkjsembed4 libkmediaplayer4 libknewstuff2-4 libknewstuff3-4
  libknotifyconfig4 libkntlm4 libkparts4 libkprintutils4 libkpty4
  libkrosscore4 libktexteditor4 libkunitconversion4 liblxc0
  libmission-control-plugins0 libnepomuk4 libnepomukquery4a libnepomukutils4
  libnss3 libnss3-1d libp11-kit-gnome-keyring libp11-kit-gnome-keyring:i386
  libpam-gnome-keyring libplasma3 libpostproc52 libsolid4 libswscale2
  libthreadweaver4 lxc lxc-templates nautilus-dropbox python3-lxc shim-signed
  steam-launcher telepathy-mission-control-5 xserver-xorg-glamoregl
105 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 33.0 MB/105 MB of archives.
After this operation, 9,392 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libdrm2 i386 2.4.46-1ubuntu1 [27.5 kB]
Get:2 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libdrm2 amd64 2.4.46-1ubuntu1 [26.7 kB]
Get:3 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libcupsppdc1 amd64 1.7.0~rc1-0ubuntu5.1 [51.8 kB]
Get:4 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libcupsmime1 amd64 1.7.0~rc1-0ubuntu5.1 [13.7 kB]
Get:5 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libcupsimage2 amd64 1.7.0~rc1-0ubuntu5.1 [17.2 kB]
Get:6 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libcupscgi1 amd64 1.7.0~rc1-0ubuntu5.1 [30.0 kB]
Get:7 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main cups-daemon amd64 1.7.0~rc1-0ubuntu5.1 [281 kB]
Get:8 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main cups-bsd amd64 1.7.0~rc1-0ubuntu5.1 [30.2 kB]
Get:9 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main cups-client amd64 1.7.0~rc1-0ubuntu5.1 [178 kB]
Get:10 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main cups-server-common all 1.7.0~rc1-0ubuntu5.1 [667 kB]
Get:11 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main cups amd64 1.7.0~rc1-0ubuntu5.1 [244 kB]
Get:12 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libcups2 i386 1.7.0~rc1-0ubuntu5.1 [210 kB]
Get:13 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libcups2 amd64 1.7.0~rc1-0ubuntu5.1 [215 kB]
Get:14 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main cups-common all 1.7.0~rc1-0ubuntu5.1 [219 kB]
Get:15 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main cups-ppdc amd64 1.7.0~rc1-0ubuntu5.1 [30.1 kB]
Get:16 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main gir1.2-dbusmenu-glib-0.4 amd64 12.10.3+13.10.20131104-0ubuntu1 [7,062 B]
Get:17 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libdbusmenu-glib4 amd64 12.10.3+13.10.20131104-0ubuntu1 [48.1 kB]
Get:18 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libdbusmenu-gtk3-4 amd64 12.10.3+13.10.20131104-0ubuntu1 [32.2 kB]
Get:19 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libdbusmenu-gtk4 amd64 12.10.3+13.10.20131104-0ubuntu1 [32.2 kB]
Get:20 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libdrm-intel1 i386 2.4.46-1ubuntu1 [62.6 kB]
Get:21 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libdrm-intel1 amd64 2.4.46-1ubuntu1 [63.0 kB]
Get:22 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libdrm-nouveau2 i386 2.4.46-1ubuntu1 [15.9 kB]
Get:23 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libdrm-nouveau2 amd64 2.4.46-1ubuntu1 [15.1 kB]
Get:24 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libdrm-radeon1 i386 2.4.46-1ubuntu1 [27.2 kB]
Get:25 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libdrm-radeon1 amd64 2.4.46-1ubuntu1 [26.3 kB]
Get:26 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libglamor0 amd64 0.5.1-0ubuntu4.2 [94.7 kB]
Get:27 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libapparmor1 amd64 2.8.0-0ubuntu31.1 [41.5 kB]
Get:28 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libapparmor-perl amd64 2.8.0-0ubuntu31.1 [36.2 kB]
Get:29 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main apparmor amd64 2.8.0-0ubuntu31.1 [369 kB]
Get:30 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main firefox amd64 25.0.1+build1-0ubuntu0.13.10.1 [29.0 MB]
Get:31 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main firefox-locale-en amd64 25.0.1+build1-0ubuntu0.13.10.1 [580 kB]
Get:32 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main indicator-application amd64 12.10.1+13.10.20131107-0ubuntu1 [28.4 kB]
Get:33 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main telepathy-mission-control-5 amd64 1:5.14.1-1ubuntu6.1 [187 kB]
Get:34 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main libmission-control-plugins0 amd64 1:5.14.1-1ubuntu6.1 [19.4 kB]
Get:35 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/multiverse nautilus-dropbox amd64 1.4.0-3ubuntu0.13.10.1 [94.2 kB]
Get:36 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main xserver-xorg-glamoregl amd64 0.5.1-0ubuntu4.2 [7,906 B]
Fetched 33.0 MB in 16s (2,015 kB/s)                                            
Extract templates from packages: 100%
Preconfiguring packages ...
Setting up udev (204-5) ...
insserv: warning: script 'bluetooth' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `bluetooth'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `bluetooth'
insserv: warning: script 'console-setup' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `console-setup'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `console-setup'
insserv: warning: script 'setvtrgb' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `setvtrgb'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `setvtrgb'
insserv: warning: script 'rfkill-store' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `rfkill-store'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `rfkill-store'
insserv: warning: script 'anacron' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `anacron'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `anacron'
insserv: warning: script 'cgroup-lite' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `cgroup-lite'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `cgroup-lite'
insserv: warning: script 'friendly-recovery' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `friendly-recovery'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `friendly-recovery'
insserv: warning: script 'console-font' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `console-font'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `console-font'
insserv: warning: script 'cron' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `cron'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `cron'
insserv: warning: script 'rfkill-restore' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `rfkill-restore'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `rfkill-restore'
insserv: warning: script 'resolvconf' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `resolvconf'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `resolvconf'
insserv: warning: script 'kmod' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `kmod'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `kmod'
udev stop/waiting
udev start/running, process 16304
update-initramfs: deferring update (trigger activated)
insserv: Service mountkernfs has to be enabled to start service udev
insserv: exiting now!
update-rc.d: error: insserv rejected the script header
dpkg: error processing udev (--configure):
 subprocess installed post-installation script returned error exit status 1
configured to not write apport reports
                                      Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.11.0-13-generic
Errors were encountered while processing:
 udev
E: Sub-process /usr/bin/dpkg returned an error code (1)

```[COLOR=#000000]

Perhaps udev can also be reverted? 

Thank you again for your help so far[/COLOR]

---

### Post by Bashing-om on 2013-11-20
slgtheindividual; Welp, that is some progress.

However !
> 
insserv: Service mountkernfs has to be enabled to start service udev
insserv: exiting now!
update-rc.d: error: insserv rejected the script header
dpkg: error processing udev (--configure):

//
My remarks:
and in respect to udev: sort of confusing ...->udev start/running, process 16304, and then ->dpkg: error processing udev (--configure):
Not at all conclusive as to what udev is doing !
//

udev stop/waiting
udev start/running, process 16304
update-initramfs: deferring update (trigger activated)
insserv: Service mountkernfs has to be enabled to start service udev
insserv: exiting now!
update-rc.d: error: insserv rejected the script header
dpkg: error processing udev (--configure):


lemme take a bit longer to look over the outputs, some I find presently disturbing ...

[INDENT][INDENT]cause and effect !
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2013-11-20
slgtheindividual; OK,

There are several things I do not understand, and others I have reservations about. Foremost is "udev" --changing of PIDs from 10383 to that of 16304; How that could happen blows me away. But, let's continue on , clean up and see what things look like afterward.
Terminal codes:
```

sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get --fix-missing install
sudo dpkg --configure --pending

```
Hoping some of those config files gets fixed or offers a means to fix them.

And now let's see what the package manager thinks, looking at dependencies; - no return is great !:
```

sudo dpkg -C

```

With these, will see what else is to do next.
Mind you I do have in mind what 3rd party applications got broke with the downgrade !

[INDENT][INDENT]We are, I hope, looking bright
[/INDENT][/INDENT]

---

### Post by slgtheindividual on 2013-11-20
ok, ran those:

```

:~$ sudo dpkg --configure -a


Setting up udev (204-5) ...
insserv: warning: script 'bluetooth' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `bluetooth'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `bluetooth'
insserv: warning: script 'console-setup' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `console-setup'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `console-setup'
insserv: warning: script 'setvtrgb' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `setvtrgb'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `setvtrgb'
insserv: warning: script 'rfkill-store' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `rfkill-store'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `rfkill-store'
insserv: warning: script 'anacron' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `anacron'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `anacron'
insserv: warning: script 'cgroup-lite' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `cgroup-lite'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `cgroup-lite'
insserv: warning: script 'friendly-recovery' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `friendly-recovery'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `friendly-recovery'
insserv: warning: script 'console-font' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `console-font'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `console-font'
insserv: warning: script 'cron' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `cron'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `cron'
insserv: warning: script 'rfkill-restore' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `rfkill-restore'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `rfkill-restore'
insserv: warning: script 'resolvconf' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `resolvconf'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `resolvconf'
insserv: warning: script 'kmod' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `kmod'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `kmod'
udev stop/waiting
udev start/running, process 23468
update-initramfs: deferring update (trigger activated)
insserv: Service mountkernfs has to be enabled to start service udev
insserv: exiting now!
update-rc.d: error: insserv rejected the script header
dpkg: error processing udev (--configure):
 subprocess installed post-installation script returned error exit status 1
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.11.0-13-generic
Errors were encountered while processing:
 udev
:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 105 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up udev (204-5) ...
insserv: warning: script 'bluetooth' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `bluetooth'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `bluetooth'
insserv: warning: script 'console-setup' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `console-setup'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `console-setup'
insserv: warning: script 'setvtrgb' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `setvtrgb'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `setvtrgb'
insserv: warning: script 'rfkill-store' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `rfkill-store'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `rfkill-store'
insserv: warning: script 'anacron' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `anacron'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `anacron'
insserv: warning: script 'cgroup-lite' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `cgroup-lite'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `cgroup-lite'
insserv: warning: script 'friendly-recovery' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `friendly-recovery'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `friendly-recovery'
insserv: warning: script 'console-font' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `console-font'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `console-font'
insserv: warning: script 'cron' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `cron'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `cron'
insserv: warning: script 'rfkill-restore' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `rfkill-restore'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `rfkill-restore'
insserv: warning: script 'resolvconf' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `resolvconf'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `resolvconf'
insserv: warning: script 'kmod' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `kmod'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `kmod'
udev stop/waiting
udev start/running, process 29088
update-initramfs: deferring update (trigger activated)
insserv: Service mountkernfs has to be enabled to start service udev
insserv: exiting now!
update-rc.d: error: insserv rejected the script header
dpkg: error processing udev (--configure):
 subprocess installed post-installation script returned error exit status 1
configured to not write apport reports
                                      Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.11.0-13-generic
Errors were encountered while processing:
 udev
E: Sub-process /usr/bin/dpkg returned an error code (1)
~$ sudo apt-get --fix-missing install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 105 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up udev (204-5) ...
insserv: warning: script 'bluetooth' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `bluetooth'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `bluetooth'
insserv: warning: script 'console-setup' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `console-setup'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `console-setup'
insserv: warning: script 'setvtrgb' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `setvtrgb'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `setvtrgb'
insserv: warning: script 'rfkill-store' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `rfkill-store'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `rfkill-store'
insserv: warning: script 'anacron' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `anacron'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `anacron'
insserv: warning: script 'cgroup-lite' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `cgroup-lite'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `cgroup-lite'
insserv: warning: script 'friendly-recovery' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `friendly-recovery'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `friendly-recovery'
insserv: warning: script 'console-font' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `console-font'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `console-font'
insserv: warning: script 'cron' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `cron'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `cron'
insserv: warning: script 'rfkill-restore' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `rfkill-restore'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `rfkill-restore'
insserv: warning: script 'resolvconf' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `resolvconf'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `resolvconf'
insserv: warning: script 'kmod' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `kmod'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `kmod'
udev stop/waiting
udev start/running, process 2601
update-initramfs: deferring update (trigger activated)
insserv: Service mountkernfs has to be enabled to start service udev
insserv: exiting now!
update-rc.d: error: insserv rejected the script header
dpkg: error processing udev (--configure):
 subprocess installed post-installation script returned error exit status 1
configured to not write apport reports
                                      Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.11.0-13-generic
Errors were encountered while processing:
 udev
E: Sub-process /usr/bin/dpkg returned an error code (1)
~$ sudo dpkg --configure --pending
Setting up udev (204-5) ...
insserv: warning: script 'bluetooth' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `bluetooth'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `bluetooth'
insserv: warning: script 'console-setup' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `console-setup'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `console-setup'
insserv: warning: script 'setvtrgb' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `setvtrgb'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `setvtrgb'
insserv: warning: script 'rfkill-store' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `rfkill-store'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `rfkill-store'
insserv: warning: script 'anacron' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `anacron'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `anacron'
insserv: warning: script 'cgroup-lite' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `cgroup-lite'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `cgroup-lite'
insserv: warning: script 'friendly-recovery' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `friendly-recovery'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `friendly-recovery'
insserv: warning: script 'console-font' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `console-font'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `console-font'
insserv: warning: script 'cron' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `cron'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `cron'
insserv: warning: script 'rfkill-restore' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `rfkill-restore'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `rfkill-restore'
insserv: warning: script 'resolvconf' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `resolvconf'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `resolvconf'
insserv: warning: script 'kmod' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `kmod'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `kmod'
udev stop/waiting
udev start/running, process 8440
update-initramfs: deferring update (trigger activated)
insserv: Service mountkernfs has to be enabled to start service udev
insserv: exiting now!
update-rc.d: error: insserv rejected the script header
dpkg: error processing udev (--configure):
 subprocess installed post-installation script returned error exit status 1
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.11.0-13-generic
Errors were encountered while processing:
 udev
:~$ sudo dpkg -C
The following packages are only half configured, probably due to problems
configuring them the first time. The configuration should be retried using
dpkg --configure <package> or the configure menu option in dselect:
 udev                 /dev/ and hotplug management daemon

```

---

### Post by Bashing-om on 2013-11-20
slgtheindividual; Sorry about the dekay,
I missed your reply.
Lots of warning for scripts;
insserv still hollering about some "update-rc.d: error: insserv rejected the script header" (yuk);
udev not configured.

Let's take dpkg's advise and 
Try this:
```

sudo dpkg --configure udev

```
I expect the wizard to ask questions for configuration, consider carefully before answering.

Then we will see what must next be done.

[INDENT][INDENT]five steps forward a 3 back
[/INDENT][/INDENT]

---

### Post by slgtheindividual on 2013-11-20
that's ok, no problem.

It seemed not to get that far:
```

:~$ sudo dpkg --configure udev


Setting up udev (204-5) ...
insserv: warning: script 'bluetooth' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `bluetooth'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `bluetooth'
insserv: warning: script 'console-setup' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `console-setup'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `console-setup'
insserv: warning: script 'setvtrgb' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `setvtrgb'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `setvtrgb'
insserv: warning: script 'rfkill-store' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `rfkill-store'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `rfkill-store'
insserv: warning: script 'anacron' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `anacron'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `anacron'
insserv: warning: script 'cgroup-lite' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `cgroup-lite'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `cgroup-lite'
insserv: warning: script 'friendly-recovery' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `friendly-recovery'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `friendly-recovery'
insserv: warning: script 'console-font' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `console-font'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `console-font'
insserv: warning: script 'cron' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `cron'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `cron'
insserv: warning: script 'rfkill-restore' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `rfkill-restore'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `rfkill-restore'
insserv: warning: script 'resolvconf' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `resolvconf'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `resolvconf'
insserv: warning: script 'kmod' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `kmod'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `kmod'
udev stop/waiting
udev start/running, process 14425
update-initramfs: deferring update (trigger activated)
insserv: Service mountkernfs has to be enabled to start service udev
insserv: exiting now!
update-rc.d: error: insserv rejected the script header
dpkg: error processing udev (--configure):
 subprocess installed post-installation script returned error exit status 1
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.11.0-13-generic
Errors were encountered while processing:
 udev

```

---

### Post by Bashing-om on 2013-11-20
slgtheindividual; Well,

'nother exercise in futility !

What script header, and how to find it !
To go with your former thought, lets see what version of "udev" is installed:
```

apt-cache policy udev
dpkg -l udev

```

AND, gota get "mountkernfs" running !

[INDENT][INDENT]work to do, work work work
[/INDENT][/INDENT]

---

### Post by slgtheindividual on 2013-11-21
ok, the info is below:

```

~$ apt-cache policy udev
udev:
  Installed: 204-5
  Candidate: 204-5
  Version table:
 *** 204-5 0
        100 /var/lib/dpkg/status
     204-0ubuntu19 0
        500 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main amd64 Packages
     204-0ubuntu18 0
        500 http://gb.archive.ubuntu.com/ubuntu/ saucy/main amd64 Packages
~$ dpkg -l udev
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
iF  udev           204-5        amd64        /dev/ and hotplug management daem



```

---

### Post by Bashing-om on 2013-11-21
slgtheindividual;

My thinking has become cloudy and difficult to focus. Calling it a night and I will pick this up once more in my AM. Will sleep on why udev does not configure.
Maybe this:
> 
Package udev

saucy-updates (admin): /dev/ and hotplug management daemon 
204-0ubuntu19: amd64 i386


which is what should be installed !
[INDENT][INDENT]'till I can better focus
[/INDENT][/INDENT]

---

### Post by slgtheindividual on 2013-11-21
Ok, no problem, thank you again for all the help so far =]

---

### Post by Bashing-om on 2013-11-21
slgtheindividual; Hello,

I think the thing to do now is to install the proper version of udev:
Particularly so as "apt-cache policy" assures that it is available in your mirror site.
```

sudo apt-get install udev=204-0ubuntu19

```
Do that and we will see what gets broke, and start (re-)configuring (??), or - hopefully all those missing components for "insserv" will be resolved when the corresponding version to "procps" is installed.

[INDENT][INDENT]cause and effect -> fix it
[/INDENT][/INDENT]

---

### Post by slgtheindividual on 2013-11-21
it says there is a dependancy problem:

```

~$ sudo apt-get install udev=204-0ubuntu19
 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies.
 udev : Depends: libudev1 (= 204-0ubuntu19) but 204-5 is to be installed
E: Unable to correct problems, you have held broken packages.

```

---

### Post by Bashing-om on 2013-11-21
slgtheindividual; still that is some progress.

I feel better with that. 
Earlier I had attempted to access info @ packages.ubuntu, the search was down .. 
Let me have time to research that dependency issue ,,, and when the search feature of packages.ubuntu is back up.. will advise on what I think.
In the meantime I will also be looking at what the package manager has to advise on dependencies.
as in:
```

apt-cache depends libudev1

```

Oh Lord ! Maybe a can of worms ? looking at :
> 
PreDepends: multiarch-support
    multiarch-support:i386


Doing :
```

apt-cache rdepends libudev1

```
says we definitely have to get this right !

[INDENT][INDENT]all we can do is try
[/INDENT][/INDENT]

---

### Post by slgtheindividual on 2013-11-21
ok cool, well I'll be away for about 5 hours, but I'll get back to you then, thank you for looking into it for me =]

---

### Post by Bashing-om on 2013-11-21
slgtheindividual; YUk.

off topic: Hey, I enjoy a good puzzle and working with good people to come up with a solution. Helping others helps me too !
See ya in bout 5 hours, thanks for that advisement.

Back on topic:
Search in packages.ubuntu still down .. while waiting, what results:
```

ls -la /var/cache/apt/archives/libdev* ##no output is OK

```
let's check what other packages may need to be re-installed, please post the output of
```

file /var/lib/dpkg/info/*.list|grep -vw text ##again no output is great!

```

[INDENT][INDENT]OH, the web we weave for ourselves [/INDENT][/INDENT]

---

### Post by ian-weisser on 2013-11-21
Here seems to be one piece of the problem:

> **slgtheindividual said:**
> 
The following packages have unmet dependencies.
 udev : Depends: libudev1 (= [COLOR=#008000]204-0ubuntu19[/COLOR]) but [COLOR=#0000ff]204-5[/COLOR] is to be installed


```
$ rmadison -u ubuntu udev
      [...]
      udev | 204-0ubuntu18 |         saucy | amd64, arm64, armhf, i386, powerpc
      udev | [COLOR=#008000]204-0ubuntu19[/COLOR] | saucy-updates | amd64, arm64, armhf, i386, powerpc
      udev | [COLOR=#0000ff]204-5[/COLOR]ubuntu6 |        trusty | amd64, arm64, armhf, i386, powerpc

```

You seem to have a Trusty 14.04 pre-release repository or PPA (instead of Saucy 13.10) in your /etc/apt/sources.list or /etc/apt/sources.list.d somewhere. That would certainly cause a lot of problems.

Disable (uncheck) *all* your PPAs and non-official repositories (including Steam and Google and all the rest).
Then try **sudo apt-get update && sudo apt-get upgrade  **again.

Reminder: PPAs are not community-supported software. Use them at your own risk.

---

### Post by Bashing-om on 2013-11-21
+10
> 
You seem to have a Trusty 14.04 pre-release repository or PPA (instead of Saucy 13.10) in your /etc/apt/sources.list or /etc/apt/sources.list.d somewhere. That would certainly cause a lot of problems.


Had a similar thought .. as also the "procps" package was elevated for something between suacy update and trusty .. a wonder in it's self how that came about .. must be some 3rd party application in testing mode (???). Of course, each time we have run "apt-get update" the situation is getting compounded.

Keeping it on my mind to check the sources !

[INDENT][INDENT]no quit in our nature
[/INDENT][/INDENT]

---

### Post by slgtheindividual on 2013-11-21
> **Bashing-om said:**
> slgtheindividual; YUk.

off topic: Hey, I enjoy a good puzzle and working with good people to come up with a solution. Helping others helps me too !
See ya in bout 5 hours, thanks for that advisement.

Back on topic:
Search in packages.ubuntu still down .. while waiting, what results:
```

ls -la /var/cache/apt/archives/libdev* ##no output is OK

```
let's check what other packages may need to be re-installed, please post the output of
```

file /var/lib/dpkg/info/*.list|grep -vw text ##again no output is great!

```
[INDENT][INDENT]OH, the web we weave for ourselves [/INDENT]
[/INDENT]



That's a good attitude to have.

Ok so I ran those:

```

~$ ls -la /var/cache/apt/archives/libdev*
ls: cannot access /var/cache/apt/archives/libdev*: No such file or directory

~$ file /var/lib/dpkg/info/*.list|grep -vw text
/var/lib/dpkg/info/blinken.list:                                                     empty
/var/lib/dpkg/info/gamine.list:                                                      empty
/var/lib/dpkg/info/gramps.list:                                                      empty
/var/lib/dpkg/info/libmuparser2:amd64.list:                                          empty
/var/lib/dpkg/info/libosmgpsmap2:amd64.list:                                         empty
/var/lib/dpkg/info/librecad.list:                                                    empty
/var/lib/dpkg/info/plymouth-theme-edubuntu.list:                                     empty
/var/lib/dpkg/info/yelp.list:                                                        empty

```

I then disabled all my PPA's (I only know how to use the gui to do this so that's what I did) and tried update and upgrade:

```

~$ sudo apt-get update && sudo apt-get upgrade
 
Ign http://gb.archive.ubuntu.com saucy InRelease
Ign http://security.ubuntu.com saucy-security InRelease
Ign http://gb.archive.ubuntu.com saucy-updates InRelease
Hit http://security.ubuntu.com saucy-security Release.gpg
Ign http://gb.archive.ubuntu.com saucy-backports InRelease
Hit http://gb.archive.ubuntu.com saucy Release.gpg
Hit http://security.ubuntu.com saucy-security Release
Hit http://gb.archive.ubuntu.com saucy-updates Release.gpg
Hit http://gb.archive.ubuntu.com saucy-backports Release.gpg
Hit http://security.ubuntu.com saucy-security/main Sources
Hit http://gb.archive.ubuntu.com saucy Release
Hit http://gb.archive.ubuntu.com saucy-updates Release                
Hit http://security.ubuntu.com saucy-security/restricted Sources      
Hit http://gb.archive.ubuntu.com saucy-backports Release              
Hit http://security.ubuntu.com saucy-security/universe Sources        
Hit http://gb.archive.ubuntu.com saucy/main Sources
Hit http://gb.archive.ubuntu.com saucy/restricted Sources
Hit http://security.ubuntu.com saucy-security/multiverse Sources
Hit http://gb.archive.ubuntu.com saucy/universe Sources
Hit http://security.ubuntu.com saucy-security/main amd64 Packages
Hit http://gb.archive.ubuntu.com saucy/multiverse Sources
Hit http://security.ubuntu.com saucy-security/restricted amd64 Packages
Hit http://gb.archive.ubuntu.com saucy/main amd64 Packages
Hit http://gb.archive.ubuntu.com saucy/restricted amd64 Packages
Hit http://security.ubuntu.com saucy-security/universe amd64 Packages
Hit http://gb.archive.ubuntu.com saucy/universe amd64 Packages
Hit http://security.ubuntu.com saucy-security/multiverse amd64 Packages
Hit http://gb.archive.ubuntu.com saucy/multiverse amd64 Packages
Hit http://security.ubuntu.com saucy-security/main i386 Packages
Hit http://security.ubuntu.com saucy-security/restricted i386 Packages
Hit http://security.ubuntu.com saucy-security/universe i386 Packages
Hit http://gb.archive.ubuntu.com saucy/main i386 Packages
Hit http://gb.archive.ubuntu.com saucy/restricted i386 Packages
Hit http://security.ubuntu.com saucy-security/multiverse i386 Packages
Hit http://gb.archive.ubuntu.com saucy/universe i386 Packages
Hit http://gb.archive.ubuntu.com saucy/multiverse i386 Packages
Hit http://gb.archive.ubuntu.com saucy/main Translation-en_GB
Hit http://gb.archive.ubuntu.com saucy/main Translation-en
Hit http://gb.archive.ubuntu.com saucy/multiverse Translation-en_GB
Hit http://security.ubuntu.com saucy-security/main Translation-en
Hit http://gb.archive.ubuntu.com saucy/multiverse Translation-en
Hit http://gb.archive.ubuntu.com saucy/restricted Translation-en_GB
Hit http://gb.archive.ubuntu.com saucy/restricted Translation-en
Hit http://security.ubuntu.com saucy-security/multiverse Translation-en
Hit http://gb.archive.ubuntu.com saucy/universe Translation-en_GB
Hit http://gb.archive.ubuntu.com saucy/universe Translation-en
Hit http://gb.archive.ubuntu.com saucy-updates/main Sources
Hit http://security.ubuntu.com saucy-security/restricted Translation-en
Hit http://gb.archive.ubuntu.com saucy-updates/restricted Sources
Hit http://gb.archive.ubuntu.com saucy-updates/universe Sources
Hit http://gb.archive.ubuntu.com saucy-updates/multiverse Sources
Hit http://security.ubuntu.com saucy-security/universe Translation-en
Hit http://gb.archive.ubuntu.com saucy-updates/main amd64 Packages
Hit http://gb.archive.ubuntu.com saucy-updates/restricted amd64 Packages
Hit http://gb.archive.ubuntu.com saucy-updates/universe amd64 Packages
Hit http://gb.archive.ubuntu.com saucy-updates/multiverse amd64 Packages
Hit http://gb.archive.ubuntu.com saucy-updates/main i386 Packages
Hit http://gb.archive.ubuntu.com saucy-updates/restricted i386 Packages
Hit http://gb.archive.ubuntu.com saucy-updates/universe i386 Packages
Hit http://gb.archive.ubuntu.com saucy-updates/multiverse i386 Packages
Hit http://gb.archive.ubuntu.com saucy-updates/main Translation-en
Hit http://gb.archive.ubuntu.com saucy-updates/multiverse Translation-en
Hit http://gb.archive.ubuntu.com saucy-updates/restricted Translation-en
Hit http://gb.archive.ubuntu.com saucy-updates/universe Translation-en
Hit http://gb.archive.ubuntu.com saucy-backports/main Sources
Ign http://security.ubuntu.com saucy-security/main Translation-en_GB
Hit http://gb.archive.ubuntu.com saucy-backports/restricted Sources
Ign http://security.ubuntu.com saucy-security/multiverse Translation-en_GB
Hit http://gb.archive.ubuntu.com saucy-backports/universe Sources
Ign http://security.ubuntu.com saucy-security/restricted Translation-en_GB
Hit http://gb.archive.ubuntu.com saucy-backports/multiverse Sources
Hit http://gb.archive.ubuntu.com saucy-backports/main amd64 Packages
Ign http://security.ubuntu.com saucy-security/universe Translation-en_GB
Hit http://gb.archive.ubuntu.com saucy-backports/restricted amd64 Packages
Hit http://gb.archive.ubuntu.com saucy-backports/universe amd64 Packages
Hit http://gb.archive.ubuntu.com saucy-backports/multiverse amd64 Packages
Hit http://gb.archive.ubuntu.com saucy-backports/main i386 Packages
Hit http://gb.archive.ubuntu.com saucy-backports/restricted i386 Packages
Hit http://gb.archive.ubuntu.com saucy-backports/universe i386 Packages
Hit http://gb.archive.ubuntu.com saucy-backports/multiverse i386 Packages
Hit http://gb.archive.ubuntu.com saucy-backports/main Translation-en
Hit http://gb.archive.ubuntu.com saucy-backports/multiverse Translation-en
Hit http://gb.archive.ubuntu.com saucy-backports/restricted Translation-en
Hit http://gb.archive.ubuntu.com saucy-backports/universe Translation-en
Ign http://gb.archive.ubuntu.com saucy-updates/main Translation-en_GB
Ign http://gb.archive.ubuntu.com saucy-updates/multiverse Translation-en_GB
Ign http://gb.archive.ubuntu.com saucy-updates/restricted Translation-en_GB
Ign http://gb.archive.ubuntu.com saucy-updates/universe Translation-en_GB
Ign http://gb.archive.ubuntu.com saucy-backports/main Translation-en_GB
Ign http://gb.archive.ubuntu.com saucy-backports/multiverse Translation-en_GB
Ign http://gb.archive.ubuntu.com saucy-backports/restricted Translation-en_GB
Ign http://gb.archive.ubuntu.com saucy-backports/universe Translation-en_GB
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  apparmor cups cups-bsd cups-client cups-common cups-daemon cups-ppdc
  cups-server-common desktop-file-utils firefox firefox-locale-en
  flashplugin-installer gir1.2-dbusmenu-glib-0.4 gir1.2-gtk-3.0 gnome-keyring
  gnome-screensaver hud indicator-application indicator-appmenu
  initramfs-tools initramfs-tools-bin kdelibs-bin kdelibs5-data
  kdelibs5-plugins kdoctools libapparmor-perl libapparmor1 libavcodec53
  libavformat53 libavutil51 libcups2 libcups2:i386 libcupscgi1 libcupsimage2
  libcupsmime1 libcupsppdc1 libdbusmenu-glib4 libdbusmenu-gtk3-4
  libdbusmenu-gtk4 libdrm-intel1 libdrm-intel1:i386 libdrm-nouveau2
  libdrm-nouveau2:i386 libdrm-radeon1 libdrm-radeon1:i386 libdrm2 libdrm2:i386
  libgail-3-0 libglamor0 libgnome-media-profiles-3.0-0 libgtk-3-0 libgtk-3-bin
  libgtk-3-common libhud-client2 libido3-0.1-0 libkcmutils4 libkde3support4
  libkdeclarative5 libkdecore5 libkdesu5 libkdeui5 libkdewebkit5 libkdnssd4
  libkemoticons4 libkfile4 libkhtml5 libkidletime4 libkio5 libkjsapi4
  libkjsembed4 libkmediaplayer4 libknewstuff2-4 libknewstuff3-4
  libknotifyconfig4 libkntlm4 libkparts4 libkprintutils4 libkpty4
  libkrosscore4 libktexteditor4 libkunitconversion4 liblxc0
  libmission-control-plugins0 libnepomuk4 libnepomukquery4a libnepomukutils4
  libnss3 libnss3-1d libp11-kit-gnome-keyring libp11-kit-gnome-keyring:i386
  libpam-gnome-keyring libplasma3 libpostproc52 libsolid4 libswscale2
  libthreadweaver4 lxc lxc-templates nautilus-dropbox python3-lxc shim-signed
  telepathy-mission-control-5 thunderbird thunderbird-gnome-support
  thunderbird-locale-en thunderbird-locale-en-us xserver-xorg-glamoregl
107 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 29.8 MB/83.7 MB of archives.
After this operation, 61.4 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main thunderbird-locale-en amd64 1:24.1.1+build1-0ubuntu0.13.10.1 [342 kB]
Get:2 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main thunderbird amd64 1:24.1.1+build1-0ubuntu0.13.10.1 [29.5 MB]
Get:3 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main thunderbird-gnome-support amd64 1:24.1.1+build1-0ubuntu0.13.10.1 [9,120 B]
Get:4 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main thunderbird-locale-en-us all 1:24.1.1+build1-0ubuntu0.13.10.1 [12.5 kB]
Fetched 29.8 MB in 8s (3,564 kB/s)                                             
Extract templates from packages: 100%
Preconfiguring packages ...
Setting up udev (204-5) ...
insserv: warning: script 'bluetooth' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `bluetooth'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `bluetooth'
insserv: warning: script 'console-setup' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `console-setup'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `console-setup'
insserv: warning: script 'setvtrgb' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `setvtrgb'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `setvtrgb'
insserv: warning: script 'rfkill-store' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `rfkill-store'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `rfkill-store'
insserv: warning: script 'anacron' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `anacron'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `anacron'
insserv: warning: script 'cgroup-lite' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `cgroup-lite'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `cgroup-lite'
insserv: warning: script 'friendly-recovery' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `friendly-recovery'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `friendly-recovery'
insserv: warning: script 'console-font' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `console-font'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `console-font'
insserv: warning: script 'cron' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `cron'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `cron'
insserv: warning: script 'rfkill-restore' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `rfkill-restore'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `rfkill-restore'
insserv: warning: script 'resolvconf' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `resolvconf'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `resolvconf'
insserv: warning: script 'kmod' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `kmod'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `kmod'
udev stop/waiting
udev start/running, process 6024
update-initramfs: deferring update (trigger activated)
insserv: Service mountkernfs has to be enabled to start service udev
insserv: exiting now!
update-rc.d: error: insserv rejected the script header
dpkg: error processing udev (--configure):
 subprocess installed post-installation script returned error exit status 1
configured to not write apport reports
                                      Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.11.0-13-generic
Errors were encountered while processing:
 udev
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by ian-weisser on 2013-11-21
This may be heretical, but since we already know the filesystems are mounted...we could simply edit /etc/init.d/udev to temporarily remove the requirement for mountkernfs. Then update/upgrade. Then revert the change.

All the rest of those insserv warnings seem to be jobs that have transitioned to upstart (well, so has udev), and are merely warnings that the LSB tags are (correctly) no longer in the init scritps.

It may not answer the question "what is the problem?" It may fail. There is some risk of unanticipated results, though I believe the risk to be fairly low.

---

### Post by Bashing-om on 2013-11-21
slgtheindividual; Welp,

Before getting back onto "udev" let us go ahead and see what the source list are:
Post back the outputs:
```

cat -n /etc/apt/sources.list
ls -la /etc/apt/sources.list.d/

```
Now those who are real good with bash can craft the command to look into each one of those files at one swipe - I ain't there yet -.
So, will make do with the slow way and see what the output is and look at the files in the /sources.list.d/ directory as needed.

reduce to simplest terms and ->
[INDENT][INDENT][INDENT]take it from there
[/INDENT][/INDENT][/INDENT]

---

### Post by slgtheindividual on 2013-11-21
ok well here is the output of those:

```

~$ cat -n /etc/apt/sources.list
     1	# deb cdrom:[Ubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016.1)]/ saucy main restricted
     2	
     3	# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     4	# newer versions of the distribution.
     5	deb http://gb.archive.ubuntu.com/ubuntu/ saucy main restricted
     6	deb-src http://gb.archive.ubuntu.com/ubuntu/ saucy main restricted
     7	
     8	## Major bug fix updates produced after the final release of the
     9	## distribution.
    10	deb http://gb.archive.ubuntu.com/ubuntu/ saucy-updates main restricted
    11	deb-src http://gb.archive.ubuntu.com/ubuntu/ saucy-updates main restricted
    12	
    13	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14	## team. Also, please note that software in universe WILL NOT receive any
    15	## review or updates from the Ubuntu security team.
    16	deb http://gb.archive.ubuntu.com/ubuntu/ saucy universe
    17	deb-src http://gb.archive.ubuntu.com/ubuntu/ saucy universe
    18	deb http://gb.archive.ubuntu.com/ubuntu/ saucy-updates universe
    19	deb-src http://gb.archive.ubuntu.com/ubuntu/ saucy-updates universe
    20	
    21	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    22	## team, and may not be under a free licence. Please satisfy yourself as to 
    23	## your rights to use the software. Also, please note that software in 
    24	## multiverse WILL NOT receive any review or updates from the Ubuntu
    25	## security team.
    26	deb http://gb.archive.ubuntu.com/ubuntu/ saucy multiverse
    27	deb-src http://gb.archive.ubuntu.com/ubuntu/ saucy multiverse
    28	deb http://gb.archive.ubuntu.com/ubuntu/ saucy-updates multiverse
    29	deb-src http://gb.archive.ubuntu.com/ubuntu/ saucy-updates multiverse
    30	
    31	## N.B. software from this repository may not have been tested as
    32	## extensively as that contained in the main release, although it includes
    33	## newer versions of some applications which may provide useful features.
    34	## Also, please note that software in backports WILL NOT receive any review
    35	## or updates from the Ubuntu security team.
    36	deb http://gb.archive.ubuntu.com/ubuntu/ saucy-backports main restricted universe multiverse
    37	deb-src http://gb.archive.ubuntu.com/ubuntu/ saucy-backports main restricted universe multiverse
    38	
    39	deb http://security.ubuntu.com/ubuntu saucy-security main restricted
    40	deb-src http://security.ubuntu.com/ubuntu saucy-security main restricted
    41	deb http://security.ubuntu.com/ubuntu saucy-security universe
    42	deb-src http://security.ubuntu.com/ubuntu saucy-security universe
    43	deb http://security.ubuntu.com/ubuntu saucy-security multiverse
    44	deb-src http://security.ubuntu.com/ubuntu saucy-security multiverse
    45	
    46	## Uncomment the following two lines to add software from Canonical's
    47	## 'partner' repository.
    48	## This software is not part of Ubuntu, but is offered by Canonical and the
    49	## respective vendors as a service to Ubuntu users.
    50	# deb http://archive.canonical.com/ubuntu saucy partner
    51	# deb-src http://archive.canonical.com/ubuntu saucy partner
    52	
    53	## This software is not part of Ubuntu, but is offered by third-party
    54	## developers who want to ship their latest software.
    55	# deb http://extras.ubuntu.com/ubuntu saucy main
    56	# deb-src http://extras.ubuntu.com/ubuntu saucy main
    57	
    58	
    59	# deb http://ftp.uk.debian.org/debian jessie main


~$ ls -la /etc/apt/sources.list.d/
total 56
drwxr-xr-x 2 root root 4096 Nov 12 01:07 .
drwxr-xr-x 6 root root 4096 Oct 31 18:43 ..
-rw-r--r-- 1 root root  178 Nov 22 01:06 google-chrome.list
-rw-r--r-- 1 root root  178 Nov 22 01:06 google-chrome.list.save
-rw-r--r-- 1 root root  126 Nov 22 01:06 nvbn-rm-ppa-saucy.list
-rw-r--r-- 1 root root  126 Nov 22 01:06 nvbn-rm-ppa-saucy.list.save
-rw-r--r-- 1 root root  164 Nov 22 01:06 private-ppa.launchpad.net_commercial-ppa-uploaders_monster-rpg2_ubuntu.list
-rw-r--r-- 1 root root  164 Nov 22 01:06 private-ppa.launchpad.net_commercial-ppa-uploaders_monster-rpg2_ubuntu.list.save
-rw-r--r-- 1 root root  157 Nov 22 01:06 private-ppa.launchpad.net_commercial-ppa-uploaders_nitro_ubuntu.list
-rw-r--r-- 1 root root  157 Nov 22 01:06 private-ppa.launchpad.net_commercial-ppa-uploaders_nitro_ubuntu.list.save
-rw-r--r-- 1 root root  157 Nov 22 01:06 private-ppa.launchpad.net_commercial-ppa-uploaders_steam_ubuntu.list
-rw-r--r-- 1 root root  157 Nov 22 01:06 private-ppa.launchpad.net_commercial-ppa-uploaders_steam_ubuntu.list.save
-rw-r--r-- 1 root root  116 Nov 22 01:06 steam.list
-rw-r--r-- 1 root root  116 Nov 22 01:06 steam.list.save

```

---

### Post by Bashing-om on 2013-11-21
slgtheindividual; Hey,

The "/etc/apt/sources.list" should fly.
I have no idea what these are, from the 3rd party directory /etc/apt/sourcrs.list.d/ :
nvbn-rm-ppa-saucy.list
private-ppa.launchpad.net_commercial-ppa-uploaders_monster-rpg2_ubuntu.list
private-ppa.launchpad.net_commercial-ppa-uploaders_nitro_ubuntu.list
private-ppa.launchpad.net_commercial-ppa-uploaders_steam_ubuntu.list

Let's check and make sure they are out of the equation:
checking one of them:
```

cat /etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_monster-rpg2_ubuntu.list

```
is the fetch line commented out ?

As to Ian's great idea:
I can see a great benefit to get this system updated. I do not, however, see the means to implement the edit to "/etc/init.d/udev" to effect mountkernfs. 
Ian to the rescue ?

We are working toward getting udev downgraded to the correct version, then I hope the offending up-start scrips get fixed.
Else we are looking at editing each and every one to make up-start happy. That is a task pending a happy outcome of "udev's" downgrade.

progress:
[INDENT][INDENT]one step at a time
[/INDENT][/INDENT]

---

### Post by slgtheindividual on 2013-11-21
ok the output of that is below:

```

~$ cat /etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_monster-rpg2_ubuntu.list
# deb https://private-ppa.launchpad.net/commercial-ppa-uploaders/monster-rpg2/ubuntu saucy main #Added by software-center; credentials stored in /etc/apt/auth.conf

```


I assume the comments here are good?

---

### Post by Bashing-om on 2013-11-21
slgtheindividual;

Yep, and will "assume" the others have also been commented out.
Back to the current situation:
packages.ubuntu search is back up.

> 
Package libudev1

saucy-updates (libs): libudev shared library 
204-0ubuntu19: amd64 i386

//
Other Packages Related to libudev1

depends
multiarch-support
Transitional package to ensure multiarch compatibility
libc6 (>= 2.17)
Embedded GNU C Library: Shared libraries	
also a virtual package provided by libc6-udeb


So, what do you show for libc6 ?
```

dpkg -l libc6

```

Mean while ->
[INDENT][INDENT]back at the ranch
[/INDENT][/INDENT]

---

### Post by ian-weisser on 2013-11-21
> **Bashing-om said:**
> 
I can see a great benefit to get this system updated. I do not, however, see the means to implement the edit to "/etc/init.d/udev" to effect mountkernfs. 


Most profuse apologies for not being clear:

I meant: "Temporarily edit line #4 of /etc/init.d/udev"
```
#!/bin/sh -e
### BEGIN INIT INFO
# Provides:          udev
[COLOR=#ff0000]# Required-Start:    mountkernfs [/COLOR]
# Required-Stop:     
# Default-Start:     S
# Default-Stop:
# Short-Description: Start udevd, populate /dev and load drivers.
### END INIT INFO
[...]

```
Remove the reference to mountkernfs.
Save (this script is run by root, so use **sudo**)
sudo apt-get update && sudo apt-get upgrade
Edit the file once more to replace the reference to mountkernfs

---

### Post by slgtheindividual on 2013-11-21
ok so here is my terminal output:
```

~$ dpkg -l libc6
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                   Version          Architecture     Description
+++-======================-================-================-=================================================
ii  libc6:amd64            2.17-93ubuntu4   amd64            Embedded GNU C Library: Shared libraries
ii  libc6:i386             2.17-93ubuntu4   i386             Embedded GNU C Library: Shared libraries


```

going to edit that file now, and try another update, I'll post after

---

### Post by Bashing-om on 2013-11-21
@ Ian;

Pleased ya popped back in .. my 13.04  "/etc/init.d/udev" is totally different and has no reference to "mountkernfs " !
Completely different file structure.

Awaiting OP's return to see where we stand in getting to "udev".

[INDENT][INDENT]3 heads are better then 2, better than 1
[/INDENT][/INDENT]

---

### Post by slgtheindividual on 2013-11-21
> **ian-weisser said:**
> Most profuse apologies for not being clear:

I meant: "Temporarily edit line #4 of /etc/init.d/udev"
```
#!/bin/sh -e
### BEGIN INIT INFO
# Provides:          udev
[COLOR=#ff0000]# Required-Start:    mountkernfs [/COLOR]
# Required-Stop:     
# Default-Start:     S
# Default-Stop:
# Short-Description: Start udevd, populate /dev and load drivers.
### END INIT INFO
[...]

```
Remove the reference to mountkernfs.
Save (this script is run by root, so use **sudo**)
sudo apt-get update && sudo apt-get upgrade
Edit the file once more to replace the reference to mountkernfs


This worked =]
so here's what I did:

made a backup of /etc/init.d/udev:

```

~$ sudo cp /etc/init.d/udev /etc/init.d/udev-orig

```

deleted the line you said using gedit:

```

~$ sudo gedit /etc/init.d/udev

```

ran an update (which completed successfully) (I seem to have lost the output for this, but it worked):
```

~$ sudo apt-get update && sudo apt-get upgrade

```

so I restored the original file and checked it in gedit

```

~$ sudo cp /etc/init.d/udev-orig /etc/init.d/udev
~$ sudo gedit /etc/init.d/udev

```

then I re-enabled my PPA's from the package manager and ran a final update which again was a success.

I just want to say a huge thank you to you both for all of your time and effort, you not only solved my problem but also taught me, so thank you =D

---

### Post by Bashing-om on 2013-11-21
slgtheindividual; OUTSTANDING !!

A big thank you to Ian.

OK.. let's look
```

dpkg -l procps udev libudev1

```
and see that all is as should be !
[INDENT][INDENT]ain't nothing but a big thing
[/INDENT][/INDENT]

---

### Post by Bucky Ball on 2013-11-21
This has been fun to watch!

Please mark the thread as solved to help others. Thanks. ;)

---

### Post by slgtheindividual on 2013-11-21
ok we have:

```

~$ dpkg -l procps udev libudev1
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                   Version          Architecture     Description
+++-======================-================-================-=================================================
ii  libudev1:amd64         204-5            amd64            libudev shared library
ii  libudev1:i386          204-5            i386             libudev shared library
ii  procps                 1:3.3.3-2ubuntu9 amd64            /proc file system utilities
ii  udev                   204-5            amd64            /dev/ and hotplug management daemon

```

is that normal?

---

### Post by slgtheindividual on 2013-11-21
> **Bucky Ball said:**
> This has been fun to watch!

Please mark the thread as solved to help others. Thanks. ;)


Will do =]

---

### Post by Bucky Ball on 2013-11-21
... and I must add congratulations to you all on your efforts and persistence with this. ;)

---

### Post by slgtheindividual on 2013-11-21
yeah, thank you again, I really appreciate it :D

---

### Post by Bashing-om on 2013-11-21
slgtheindividual; welp,

The package manager is happy happy happy, so I am not about to complain.
To be honest though I had expected the versions of "libudev1" to be at 204-0ubuntu19;
and udev to also be at 204-0ubuntu19 .
But the package manager says all is good (ii , in the first colums). I am going to leave it at that.

[INDENT][INDENT]all's well that ends well
[/INDENT][/INDENT]

---

### Post by slgtheindividual on 2013-11-21
> **Bashing-om said:**
> slgtheindividual; welp,

The package manager is happy happy happy, so I am not about to complain.
To be honest though I had expected the versions of "libudev1" to be at 204-0ubuntu19;
and udev to also be at 204-0ubuntu19 .
But the package manager says all is good (ii , in the first colums). I am going to leave it at that.
[INDENT][INDENT]all's well that ends well
[/INDENT]
[/INDENT]



ok, that's no problem, thank you for all the help =]

---

### Post by ian-weisser on 2013-11-22
> **Bashing-om said:**
> To be honest though I had expected the versions of "libudev1" to be at 204-0ubuntu19;
and udev to also be at 204-0ubuntu19 .

While this workaround to restore the package manager to usefulness has worked (hooray),
the original cause (likely a PPA or non-official repository) has not been addressed. The problem may recur.

---

### Post by slgtheindividual on 2013-12-15
Just for anyone having a similar problem, after this problem was solved I had a new related problem with init-udev at startup, the thread on that is here
[URL="http://ubuntuforums.org/showthread.php?t=2192681"]
http://ubuntuforums.org/showthread.php?t=2192681[/URL]

---


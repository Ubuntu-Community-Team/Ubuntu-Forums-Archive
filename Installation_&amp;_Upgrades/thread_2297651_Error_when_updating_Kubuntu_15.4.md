---
title: "Error when updating Kubuntu 15.4"
date: 2015-10-05
forum: Installation &amp; Upgrades
---

### Post by pinstripedtie2 on 2015-10-05
Hello, I just installed Kubuntu 15.4 this weekend and have had two updates come across.
Both times I tried to update, I got an ERROR message and it said the files could not be
downloaded or something like that.

What could be wrong with this? I did not change or edit the repositories in any way. In fact,
I hadn't done much of anything other than to change the desktop background.

My puter is an MSI with an AMD FX - 4300 quad core processor - 8gigs mem - 128 Crucial SSD

Have had fluky things going on with the system already, besides the above. One time I booted 
up and there was no volume adjustment. Also, the entire system crashed once with sound going 
into repeat mode. Had to do hard reboot.

---

### Post by oldos2er on 2015-10-05
We need to know why the files cannot be downloaded. Can you please run the following in a konsole, and copy/paste all the output here? ```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by pinstripedtie2 on 2015-10-05
[FONT=monospace][COLOR=#000000]Here it is... PLUS, when I came home tonight and booted the system, It froze at the black screen, prior to reaching the desktop.

```
:~$ sudo apt-get update && sudo apt-get upgrade [/COLOR]
[sudo] password for ronny:  
Ign [http://dl.google.com](http://dl.google.com) stable InRelease 
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid InRelease                                        
Hit [http://dl.google.com](http://dl.google.com) stable Release                                       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-updates InRelease               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) vivid-security InRelease 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-backports InRelease 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid Release.gpg 
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) vivid-security Release.gpg [933 B] 
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-updates Release.gpg [933 B]             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-backports Release.gpg                      
Hit [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages 
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) vivid-security Release [63.5 kB]                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid Release                                 
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                                      
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-updates Release [63.5 kB]                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-backports Release                                
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                                  
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en 
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) vivid-security/main Sources [44.8 kB] 
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) vivid-security/restricted Sources [2,792 B] 
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) vivid-security/universe Sources [18.0 kB] 
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) vivid-security/multiverse Sources [1,966 B] 
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) vivid-security/main amd64 Packages [119 kB] 
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-updates/main Sources [90.8 kB] 
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) vivid-security/restricted amd64 Packages [10.4 kB] 
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-updates/restricted Sources [3,687 B]     
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) vivid-security/universe amd64 Packages [57.1 kB] 
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-updates/universe Sources [40.4 kB] 
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-updates/multiverse Sources [1,966 B] 
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) vivid-security/multiverse amd64 Packages [5,195 B] 
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-updates/main amd64 Packages [208 kB] 
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) vivid-security/main i386 Packages [119 kB] 
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-updates/restricted amd64 Packages [13.1 kB] 
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) vivid-security/restricted i386 Packages [10.2 kB] 
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-updates/universe amd64 Packages [111 kB] 
Get:22 [http://security.ubuntu.com](http://security.ubuntu.com) vivid-security/universe i386 Packages [57.1 kB] 
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-updates/multiverse amd64 Packages [5,195 B] 
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-updates/main i386 Packages [206 kB] 
Get:25 [http://security.ubuntu.com](http://security.ubuntu.com) vivid-security/multiverse i386 Packages [5,383 B] 
Get:26 [http://security.ubuntu.com](http://security.ubuntu.com) vivid-security/main Translation-en [63.4 kB]     
Get:27 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-updates/restricted i386 Packages [12.8 kB]    
Get:28 [http://security.ubuntu.com](http://security.ubuntu.com) vivid-security/multiverse Translation-en [2,246 B] 
Get:29 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-updates/universe i386 Packages [112 kB] 
Get:30 [http://security.ubuntu.com](http://security.ubuntu.com) vivid-security/restricted Translation-en [2,607 B] 
Get:31 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-updates/multiverse i386 Packages [5,383 B] 
Get:32 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-updates/main Translation-en [102 kB] 
Get:33 [http://security.ubuntu.com](http://security.ubuntu.com) vivid-security/universe Translation-en [35.3 kB] 
Get:34 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-updates/multiverse Translation-en [2,246 B] 
Get:35 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-updates/restricted Translation-en [2,969 B] 
Get:36 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-updates/universe Translation-en [65.3 kB] 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-backports/main Sources 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-backports/restricted Sources 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-backports/multiverse Sources 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-backports/main amd64 Packages 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-backports/restricted amd64 Packages 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-backports/multiverse amd64 Packages 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-backports/main i386 Packages 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-backports/restricted i386 Packages 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-backports/multiverse i386 Packages 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-backports/main Translation-en                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-backports/multiverse Translation-en              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-backports/restricted Translation-en              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid/main Sources                                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid/restricted Sources                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid/universe Sources                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid/multiverse Sources                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid/main amd64 Packages                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid/restricted amd64 Packages                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid/universe amd64 Packages                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid/multiverse amd64 Packages                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid/main i386 Packages                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid/restricted i386 Packages                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid/universe i386 Packages                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid/multiverse i386 Packages                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid/main Translation-en                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid/multiverse Translation-en                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid/restricted Translation-en                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid/universe Translation-en                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-backports/universe Sources                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-backports/universe amd64 Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-backports/universe i386 Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-backports/universe Translation-en                
Fetched 1,666 kB in 9s (177 kB/s)                                                       
Reading package lists... Done 
Reading package lists... Done 
Building dependency tree        
Reading state information... Done 
Calculating upgrade... Done 
The following packages will be upgraded: 
  linux-headers-3.19.0-30 linux-headers-3.19.0-30-generic 
  linux-image-3.19.0-30-generic linux-image-extra-3.19.0-30-generic 
4 upgraded, 0 newly installed, 0 to remove and 0 not upgraded. 
2 not fully installed or removed. 
Need to get 65.4 MB of archives. 
After this operation, 1,024 B of additional disk space will be used. 
Do you want to continue? [Y/n] y 
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) vivid-updates/main linux-image-3.19.0-30-gene
ric amd64 3.19.0-30.34 [16.9 MB] 
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) vivid-updates/main linux-headers-3.19.0-30 al
l 3.19.0-30.34 [9,339 kB] 
Get:3 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) vivid-updates/main linux-headers-3.19.0-30-ge
neric amd64 3.19.0-30.34 [760 kB] 
Get:4 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) vivid-updates/main linux-image-extra-3.19.0-3
0-generic amd64 3.19.0-30.34 [38.5 MB] 
Fetched 65.4 MB in 4min 23s (248 kB/s)                                                  
(Reading database ... 167204 files and directories currently installed.) 
Preparing to unpack .../linux-image-3.19.0-30-generic_3.19.0-30.34_amd64.deb ... 
Done. 
Unpacking linux-image-3.19.0-30-generic (3.19.0-30.34) over (3.19.0-30.33) ... 
Examining /etc/kernel/postrm.d . 
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.19.0-30-generic /boot/vmlinu
z-3.19.0-30-generic 
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.19.0-30-generic /boot/vmlinuz
-3.19.0-30-generic 
Preparing to unpack .../linux-headers-3.19.0-30_3.19.0-30.34_all.deb ... 
Unpacking linux-headers-3.19.0-30 (3.19.0-30.34) over (3.19.0-30.33) ... 
Preparing to unpack .../linux-headers-3.19.0-30-generic_3.19.0-30.34_amd64.deb ... 
Unpacking linux-headers-3.19.0-30-generic (3.19.0-30.34) over (3.19.0-30.33) ... 
Preparing to unpack .../linux-image-extra-3.19.0-30-generic_3.19.0-30.34_amd64.deb ... 
Unpacking linux-image-extra-3.19.0-30-generic (3.19.0-30.34) over (3.19.0-30.33) ... 
Setting up apport (2.17.2-0ubuntu1.5) ... 
Traceback (most recent call last): 
  File "/usr/bin/pycompile", line 39, in <module> 
    from debpython.option import Option, compile_regexpr 
  File "/usr/share/python/debpython/option.py", line 43, in <module> 
    class Option(optparse.Option): 
  File "/usr/share/python/debpython/option.py", line 45, in Option 
    TYPE_CHECKER = copy(optparse.Option.TYPE_CHECKER) 
AttributeError: class Option has no attribute 'TYPE_CHECKER' 
dpkg: error processing package apport (--configure): 
 subprocess installed post-installation script returned error exit status 1 
dpkg: dependency problems prevent configuration of apport-kde: 
 apport-kde depends on apport (>= 0.41); however: 
  Package apport is not configured yet. 

dpkg: error processing package apport-kde (--configure): 
 dependency problems - leaving unconfigured 
Setting up linux-image-3.19.0-30-generic (3.19.0-30.34) ... 
No apport report written because the error message indicates its a followup error from a
 previous failure. 
                  Running depmod. 
update-initramfs: deferring update (hook will be called later) 
Not updating initrd symbolic links since we are being updated/reinstalled  
(3.19.0-30.33 was configured last, according to dpkg) 
Not updating image symbolic links since we are being updated/reinstalled  
(3.19.0-30.33 was configured last, according to dpkg) 
Examining /etc/kernel/postinst.d. 
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.19.0-30-generic /boot/vml
inuz-3.19.0-30-generic 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.19.0-30-generic /boot/vmli
nuz-3.19.0-30-generic 
update-initramfs: Generating /boot/initrd.img-3.19.0-30-generic 
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.19.0-30-generic /boot/vmlinuz-3.1
9.0-30-generic 
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 3.19.0-30-generic /boot/
vmlinuz-3.19.0-30-generic 
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.19.0-30-generic /boot/vmli
nuz-3.19.0-30-generic 
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.19.0-30-generic /boot/vmlin
uz-3.19.0-30-generic 
Generating grub configuration file ... 
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no 
longer supported. 
Found linux image: /boot/vmlinuz-3.19.0-30-generic 
Found initrd image: /boot/initrd.img-3.19.0-30-generic 
Found linux image: /boot/vmlinuz-3.19.0-15-generic 
Found initrd image: /boot/initrd.img-3.19.0-15-generic 
Found memtest86+ image: /boot/memtest86+.elf 
Found memtest86+ image: /boot/memtest86+.bin 
done 
Setting up linux-headers-3.19.0-30 (3.19.0-30.34) ... 
Setting up linux-headers-3.19.0-30-generic (3.19.0-30.34) ... 
Setting up linux-image-extra-3.19.0-30-generic (3.19.0-30.34) ... 
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.19.0-30-generic /boot/vml
inuz-3.19.0-30-generic 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.19.0-30-generic /boot/vmli
nuz-3.19.0-30-generic 
update-initramfs: Generating /boot/initrd.img-3.19.0-30-generic 
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.19.0-30-generic /boot/vmlinuz-3.1
9.0-30-generic 
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 3.19.0-30-generic /boot/
vmlinuz-3.19.0-30-generic 
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.19.0-30-generic /boot/vmli
nuz-3.19.0-30-generic 
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.19.0-30-generic /boot/vmlin
uz-3.19.0-30-generic 
Generating grub configuration file ... 
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no 
longer supported. 
Found linux image: /boot/vmlinuz-3.19.0-30-generic 
Found initrd image: /boot/initrd.img-3.19.0-30-generic 
Found linux image: /boot/vmlinuz-3.19.0-15-generic 
Found initrd image: /boot/initrd.img-3.19.0-15-generic 
Found memtest86+ image: /boot/memtest86+.elf 
Found memtest86+ image: /boot/memtest86+.bin 
done 
Errors were encountered while processing: 
 apport 
 apport-kde 
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

[/FONT]

I also just tried installing synaptic/Muon package manager and it erred out!

---

### Post by Bashing-om on 2015-10-06
pinstripedtie2; Hello;

The package manager is advising problems in relation to "apport" .
As a 1st poke at the problem, what results:
```

sudo apt-get install --reinstall apport apport-kde

```
Keep in mind that apport is the crash reporting utility, and in a stable release crash reporting has no value and the utility should be disabled.
That control file is /etc/default/apport
and the field that says enabled=1  change it to enabled=0 to disable Apport crash reporting.
You do not want to remove the utility, as it serves many other purposes .

We see what results with the attempt to --reinstall, and take the matter up from there.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by pinstripedtie2 on 2015-10-06
Hi, here is the result:

       [FONT=monospace][COLOR=#000000]$ sudo apt-get install --reinstall apport apport-kde [/COLOR]
[sudo] password for ronny:  
Reading package lists... Done 
Building dependency tree        
Reading state information... Done 
0 upgraded, 0 newly installed, 2 reinstalled, 0 to remove and 0 not upgraded. 
2 not fully installed or removed. 
After this operation, 0 B of additional disk space will be used. 
E: Internal Error, No file name for apport:amd64


Ok... this is what I tried: gedit [/FONT][FONT=monospace]/etc/default/apport
which brought up the file and I changed it to 0 , but it said I do not have permission.
So, later... then I thought I'd try sudo gedit [/FONT]/etc/default/apport
and it did change it with a string of errors in the konsole. (forgot to copy them before closing)

But now I went to install Audacity from the Muon Discover prog. and it gave me a big red error prompt / pop-up.

Wow... now after starting Audacity, my desktop is going wacky! 
I click the taskbar tab to the program to minimize and it takes
three times to do so. Then it starts doing other really wacky things.

Maybe I should try re-installing. I hate to do this... but I have not 
had to much luck with many distros of late. Mint ran good for a
few months and started acting up... though not as bad as this 
distro is.

---

### Post by Bashing-om on 2015-10-06
pinstripedtie2; Strange that ;

Ok, let's take a gander and see what a status might be:
```

apt-cache policy apport
apt-cache policy apport-kde

```

Until such time as we can get update and upgrade to run clean, will not be able to install any other applications.

[INDENT][INDENT]what does it take
[INDENT][INDENT][INDENT]to get a package manager
[INDENT][INDENT][INDENT]satisfied
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by pinstripedtie2 on 2015-10-06
[FONT=monospace][COLOR=#000000]Here is the output of your code:

~$ apt-cache policy apport [/COLOR]
apport: 
  Installed: 2.17.2-0ubuntu1.5 
  Candidate: 2.17.2-0ubuntu1.5 
  Version table: 
 *** 2.17.2-0ubuntu1.5 0 
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) vivid-updates/main amd64 Packages 
        500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) vivid-security/main amd64 Packages 
        100 /var/lib/dpkg/status 
     2.17.2-0ubuntu1 0 
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) vivid/main amd64 Packages 
ronny@ronny-MS-7641:~$ apt-cache policy apport-kde 
apport-kde: 
  Installed: 2.17.2-0ubuntu1.5 
  Candidate: 2.17.2-0ubuntu1.5 
  Version table: 
 *** 2.17.2-0ubuntu1.5 0 
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) vivid-updates/universe amd64 Packages 
        500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) vivid-security/universe amd64 Packages 
        100 /var/lib/dpkg/status 
     2.17.2-0ubuntu1 0 
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) vivid/universe amd64 Packages

[/FONT]

---

### Post by Bashing-om on 2015-10-06
pinstripedtie2; Hummm ...

I do not understand all I do not know ..... Not adding up huh ?
we have on one hand the package manager complaining :
> 
E: Internal Error, No file name for apport:amd64

But the system says it is installed.

What does the package manager say about this matter ?
```

dpkg -l apport
dpkg -L apport
dpkg -l apport-kde

```

maybe what we have is a corrupted control file ?

[INDENT][INDENT]sometimes I do wonder
[/INDENT][/INDENT]

---

### Post by pinstripedtie2 on 2015-10-06
Here ya go!

       [FONT=monospace][COLOR=#000000]~$ dpkg -l apport [/COLOR]
Desired=Unknown/Install/Remove/Purge/Hold 
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend 
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad) 
||/ Name             Version       Architecture  Description 
+++-================-=============-=============-===================================== 
iF  apport           2.17.2-0ubunt all           automatically generate crash reports  
ronny@ronny-MS-7641:~$ dokg -L apport 
No command 'dokg' found, did you mean: 
 Command 'dpkg' from package 'dpkg' (main) 
 Command 'dog' from package 'sheepdog' (universe) 
dokg: command not found 
ronny@ronny-MS-7641:~$ dpkg -l apport-kde 
Desired=Unknown/Install/Remove/Purge/Hold 
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend 
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad) 
||/ Name             Version       Architecture  Description 
+++-================-=============-=============-===================================== 
iU  apport-kde       2.17.2-0ubunt all           KDE frontend for the apport crash rep

[/FONT]

---

### Post by Bashing-om on 2015-10-06
pinstripedtie2; Yeah ..

That helps;
Try:
```

sudo dpkg-reconfigure apport

```
If that completes ... same for apport-kde
```

sudo dpkg-reconfigure apport-kde

```

Maybe .. else I guess we can remove and re-install .

[INDENT][INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT][/INDENT]

---

### Post by pinstripedtie2 on 2015-10-06
I re-entered it before I thought you responded:

```
~$ dpkg -l apport 
Desired=Unknown/Install/Remove/Purge/Hold 
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend 
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad) 
||/ Name             Version       Architecture  Description 
+++-================-=============-=============-===================================== 
iF  apport           2.17.2-0ubunt all           automatically generate crash reports  
ronny@ronny-MS-7641:~$ dpkg -L apport 
/. 
/usr 
/usr/share 
/usr/share/apport 
/usr/share/apport/apport 
/usr/share/apport/gcc_ice_hook 
/usr/share/apport/package-hooks 
/usr/share/apport/package-hooks/source_linux.py 
/usr/share/apport/package-hooks/source_linux-nexus7.py 
/usr/share/apport/package-hooks/source_ubiquity.py 
/usr/share/apport/package-hooks/source_apport.py 
/usr/share/apport/package-hooks/source_debian-installer.py 
/usr/share/apport/unkillable_shutdown 
/usr/share/apport/dump_acpi_tables.py 
/usr/share/apport/general-hooks 
/usr/share/apport/general-hooks/generic.py 
/usr/share/apport/general-hooks/ubuntu-gnome.py 
/usr/share/apport/general-hooks/parse_segv.py 
/usr/share/apport/general-hooks/cloud_archive.py 
/usr/share/apport/general-hooks/clickinfo.py 
/usr/share/apport/general-hooks/powerpc.py 
/usr/share/apport/general-hooks/ubuntu.py 
/usr/share/apport/general-hooks/wayland_session.py 
/usr/share/apport/apportcheckresume 
/usr/share/apport/java_uncaught_exception 
/usr/share/apport/kernel_oops 
/usr/share/apport/package_hook 
/usr/share/apport/whoopsie-upload-all 
/usr/share/apport/recoverable_problem 
/usr/share/apport/apport.jar 
/usr/share/apport/kernel_crashdump 
/usr/share/apport/root_info_wrapper 
/usr/share/apport/testsuite 
/usr/share/apport/testsuite/crash.class 
/usr/share/apport/testsuite/crash.jar 
/usr/share/apport/is-enabled 
/usr/share/apport/iwlwifi_error_dump 
/usr/share/apport/apport-checkreports 
/usr/share/icons 
/usr/share/icons/hicolor 
/usr/share/icons/hicolor/scalable 
/usr/share/icons/hicolor/scalable/mimetypes 
/usr/share/icons/hicolor/scalable/apps 
/usr/share/icons/hicolor/scalable/apps/apport.svg 
/usr/share/icons/hicolor/48 
/usr/share/icons/hicolor/48/mimetypes 
/usr/share/icons/hicolor/48/apps 
/usr/share/icons/hicolor/48/apps/apport.png 
/usr/share/icons/hicolor/32 
/usr/share/icons/hicolor/32/mimetypes 
/usr/share/icons/hicolor/32/apps 
/usr/share/icons/hicolor/32/apps/apport.png 
/usr/share/icons/hicolor/64 
/usr/share/icons/hicolor/64/mimetypes 
/usr/share/icons/hicolor/64/apps 
/usr/share/icons/hicolor/64/apps/apport.png 
/usr/share/polkit-1 
/usr/share/polkit-1/actions 
/usr/share/polkit-1/actions/com.ubuntu.apport.policy 
/usr/share/python 
/usr/share/python/runtime.d 
/usr/share/python/runtime.d/apport.rtupdate 
/usr/share/mime 
/usr/share/mime/packages 
/usr/share/mime/packages/apport.xml 
/usr/share/doc 
/usr/share/doc/apport 
/usr/share/doc/apport/symptoms.txt 
/usr/share/doc/apport/README 
/usr/share/doc/apport/crashdb-conf.txt.gz 
/usr/share/doc/apport/copyright 
/usr/share/doc/apport/NEWS.gz 
/usr/share/doc/apport/package-hooks.txt.gz 
/usr/share/man 
/usr/share/man/man1 
/usr/share/man/man1/apport-unpack.1.gz 
/usr/share/man/man1/apport-cli.1.gz 
/usr/share/man/man1/apport-bug.1.gz 
/usr/bin 
/usr/bin/apport-unpack 
/usr/bin/apport-cli 
/usr/bin/apport-bug 
/usr/lib 
/usr/lib/pm-utils 
/usr/lib/pm-utils/sleep.d 
/usr/lib/pm-utils/sleep.d/000record-status 
/lib 
/lib/udev 
/lib/udev/rules.d 
/lib/udev/rules.d/50-apport.rules 
/etc 
/etc/apport 
/etc/apport/blacklist.d 
/etc/apport/blacklist.d/apport 
/etc/apport/blacklist.d/README.blacklist 
/etc/apport/crashdb.conf 
/etc/logrotate.d 
/etc/logrotate.d/apport 
/etc/init.d 
/etc/init.d/apport 
/etc/bash_completion.d 
/etc/bash_completion.d/apport_completion 
/etc/default 
/etc/default/apport 
/etc/init 
/etc/init/apport.conf 
/etc/cron.daily 
/etc/cron.daily/apport 
/usr/share/apport/package-hooks/source_linux-meta.py 
/usr/share/icons/hicolor/scalable/mimetypes/text-x-apport.svg 
/usr/share/icons/hicolor/48/mimetypes/text-x-apport.png 
/usr/share/icons/hicolor/32/mimetypes/text-x-apport.png 
/usr/share/icons/hicolor/64/mimetypes/text-x-apport.png 
/usr/share/doc/apport/changelog.Debian.gz 
/usr/share/man/man1/ubuntu-bug.1.gz 
/usr/share/man/man1/apport-collect.1.gz 
/usr/bin/ubuntu-bug 
/usr/bin/apport-collect 
ronny@ronny-MS-7641:~$ dpkg -l apport-kde 
Desired=Unknown/Install/Remove/Purge/Hold 
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend 
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad) 
||/ Name             Version       Architecture  Description 
+++-================-=============-=============-===================================== 
iU  apport-kde       2.17.2-0ubunt all           KDE frontend for the apport crash rep
```

Find the output to both lines of code below:

> **Bashing-om said:**
> pinstripedtie2; Yeah ..

That helps;
Try:
```

sudo dpkg-reconfigure apport

```

OUTPUT:  /usr/sbin/dpkg-reconfigure: apport is broken or not fully installed


If that completes ... same for apport-kde
```

sudo dpkg-reconfigure apport-kde

```

OUTPUT:  /usr/sbin/dpkg-reconfigure: apport-kde is broken or not fully installed


Maybe .. else I guess we can remove and re-install .
[INDENT][INDENT][INDENT]where there is a will there is a way
[/INDENT]
[/INDENT]
[/INDENT]


---

### Post by Bashing-om on 2015-10-06
pinstripedtie2; Well ..

With that many files I think it is a waste of time to hunt for the corrupted one(s).
Let's purge and reinstall !
```

sudo apt-get purge apport
sudo apt-get purge apport-kde
sudo apt-get install apport
sudo apt-get install apport-kde

```

[INDENT][INDENT]how now brown cow
[/INDENT][/INDENT]

---

### Post by pinstripedtie2 on 2015-10-06
```
~$ sudo apt-get purge apport 
[sudo] password for ronny:  
Reading package lists... Done 
Building dependency tree        
Reading state information... Done 
Package 'apport' is not installed, so not removed 
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded. 
3 not fully installed or removed. 
After this operation, 0 B of additional disk space will be used. 
Setting up python-xdg (0.25-4) ... 
Traceback (most recent call last): 
  File "/usr/bin/pycompile", line 39, in <module> 
    from debpython.option import Option, compile_regexpr 
  File "/usr/share/python/debpython/option.py", line 43, in <module> 
    class Option(optparse.Option): 
  File "/usr/share/python/debpython/option.py", line 45, in Option 
    TYPE_CHECKER = copy(optparse.Option.TYPE_CHECKER) 
AttributeError: class Option has no attribute 'TYPE_CHECKER' 
dpkg: error processing package python-xdg (--configure): 
 subprocess installed post-installation script returned error exit status 1 
dpkg: dependency problems prevent configuration of python-zeitgeist: 
 python-zeitgeist depends on python-xdg; however: 
  Package python-xdg is not configured yet. 

dpkg: error processing package python-zeitgeist (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of zeitgeist: 
 zeitgeist depends on python-zeitgeist; however: 
  Package python-zeitgeist is not configured yet. 

dpkg: error processing package zeitgeist (--configure): 
 dependency problems - leaving unconfigured 
Errors were encountered while processing: 
 python-xdg 
 python-zeitgeist 
 zeitgeist 
E: Sub-process /usr/bin/dpkg returned an error code (1) 
ronny@ronny-MS-7641:~$ sudo apt-get purge apport-kde 
Reading package lists... Done 
Building dependency tree        
Reading state information... Done 
Package 'apport-kde' is not installed, so not removed 
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded. 
3 not fully installed or removed. 
After this operation, 0 B of additional disk space will be used. 
Setting up python-xdg (0.25-4) ... 
Traceback (most recent call last): 
  File "/usr/bin/pycompile", line 39, in <module> 
    from debpython.option import Option, compile_regexpr 
  File "/usr/share/python/debpython/option.py", line 43, in <module> 
    class Option(optparse.Option): 
  File "/usr/share/python/debpython/option.py", line 45, in Option 
    TYPE_CHECKER = copy(optparse.Option.TYPE_CHECKER) 
AttributeError: class Option has no attribute 'TYPE_CHECKER' 
dpkg: error processing package python-xdg (--configure): 
 subprocess installed post-installation script returned error exit status 1 
dpkg: dependency problems prevent configuration of python-zeitgeist: 
 python-zeitgeist depends on python-xdg; however: 
  Package python-xdg is not configured yet. 

dpkg: error processing package python-zeitgeist (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of zeitgeist: 
 zeitgeist depends on python-zeitgeist; however: 
  Package python-zeitgeist is not configured yet. 

dpkg: error processing package zeitgeist (--configure): 
 dependency problems - leaving unconfigured 
Errors were encountered while processing: 
 python-xdg 
 python-zeitgeist 
 zeitgeist 
E: Sub-process /usr/bin/dpkg returned an error code (1) 
ronny@ronny-MS-7641:~$ sudo apt-get install apport 
Reading package lists... Done 
Building dependency tree        
Reading state information... Done 
Suggested packages: 
  apport-gtk apport-kde 
The following NEW packages will be installed: 
  apport 
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded. 
3 not fully installed or removed. 
Need to get 0 B/115 kB of archives. 
After this operation, 762 kB of additional disk space will be used. 
Selecting previously unselected package apport. 
(Reading database ... 182782 files and directories currently installed.) 
Preparing to unpack .../apport_2.17.2-0ubuntu1.5_all.deb ... 
Unpacking apport (2.17.2-0ubuntu1.5) ... 
Processing triggers for hicolor-icon-theme (0.14-0ubuntu1) ... 
Processing triggers for shared-mime-info (1.3-1) ... 
Unknown media type in type 'all/all' 
Unknown media type in type 'all/allfiles' 
Processing triggers for man-db (2.7.0.2-5) ... 
Processing triggers for systemd (219-7ubuntu6) ... 
Processing triggers for ureadahead (0.100.0-19) ... 
ureadahead will be reprofiled on next reboot 
Setting up python-xdg (0.25-4) ... 
Traceback (most recent call last): 
  File "/usr/bin/pycompile", line 39, in <module> 
    from debpython.option import Option, compile_regexpr 
  File "/usr/share/python/debpython/option.py", line 43, in <module> 
    class Option(optparse.Option): 
  File "/usr/share/python/debpython/option.py", line 45, in Option 
    TYPE_CHECKER = copy(optparse.Option.TYPE_CHECKER) 
AttributeError: class Option has no attribute 'TYPE_CHECKER' 
dpkg: error processing package python-xdg (--configure): 
 subprocess installed post-installation script returned error exit status 1 
dpkg: dependency problems prevent configuration of python-zeitgeist: 
 python-zeitgeist depends on python-xdg; however: 
  Package python-xdg is not configured yet. 

dpkg: error processing package python-zeitgeist (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of zeitgeist: 
 zeitgeist depends on python-zeitgeist; however: 
  Package python-zeitgeist is not configured yet. 

dpkg: error processing package zeitgeist (--configure): 
 dependency problems - leaving unconfigured 
Setting up apport (2.17.2-0ubuntu1.5) ... 
Traceback (most recent call last): 
  File "/usr/bin/pycompile", line 39, in <module> 
    from debpython.option import Option, compile_regexpr 
  File "/usr/share/python/debpython/option.py", line 43, in <module> 
    class Option(optparse.Option): 
  File "/usr/share/python/debpython/option.py", line 45, in Option 
    TYPE_CHECKER = copy(optparse.Option.TYPE_CHECKER) 
AttributeError: class Option has no attribute 'TYPE_CHECKER' 
dpkg: error processing package apport (--configure): 
 subprocess installed post-installation script returned error exit status 1 
Processing triggers for systemd (219-7ubuntu6) ... 
Processing triggers for ureadahead (0.100.0-19) ... 
Errors were encountered while processing: 
 python-xdg 
 python-zeitgeist 
 zeitgeist 
 apport 
E: Sub-process /usr/bin/dpkg returned an error code (1) 
ronny@ronny-MS-7641:~$ sudo apt-get install apport-kde 
Reading package lists... Done 
Building dependency tree        
Reading state information... Done 
The following NEW packages will be installed: 
  apport-kde 
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded. 
4 not fully installed or removed. 
Need to get 0 B/17.8 kB of archives. 
After this operation, 214 kB of additional disk space will be used. 
Selecting previously unselected package apport-kde. 
(Reading database ... 182865 files and directories currently installed.) 
Preparing to unpack .../apport-kde_2.17.2-0ubuntu1.5_all.deb ... 
Unpacking apport-kde (2.17.2-0ubuntu1.5) ... 
Processing triggers for desktop-file-utils (0.22-1ubuntu3) ... 
Processing triggers for mime-support (3.58ubuntu1) ... 
Setting up apport (2.17.2-0ubuntu1.5) ... 
Traceback (most recent call last): 
  File "/usr/bin/pycompile", line 39, in <module> 
    from debpython.option import Option, compile_regexpr 
  File "/usr/share/python/debpython/option.py", line 43, in <module> 
    class Option(optparse.Option): 
  File "/usr/share/python/debpython/option.py", line 45, in Option 
    TYPE_CHECKER = copy(optparse.Option.TYPE_CHECKER) 
AttributeError: class Option has no attribute 'TYPE_CHECKER' 
dpkg: error processing package apport (--configure): 
 subprocess installed post-installation script returned error exit status 1 
Setting up python-xdg (0.25-4) ... 
Traceback (most recent call last): 
  File "/usr/bin/pycompile", line 39, in <module> 
    from debpython.option import Option, compile_regexpr 
  File "/usr/share/python/debpython/option.py", line 43, in <module> 
    class Option(optparse.Option): 
  File "/usr/share/python/debpython/option.py", line 45, in Option 
    TYPE_CHECKER = copy(optparse.Option.TYPE_CHECKER) 
AttributeError: class Option has no attribute 'TYPE_CHECKER' 
dpkg: error processing package python-xdg (--configure): 
 subprocess installed post-installation script returned error exit status 1 
dpkg: dependency problems prevent configuration of python-zeitgeist: 
 python-zeitgeist depends on python-xdg; however:No apport report written because the er
ror message indicates its a followup error from a previous failure. 

  Package python-xdg is not configured yet. 

dpkg: error processing package python-zeitgeist (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of zeitgeist: 
 zeitgeist depends on python-zeitgeist; however: 
  Package python-zeitgeist is not configured yet. 

dpkg: error processing package zeitgeist (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of apport-kde: 
 apport-kde depends on apport (>= 0.41); however: 
  Package apport is not configured yet. 

dpkg: error processing package apport-kde (--configure): 
 dependency problems - leaving unconfigured 
No apport report written because MaxReports is reached already 
                                                              No apport report written b
ecause MaxReports is reached already 
                                    Errors were encountered while processing: 
 apport 
 python-xdg 
 python-zeitgeist 
 zeitgeist 
 apport-kde 
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

By the way, I used UNetbootin to install this OS. Maybe I should try re-installing burning to a disk?

---

### Post by Bashing-om on 2015-10-06
pinstripedtie2; Welp ...

Looks like we just keep getting deeper. But I do not think of this as a bad install .
However; As much as I might like to solve this ,, a fresh install will be a quicker solution.

I am done in for this session .. we can pick this back up in my morn . Perhaps others can chime in with their guidance.

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by pinstripedtie2 on 2015-10-06
Thank You for all your effort! I do appreciate you giving it your best. I will go ahead and re-download a fresh copy and burn it to disk tonight.

---

### Post by Bashing-om on 2015-10-07
pinstripedtie2; Hey !

Not at all or even close to my best .. We can put that .iso in our back pocket, and continue to trouble shoot this install .. And fix it.
It will take time and effort to make the package manager happy . If you have the time, I am more than willing. It is a puzzle, and doing these puzzles sure beats doing jig-saw puzzles !

We are presently prosecuting:
> 
Package python-xdg is not configured yet.


We poke at that one, and see where it leads:
```

sudo dpkg-reconfigure python-xdg

```

The good news is that we do not see the package manager complaining about apport. (keep in mind we may/likely have to disable crash reporting once more) .

[INDENT][INDENT]it is what it is
[INDENT][INDENT][INDENT]and the package manager does not lie
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by pinstripedtie2 on 2015-10-07
Sorry to steal the fun out of it... but I actually did what I said I was going to do and re-downloaded and installed it.
It's now working fine. But when I went to re-install the first time, I got several messages saying something about 
failed, failed, error, error... etc.

So I stopped it and restarted again and everything went fine from there. Weird! :confused:

---

### Post by Bashing-om on 2015-10-07
pinstripedtie2; Well ...


Any solution is better than no solution. The important thing is that you are up and no worse (maybe) for the wear .
I would be concerned:
> 
But when I went to re-install the first time, I got several messages saying something about 
failed, failed, error, error... etc.

So I stopped it and restarted again and everything went fine from there. Weird! 

enough to run a SMART test on the hard drive(s).

[INDENT][INDENT]just as an ounce of prevention
[/INDENT][/INDENT]

---

### Post by pinstripedtie2 on 2015-10-07
Oh yah... that could be an issue. But I updated the SSD firmware not too long ago.

---


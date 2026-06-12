---
title: "Cannot install VMWare player"
date: 2007-04-22
forum: Installation &amp; Upgrades
---

### Post by Physicist on 2007-04-22
Ubuntu 7.04.

I tried to install VM Player using Synaptic Package Manager, but get the following error.
It seems to not configured correctly. I am new to VMWare stuff. 

```

Preconfiguring packages ...
Selecting previously deselected package vmware-player-kernel-modules-2.6.20-15.
(Reading database ... 127813 files and directories currently installed.)
Unpacking vmware-player-kernel-modules-2.6.20-15 (from .../vmware-player-kernel-modules-2.6.20-15_2.6.20.5-15.20_i386.deb) ...
Selecting previously deselected package vmware-player-kernel-modules.
Unpacking vmware-player-kernel-modules (from .../vmware-player-kernel-modules_2.6.20.15.14_i386.deb) ...
Selecting previously deselected package vmware-player.
Unpacking vmware-player (from .../vmware-player_1.0.2-2_i386.deb) ...
vmware-player-v1-0-2 license has already been accepted
Selecting previously deselected package vmware-tools-kernel-modules-2.6.20-15.
Unpacking vmware-tools-kernel-modules-2.6.20-15 (from .../vmware-tools-kernel-modules-2.6.20-15_2.6.20.5-15.20_i386.deb) ...
Selecting previously deselected package vmware-tools-kernel-modules.
Unpacking vmware-tools-kernel-modules (from .../vmware-tools-kernel-modules_2.6.20.15.14_i386.deb) ...
Selecting previously deselected package xserver-xorg-video-vmware.
Unpacking xserver-xorg-video-vmware (from .../xserver-xorg-video-vmware_1%3a10.15.0-0ubuntu1_i386.deb) ...
Setting up vmware-player-kernel-modules-2.6.20-15 (2.6.20.5-15.20) ...

Setting up vmware-player-kernel-modules (2.6.20.15.14) ...
Setting up vmware-player (1.0.2-2) ...
Now configuring VMware Player.  (This may take some time...) 
Configuring a bridged network for vmnet0.

Configuring a NAT network for vmnet8.

Probing for an unused private subnet (this can take some time)...

The subnet 172.16.203.0/255.255.255.0 appears to be unused.

Configuring a host-only network for vmnet1.

Probing for an unused private subnet (this can take some time)...

The subnet 172.16.54.0/255.255.255.0 appears to be unused.

Starting VMware services:
   Virtual machine monitor                                             done
   Virtual ethernet                                                    done
VMware Player is installed, but it has not been (correctly) configured
for the running kernel. To (re-)configure it, invoke the
following command: /usr/bin/vmware-config.pl.

invoke-rc.d: initscript vmware-player, action "start" failed.
dpkg: error processing vmware-player (--configure):
 subprocess post-installation script returned error exit status 1
Setting up vmware-tools-kernel-modules-2.6.20-15 (2.6.20.5-15.20) ...

Setting up vmware-tools-kernel-modules (2.6.20.15.14) ...
Setting up xserver-xorg-video-vmware (10.15.0-0ubuntu1) ...
Errors were encountered while processing:
 vmware-player
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up vmware-player (1.0.2-2) ...
Now configuring VMware Player.  (This may take some time...) 
Configuring a bridged network for vmnet0.

Configuring a NAT network for vmnet8.

Probing for an unused private subnet (this can take some time)...

The subnet 192.168.128.0/255.255.255.0 appears to be unused.

The file /etc/vmware/vmnet8/dhcpd/dhcpd.conf that this program was about to 
install already exists.  Overwrite? [yes] 

The file /etc/vmware/vmnet8/dhcpd/dhcpd.leases that this program was about to 
install already exists.  Overwrite? [yes] 

The file /etc/vmware/vmnet8/dhcpd/dhcpd.leases~ that this program was about to 
install already exists.  Overwrite? [yes] 

The file /etc/vmware/vmnet8/nat/nat.conf that this program was about to install 
already exists.  Overwrite? [yes] 

Configuring a host-only network for vmnet1.

Probing for an unused private subnet (this can take some time)...

The subnet 172.16.3.0/255.255.255.0 appears to be unused.

The file /etc/vmware/vmnet1/dhcpd/dhcpd.conf that this program was about to 
install already exists.  Overwrite? [yes] 

The file /etc/vmware/vmnet1/dhcpd/dhcpd.leases that this program was about to 
install already exists.  Overwrite? [yes] 

The file /etc/vmware/vmnet1/dhcpd/dhcpd.leases~ that this program was about to 
install already exists.  Overwrite? [yes] 

Starting VMware services:
   Virtual machine monitor                                             done
   Virtual ethernet                                                    done
VMware Player is installed, but it has not been (correctly) configured
for the running kernel. To (re-)configure it, invoke the
following command: /usr/bin/vmware-config.pl.

invoke-rc.d: initscript vmware-player, action "start" failed.
dpkg: error processing vmware-player (--configure):
 subprocess post-installation script returned error exit status 1

```

Then when I try to run vmware-config.pl

it give me the following 

```

user@host:~$ sudo /usr/bin/vmware-config.pl
Password:
Making sure services for VMware Server are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done
   Bridged networking on /dev/vmnet0                                   done
   DHCP server on /dev/vmnet1                                          done
   Host-only networking on /dev/vmnet1                                 done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done
   Host-only networking on /dev/vmnet8                                 done
   Virtual ethernet                                                    done

You must read and accept the End User License Agreement to continue.
Press enter to display it. 

/usr/share/doc/vmware-player/EULA: No such file or directory

Do you accept? (yes/no) yes

Thank you.

Configuring fallback GTK+ 2.4 libraries.

The file /usr/share/mime/packages/vmware.xml that this program was about to 
install already exists.  Overwrite? [yes] yes

In which directory do you want to install the mime type icons? 
[/usr/share/icons] 

What directory contains your desktop menu entry files? These files have a 
.desktop file extension. [/usr/share/applications] 

In which directory do you want to install the application's icon? 
[/usr/share/pixmaps] 

The file /usr/share/pixmaps/vmware-server.png that this program was about to 
install already exists.  Overwrite? [yes] 

/usr/share/applications/vmware-server.desktop: warning: The 'Application' category is not defined by the desktop entry specification.  Please use one of "AudioVideo", "Audio", "Video", "Development", "Education", "Game", "Graphics", "Network", "Office", "Settings", "System", "Utility" instead
/usr/share/applications/vmware-console-uri-handler.desktop: warning: The 'Application' category is not defined by the desktop entry specification.  Please use one of "AudioVideo", "Audio", "Video", "Development", "Education", "Game", "Graphics", "Network", "Office", "Settings", "System", "Utility" instead
Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] yes

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.20-15-generic/build/include] 

Extracting the sources of the vmmon module.

tar: /usr/lib/vmware-player/modules/source/vmmon.tar: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
Unable to untar the "/usr/lib/vmware-player/modules/source/vmmon.tar" file in 
the "/tmp/vmware-config2" directory.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

usrname@host:~$ 

```

I did not find tutorial at
```

http://www.howtoforge.com/ubuntu_vmware_server

```
helps with my problem.

---

### Post by pmdkh on 2007-04-22
I am having a similar problem using 6.10.  When I go to install VMWare Player, I get some errors.  However, VMWare Player still shows up under Applications --> System Tools.  Does anyone know if I need to do something more?

```
Setting up vmware-player (1.0.2-2) ...
Now configuring VMware Player.  (This may take some time...) 
Configuring a bridged network for vmnet0.

Configuring a NAT network for vmnet8.

Probing for an unused private subnet (this can take some time)...



The subnet 192.168.113.0/255.255.255.0 appears to be unused.

The file /etc/vmware/vmnet8/dhcpd/dhcpd.conf that this program was about to 
install already exists.  Overwrite? [yes] 

The file /etc/vmware/vmnet8/dhcpd/dhcpd.leases that this program was about to 
install already exists.  Overwrite? [yes] 

The file /etc/vmware/vmnet8/dhcpd/dhcpd.leases~ that this program was about to 
install already exists.  Overwrite? [yes] 

The file /etc/vmware/vmnet8/nat/nat.conf that this program was about to install 
already exists.  Overwrite? [yes] 

Configuring a host-only network for vmnet1.

Probing for an unused private subnet (this can take some time)...


The subnet 192.168.54.0/255.255.255.0 appears to be unused.

The file /etc/vmware/vmnet1/dhcpd/dhcpd.conf that this program was about to 
install already exists.  Overwrite? [yes] 

The file /etc/vmware/vmnet1/dhcpd/dhcpd.leases that this program was about to 
install already exists.  Overwrite? [yes] 

The file /etc/vmware/vmnet1/dhcpd/dhcpd.leases~ that this program was about to 
install already exists.  Overwrite? [yes] 

Starting VMware services:
   Virtual machine monitor                                            failed
   Virtual ethernet                                                   failed
Module vmnet is not loaded.  Please verify that it is loaded before
running this script.

invoke-rc.d: initscript vmware-player, action "start" failed.
dpkg: error processing vmware-player (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 vmware-player
```

---

### Post by enchanter on 2007-04-23
Hi there all,

I am having a similar problem.
I tried installing the vmware-player package for 7.04 but it gave the same problem as the first poster.  I have since tried installing the latest version from the vmware website 1.0.3 but am getting a compilation error.  :confused: 

--- output -------------------------------------------------------------------------------------------

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config4/vmmon-only'
make -C /lib/modules/2.6.20-15-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /tmp/vmware-config4/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config4/vmmon-only/linux/driver.c:80:
/tmp/vmware-config4/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or ‘...’ before ‘compat_exit’
/tmp/vmware-config4/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or ‘...’ before ‘exit_code’
/tmp/vmware-config4/vmmon-only/./include/compat_kernel.h:21: warning: type defaults to ‘int’ in declaration of ‘_syscall1’
make[2]: *** [/tmp/vmware-config4/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config4/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config4/vmmon-only'
Unable to build the vmmon module.
 
--- end output --------------------------------------------------------------------------

anyone seen this error?  does anyone have a workaround?

Best Regards
Enchanter.

---

### Post by pmdkh on 2007-04-23
Bump.

---

### Post by rgcrowley on 2007-04-24
I am getting the exact same error.  I've tried on several machine and get the same thing on each.  This has crippled me since I have to use some windows programs at work.  I had to revert back to using a windows machine until Feisty works with vmware.



> **enchanter said:**
> Hi there all,

I am having a similar problem.
I tried installing the vmware-player package for 7.04 but it gave the same problem as the first poster.  I have since tried installing the latest version from the vmware website 1.0.3 but am getting a compilation error.  :confused: 

--- output -------------------------------------------------------------------------------------------

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config4/vmmon-only'
make -C /lib/modules/2.6.20-15-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /tmp/vmware-config4/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config4/vmmon-only/linux/driver.c:80:
/tmp/vmware-config4/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or ‘...’ before ‘compat_exit’
/tmp/vmware-config4/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or ‘...’ before ‘exit_code’
/tmp/vmware-config4/vmmon-only/./include/compat_kernel.h:21: warning: type defaults to ‘int’ in declaration of ‘_syscall1’
make[2]: *** [/tmp/vmware-config4/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config4/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config4/vmmon-only'
Unable to build the vmmon module.
 
--- end output --------------------------------------------------------------------------

anyone seen this error?  does anyone have a workaround?

Best Regards
Enchanter.

---

### Post by koshari on 2007-04-26
vm ware died on me also after upgrading to feisty, 

after running vmware-config.lp

i get

```
Making sure services for VMware Server are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done
   Bridged networking on /dev/vmnet0                                   done
   DHCP server on /dev/vmnet1                                          done
   Host-only networking on /dev/vmnet1                                 done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done
   Host-only networking on /dev/vmnet8                                 done
   Virtual ethernet                                                    done

((((     stuff here taken out to save space.....))))))))

In file included from /tmp/vmware-config1/vmmon-only/linux/driver.c:80:
/tmp/vmware-config1/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;compat_exit&#8217;
/tmp/vmware-config1/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;exit_code&#8217;
/tmp/vmware-config1/vmmon-only/./include/compat_kernel.h:21: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;_syscall1&#8217;
make[2]: *** [/tmp/vmware-config1/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config1/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config1/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.


```

after a wild goose chase of modding the source files and re tarring, which still didnt work in my case i simply downloaded some pre patched tars here, 

[http://icanthack.com/?p=53](http://icanthack.com/?p=53)

and replaced mine with these and presto, the script worked.

now i vmware server back :-)

---

### Post by enchanter on 2007-04-27
I managed to get vmware player working by extracting the tar file editing the source file and re-tarring the files.  It is a workaround, but a real pain.

It is interesting that the packaged install for vmware player does not work.  I downloaded the latest version (1.0.3) from vmware's website and compiled that.  One other thing that I did, I removed all trace of vmware player form my machine to get a clean install.


link to thread describing the kludge to the source file.
[http://ubuntuforums.org/showthread.php?t=338305](http://ubuntuforums.org/showthread.php?t=338305)

link to 1.0.3 download for vmware player
[http://download3.vmware.com/software/vmplayer/VMware-player-1.0.3-34682.tar.gz](http://download3.vmware.com/software/vmplayer/VMware-player-1.0.3-34682.tar.gz)

Although I have just noticed that there is a new version out.  1.0.4, I will investigate that at some point.

best of luck,
Enchanter.

---

### Post by Tine on 2007-04-27
Have you tried any-to-any upgrade?

[http://www.vmware.com/community/thread.jspa?messageID=76957&tstart=0](http://www.vmware.com/community/thread.jspa?messageID=76957&tstart=0)

---

### Post by wpainter on 2007-04-27
I have a question that goes like this I run  "sudo vmware-config.pl" and get the following output I have tried a lot of what I read here, help appriciated from anyone that understands this better than  I! Thanks  Please let me know if this should be posted in another area!

PS the Perl directories are ther e I checked them



wpainter@wpainter-desktop:/tmp/vmware-config7/control-only$ cat /tmp/vmware-config9/control-only/make.log|more
Checking if your kit is complete...
Looks good
Writing Makefile for VMware::VmPerl
make: Entering directory `/tmp/vmware-config9/control-only'
cp VmPerl/VM.pm blib/lib/VMware/VmPerl/VM.pm
cp Control.pm blib/lib/VMware/Control.pm
AutoSplitting blib/lib/VMware/Control.pm (blib/lib/auto/VMware/Control)
cp Profiler.pm blib/lib/VMware/Control/Profiler.pm
AutoSplitting blib/lib/VMware/Control/Profiler.pm (blib/lib/auto/VMware/Control/Profiler)
cp VmPerl/ConnectParams.pm blib/lib/VMware/VmPerl/ConnectParams.pm
cp Server.pm blib/lib/VMware/Control/Server.pm
cp Keycode.pm blib/lib/VMware/Control/Keycode.pm
cp VMScript.pm blib/lib/VMware/Control/VMScript.pm
cp VmPerl/VmPerl.pm blib/lib/VMware/VmPerl.pm
AutoSplitting blib/lib/VMware/VmPerl.pm (blib/lib/auto/VMware/VmPerl)
cp VmPerl/Server.pm blib/lib/VMware/VmPerl/Server.pm
cp VM.pm blib/lib/VMware/Control/VM.pm
cp VmPerl/Question.pm blib/lib/VMware/VmPerl/Question.pm
In file included from VmPerl.xs:6:
/usr/lib/perl/5.8/CORE/perl.h:420:24: error: sys/types.h: No such file or directory
/usr/lib/perl/5.8/CORE/perl.h:451:19: error: ctype.h: No such file or directory
/usr/lib/perl/5.8/CORE/perl.h:463:23: error: locale.h: No such file or directory
/usr/lib/perl/5.8/CORE/perl.h:480:20: error: setjmp.h: No such file or directory
/usr/lib/perl/5.8/CORE/perl.h:486:26: error: sys/param.h: No such file or directory
/usr/lib/perl/5.8/CORE/perl.h:491:23: error: stdlib.h: No such file or directory
/usr/lib/perl/5.8/CORE/perl.h:496:23: error: unistd.h: No such file or directory
/usr/lib/perl/5.8/CORE/perl.h:776:23: error: string.h: No such file or directory
/usr/lib/perl/5.8/CORE/perl.h:925:27: error: netinet/in.h: No such file or directory
/usr/lib/perl/5.8/CORE/perl.h:929:26: error: arpa/inet.h: No such file or directory
/usr/lib/perl/5.8/CORE/perl.h:939:25: error: sys/stat.h: No such file or directory
/usr/lib/perl/5.8/CORE/perl.h:961:21: error: time.h: No such file or directory
/usr/lib/perl/5.8/CORE/perl.h:968:25: error: sys/time.h: No such file or directory
/usr/lib/perl/5.8/CORE/perl.h:975:27: error: sys/times.h: No such file or directory
/usr/lib/perl/5.8/CORE/perl.h:982:19: error: errno.h: No such file or directory
/usr/lib/perl/5.8/CORE/perl.h:997:25: error: sys/socket.h: No such file or directory
/usr/lib/perl/5.8/CORE/perl.h:1024:21: error: netdb.h: No such file or directory
/usr/lib/perl/5.8/CORE/perl.h:1127:24: error: sys/ioctl.h: No such file or directory
/usr/lib/perl/5.8/CORE/perl.h:1156:23: error: dirent.h: No such file or directory
In file included from /usr/lib/gcc/x86_64-linux-gnu/4.1.2/include/syslimits.h:7,
                 from /usr/lib/gcc/x86_64-linux-gnu/4.1.2/include/limits.h:11,
                 from /usr/lib/perl/5.8/CORE/perl.h:1510,
                 from VmPerl.xs:6:
/usr/lib/gcc/x86_64-linux-gnu/4.1.2/include/limits.h:122:61: error: limits.h: No such file or directory
In file included from /usr/lib/perl/5.8/CORE/perl.h:2120,
                 from VmPerl.xs:6:
/usr/lib/perl/5.8/CORE/handy.h:136:25: error: inttypes.h: No such file or directory
In file included from /usr/lib/perl/5.8/CORE/perl.h:2284,
                 from VmPerl.xs:6:
/usr/lib/perl/5.8/CORE/unixish.h:106:21: error: signal.h: No such file or directory
In file included from VmPerl.xs:6:
/usr/lib/perl/5.8/CORE/perl.h:2421:33: error: pthread.h: No such file or directory
In file included from VmPerl.xs:6:
/usr/lib/perl/5.8/CORE/perl.h:2423: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;perl_os_thread&#8217;
/usr/lib/perl/5.8/CORE/perl.h:2424: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;perl_mutex&#8217;
/usr/lib/perl/5.8/CORE/perl.h:2425: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;perl_cond&#8217;
/usr/lib/perl/5.8/CORE/perl.h:2426: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;perl_key&#8217;
In file included from /usr/lib/perl/5.8/CORE/iperlsys.h:51,
                 from /usr/lib/perl/5.8/CORE/perl.h:2733,
                 from VmPerl.xs:6:
/usr/lib/perl/5.8/CORE/perlio.h:65:19: error: stdio.h: No such file or directory
In file included from /usr/lib/perl/5.8/CORE/iperlsys.h:51,
                 from /usr/lib/perl/5.8/CORE/perl.h:2733,
                 from VmPerl.xs:6:
/usr/lib/perl/5.8/CORE/perlio.h:259: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
/usr/lib/perl/5.8/CORE/perlio.h:262: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
/usr/lib/perl/5.8/CORE/perlio.h:265: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
/usr/lib/perl/5.8/CORE/perlio.h:268: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;FILE&#8217;
In file included from /usr/lib/perl/5.8/CORE/perl.h:2747,
                 from VmPerl.xs:6:
/usr/lib/perl/5.8/CORE/sv.h:389: error: expected specifier-qualifier-list before &#8216;DIR&#8217;
In file included from /usr/lib/perl/5.8/CORE/op.h:497,
                 from /usr/lib/perl/5.8/CORE/perl.h:2754,
                 from VmPerl.xs:6:
/usr/lib/perl/5.8/CORE/reentr.h:72:20: error: pwd.h: No such file or directory
/usr/lib/perl/5.8/CORE/reentr.h:75:20: error: grp.h: No such file or directory
/usr/lib/perl/5.8/CORE/reentr.h:85:26: error: crypt.h: No such file or directory
/usr/lib/perl/5.8/CORE/reentr.h:90:27: error: shadow.h: No such file or directory
In file included from /usr/lib/perl/5.8/CORE/op.h:497,
                 from /usr/lib/perl/5.8/CORE/perl.h:2754,
                 from VmPerl.xs:6:
/usr/lib/perl/5.8/CORE/reentr.h:612: error: field &#8216;_crypt_struct&#8217; has incomplete type
/usr/lib/perl/5.8/CORE/reentr.h:620: error: field &#8216;_drand48_struct&#8217; has incomplete type
/usr/lib/perl/5.8/CORE/reentr.h:624: error: field &#8216;_grent_struct&#8217; has incomplete type
/usr/lib/perl/5.8/CORE/reentr.h:635: error: field &#8216;_hostent_struct&#8217; has incomplete type
/usr/lib/perl/5.8/CORE/reentr.h:654: error: field &#8216;_netent_struct&#8217; has incomplete type
/usr/lib/perl/5.8/CORE/reentr.h:669: error: field &#8216;_protoent_struct&#8217; has incomplete type
/usr/lib/perl/5.8/CORE/reentr.h:684: error: field &#8216;_pwent_struct&#8217; has incomplete type
/usr/lib/perl/5.8/CORE/reentr.h:695: error: field &#8216;_servent_struct&#8217; has incomplete type
/usr/lib/perl/5.8/CORE/reentr.h:710: error: field &#8216;_spent_struct&#8217; has incomplete type
/usr/lib/perl/5.8/CORE/reentr.h:721: error: field &#8216;_gmtime_struct&#8217; has incomplete type
/usr/lib/perl/5.8/CORE/reentr.h:724: error: field &#8216;_localtime_struct&#8217; has incomplete type
/usr/lib/perl/5.8/CORE/reentr.h:771: error: field &#8216;_random_struct&#8217; has incomplete type
/usr/lib/perl/5.8/CORE/reentr.h:772: error: expected specifier-qualifier-list before &#8216;int32_t&#8217;
In file included from /usr/lib/perl/5.8/CORE/perl.h:2756,
                 from VmPerl.xs:6:
/usr/lib/perl/5.8/CORE/av.h:13: error: expected specifier-qualifier-list before &#8216;ssize_t&#8217;
In file included from /usr/lib/perl/5.8/CORE/perl.h:2759,
                 from VmPerl.xs:6:
/usr/lib/perl/5.8/CORE/scope.h:232: error: expected specifier-qualifier-list before &#8216;sigjmp_buf&#8217;
In file included from VmPerl.xs:6:
/usr/lib/perl/5.8/CORE/perl.h:2931: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;getuid&#8217;
/usr/lib/perl/5.8/CORE/perl.h:2932: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;geteuid&#8217;
/usr/lib/perl/5.8/CORE/perl.h:2933: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;getgid&#8217;
/usr/lib/perl/5.8/CORE/perl.h:2934: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;getegid&#8217;
In file included from VmPerl.xs:6:
/usr/lib/perl/5.8/CORE/perl.h:3238:22: error: math.h: No such file or directory
In file included from /usr/lib/perl/5.8/CORE/perl.h:3881,
                 from VmPerl.xs:6:
/usr/lib/perl/5.8/CORE/thrdvar.h:85: error: field &#8216;Tstatbuf&#8217; has incomplete type
/usr/lib/perl/5.8/CORE/thrdvar.h:86: error: field &#8216;Tstatcache&#8217; has incomplete type
/usr/lib/perl/5.8/CORE/thrdvar.h:91: error: field &#8216;Ttimesbuf&#8217; has incomplete type
In file included from /usr/lib/perl/5.8/CORE/perl.h:3883,
                 from VmPerl.xs:6:
/usr/lib/perl/5.8/CORE/intrpvar.h:66: error: expected specifier-qualifier-list before &#8216;time_t&#8217;
In file included from /usr/lib/perl/5.8/CORE/perl.h:3950,

---

### Post by Physicist on 2007-04-28
NOW problem solved. I followed this tutorial:
  [http://icanthack.com/?p=53](http://icanthack.com/?p=53)
 and have vmware-server successfully running. BUt the problem is there is now sound in my win xp virtual machine. Anyone know what is wrong? I am a total newbie to vmware.

---

### Post by Moodel on 2007-05-02
For those that may still have a problem running VMWare player with the newer 2.6.x Kernel there is a Beta version available for download [here.]("http://www.vmware.com/beta/player/download.html")

---

### Post by eponymous on 2007-05-03
koshari's link worked for me, it's in this thread up a few posts.

---

### Post by jhansonxi on 2007-05-04
Player v1.0.4 works on i386 Feisty with the basic compat_kernel.h fix as outlined in [**this post**](http://ubuntuforums.org/showpost.php?p=2127036).  I was having a problem with 1.0.2 and a Lexmark X3350 in Win98SE and XP that would function only on the initial install but fail to be found in subsequent reboots of the guest OS.  This problem was eliminated with v1.0.3 and 1.0.4 but they're not in the repos.

---


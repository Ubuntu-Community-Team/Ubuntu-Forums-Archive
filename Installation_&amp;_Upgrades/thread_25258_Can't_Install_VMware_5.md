---
title: "Can't Install VMware 5"
date: 2005-04-09
forum: Installation &amp; Upgrades
---

### Post by nickx on 2005-04-09
Guys, 

I did a very large check on the forum and tried several solutions but nothing worked yet I just can't get VMware to install. 

It stops at: 

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

I tried to give other directorys and installed and downloaded linux-headers-2.6.10-5 and linux-headers-2.6.10-5 but no go, I point to that dir but still no go :) Please help me !! thnx




```

In which directory do you want to install the application's icon?
[/usr/share/pixmaps]

Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Workstation is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for
your system (you need to have a C compiler installed on your system)? [yes] y

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] /usr/include/linux/

The header files in /usr/include are generally for C libraries, not for the
running kernel. If you do not have kernel header files in your /usr/src
directory, you probably do not have the kernel-source package installed. Are yousure that /usr/include contains the header files associated with your running
kernel? [no]

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] /usr/include/

The header files in /usr/include are generally for C libraries, not for the
running kernel. If you do not have kernel header files in your /usr/src
directory, you probably do not have the kernel-source package installed. Are yousure that /usr/include contains the header files associated with your running
kernel? [no] yes

The directory of kernel headers (version 2.6.0-test7) does not match your
running kernel (version 2.6.10-5-686).  Even if the module were to compile
successfully, it would not load into the running kernel.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

The path "/usr/src/linux/include" is not an existing directory.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

```

---

### Post by nickx on 2005-04-09
I fixed the problem via this way:



You need to install the headers for the release of the kernel you have installed. To find this out you can type

>> uname -r

to get the header you can apt-get install them,

>> sudo apt-get install linux-headers-`uname -r`

or select the appropriate package in synaptic.

Note: you'll also need gcc etc which if you don't have already you can get with

>> sudo apt-get install build-essential

After installation the vmware installer should just pick up the right place and not require anything but the defaults.

If it's still being stupid, the path to include can be found in /lib/modules/<<module release number>>/build/include

Cheers.


thank you anyway...

---

### Post by ramai on 2005-06-16
[QUOTE=nickx]I fixed the problem via this way:



You need to install the headers for the release of the kernel you have installed. To find this out you can type

>> uname -r

to get the header you can apt-get install them,

>> sudo apt-get install linux-headers-`uname -r`

or select the appropriate package in synaptic.

Note: you'll also need gcc etc which if you don't have already you can get with

>> sudo apt-get install build-essential

After installation the vmware installer should just pick up the right place and not require anything but the defaults.

If it's still being stupid, the path to include can be found in /lib/modules/<<module release number>>/build/include

Cheers.


thank you anyway...[/QUOTE]
 thanks nickx !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by jasonhh on 2005-06-30
Thanks!!!!  :)

---

### Post by torena on 2005-07-13
[QUOTE=nickx]I fixed the problem via this way:



You need to install the headers for the release of the kernel you have installed. To find this out you can type

>> uname -r

to get the header you can apt-get install them,

>> sudo apt-get install linux-headers-`uname -r`

or select the appropriate package in synaptic.

Note: you'll also need gcc etc which if you don't have already you can get with

>> sudo apt-get install build-essential

After installation the vmware installer should just pick up the right place and not require anything but the defaults.

If it's still being stupid, the path to include can be found in /lib/modules/<<module release number>>/build/include

Cheers.


thank you anyway...[/QUOTE]

That still didn't work for me.  The directories are there but I still get the error that linux, asm or something else directories aren't in there, which they are.  I heard this was a pain to install and I'm used to that by now, but this is just awful. :/

Unfortunately Crossover Office and Wine don't emulate Windows programs very well.  There are two programs I absolutely need to be completely independent of Windows - a good finance manager (I've been using AceMoney which is Windows only and it's FANTASTIC but the dates get unsorted and I can't sort them back in Ubuntu) and something that can communicate with my iRiver IFP-890 and allow me to transfer mp3s back and forth (dmesg sees the device but doesn't tell me where it's located so I can't mount it and ifplib and others aren't helping).  

Sorry, didn't mean for this to be a bitchfest. ;)  Are there any other ideas to get VMWare running?

---

### Post by t2kburl on 2005-07-14
[QUOTE=torena]That still didn't work for me.  The directories are there but I still get the error that linux, asm or something else directories aren't in there, which they are.  I heard this was a pain to install and I'm used to that by now, but this is just awful. :/[/QUOTE]

please post the output of vmware-config.pl

---

### Post by skirkpatrick on 2005-07-14
I believe VMware is looking for the /usr/src/linux directory as the root of the kernel headers.  You can fix this by:
> 
cd /usr/linux
sudo ln -s linux-headers-2.6.10-5 linux

Replace, if necessary, *linux-headers-2.6.10-5* with the directory that contains an *include* directory.

---

### Post by pauljwells on 2005-07-30
[QUOTE=nickx]I fixed the problem via this way:



You need to install the headers for the release of the kernel you have installed. To find this out you can type

>> uname -r

to get the header you can apt-get install them,

>> sudo apt-get install linux-headers-`uname -r`

or select the appropriate package in synaptic.

Note: you'll also need gcc etc which if you don't have already you can get with

>> sudo apt-get install build-essential

After installation the vmware installer should just pick up the right place and not require anything but the defaults.

If it's still being stupid, the path to include can be found in /lib/modules/<<module release number>>/build/include

Cheers.


thank you anyway...[/QUOTE]
 This worked for me perfectly! Many thanks

---

### Post by _zulu_ on 2005-08-06
Thanks mate installed perfectly!!!

---

### Post by wazzup on 2005-08-09
hmmm... I can't seem to get it to work:

> None of VMware Workstation's pre-built vmmon modules is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running 
kernel? [**/lib/modules/2.6.10-5-386/build/include**] 

Extracting the sources of the vmmon module.

Building the vmmon module.

make: Entering directory `/tmp/vmware-config7/vmmon-only'
make[1]: Entering directory `/tmp/vmware-config7/vmmon-only'
make[2]: Entering directory `/tmp/vmware-config7/vmmon-only/driver-2.6.10-5-386'
make[2]: Leaving directory `/tmp/vmware-config7/vmmon-only/driver-2.6.10-5-386'
make[2]: Entering directory `/tmp/vmware-config7/vmmon-only/driver-2.6.10-5-386'
../linux/driver.c:25:27: linux/wrapper.h: No such file or directory
In file included from ../linux/driver.c:45:
../linux/driver.h:51:1: warning: "DEVICE_NAME_SIZE" redefined
In file included from /lib/modules/2.6.10-5-386/build/include/linux/miscdevice.h:5,
                 from ../linux/driver.h:12,
                 from ../linux/driver.c:45:
/lib/modules/2.6.10-5-386/build/include/linux/device.h:25:1: warning: this is the location of the previous definition
../linux/driver.c:133: warning: initialization from incompatible pointer type
../linux/driver.c: In function `init_module':
../linux/driver.c:246: error: structure has no member named `prev'
../linux/driver.c:247: error: structure has no member named `next'
../linux/driver.c: In function `Panic':
../linux/driver.c:1304: warning: implicit declaration of function `_exit'
../include/vm_asm.h: In function `Div643264':
../include/vm_asm.h:1095: warning: use of memory input without lvalue in asm operand 4 is deprecated
make[2]: *** [driver.o] Error 1
make[2]: Leaving directory `/tmp/vmware-config7/vmmon-only/driver-2.6.10-5-386'
make[1]: *** [driver] Error 2
make[1]: Leaving directory `/tmp/vmware-config7/vmmon-only'
make: *** [auto-build] Error 2
make: Leaving directory `/tmp/vmware-config7/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and 
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

# uname -r
2.6.10-5-386

aparrently I am missing files... ?

PS: I'm trying to install  VMware Workstation 4.0.5 build-6030 for Linux (not 5)

---

### Post by wazzup on 2005-08-09
Hold on, I just tried again with: VMware-workstation-4.5.2-8848

with succes.

so ... make sure you're installing an up-to-date version *sigh*  ](*,)

---

### Post by thelevin8r on 2005-09-02
I'm sure I am being an idiot here. I need a non-noob to help me out. I am trying to install vmware on Ubutu 5.04 following the instruction in this thread bit not making progress

From this web site: [http://www.mrbass.org/linux/ubuntu/](http://www.mrbass.org/linux/ubuntu/)
I followed these instructions. The results you see are all up to date because I did all of these before, I just did them again so I could post my results.

uname -a
Linux hostname 2.6.10-5-386
sudo apt-cache search headers 2.6.10-5-386
linux-headers-2.6.10-5-386 - Linux kernel headers 2.6.10 on 386
sudo apt-get install linux-headers-2.6.10-5-386
sudo apt-get install gcc
Now your ready to install VMWare with the script

This is the terminal output. I really hope someone can show me what I missed, I'm a total noob.

root@LinuxLaptopA:/home/human # uname -a
Linux LinuxLaptopA 2.6.10-5-386 #1 Thu Aug 18 22:23:56 UTC 2005 i686 GNU/Linux
root@LinuxLaptopA:/home/human # sudo apt-cache search headers 2.6.10-5-386
linux-headers-2.6.10-5-386 - Linux kernel headers 2.6.10 on 386
root@LinuxLaptopA:/home/human # sudo apt-get install linux-headers-2.6.10-5-386
Reading package lists... Done
Building dependency tree... Done
linux-headers-2.6.10-5-386 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@LinuxLaptopA:/home/human #  sudo apt-get install gcc
Reading package lists... Done
Building dependency tree... Done
gcc is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@LinuxLaptopA:/home/human # ls -l
total 8
drwxr-xr-x  2 human human 4096 2005-09-01 21:32 Desktop
drwxr-xr-x  4 human human 4096 2005-09-01 22:05 software
root@LinuxLaptopA:/home/human # cd software/vmware-distrib
root@LinuxLaptopA:/home/human/software/vmware-distrib # ls -l
total 372
drwxr-xr-x   2 human human   4096 1969-12-31 16:00 bin
drwxr-xr-x   2 human human   4096 1969-12-31 16:00 doc
drwxr-xr-x   2 human human   4096 1969-12-31 16:00 etc
-r-xr-xr-x   1 human human 257029 2005-03-23 03:54 FILES
drwxr-xr-x   2 human human   4096 1969-12-31 16:00 installer
drwxr-xr-x  17 human human   4096 1969-12-31 16:00 lib
drwxr-xr-x   3 human human   4096 1969-12-31 16:00 man
-r-xr-xr-x   1 human human  87995 2005-03-23 03:54 vmware-install.pl
root@LinuxLaptopA:/home/human/software/vmware-distrib # sudo sh vmware-install.pl
vmware-install.pl: line 8: use: command not found
vmware-install.pl: line 11: my: command not found
vmware-install.pl: line 12: my: command not found
vmware-install.pl: line 13: my: command not found
vmware-install.pl: line 14: my: command not found
vmware-install.pl: line 15: my: command not found
vmware-install.pl: line 16: my: command not found
vmware-install.pl: line 17: my: command not found
vmware-install.pl: line 18: my: command not found
vmware-install.pl: line 19: my: command not found
vmware-install.pl: line 20: my: command not found
vmware-install.pl: line 21: my: command not found
vmware-install.pl: line 22: my: command not found
vmware-install.pl: line 25: my: command not found
vmware-install.pl: line 28: my: command not found
vmware-install.pl: line 32: my: command not found
vmware-install.pl: line 33: my: command not found
vmware-install.pl: line 34: my: command not found
vmware-install.pl: line 35: my: command not found
vmware-install.pl: line 36: my: command not found
vmware-install.pl: line 37: my: command not found
vmware-install.pl: line 38: my: command not found
vmware-install.pl: line 40: my: command not found
vmware-install.pl: line 41: my: command not found
vmware-install.pl: line 42: my: command not found
vmware-install.pl: line 43: my: command not found
vmware-install.pl: line 44: my: command not found
vmware-install.pl: line 47: sub: command not found
vmware-install.pl: line 48: undef: command not found
vmware-install.pl: line 49: undef: command not found
vmware-install.pl: line 50: undef: command not found
vmware-install.pl: line 51: undef: command not found
vmware-install.pl: line 52: undef: command not found
vmware-install.pl: line 54: syntax error near unexpected token `INSTALLDB,'
vmware-install.pl: line 54: `  open(INSTALLDB, '<' . $gInstallerMainDB) '

---

### Post by Maier on 2005-09-02
First of, why do you use sudo when you allready are logged in as root ? :)

Open a Terminal as a normal user.

cd /home/human/software/vmware-distrib/

sudo ./vmware-install.pl

type the password for your root account, when prompted..

And you should be ready to rumble :)


Worked like a charm here :)

---

### Post by mlomker on 2005-09-02
apt-get install build-essential

That's the bare minimum for compiling packages.  That doesn't explain why your system wasn't finding perl, though.  If you are already root then ./vmware-install.pl should be all you need to type.

---

### Post by Maier on 2005-09-03
mlomker not even sure u need the build essential.. i didnt anyways :)

---

### Post by thelevin8r on 2005-09-04
[QUOTE=Maier]First of, why do you use sudo when you allready are logged in as root ? :) [/QUOTE]

Cuz I was grasping at straws, and a n00b  ](*,) 

I follow your steps and it worked perfectly! My only last issue that the sound will not work, probably has to do with my hardware, but as soon as I start a VM I get this message:

"Failed to open sound device /dev/dsp: Device or resource busy
Virtual device sound will start disconnected."

---

### Post by Maier on 2005-09-04
hm.. are you running xmms og anything else that could use your soundcard, before starting up your vmware session ?

If yes : try and shut them down first,,

if no : see if you have the correct drivers installed (assuming ALSA), having the corectly "updated" saves a lot of trouble later on.. :)

glad i could help out though :)

---

### Post by thierrybo on 2006-07-17
Here is a successfull vmware-config.pl for vmware 5.5 :

> Do you accept? (yes/no) yes

Thank you.

Configuring fallback GTK+ 2.4 libraries.

In which directory do you want to install the mime type icons?
[/usr/share/icons]

What directory contains your desktop menu entry files? These files have a
.desktop file extension. [/usr/share/applications]

In which directory do you want to install the application's icon?
[/usr/share/pixmaps]

Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Workstation is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for
your system (you need to have a C compiler installed on your system)? [yes]

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.12-10-386/build/include]

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: entrant dans le répertoire « /tmp/vmware-config0/vmmon-only »
make -C /lib/modules/2.6.12-10-386/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: entrant dans le répertoire « /usr/src/linux-headers-2.6.12-10-386 »
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/driver.o
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/hostif.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/cpuid.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/hash.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/memtrack.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/phystrack.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/task.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/vmx86.o
  CC [M]  /tmp/vmware-config0/vmmon-only/vmcore/moduleloop.o
  LD [M]  /tmp/vmware-config0/vmmon-only/vmmon.o
  Building modules, stage 2.
  MODPOST
  CC      /tmp/vmware-config0/vmmon-only/vmmon.mod.o
  LD [M]  /tmp/vmware-config0/vmmon-only/vmmon.ko
make[1]: quittant le répertoire « /usr/src/linux-headers-2.6.12-10-386 »
cp -f vmmon.ko ./../vmmon.o
make: quittant le répertoire « /tmp/vmware-config0/vmmon-only »
The module loads perfectly in the running kernel.

Do you want networking for your virtual machines? (yes/no/help) [yes]

Configuring a bridged network for vmnet0.

Your computer has multiple ethernet network interfaces available: eth0, wlan0.
Which one do you want to bridge to vmnet0? [eth0]

The following bridged networks have been defined:

. vmnet0 is bridged to eth0

Do you wish to configure another bridged network? (yes/no) [no]

Do you want to be able to use NAT networking in your virtual machines? (yes/no)
[yes]

Configuring a NAT network for vmnet8.

Do you want this program to probe for an unused private subnet? (yes/no/help)
[yes]

Probing for an unused private subnet (this can take some time)...

The subnet 172.16.129.0/255.255.255.0 appears to be unused.

The following NAT networks have been defined:

. vmnet8 is a NAT network on private subnet 172.16.129.0.

Do you wish to configure another NAT network? (yes/no) [no]

Do you want to be able to use host-only networking in your virtual machines?
[yes]

Configuring a host-only network for vmnet1.

Do you want this program to probe for an unused private subnet? (yes/no/help)
[yes]

Probing for an unused private subnet (this can take some time)...

The subnet 172.16.115.0/255.255.255.0 appears to be unused.

The following host-only networks have been defined:

. vmnet1 is a host-only network on private subnet 172.16.115.0.

Do you wish to configure another host-only network? (yes/no) [no]

Extracting the sources of the vmnet module.

Building the vmnet module.

Using 2.6.x kernel build system.
make: entrant dans le répertoire « /tmp/vmware-config0/vmnet-only »
make -C /lib/modules/2.6.12-10-386/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: entrant dans le répertoire « /usr/src/linux-headers-2.6.12-10-386 »
  CC [M]  /tmp/vmware-config0/vmnet-only/driver.o
  CC [M]  /tmp/vmware-config0/vmnet-only/hub.o
  CC [M]  /tmp/vmware-config0/vmnet-only/userif.o
  CC [M]  /tmp/vmware-config0/vmnet-only/netif.o
  CC [M]  /tmp/vmware-config0/vmnet-only/bridge.o
  CC [M]  /tmp/vmware-config0/vmnet-only/procfs.o
  CC [M]  /tmp/vmware-config0/vmnet-only/smac_compat.o
  SHIPPED /tmp/vmware-config0/vmnet-only/smac_linux.x386.o
  LD [M]  /tmp/vmware-config0/vmnet-only/vmnet.o
  Building modules, stage 2.
  MODPOST
Warning: could not open /tmp/vmware-config0/vmnet-only/includeCheck.h: Invalid argument
  CC      /tmp/vmware-config0/vmnet-only/vmnet.mod.o
  LD [M]  /tmp/vmware-config0/vmnet-only/vmnet.ko
make[1]: quittant le répertoire « /usr/src/linux-headers-2.6.12-10-386 »
cp -f vmnet.ko ./../vmnet.o
make: quittant le répertoire « /tmp/vmware-config0/vmnet-only »
The module loads perfectly in the running kernel.

Starting VMware services:
   Virtual machine monitor                                             done
   Virtual ethernet                                                    done
   Bridged networking on /dev/vmnet0                                   done
   Host-only networking on /dev/vmnet1 (background)                    done
   Host-only networking on /dev/vmnet8 (background)                    done
   NAT service on /dev/vmnet8                                          done

The configuration of VMware Workstation 5.5.1 build-19175 for Linux for this
running kernel completed successfully.

You can now run VMware Workstation by invoking the following command:
"/usr/bin/vmware".

Enjoy,

--the VMware team


---

### Post by matjaz_pirnovar on 2006-08-17
> **nickx said:**
> I fixed the problem via this way:



You need to install the headers for the release of the kernel you have installed. To find this out you can type

>> uname -r

to get the header you can apt-get install them,

>> sudo apt-get install linux-headers-`uname -r`

or select the appropriate package in synaptic.

Note: you'll also need gcc etc which if you don't have already you can get with

>> sudo apt-get install build-essential

After installation the vmware installer should just pick up the right place and not require anything but the defaults.

If it's still being stupid, the path to include can be found in /lib/modules/<<module release number>>/build/include

Cheers.


thank you anyway...


Hey,

Everything runs and installs fine until I try to run it.
Then home window and vmware window pop out as if just about to start and in terminal I get:

> matjaz@PCPlus:~$ /usr/bin/vmplayer
/usr/lib/vmware/bin/vmplayer: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)


When I close the home window everything stops as if nothing has happened.
What does it mean: No version information available? Is that why it doesn't open?

What am I doing wrong?

Thanks.

---

### Post by loboson on 2006-10-22
Worked for me also. Many thanks. :)

Pd: Nicely programmed pl script from vmware folks..

[QUOTE=nickx;123473]I fixed the problem via this way:

>> sudo apt-get install linux-headers-`uname -r`
/lib/modules/<<module release number>>/build/include

---

### Post by Goatie2k7 on 2007-07-03
> What is the location of the directory of C header files that match your running 
kernel? [/usr/src/linux/include] /lib/modules/2.6.20-15-generic/build/include

The directory of kernel headers (version @@VMWARE@@ UTS_RELEASE) does not match 
your running kernel (version 2.6.20-15-generic).  Even if the module were to 
compile successfully, it would not load into the running kernel.

What is the location of the directory of C header files that match your running 
kernel? [/usr/src/linux/include] /usr/include


I'm running Ubuntu on a virtual server and I'm trying to install the VMware Tools but I can't get past this point.

I've tried all the various advice on this post but I can't seem to get it to work! :(

---

### Post by thierrybo on 2007-07-03
> 2.6.20-15-generic

this MUST match the linux version from the output of ```
cat /proc/version
```

---

### Post by Goatie2k7 on 2007-07-03
OK, before you point out the obvious.  I updated my machine and that's why it says '16' now not '15'.  I tried the same as previous with '16' in it's place and it still didn't work.

Here's the result of my cat /proc/version command

> Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Thu Jun 7 20:19:32 UTC 2007

---

### Post by thierrybo on 2007-07-05
OK,

so did you have installed headers files for you new kernel ( linux-headers-2.6.20-16-generic packet) ? You just no need only to change /lib/modules/2.6.20-15-generic/build/include with /lib/modules/2.6.20-16-generic/build/include , you have to install the headers files.

---

### Post by Goatie2k7 on 2007-07-06
> You just no need only to change /lib/modules/2.6.20-15-generic/build/include with /lib/modules/2.6.20-16-generic/build/include , you have to install the headers files.

Even after doing:

sudo apt-get install linux-headers-`uname -r`

it still won't work when I select the directory you mentioned.  It's really starting to bug me..I don't understand why it doesn't like my c  header files.

---

### Post by thierrybo on 2007-07-06
Well, for me this was not the /lib... directory but /usr/src/linux-headers-2.6.20-15-generic/include

---

### Post by C_B-A on 2007-07-22
Well I got the exact same problem with the 2.6.20-16-generic kernel

```
What is the location of the directory of C header files that match your running 
kernel? [/usr/src/linux/include] /usr/src/linux-headers-2.6.20-16-generic/include

The directory of kernel headers (version @@VMWARE@@ UTS_RELEASE) does not match 
your running kernel (version 2.6.20-16-generic).  Even if the module were to 
compile successfully, it would not load into the running kernel.
```

any ideas? I already tried some of the things you mentioned, but nothing seems to work.

---

### Post by upthelum on 2007-07-22
I have the same problem now after a slog to get here. Feels like this is a common problem so sorry for bringing it up again but i am not sure how to install the header files can someone tell me please? 
Thanks

---

### Post by krzysz00 on 2007-08-20
this thread got me here (I'm installing the latest version of VMware Server)
i can'r compile the module

this is the terminal output


Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config1/vmmon-only'
make -C /lib/modules/2.6.20-15-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /tmp/vmware-config1/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config1/vmmon-only/linux/driver.c:80:
/tmp/vmware-config1/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or ‘...’ before ‘compat_exit’
/tmp/vmware-config1/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or ‘...’ before ‘exit_code’
/tmp/vmware-config1/vmmon-only/./include/compat_kernel.h:21: warning: type defaults to ‘int’ in declaration of ‘_syscall1’
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

can i get some help, please?

---

### Post by krzysz00 on 2007-08-23
can you provide VMWare with modules you downloaded off the internet?

---

### Post by mrfelker on 2007-08-23
Also you may try to answers on the VMware Forums.

---

### Post by Ocyberbum on 2007-08-23
> **Goatie2k7 said:**
> I'm running Ubuntu on a virtual server and I'm trying to install the VMware Tools but I can't get past this point.

I've tried all the various advice on this post but I can't seem to get it to work! :(

ok i'm also having the same problem and i can't seem to get past this point either. i've tried updating 

sudo apt-get install linux-headers-`uname -r` build-essential
reading package lists... Done
Building dependency tree
Reading state information... Done
linux-headers-2.6.20-15-generic is already the newest version.
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.

i did uname -a
2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686 GNU/Linux

here is the output for trying to find the c headers

/usr/share/applications/vmware-workstation.desktop: warning: The 'Application' c
ategory is not defined by the desktop entry specification.  Please use one of "A
udioVideo", "Audio", "Video", "Development", "Education", "Game", "Graphics", "N
etwork", "Office", "Settings", "System", "Utility" instead
/usr/share/applications/vmware-player.desktop: warning: The 'Application' catego
ry is not defined by the desktop entry specification.  Please use one of "AudioV
ideo", "Audio", "Video", "Development", "Education", "Game", "Graphics", "Networ
k", "Office", "Settings", "System", "Utility" instead
Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Workstation is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for
your system (you need to have a C compiler installed on your system)? [yes]

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

The path "/usr/src/linux/include" is not an existing directory.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] /lib/modules/2.6.20-15-generic/build/include

The directory of kernel headers (version @@VMWARE@@ UTS_RELEASE) does not match
your running kernel (version 2.6.20-15-generic).  Even if the module were to
compile successfully, it would not load into the running kernel.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] /usr/src/linux-headers-2.6.20-15-generic/includ                                                              e

The directory of kernel headers (version @@VMWARE@@ UTS_RELEASE) does not match
your running kernel (version 2.6.20-15-generic).  Even if the module were to
compile successfully, it would not load into the running kernel.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] /lib/modules/2.6.20-15-generic/build/include

The directory of kernel headers (version @@VMWARE@@ UTS_RELEASE) does not match
your running kernel (version 2.6.20-15-generic).  Even if the module were to
compile successfully, it would not load into the running kernel.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] /lib/modules/2.6.20-15-generic/build/include/

The directory of kernel headers (version @@VMWARE@@ UTS_RELEASE) does not match
your running kernel (version 2.6.20-15-generic).  Even if the module were to
compile successfully, it would not load into the running kernel.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]


im not sure what i should do next? im trying to install VMware Workstation 5.5.1 build-19175 for Linux 

thanks

---

### Post by Ocyberbum on 2007-08-25
never mind, i dloaded vm6 and it installed with no problems

---

### Post by jenciso on 2007-10-14
> **Ocyberbum said:**
> 
The directory of kernel headers (version @@VMWARE@@ UTS_RELEASE) does not match
your running kernel (version 2.6.20-15-generic).  Even if the module were to
compile successfully, it would not load into the running kernel.

Hi!
I have this problem too, trying to install wmtools into an kubunutu 7 running inside a wmvare workstation 5.5.1 on winxp...

I (think) I've done everything I read on this post, but still can't install - or rather: I can't run vmware-config-tools.pl after installed, so installation is not completed...

Can someone explain where ubuntu is taking the @@VMWARE@@ from? It shouldn't know its inside a vwmare...should it?

I really can't download vmw6 like ocyberbum, so if someone can help me, I'll send him/her a x-mas present ;-)

thanks
/j

---

### Post by jjcv on 2007-10-15
This worked great for me - installed on a PC and Laptop.

Installing VMWareWorkstationr on Ubuntu 7.10

   1. Download VMware Workstation (or server)  source from the VMware website.
   2. Download this installer patch.  [http://knihovny.cvut.cz/ftp/pub/vmware/vmware-any-any-update113.tar.gz](http://knihovny.cvut.cz/ftp/pub/vmware/vmware-any-any-update113.tar.gz)
   3. Extract all the archives to some location on your system (tar -zxvf VMware-r* ; tar -zxvf vmware*)
   4. Ensure that you have build-essential installed in order to compile these sources (sudo aptitude install build-essential)
   5. Run sudo ./vmware-install.pl located within the vmwarr-* unpacked archive.
   6. Select all the default options *EXCEPT* do not compile the modules at this point. (Do you want this program to try to build the vmmon module for your system? NO)
   7. Run sudo ./runme.pl located within the vmware-any* archive. This will launch step 8.
   8. Select the default options and this time answer YES to compile the proper modules.
   9. Run vmware-server using the command vmware or via your Applications Menu.

Modifed from [http://ubuntu-tutorials.com/2007/09/26/how-to-install-vmware-server-on-ubuntu-710/](http://ubuntu-tutorials.com/2007/09/26/how-to-install-vmware-server-on-ubuntu-710/)

---

### Post by videoordvd on 2007-10-25
I was having the same problem and this worked like a charm. Thanks a lot jjcv!

Do you know what the problem is that necessitates the patch?

---

### Post by djbon2112 on 2008-02-27
Sorry for the bump, but I'm having a similar problem:

```
What is the location of the directory of C header files that match your running 
kernel? [/usr/src/linux/include] /usr/src/linux-headers-2.6.22-14-rt/include

The directory of kernel headers (version @@VMWARE@@ UTS_RELEASE) does not match 
your running kernel (version 2.6.22-14-rt).  Even if the module were to compile 
successfully, it would not load into the running kernel.

```

Anyone have any ideas?

---

### Post by ruffwuk on 2008-05-30
I have the same issue.  i pointed the install to the c header files and got a similar error.


[INDENT][I]Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config1/vmmon-only'
make -C /usr/src/linux-headers-2.6.24-16-server/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-server'
  CC [M]  /tmp/vmware-config1/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config1/vmmon-only/./include/vmware.h:25,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:48:
/tmp/vmware-config1/vmmon-only/./include/vm_basic_types.h:161: error: conflicting types for ‘uintptr_t’
include/linux/types.h:40: error: previous declaration of ‘uintptr_t’ was here
In file included from /tmp/vmware-config1/vmmon-only/linux/driver.h:20,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:49:
/tmp/vmware-config1/vmmon-only/./include/compat_wait.h:37:5: warning: "VMW_HAVE_EPOLL" is not defined
/tmp/vmware-config1/vmmon-only/./include/compat_wait.h:43:5: warning: "VMW_HAVE_EPOLL" is not defined
In file included from /tmp/vmware-config1/vmmon-only/linux/driver.h:20,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:49:
/tmp/vmware-config1/vmmon-only/./include/compat_wait.h:60: error: conflicting types for ‘poll_initwait’
include/linux/poll.h:65: error: previous declaration of ‘poll_initwait’ was here
/tmp/vmware-config1/vmmon-only/linux/driver.c:147: warning: initialization from incompatible pointer type
/tmp/vmware-config1/vmmon-only/linux/driver.c:151: warning: initialization from incompatible pointer type
/tmp/vmware-config1/vmmon-only/linux/driver.c: In function ‘LinuxDriver_Ioctl’:
/tmp/vmware-config1/vmmon-only/linux/driver.c:1659: error: ‘struct mm_struct’ has no member named ‘dumpable’
make[2]: *** [/tmp/vmware-config1/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config1/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-server'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config1/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.[/I][/INDENT]

---


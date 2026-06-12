---
title: "Vmwere Server 2.0.2 on ubuntu 11.10"
date: 2012-01-05
forum: Installation &amp; Upgrades
---

### Post by weapon-x on 2012-01-05
Hi guys , 

I have installed 11.10 ver.


```
Linux ubuntu 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:34:47 UTC 2011 i686 i686 i386 GNU/Linux

```

while installing Vm i m stuck at this :

```
None of the pre-built vmmon modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] 

The path "/usr/src/linux/include" is not an existing directory.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] 

```

please help

---

### Post by e79 on 2012-01-05
```
sudo apt-get install linux-headers-3.0.0-14-generic
```

```
sudo ./vmware-install.pl
```

---

### Post by weapon-x on 2012-01-06
@e79 thanks for reply 

i followed to command after hit and trial i got this error

```
What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] /usr/src/linux-headers-3.0.0-14/include

The directory of kernel headers (version @@VMWARE@@ UTS_RELEASE) does not match
your running kernel (version 3.0.0-14-generic).  Even if the module were to 
compile successfully, it would not load into the running kernel.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] 
```

---

### Post by e79 on 2012-01-06
In that case have a look on the Ubuntu help site :

[https://help.ubuntu.com/community/VMware/Server](https://help.ubuntu.com/community/VMware/Server)

Look at the first section. Though they do not list 11.10 for now, I would try the 11.04 way.

Quoting:
> **Ubuntu 11.04 (VMware Server 2.0.x)**

 [http://ubuntuforums.org/showthread.php?p=10761345](http://ubuntuforums.org/showthread.php?p=10761345) 
 
**Ubuntu 10.10 (VMware Server 2.0.x)**

 The same procedure as for Ubuntu 10.04 applies and works. 
 
**Ubuntu 10.04 (VMware Server 2.0.x)**

 The same procedure as for Ubuntu 9.10 applies and works. 
 
**Ubuntu 9.10 (VMWare Server 2.0.x)**

 Both **vmware-server.2.0.1-156745** and **vmware-server.2.0.2-203138** can be installed from scratch by using a script I built. For more details you can visit [How to install VMware Server 2.0.x on Ubuntu 9.10 Karmic Koala]("http://radu.cotescu.com/2009/10/30/how-to-install-vmware-server-2-0-x-on-ubuntu-9-10-karmic-koala/"). 

[LIST=1]
[*]Download VMware Server ([2.0.1]("https://www.vmware.com/freedownload/p/download.php?product=server20") or [2.0.2]("http://www.vmware.com/download/server/getserver.html"))  &#8211; gz format, not rpm. For the 2.0.2 version you might need to wait a  couple of hours until you will receive the license key. Whichever  version you choose, keep the license key near.
[*]Download my script from [here]("http://codebin.cotescu.com/vmware/vmware-server-2.0.x-kernel-2.6.3x-install.sh") (right click, save as).
[*]Run  the script with super user rights either in the same folder where you  have downloaded the server archive, or by providing it the path to that  folder. The script will download the needed patch from my server. ***Make sure the folder where you have downloaded the server's archive doesn't contain spaces in its path name***.  You will reach to a point where a lot of warnings appear on your  terminal. Do not worry unless the script exits. If it exits, it will  give you a decent warning from which you should be able to tell what&#8217;s  wrong. Also, the VSOCK module will not work (will fail to compile),  giving you a hint that your kernel sources might not be the ones for  your running kernel. This is not true, as the script takes care of this  before doing the hard work. Anyway, VMware Server will work without it.
[*]When  you are asked about adding users to the server, if you do not provide  your own account, the user used for loging in the web console of the  server will be root (maybe you should add yourself there).
[*]Provide the license key when asked about it.
[/LIST]
If you experience problems with the script please write them in the post's comments so that I can offer assistance. Cheers

e79

---

### Post by bindir on 2012-01-06
> **e79 said:**
> In that case have a look on the Ubuntu help site :

[https://help.ubuntu.com/community/VMware/Server](https://help.ubuntu.com/community/VMware/Server)

Look at the first section. Though they do not list 11.10 for now, I would try the 11.04 way.

Quoting:
Cheers

e79

the 11.04 way doesn't seem to be working for me:

./vmware-server-2.0.x-kernel-2.6.3x-install.sh 
You have VMware Server archive: 
        VMware-server-2.0.2-203138.x86_64.tar.gz
Checking for needed packages on Ubuntu
You do have the linux-headers-3.0.0-14-server package...
You do have the build-essential package...
You do have the patch package...
Extracting the contents of VMware-server-2.0.2-203138.x86_64.tar.gz
Found .tar file for vsock module
Found .tar file for vmci module
Found .tar file for vmnet module
Found .tar file for vmmon module
Extracting .tar files in order to apply the patch...
Untarring /root/v/rad//vmware-server-distrib/lib/modules/source/vsock.tar
Untarring /root/v/rad//vmware-server-distrib/lib/modules/source/vmci.tar
Untarring /root/v/rad//vmware-server-distrib/lib/modules/source/vmnet.tar
Untarring /root/v/rad//vmware-server-distrib/lib/modules/source/vmmon.tar
Testing patch...
Creating some simlinks for the newer kernels...
ln: creating symbolic link `/usr/src/linux-headers-3.0.0-14-server/include/linux/autoconf.h': File exists
ln: creating symbolic link `/usr/src/linux-headers-3.0.0-14-server/include/linux/utsrelease.h': File exists
Applying patch...
Preparing new tar file for vsock module
Preparing new tar file for vmci module
Preparing new tar file for vmnet module
Preparing new tar file for vmmon module
Checking that the compiling will succeed...
Trying to compile vmci module to see if it works
Performing make in /root/v/rad//vmware-server-distrib/lib/modules/source/vmci-only
Using 2.6.x kernel build system.
/root/v/rad/vmware-server-distrib/lib/modules/source/vmci-only/linux/driver.c:37:28: fatal error: linux/smp_lock.h: No such file or directory
compilation terminated.
make[2]: *** [/root/v/rad/vmware-server-distrib/lib/modules/source/vmci-only/linux/driver.o] Error 1
make[1]: *** [_module_/root/v/rad/vmware-server-distrib/lib/modules/source/vmci-only] Error 2
make: *** [vmci.ko] Error 2
There is a problem compiling the vmci module after it was patched. :(

---


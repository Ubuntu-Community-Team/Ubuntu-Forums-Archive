---
title: "VMWare Server 2 on 11.04 Natty Narwhal"
date: 2011-05-02
forum: Installation &amp; Upgrades
---

### Post by sirusdv on 2011-05-02
Saw a bunch of people like myself have been having issues getting vmware-server to compile / install after upgrading to natty so I created a new patch set for for the raducotescu script.

Follow the following guide 

[https://help.ubuntu.com/community/VMware/Server](https://help.ubuntu.com/community/VMware/Server)

But before executing the vmware-server-2.0.x-kernel-2.6.3x-install.sh script extract the attached file and overwrite the one that comes with the package. 

You should now be able to build all the modules and complete installation.

---

### Post by collisionystm on 2011-05-02
many thanks good sir. I was just pondering this today!

---

### Post by sirusdv on 2011-05-03
If someone is familiar with the wiki formatting guidelines it would be beneficial to update it with this patch for 11.04.

---

### Post by gewin on 2011-05-03
Many thanks, I will give it a try. I have vmserver running on 10.04 and was not at all confident that it would run on 11.04.

Unfortunately VMs created on the 10.04 server don't seem to run in a stable way using vmplayer on 11.04. I have a 64bit windows 7 vm created on vmserver on ubuntu 10.04. This vm moved to a Windows 7 machine runs fine with VMplayer. If I move it to 11.04 on the same hardware VMplayer starts to boot the Windows 7 vm then crashes. I will try it under vmserver.

---

### Post by gewin on 2011-05-03
Excellent, I have it working using your solution and my VMs including windows 7 seem stable. I am using Remmina to access the VMs as the console plugin for Firefox doesn't work.

---

### Post by Slingers on 2011-05-04
Hi guys, 

I'm new to this whole forum thing and not to mention Linux!!!  so please go easy one me :)

So far i am loving it but like all new things there is always something you get stuck on!  

I have followed your instructions and downloaded the other file from the vmware/server page, i have downloaded your patch and put it in the folder and when i run the .sh file as root from a terminal it all runs ok, it tells me i have all the necessary packages and modules but when it tries to untarr the vmmon-temp.tar file it returns this error.  

*vmmon-temp.tar tarball failed to extract in the directory vmmon-temp-only. :(*

I have spent a number of very late nights working on just this problem and doing a ton of research (because it happened to me in 10.04 too) but unfortunately i have been unable to find a resolution.  Is there some where you can point me to help me work this out or if not would you mind helping me regarding this query?

Thank you in advance for your assistance and i hope i have done this alright!

---

### Post by mozi123 on 2011-05-04
Thank you!!

> **Slingers said:**
> 
*vmmon-temp.tar tarball failed to extract in the directory vmmon-temp-only. :(*


Remove the folder with unpacked vmware distro and try again.

---

### Post by thunderblock on 2011-05-07
A thousand thanks [sirusdv]("http://ubuntuforums.org/member.php?u=1289848") for saving the day.  It worked perfectly.  Whether or not Vmware Server will run is a roll of the dice after every upgrade.   Its a house of cards.  Thanks again.

---

### Post by marcos.lohmann on 2011-05-09
hi [sirusdv]("http://ubuntuforums.org/member.php?u=1289848"),

Do you mind to post detailed instructions on what to do with the file (the patch)?
I have already downloaded and gunzipped, but dont know how to apply it in case of pre-installed vmware server... you mentioned to overwrite the old file "before install"... does it mean I need to remove and re-install vmware server from scratch with the patch? 

> But before executing the vmware-server-2.0.x-kernel-2.6.3x-install.sh  script extract the attached file and overwrite the one that comes with  the package. 

Thanks

---

### Post by ericstott on 2011-05-10
So I downloaded the new .update file, unpacked it, and ran the .sh file.
I am getting this error: vmware-server-2.0.x-kernel-2.6.3x-install.sh: 43: Syntax error: word unexpected (expecting ")")

what am I doing wrong?

I ran this command: chmod o+x vmware-server-2.0.x-kernel-2.6.3x-install.sh
and it worked

---

### Post by karhukuoma on 2011-05-12
```

./vmware-server-2.0.x-kernel-2.6.3x-install.sh
You have VMware Server archive:
        VMware-server-2.0.2-203138.x86_64.tar.gz
Checking for needed packages on Ubuntu
You do have the linux-headers-2.6.38-9-generic package...
You do have the build-essential package...
You do have the patch package...
Extracting the contents of VMware-server-2.0.2-203138.x86_64.tar.gz
Found .tar file for vmnet module
Found .tar file for vmmon module
Found .tar file for vmci module
Found .tar file for vsock module
Extracting .tar files in order to apply the patch...
Untarring /tmp/vmware-server-distrib/lib/modules/source/vmnet.tar
Untarring /tmp/vmware-server-distrib/lib/modules/source/vmmon.tar
Untarring /tmp/vmware-server-distrib/lib/modules/source/vmci.tar
Untarring /tmp/vmware-server-distrib/lib/modules/source/vsock.tar
Testing patch...
Applying patch...
Preparing new tar file for vmnet module
Preparing new tar file for vmmon module
Preparing new tar file for vmci module
Preparing new tar file for vsock module
Checking that the compiling will succeed...
Trying to compile vmnet module to see if it works
Performing make in /tmp/vmware-server-distrib/lib/modules/source/vmnet-only
Using 2.6.x kernel build system.
In file included from /tmp/vmware-server-distrib/lib/modules/source/vmnet-only/driver.c:19:0:
/tmp/vmware-server-distrib/lib/modules/source/vmnet-only/driver-config.h:35:28: fatal error: linux/autoconf.h: No such file or directory
compilation terminated.
make[2]: *** [/tmp/vmware-server-distrib/lib/modules/source/vmnet-only/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-server-distrib/lib/modules/source/vmnet-only] Error 2
make: *** [vmnet.ko] Error 2
There is a problem compiling the vmnet module after it was patched. :(

```

I'm using raducotescu-vmware-server-linux-2.6.3x-kernel-f271f27.tar.gz with updated vmware-server-2.0.2-203138-update.patch from this thread. What could I've missed?

**Update**
##########
This has been fixed like this:
```

sudo su -
goto /usr/src/linux-headers-2.6.38-9-generic/include/linux
cat ../generated/utsrelease.h >> version.h
ln -s ../generated/autoconf.h

```
kudos to [thingy@vmware-communities]("http://communities.vmware.com/message/1684660#1684660")

---

### Post by darnelali on 2011-05-13
This is what I did, hope it helps!

root login

cd /usr/src
mkdir vmware
cd vmware
Download VMWARE SERVER 2.0.2
wget [http://ubuntuforums.org/attachment.php?attachmentid=190878&d=1304365853](http://ubuntuforums.org/attachment.php?attachmentid=190878&d=1304365853)
gunzip vmware-server-2.0.2-203138-update.patch.gz
wget [http://ubuntuforums.org/attachment.php?attachmentid=94477&d=1227872015](http://ubuntuforums.org/attachment.php?attachmentid=94477&d=1227872015)
tar zxf raducotescu-vmware-server-linux-2.6.3x-kernel-release-1.6-0-gbb26dce.tar.gz
mv VMware-server-2.0.2-203138.i386.tar.gz raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce
mv vmware-server-2.0.2-203138-update.patch raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce
cd raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce
./vmware-server-2.0.x-kernel-2.6.3x-install.sh

---

### Post by mdacova on 2011-05-13
tar zxf raducotescu-vmware-server-linux-2.6.3x-kernel-release-1.6-0-


where can I find the above file

---

### Post by mdacova on 2011-05-13
> **mdacova said:**
> tar zxf raducotescu-vmware-server-linux-2.6.3x-kernel-release-1.6-0-


where can I find the above file

ok found it thanks google, ran the steps above and have a working vmserver now 

link to the missing file [https://github.com/raducotescu/vmware-server-linux-2.6.3x-kernel/tree/release-1.5](https://github.com/raducotescu/vmware-server-linux-2.6.3x-kernel/tree/release-1.5)

---

### Post by wush2011 on 2011-05-13
Tried to install VMware server 2_64bit on Ubunto64 bit without success

Kernel:
Ubuntu 10.04.2
2.6.32-31-server #61-Ubuntu SMP Fri Apr 8 19:44:42 UTC 2011 x86_64 GNU/Linux

Files:
raducotescu-vmware-server-linux-2.6.3x-kernel-release-1.6-0-gbb26dce.tar.gz
VMware-server-2.0.2-203138.x86_64.tar.gz
vmware-server-2.0.2-203138-update.patch.gz


**Doesnt work**

New Solution: Change back to debian. 
> root@si-demo-5:/home/mark/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce# ./vmware-server-2.0.x-kernel-2.6.3x-install.sh
You have VMware Server archive:
        VMware-server-2.0.2-203138.x86_64.tar.gz
Checking for needed packages on Ubuntu
You do have the linux-headers-2.6.32-31-server package...
You do have the build-essential package...
You do have the patch package...
Extracting the contents of VMware-server-2.0.2-203138.x86_64.tar.gz
Found .tar file for vmmon module
Found .tar file for vmci module
Found .tar file for vmnet module
Found .tar file for vsock module
Extracting .tar files in order to apply the patch...
Untarring /home/mark/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce/vmware-server-distrib/lib/modules/source/vmmon.tar
Untarring /home/mark/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce/vmware-server-distrib/lib/modules/source/vmci.tar
Untarring /home/mark/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce/vmware-server-distrib/lib/modules/source/vmnet.tar
Untarring /home/mark/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce/vmware-server-distrib/lib/modules/source/vsock.tar
Testing patch...
Creating some simlinks for the newer kernels...
ln: creating symbolic link `/usr/src/linux-headers-2.6.32-31-server/include/linux/autoconf.h': File exists
ln: creating symbolic link `/usr/src/linux-headers-2.6.32-31-server/include/linux/utsrelease.h': File exists
Applying patch...
Preparing new tar file for vmmon module
Preparing new tar file for vmci module
Preparing new tar file for vmnet module
Preparing new tar file for vsock module
Checking that the compiling will succeed...
Trying to compile vmmon module to see if it works
Performing make in /home/mark/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce/vmware-server-distrib/lib/modules/source/vmmon-only
Using 2.6.x kernel build system.
In file included from /home/mark/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce/vmware-server-distrib/lib/modules/source/vmmon-only/./common/vmx86.h:32,
                 from /home/mark/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce/vmware-server-distrib/lib/modules/source/vmmon-only/linux/driver.h:29,
                 from /home/mark/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce/vmware-server-distrib/lib/modules/source/vmmon-only/linux/driver.c:101:
/home/mark/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce/vmware-server-distrib/lib/modules/source/vmmon-only/./include/x86msr.h:164:1: warning: "MSR_THERM2_CTL" redefined
In file included from /usr/src/linux-headers-2.6.32-31-server/arch/x86/include/asm/msr.h:4,
                 from /usr/src/linux-headers-2.6.32-31-server/arch/x86/include/asm/processor.h:21,
                 from include/linux/prefetch.h:14,
                 from include/linux/list.h:6,
                 from include/linux/module.h:9,
                 from /home/mark/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce/vmware-server-distrib/lib/modules/source/vmmon-only/./include/compat_module.h:27,
                 from /home/mark/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce/vmware-server-distrib/lib/modules/source/vmmon-only/linux/driver.c:26:
/usr/src/linux-headers-2.6.32-31-server/arch/x86/include/asm/msr-index.h:230:1: warning: this is the location of the previous definition
In file included from /home/mark/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce/vmware-server-distrib/lib/modules/source/vmmon-only/./common/vmx86.h:32,
                 from /home/mark/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce/vmware-server-distrib/lib/modules/source/vmmon-only/linux/driver.h:29,
                 from /home/mark/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce/vmware-server-distrib/lib/modules/source/vmmon-only/linux/driver.c:101:
/home/mark/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce/vmware-server-distrib/lib/modules/source/vmmon-only/./include/x86msr.h:164:1: warning: "MSR_THERM2_CTL" redefined
In file included from /usr/src/linux-headers-2.6.32-31-server/arch/x86/include/asm/msr.h:4,
                 from /usr/src/linux-headers-2.6.32-31-server/arch/x86/include/asm/processor.h:21,
                 from include/linux/prefetch.h:14,
                 from include/linux/list.h:6,
                 from include/linux/module.h:9,
                 from /home/mark/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce/vmware-server-distrib/lib/modules/source/vmmon-only/./include/compat_module.h:27,
                 from /home/mark/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce/vmware-server-distrib/lib/modules/source/vmmon-only/linux/driver.c:26:
/usr/src/linux-headers-2.6.32-31-server/arch/x86/include/asm/msr-index.h:230:1: warning: this is the location of the previous definition
/home/mark/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce/vmware-server-distrib/lib/modules/source/vmmon-only/linux/hostif.c:37:1: warning: "HAVE_UNLOCKED_IOCTL" redefined
In file included from /home/mark/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce/vmware-server-distrib/lib/modules/source/vmmon-only/./include/compat_fs.h:22,
                 from /home/mark/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce/vmware-server-distrib/lib/modules/source/vmmon-only/linux/hostif.c:34:
include/linux/fs.h:1480:1: warning: this is the location of the previous definition
In file included from /home/mark/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce/vmware-server-distrib/lib/modules/source/vmmon-only/./common/vmx86.h:32,
                 from /home/mark/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce/vmware-server-distrib/lib/modules/source/vmmon-only/./common/hostif.h:32,
                 from /home/mark/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce/vmware-server-distrib/lib/modules/source/vmmon-only/linux/hostif.c:74:
/home/mark/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce/vmware-server-distrib/lib/modules/source/vmmon-only/./include/x86msr.h:164:1: warning: "MSR_THERM2_CTL" redefined
In file included from /usr/src/linux-headers-2.6.32-31-server/arch/x86/include/asm/msr.h:4,
                 from /usr/src/linux-headers-2.6.32-31-server/arch/x86/include/asm/processor.h:21,
                 from /usr/src/linux-headers-2.6.32-31-server/arch/x86/include/asm/thread_info.h:22,
                 from include/linux/thread_info.h:56,
                 from include/linux/preempt.h:9,
                 from include/linux/spinlock.h:50,
                 from include/linux/mmzone.h:7,
                 from include/linux/gfp.h:4,
                 from include/linux/mm.h:8,
                 from /home/mark/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce/vmware-server-distrib/lib/modules/source/vmmon-only/./include/compat_page.h:23,
                 from /home/mark/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce/vmware-server-distrib/lib/modules/source/vmmon-only/linux/hostif.c:32:
/usr/src/linux-headers-2.6.32-31-server/arch/x86/include/asm/msr-index.h:230:1: warning: this is the location of the previous definition
/home/mark/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce/vmware-server-distrib/lib/modules/source/vmmon-only/linux/hostif.c: In function âHostIFDoIoctlâ:
/home/mark/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce/vmware-server-distrib/lib/modules/source/vmmon-only/linux/hostif.c:3417: warning: control reaches end of non-void function
In file included from /home/mark/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce/vmware-server-distrib/lib/modules/source/vmmon-only/common/vmx86.h:32,
                 from /home/mark/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce/vmware-server-distrib/lib/modules/source/vmmon-only/common/vmx86.c:40:
/home/mark/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce/vmware-server-distrib/lib/modules/source/vmmon-only/./include/x86msr.h:164:1: warning: "MSR_THERM2_CTL" redefined
In file included from /usr/src/linux-headers-2.6.32-31-server/arch/x86/include/asm/msr.h:4,
                 from /usr/src/linux-headers-2.6.32-31-server/arch/x86/include/asm/processor.h:21,
                 from /usr/src/linux-headers-2.6.32-31-server/arch/x86/include/asm/thread_info.h:22,
                 from include/linux/thread_info.h:56,
                 from include/linux/preempt.h:9,
                 from include/linux/spinlock.h:50,
                 from include/linux/seqlock.h:29,
                 from include/linux/time.h:8,
                 from include/linux/timex.h:56,
                 from include/linux/sched.h:56,
                 from /home/mark/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce/vmware-server-distrib/lib/modules/source/vmmon-only/common/vmx86.c:32:
/usr/src/linux-headers-2.6.32-31-server/arch/x86/include/asm/msr-index.h:230:1: warning: this is the location of the previous definition
In file included from /home/mark/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce/vmware-server-distrib/lib/modules/source/vmmon-only/./common/vmx86.h:32,
                 from /home/mark/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce/vmware-server-distrib/lib/modules/source/vmmon-only/vmcore/moduleloop.c:35:
/home/mark/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce/vmware-server-distrib/lib/modules/source/vmmon-only/./include/x86msr.h:164:1: warning: "MSR_THERM2_CTL" redefined
In file included from /usr/src/linux-headers-2.6.32-31-server/arch/x86/include/asm/msr.h:4,
                 from /usr/src/linux-headers-2.6.32-31-server/arch/x86/include/asm/processor.h:21,
                 from /usr/src/linux-headers-2.6.32-31-server/arch/x86/include/asm/thread_info.h:22,
                 from include/linux/thread_info.h:56,
                 from include/linux/preempt.h:9,
                 from include/linux/spinlock.h:50,
                 from include/linux/seqlock.h:29,
                 from include/linux/time.h:8,
                 from include/linux/timex.h:56,
                 from include/linux/sched.h:56,
                 from /home/mark/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce/vmware-server-distrib/lib/modules/source/vmmon-only/./include/compat_sched.h:23,
                 from /home/mark/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce/vmware-server-distrib/lib/modules/source/vmmon-only/vmcore/moduleloop.c:31:
/usr/src/linux-headers-2.6.32-31-server/arch/x86/include/asm/msr-index.h:230:1: warning: this is the location of the previous definition
Trying to compile vmci module to see if it works
Performing make in /home/mark/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce/vmware-server-distrib/lib/modules/source/vmci-only
Using 2.6.x kernel build system.
Trying to compile vmnet module to see if it works
Performing make in /home/mark/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce/vmware-server-distrib/lib/modules/source/vmnet-only
Using 2.6.x kernel build system.
/home/mark/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce/vmware-server-distrib/lib/modules/source/vmnet-only/driver.c:121: warning: data definition has no type or storage class
/home/mark/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce/vmware-server-distrib/lib/modules/source/vmnet-only/driver.c:121: warning: type defaults to âintâ in declaration of âDEFINE_SEMAPHOREâ
/home/mark/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce/vmware-server-distrib/lib/modules/source/vmnet-only/driver.c:121: warning: parameter names (without types) in function declaration
/home/mark/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce/vmware-server-distrib/lib/modules/source/vmnet-only/filter.c:82: warning: type defaults to âintâ in declaration of âDEFINE_SEMAPHOREâ
/home/mark/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce/vmware-server-distrib/lib/modules/source/vmnet-only/filter.c:82: warning: parameter names (without types) in function declaration
/home/mark/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce/vmware-server-distrib/lib/modules/source/vmnet-only/filter.c: In function âVNetFilter_HandleUserCallâ:
/home/mark/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce/vmware-server-distrib/lib/modules/source/vmnet-only/filter.c:1089: error: âfilterIoctlSemâ undeclared (first use in this function)
/home/mark/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce/vmware-server-distrib/lib/modules/source/vmnet-only/filter.c:1089: error: (Each undeclared identifier is reported only once
/home/mark/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce/vmware-server-distrib/lib/modules/source/vmnet-only/filter.c:1089: error: for each function it appears in.)
make[2]: *** [/home/mark/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce/vmware-server-distrib/lib/modules/source/vmnet-only/filter.o] Error 1
make[1]: *** [_module_/home/mark/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce/vmware-server-distrib/lib/modules/source/vmnet-only] Error 2
make: *** [vmnet.ko] Error 2
There is a problem compiling the vmnet module after it was patched. :(




---

### Post by fabriciolf on 2011-05-13
Gostaria de agradecer ao amigo sirusdv pelo empenho.

Depois da bateção de cabeça consegui instalar o VMware Server.

Obrigado pelo ótimo trabalho!!

Fabrício L. F.
[email]fabriciolf@gmail.com[/email]

---

### Post by RazorFish1 on 2011-05-14
Is everyone running Remmina to access the VM since the plugin is not working on Firefox 4.x?  Has someone solved how to make the plugin work in Firefox?

---

### Post by BDNiner on 2011-05-15
> **RazorFish1 said:**
> Is everyone running Remmina to access the VM since the plugin is not working on Firefox 4.x?  Has someone solved how to make the plugin work in Firefox?

[I]I have found a solution to that problem online:

In the Firefox address bar, enter "about:config"

Click past the mandatory warning message.

Enter "security.enable_ssl2" into the filter box and change the value from "false" to "true". You can do this by simply double clicking on it.[/I]

Now you should be able to use firefox: For the blog I located the answer you can check here:
[http://tuxnetworks.blogspot.com/2010/03/vmware-server-console-connection-was.html](http://tuxnetworks.blogspot.com/2010/03/vmware-server-console-connection-was.html)

---

### Post by RazorFish1 on 2011-05-19
> **BDNiner said:**
> [I]Now you should be able to use firefox[/url]

I applied this change and the add-on will still not load.  Could it be that I'm running FireFox 4.01 rather than a 3.x version?  Do I need to downgrade FireFox?

---

### Post by mael on 2011-05-23
> **RazorFish1 said:**
> I applied this change and the add-on will still not load.  Could it be that I'm running FireFox 4.01 rather than a 3.x version?  Do I need to downgrade FireFox?

i have the same problem - but i don't even use firefox at all. i ran the vmrc directly from the console before with a special start script (which is circulating everywhere) and now the vmrc isn't starting at all. no message is printed, i cannot get it to work. 
i think it is because of one or more libraries shipped with vmrc which aren't compatible with natty

i really need vmrc at my workplace, the next thing i would do is restore ubuntu 10.10 from a previous system image

thanks for any help!!

here is the output of ldd with the startup script for vmrc:>         linux-gate.so.1 =>  (0xb7817000)
        libX11.so.6 => /usr/lib/i386-linux-gnu/libX11.so.6 (0xb76d8000)
        libXext.so.6 => /usr/lib/i386-linux-gnu/libXext.so.6 (0xb76c8000)
        libXi.so.6 => /usr/lib/i386-linux-gnu/libXi.so.6 (0xb76b9000)
        libstdc++.so.6 => /usr/lib/i386-linux-gnu/libstdc++.so.6 (0xb75ce000)
        libXinerama.so.1 => /usr/lib/i386-linux-gnu/libXinerama.so.1 (0xb75ca000)
        libXau.so.6 => /usr/lib/i386-linux-gnu/libXau.so.6 (0xb75c6000)
        libXcursor.so.1 => /usr/lib/i386-linux-gnu/libXcursor.so.1 (0xb75bb000)
        libXrandr.so.2 => /usr/lib/i386-linux-gnu/libXrandr.so.2 (0xb75b3000)
        libdl.so.2 => /lib/i386-linux-gnu/libdl.so.2 (0xb75af000)
        libm.so.6 => /lib/i386-linux-gnu/libm.so.6 (0xb7589000)
        libpthread.so.0 => /lib/i386-linux-gnu/libpthread.so.0 (0xb7570000)
        librt.so.1 => /lib/i386-linux-gnu/librt.so.1 (0xb7566000)
        libexpat.so.0 => /home/fsc/.mozilla/firefox/hwlt9ck8.fsc neu/extensions/VMwareVMRC@vmware.com/plugins/lib/libexpat.so.0/libexpat.so.0 (0xb7547000)
        libfontconfig.so.1 => /usr/lib/i386-linux-gnu/libfontconfig.so.1 (0xb7518000)
        libfreetype.so.6 => /usr/lib/i386-linux-gnu/libfreetype.so.6 (0xb7492000)
        libXrender.so.1 => /usr/lib/i386-linux-gnu/libXrender.so.1 (0xb7488000)
        libXft.so.2 => /usr/lib/i386-linux-gnu/libXft.so.2 (0xb7473000)
        libglib-2.0.so.0 => /lib/i386-linux-gnu/libglib-2.0.so.0 (0xb739c000)
        libgmodule-2.0.so.0 => /usr/lib/i386-linux-gnu/libgmodule-2.0.so.0 (0xb7398000)
        libgobject-2.0.so.0 => /usr/lib/i386-linux-gnu/libgobject-2.0.so.0 (0xb7351000)
        libgthread-2.0.so.0 => /usr/lib/i386-linux-gnu/libgthread-2.0.so.0 (0xb734c000)
        libatk-1.0.so.0 => /usr/lib/i386-linux-gnu/libatk-1.0.so.0 (0xb732f000)
        libpango-1.0.so.0 => /usr/lib/i386-linux-gnu/libpango-1.0.so.0 (0xb72ef000)
        libpangoft2-1.0.so.0 => /usr/lib/i386-linux-gnu/libpangoft2-1.0.so.0 (0xb72c7000)
        libpangoxft-1.0.so.0 => /usr/lib/i386-linux-gnu/libpangoxft-1.0.so.0 (0xb72bf000)
        libpangox-1.0.so.0 => /usr/lib/i386-linux-gnu/libpangox-1.0.so.0 (0xb72b3000)
        libgdk-x11-2.0.so.0 => /usr/lib/libgdk-x11-2.0.so.0 (0xb7219000)
        libgdk_pixbuf-2.0.so.0 => /usr/lib/libgdk_pixbuf-2.0.so.0 (0xb71fc000)
        libgtk-x11-2.0.so.0 => /usr/lib/libgtk-x11-2.0.so.0 (0xb6e23000)
        libsigc-2.0.so.0 => /usr/lib/libsigc-2.0.so.0 (0xb6e1d000)
        libglibmm-2.4.so.1 => /usr/lib/libglibmm-2.4.so.1 (0xb6dba000)
        libglibmm_generate_extra_defs-2.4.so.1 => /usr/lib/libglibmm_generate_extra_defs-2.4.so.1 (0xb6db3000)
        libatkmm-1.6.so.1 => /usr/lib/libatkmm-1.6.so.1 (0xb6d6f000)                                                                                                                                               
        libpangomm-1.4.so.1 => /usr/lib/libpangomm-1.4.so.1 (0xb6d44000)                                                                                                                                           
        libgdkmm-2.4.so.1 => /usr/lib/libgdkmm-2.4.so.1 (0xb6cf9000)                                                                                                                                               
        libgtkmm-2.4.so.1 => /usr/lib/libgtkmm-2.4.so.1 (0xb699d000)                                                                                                                                               
        libart_lgpl_2.so.2 => /usr/lib/libart_lgpl_2.so.2 (0xb6985000)                                                                                                                                             
        libxml2.so.2 => /usr/lib/libxml2.so.2 (0xb685c000)                                                                                                                                                         
        librsvg-2.so.2 => /usr/lib/librsvg-2.so.2 (0xb682b000)                                                                                                                                                     
        libsexymm.so.2 => /home/fsc/.mozilla/firefox/hwlt9ck8.fsc neu/extensions/VMwareVMRC@vmware.com/plugins/lib/libsexymm.so.2/libsexymm.so.2 (0xb6813000)                                                      
        libsexy.so.2 => /usr/lib/libsexy.so.2 (0xb6803000)                                                                                                                                                         
        libview.so.2 => /home/fsc/.mozilla/firefox/hwlt9ck8.fsc neu/extensions/VMwareVMRC@vmware.com/plugins/lib/libview.so.2/libview.so.2 (0xb67a9000)                                                            
        libz.so.1 => /lib/i386-linux-gnu/libz.so.1 (0xb6794000)                                                                                                                                                    
        libXdmcp.so.6 => /usr/lib/i386-linux-gnu/libXdmcp.so.6 (0xb678e000)                                                                                                                                        
        libXfixes.so.3 => /usr/lib/i386-linux-gnu/libXfixes.so.3 (0xb6788000)                                                                                                                                      
        libpangocairo-1.0.so.0 => /usr/lib/i386-linux-gnu/libpangocairo-1.0.so.0 (0xb677c000)                                                                                                                      
        libcairo.so.2 => /usr/lib/libcairo.so.2 (0xb66c8000)                                                                                                                                                       
        libcairomm-1.0.so.1 => /usr/lib/libcairomm-1.0.so.1 (0xb66a4000)                                                                                                                                           
        libpng12.so.0 => /lib/i386-linux-gnu/libpng12.so.0 (0xb667f000)                                                                                                                                            
        libvmwarebase.so.0 => /home/fsc/.mozilla/firefox/hwlt9ck8.fsc neu/extensions/VMwareVMRC@vmware.com/plugins/lib/libvmwarebase.so.0/libvmwarebase.so.0 (0xb5f7d000)                                          
        libvmwareui.so.0 => /home/fsc/.mozilla/firefox/hwlt9ck8.fsc neu/extensions/VMwareVMRC@vmware.com/plugins/lib/libvmwareui.so.0/libvmwareui.so.0 (0xb534f000)                                                
        libgvmomi.so.0 => /home/fsc/.mozilla/firefox/hwlt9ck8.fsc neu/extensions/VMwareVMRC@vmware.com/plugins/lib/libgvmomi.so.0/libgvmomi.so.0 (0xb4fd2000)
        libgcc_s.so.1 => /lib/i386-linux-gnu/libgcc_s.so.1 (0xb4fb6000)                                                                                                                                            
        libc.so.6 => /lib/i386-linux-gnu/libc.so.6 (0xb4e55000)
        /lib/ld-linux.so.2 (0xb7818000)
        libxcb.so.1 => /usr/lib/i386-linux-gnu/libxcb.so.1 (0xb4e3c000)
        libexpat.so.1 => /lib/i386-linux-gnu/libexpat.so.1 (0xb4e12000)
        libpcre.so.3 => /lib/i386-linux-gnu/libpcre.so.3 (0xb4dd2000)
        libgio-2.0.so.0 => /usr/lib/i386-linux-gnu/libgio-2.0.so.0 (0xb4ccf000)
        libXcomposite.so.1 => /usr/lib/i386-linux-gnu/libXcomposite.so.1 (0xb4ccb000)
        libXdamage.so.1 => /usr/lib/i386-linux-gnu/libXdamage.so.1 (0xb4cc7000)
        libgiomm-2.4.so.1 => /usr/lib/libgiomm-2.4.so.1 (0xb4bda000)
        libcroco-0.6.so.3 => /usr/lib/libcroco-0.6.so.3 (0xb4ba6000)
        libpixman-1.so.0 => /usr/lib/libpixman-1.so.0 (0xb4b39000)
        libxcb-shm.so.0 => /usr/lib/i386-linux-gnu/libxcb-shm.so.0 (0xb4b35000)
        libxcb-render.so.0 => /usr/lib/i386-linux-gnu/libxcb-render.so.0 (0xb4b2d000)
        libcurl.so.4 => /usr/lib/libcurl.so.4 (0xb4ada000)
        libresolv.so.2 => /lib/i386-linux-gnu/libresolv.so.2 (0xb4ac4000)
        libselinux.so.1 => /lib/i386-linux-gnu/libselinux.so.1 (0xb4aa9000)
        libidn.so.11 => /usr/lib/libidn.so.11 (0xb4a77000)
        liblber-2.4.so.2 => /usr/lib/liblber-2.4.so.2 (0xb4a6a000)
        libldap_r-2.4.so.2 => /usr/lib/libldap_r-2.4.so.2 (0xb4a25000)
        libgssapi_krb5.so.2 => /usr/lib/i386-linux-gnu/libgssapi_krb5.so.2 (0xb49f4000)
        libssl.so.0.9.8 => /lib/libssl.so.0.9.8 (0xb49ac000)
        libcrypto.so.0.9.8 => /lib/libcrypto.so.0.9.8 (0xb4860000)
        libsasl2.so.2 => /usr/lib/libsasl2.so.2 (0xb4849000)
        libgnutls.so.26 => /usr/lib/i386-linux-gnu/libgnutls.so.26 (0xb47b3000)
        libgcrypt.so.11 => /lib/i386-linux-gnu/libgcrypt.so.11 (0xb473e000)
        libkrb5.so.3 => /usr/lib/i386-linux-gnu/libkrb5.so.3 (0xb4690000)
        libk5crypto.so.3 => /usr/lib/i386-linux-gnu/libk5crypto.so.3 (0xb466c000)
        libcom_err.so.2 => /lib/i386-linux-gnu/libcom_err.so.2 (0xb4668000)
        libkrb5support.so.0 => /usr/lib/i386-linux-gnu/libkrb5support.so.0 (0xb4660000)
        libkeyutils.so.1 => /lib/i386-linux-gnu/libkeyutils.so.1 (0xb465b000)
        libtasn1.so.3 => /usr/lib/i386-linux-gnu/libtasn1.so.3 (0xb464a000)
        libgpg-error.so.0 => /lib/i386-linux-gnu/libgpg-error.so.0 (0xb4645000)


---

### Post by f17th on 2011-05-24
Hiya

I managed to get VMWare Server 2 Installed on my copy of Ubuntu 11.04. 
I ran into a load of problems with it not working with Firefox 4 and I don't exactly get on with the web interface. 

How would I go about uninstalling this from my system ?

Also is is possible to install VM Server 1.10 on Ubuntu 11.04 ?

Thanks very much 
Gav

---

### Post by jarednevans on 2011-05-26
Hi,

This isn't clear.  What's the command to apply the patch file and where exactly?

---

### Post by jarednevans on 2011-05-26
OK, I figured it out: 

put vmware-server-2.0.2-203138-update.patch in the raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce directory

then run

vmware-server-2.0.x-kernel-2.6.3x-install.sh

---

### Post by jarednevans on 2011-05-26
.

---

### Post by f17th on 2011-05-27
Anyone have any ideas on how to uninstall from my system ?

After downgrading to firefox 3 with foxtester it won't launch any of the console screens. Reports that it has taken too long for the request hence VM Server 2 is unusable for me.

Is there another method I can try or a fix for this ?

Either that or I wish to uninstall and get VM Server 1 installed and working as that at least comes with a integrated management console.

Thanks 
Gav

---

### Post by jarednevans on 2011-05-27
I've not been able to get the "true" VMware console to the virtual machines working in the latest Ubuntu/Firefox release.

But, there's an alternative to the VMware console: You can use vinagre to VNC into the virtual machines after they are started.  You'll need to add two lines at the end of VM's .vmx file then restart the VM:

RemoteDisplay.vnc.enabled = "TRUE"
RemoteDisplay.vnc.port = "5900"

However, I need the "true" VMware console to the VM I'm running due to a video conferencing software using a webcam, and the VNC approach doesn't refresh fast enough for a smooth video experience.  

I've removed VMware Server 2 from my Ubuntu desktop and replaced it with VMware Player which allows you to create and run a VM.  This is acceptable for me since I only need to run one VM at a time.

Hope this will help out!

---

### Post by f17th on 2011-05-29
How did you uninstall VM Ware server 2?

Sorry I've only started using ubuntu, and not sure how to uninstall after using that script.

Any help will be much appreciated

Gav

---

### Post by jarednevans on 2011-05-31
run /usr/bin/vmware-uninstall with super-user privs.

---

### Post by yandrak08 on 2011-06-01
Hi I'm new here. And I have a problem installing VMWare 2.0.1 on my Ubuntu 11.04 The problem is this step:

What is the directory location of C header files that match the performance
kernel? [/ usr / src / linux / include]

The path "/ usr / src / linux / include" is not an existing directory.

I installed this:
$ sudo apt-get install build-essential linux-headers-`uname-r`

I also tried what it says sirusdv, but it gives this error:

There is no file containing the VMware Server Indicated happened!

What I can do?

---

### Post by kgb_hc on 2011-06-02
Edit:
Disregard this post, I will start my own thread for it. Sorry for unnecessarily bumping it. 


Hi,
I have been trying to install VMware server for a few days now, following various guides and using different patching solutions. But no matter what I try, I always get some error message at the end. Right now I get the error message described below.

I'm using the latest Ubuntu server LTS, 10.04.2, with Kernel 2.6.32-31-generic on x86_64. Trying to install VMWare server 2.0.2-203138. 

```
You have VMware Server archive:
        VMware-server-2.0.2-203138.x86_64.tar.gz
Checking for needed packages on Ubuntu
You do have the linux-headers-2.6.32-31-generic package...
You do have the build-essential package...
You do have the patch package...
Extracting the contents of VMware-server-2.0.2-203138.x86_64.tar.gz
Found .tar file for vmci module
Found .tar file for vmnet module
Found .tar file for vmmon module
Found .tar file for vsock module
Extracting .tar files in order to apply the patch...
Untarring /home/vm/vmware_server_package//vmware-server-distrib/lib/modules/source/vmci.tar
Untarring /home/vm/vmware_server_package//vmware-server-distrib/lib/modules/source/vmnet.tar
Untarring /home/vm/vmware_server_package//vmware-server-distrib/lib/modules/source/vmmon.tar
Untarring /home/vm/vmware_server_package//vmware-server-distrib/lib/modules/source/vsock.tar
Testing patch...
Creating some simlinks for the newer kernels...
ln: creating symbolic link `/usr/src/linux-headers-2.6.32-31-generic/include/linux/autoconf.h': File exists
ln: creating symbolic link `/usr/src/linux-headers-2.6.32-31-generic/include/linux/utsrelease.h': File exists
Applying patch...
Preparing new tar file for vmci module
Preparing new tar file for vmnet module
Preparing new tar file for vmmon module
Preparing new tar file for vsock module
Checking that the compiling will succeed...
Trying to compile vmci module to see if it works
Performing make in /home/vm/vmware_server_package//vmware-server-distrib/lib/modules/source/vmci-only
Using 2.6.x kernel build system.
Trying to compile vmnet module to see if it works
Performing make in /home/vm/vmware_server_package//vmware-server-distrib/lib/modules/source/vmnet-only
Using 2.6.x kernel build system.
/home/vm/vmware_server_package/vmware-server-distrib/lib/modules/source/vmnet-only/driver.c:121: warning: data definition has no type or storage class
/home/vm/vmware_server_package/vmware-server-distrib/lib/modules/source/vmnet-only/driver.c:121: warning: type defaults to âintâ in declaration of âDEFINE_SEMAPHOREâ
/home/vm/vmware_server_package/vmware-server-distrib/lib/modules/source/vmnet-only/driver.c:121: warning: parameter names (without types) in function declaration
/home/vm/vmware_server_package/vmware-server-distrib/lib/modules/source/vmnet-only/filter.c:82: warning: type defaults to âintâ in declaration of âDEFINE_SEMAPHOREâ
/home/vm/vmware_server_package/vmware-server-distrib/lib/modules/source/vmnet-only/filter.c:82: warning: parameter names (without types) in function declaration
/home/vm/vmware_server_package/vmware-server-distrib/lib/modules/source/vmnet-only/filter.c: In function âVNetFilter_HandleUserCallâ:
/home/vm/vmware_server_package/vmware-server-distrib/lib/modules/source/vmnet-only/filter.c:1089: error: âfilterIoctlSemâ undeclared (first use in this function)
/home/vm/vmware_server_package/vmware-server-distrib/lib/modules/source/vmnet-only/filter.c:1089: error: (Each undeclared identifier is reported only once
/home/vm/vmware_server_package/vmware-server-distrib/lib/modules/source/vmnet-only/filter.c:1089: error: for each function it appears in.)
make[2]: *** [/home/vm/vmware_server_package/vmware-server-distrib/lib/modules/source/vmnet-only/filter.o] Error 1
make[1]: *** [_module_/home/vm/vmware_server_package/vmware-server-distrib/lib/modules/source/vmnet-only] Error 2
make: *** [vmnet.ko] Error 2
There is a problem compiling the vmnet module after it was patched. :(
```I'm using the same script and patch as this guy did:


> **karhukuoma said:**
> I'm using raducotescu-vmware-server-linux-2.6.3x-kernel-f271f27.tar.gz with updated vmware-server-2.0.2-203138-update.patch from this thread. What could I've missed?

**Update**
##########
This has been fixed like this:
```

sudo su -
goto /usr/src/linux-headers-2.6.38-9-generic/include/linux
cat ../generated/utsrelease.h >> version.h
ln -s ../generated/autoconf.h

```kudos to [thingy@vmware-communities]("http://communities.vmware.com/message/1684660#1684660")

Also, a lot of guides tell me to use files in the  /usr/src/linux-headers-2.6.32-31-generic/generated/ directory but I  don't have that directory at all. 

Anyone have any ideas?

Thanks in advance!

---

### Post by rjvdhiman on 2011-06-02
Hi,

I downloaded the patch and overwrite with the existing one. then I executed the .sh script but It gives  me an error in compiling the vmnet module and it stops.

I am attaching a text file showing the output. 

your help will be highly appreciable.

thanks.

---

### Post by aznnico on 2011-06-15
*bump* I have the exact same problem with vmnet module failing :( on kernel 2.6.32-28-server and vmware server 2.0.2

---

### Post by f17th on 2011-06-15
Has anyone got a solution to controlling the Guest OS's from Ubuntu ?

I tried an older version of Firefox but that doesn't seem to work either. I can power on machines, create etc. However when trying to remote control them with the console tab nothing happens.

Can anyone advise ?

Thanks

---

### Post by bonuswhore on 2011-06-27
thanks for this script, I was able to get vmware and its kernel modules installed.

However, after it completes installation  I ran 'vmware' from a terminal, and it launched my browser (firefox 5)  at a localhost:8333/ui  

however this just brings up a blank page, or a failure.   Is it because vmware doesn't like firefox 5?   How else can I access vmware, do I need to install an alternate browser (any suggestions?)

also, is it possible to install vmware-server 1.x on ubuntu 11.04?   I really dislike the web-based interface of vmware server 2, I've always preferred vmware server 1.x which has its own dedicated console app.  I tried installing but the kernel modules failed to compile.  Is there a patch for vmware server 1.x?

also I have a few dozen virtual machines I'm trying to access from ubuntu and they are all machines I built and used on windows using vmware server 1.x, I'm not completely sure I'll be able to run them with vmware server 2.x and still be able to run them on my dual-boot windows 7 vmware 1.x in the future

---

### Post by mael on 2011-06-27
i'm switching over to ESXi now... there is no future in the vmware server products

but you need a windows-VM to run the vSphere client to manage it :(

---

### Post by f17th on 2011-06-28
This is exactly my problem with VM Ware server 2, I can't get it to launch any of the console sessions as the plugin isn't working.

I've tried using Firefox 3.5 as well!
Has anyone got another suggestion?

I have tried to compile VM Server 1 on Ubuntu 11.04 but have had no success as it fails on compiling the Vmon modules.

I am about to give up and use Virtual Box but this means rebuilding my images as the Virtual Hyper-visors are incompatible :(

---

### Post by bonuswhore on 2011-06-30
> **f17th said:**
> This is exactly my problem with VM Ware server 2, I can't get it to launch any of the console sessions as the plugin isn't working.

I've tried using Firefox 3.5 as well!
Has anyone got another suggestion?

I have tried to compile VM Server 1 on Ubuntu 11.04 but have had no success as it fails on compiling the Vmon modules.

I am about to give up and use Virtual Box but this means rebuilding my images as the Virtual Hyper-visors are incompatible :(


maybe try chrome or some other browser?  I'm guessing it only wants to work on IE, which is obviously a problem here.  maybe you can connect to it from another machine on the network with IE?

personally I gave up and have migrated to virtualbox, as I found it would boot my existing windows virtual machines just fine after I enabled IO Apic in the vm settings

---

### Post by tokyo-joe on 2011-07-05
The patch file includes "vmware-server-2.0.2-203138-update.patch". How can I put this patch on the installation package?
Which specific file should be replaced with the patch?

I'm fairly new to this kind of work.

---

### Post by adbydesigns on 2011-07-10
All hateto ask  i am new to all of this and i need to run the update patch to get my vmware server running i think i did the wget ok and i can seethe files when i do a ls but where do i go from there how do i unconpress them ect

thanks in advanse

---

### Post by LJAzarcon on 2011-07-15
Issues with connection reset in Firefox or page wont load, this worked for me.

Well, it appears that with Firefox 3.5 a new problem has emerged. When  you try and connect to the VMware Server console you get an error  complaining that "the connection was reset" and suggesting that the site  may be down.

To fix this, you need to modify a setting in Firefox.

In the address bar, enter "about:config"

Click past the mandatory warning message.

Enter  "security.enable_ssl2" into the filter box and change the value from  "false" to "true". You can do this by simply clicking on it.

Now your vmware console should be back to normal. 

[http://tuxnetworks.blogspot.com/2010/03/vmware-server-console-connection-was.html](http://tuxnetworks.blogspot.com/2010/03/vmware-server-console-connection-was.html)

---

### Post by toddkaufmann on 2011-07-21
"I've seen some conflicting instructions here, but this is what worked for me. 
I have the 11.04 Server, did an update to get the latest kernel and updates, and rebooted so I now have: 
2.6.38-10-server #46-Ubuntu SMP Tue Jun 28 16:31:00 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux 

I may have added some extra packages (like kernel sources) in initial attempts to get this working, but I think the raducotescu script handles getting the packages you need. 

1. Get VMware-server-2.0.2-203138.x86_64.tar.gz from the VMware site, register for free license key(s) etc. 
2. At [https://github.com/raducotescu/vmware-server-linux-2.6.3x-kernel/tree/release-1.6](https://github.com/raducotescu/vmware-server-linux-2.6.3x-kernel/tree/release-1.6) there is a 'Downloads' button near the top; click it to get a popup that will let you select a tar.gz or zip file and download (the choice is yours). Put it in the same directory. 
3. Unpack the archive; for example, 
unzip raducotescu-vmware-server-linux-2.6.3x-kernel-release-1.6-0-gbb26dce.zip 
4. Run the script: 
./raducotescu-vmware-server-linux-2.6.3x-kernel-e26b34e/vmware-server-2.0.x-kernel-2.6.3x-install.sh 

This takes care of unpacking the VMware archive, patching scripts, other pre-requisites as well (I think), and starts up the installer. 

From here, it was just Enter, Enter, Enter, ... the whole way, and everything built without a problem. "

---

### Post by f17th on 2011-07-21
What have you done in regards to controlling the VM Guest OS's

I had it all working but couldn't control the Guests from my Ubuntu machine so have pretty much given up and gone across to VirtualBox.

I am still interested to see if anyone can get it working with the Firefox plugin. (Maybe its just me that it doesn't work with)

---

### Post by toddkaufmann on 2011-07-24
re: control by firefox plugin--
I encountered this problem later..  I am accessing the VMware Server install on the 11.04 host remotely via ssh, and tunneling port 8222 through that to get to the VMware web interface.  I couldn't install the plugin locally, because I'm running OS X.

I set up a VNC desktop on the Ubuntu server, but it had Firefox 5, which is not supported.  So I downloaded 3.6.x from mozilla.org, and installed it in another directory, but I couldn't get that to run...  "firefox-bin not found" when it was in the current directory and on my PATH.  Same problem with the executable when downloading and unzip'ing the xpi from the VMware server.

I didn't have more time to mess with this, so I just fired up my Windows 7 virtual machine running locally on my Macbook, and tunneled 902 (the VMware console connection) over ssh(*) to the server, and accessed it using IE8.
Not  ideal, but it works.


(*) I may try changing the port number to something non-privileged so I don't have to run this tunnel as root.

---

### Post by sd33t on 2011-07-31
I finally got Ubuntu 10.04 running as a guest on VMware Server 2.0.2, Linux Mint 11 Host OS.

The 3.5x version of firefox can still be downloaded from some secret place on Mozilla.org
 [http://www.mozilla.com/en-US/products/download.html?product=firefox-3.5.9&os=linux&#9001;=en-US]("http://www.mozilla.com/en-US/products/download.html?product=firefox-3.5.9&os=linux&lang=en-US")
Running multiple versions of firefox is superbly accomplished by installing this add-on to your current firefox version ~
 [http://www.webgapps.org/add-ons/foxtester](http://www.webgapps.org/add-ons/foxtester)

I could not succeed in accessing the console to install the OS in any of the various other ways described in various places.  Of course once you get networking started then you no longer need it much, can ssh.

I had the most trouble installing the VMware tools on the guest.  Not sure why.  I finally reinstalled the guest Ubuntu (goes very fast from iso image) and had no problems the second time around using the "Installing from host Ubuntu" recipe at the bottom of this page - [https://help.ubuntu.com/community/VMware/Tools](https://help.ubuntu.com/community/VMware/Tools)
I can't recall if it differs at all from the VMware instructions in the VMwave doc
 VMware Tools Installation Guide For Operating System Specific Packages (avail at:)
[http://www.google.com/url?sa=t&source=web&cd=1&sqi=2&ved=0CBUQFjAA&url=http%3A%2F%2Fwww.vmware.com%2Fpdf%2Fosp_install_guide.pdf&rct=j&q=VMware%20Tools%20Installation%20Guide%20For%20Operating%20System%20Specific%20Packages&ei=3741TqGbEYP30gHfhbWJDA&usg=AFQjCNHONN3oGw-k7rUa7ChE_vMqYUIpog&cad=rja](http://www.google.com/url?sa=t&source=web&cd=1&sqi=2&ved=0CBUQFjAA&url=http%3A%2F%2Fwww.vmware.com%2Fpdf%2Fosp_install_guide.pdf&rct=j&q=VMware%20Tools%20Installation%20Guide%20For%20Operating%20System%20Specific%20Packages&ei=3741TqGbEYP30gHfhbWJDA&usg=AFQjCNHONN3oGw-k7rUa7ChE_vMqYUIpog&cad=rja)

Thanks to all those who have contributed to the scripts and posted them!

-SD

---

### Post by 41niteonly on 2011-08-05
Edit: It appears to me that raducotescu has updated his patch and this threads patch is the same.

Can this patch be placed outside the ubuntuforums.org login ringwall?

It would be so much easier to wget it directly onto a server.

---

### Post by pmorrone on 2011-08-08
> **toddkaufmann said:**
> "I've seen some conflicting instructions here, but this is what worked for me. 
I have the 11.04 Server, did an update to get the latest kernel and updates, and rebooted so I now have: 
2.6.38-10-server #46-Ubuntu SMP Tue Jun 28 16:31:00 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux 

I may have added some extra packages (like kernel sources) in initial attempts to get this working, but I think the raducotescu script handles getting the packages you need. 

1. Get VMware-server-2.0.2-203138.x86_64.tar.gz from the VMware site, register for free license key(s) etc. 
2. At [https://github.com/raducotescu/vmware-server-linux-2.6.3x-kernel/tree/release-1.6](https://github.com/raducotescu/vmware-server-linux-2.6.3x-kernel/tree/release-1.6) there is a 'Downloads' button near the top; click it to get a popup that will let you select a tar.gz or zip file and download (the choice is yours). Put it in the same directory. 
3. Unpack the archive; for example, 
unzip raducotescu-vmware-server-linux-2.6.3x-kernel-release-1.6-0-gbb26dce.zip 
4. Run the script: 
./raducotescu-vmware-server-linux-2.6.3x-kernel-e26b34e/vmware-server-2.0.x-kernel-2.6.3x-install.sh 

This takes care of unpacking the VMware archive, patching scripts, other pre-requisites as well (I think), and starts up the installer. 

From here, it was just Enter, Enter, Enter, ... the whole way, and everything built without a problem. "

Thank you much for putting together this solution.  I tried to run the script as you have outlined but I am running into a problem.  I download the VMware Server 2 file from the VMware website and the release file from your link above.  I am able to extract the files from the release file, however, when I run the script in the terminal I receive the following error message:

phil@ubuntu:~$ ./Downloads/raducotescu-vmware-server-linux-2.6.3x-kernel-e26b34e/vmware-server-2.0.x-kernel-2.6.3x-install.sh
This script must be run as root!
phil@ubuntu:~$ sudo ./Downloads/raducotescu-vmware-server-linux-2.6.3x-kernel-e26b34e/vmware-server-2.0.x-kernel-2.6.3x-install.sh
[sudo] password for phil: 
There is no archive containing VMware Server in the path you indicated!

I also took a screenshot of the directory where the compressed files are saved under.  Do you know what I may be doing wrong?

---

### Post by dpkubu on 2011-08-14
Thanks for the directions I got the vm-server running but Now I cannot access internet, I am still a new user please help

---

### Post by dpkubu on 2011-08-14
Thanks for the directions I got the vm-server running but Now I cannot access internet, I am still a new user please help

```
 
@tornado:~$ifconfig -a
eth0      Link encap:Ethernet  HWaddr e0:69:95:d2:1c:81
          inet addr:192.168.0.96  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::e269:95ff:fed2:1c81/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1629 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1764 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:419339 (419.3 KB)  TX bytes:1184336 (1.1 MB)
          Interrupt:20 Memory:fe400000-fe420000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5018 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5018 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:3643311 (3.6 MB)  TX bytes:3643311 (3.6 MB)

vmnet1    Link encap:AMPR NET/ROM  HWaddr
          inet addr:172.16.243.1  Mask:255.255.255.0
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet8    Link encap:AMPR NET/ROM  HWaddr
          inet addr:172.16.121.1  Mask:255.255.255.0
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

@tornado:~$ ping yahoo.com
ping: unknown host yahoo.com

```

---

### Post by Thegmandrive on 2011-08-14
> **darnelali said:**
> This is what I did, hope it helps!

root login

cd /usr/src
mkdir vmware
cd vmware
Download VMWARE SERVER 2.0.2
wget [http://ubuntuforums.org/attachment.php?attachmentid=190878&d=1304365853](http://ubuntuforums.org/attachment.php?attachmentid=190878&d=1304365853)
gunzip vmware-server-2.0.2-203138-update.patch.gz
wget [http://ubuntuforums.org/attachment.php?attachmentid=94477&d=1227872015](http://ubuntuforums.org/attachment.php?attachmentid=94477&d=1227872015)
tar zxf raducotescu-vmware-server-linux-2.6.3x-kernel-release-1.6-0-gbb26dce.tar.gz
mv VMware-server-2.0.2-203138.i386.tar.gz raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce
mv vmware-server-2.0.2-203138-update.patch raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce
cd raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce
./vmware-server-2.0.x-kernel-2.6.3x-install.sh


I followed this process, almost exactly, and it installed great on the latest 11.04 natty with the latest updates. As of 08/14/2011.

I tried installing vmware on 10.04 and couldn't get it to work :) glad it worked on Natty!!

Thanks gents.

---

### Post by one9one on 2011-08-30
> **Thegmandrive said:**
> I followed this process, almost exactly, and it installed great on the latest 11.04 natty with the latest updates. As of 08/14/2011.

I tried installing vmware on 10.04 and couldn't get it to work :) glad it worked on Natty!!

Thanks gents.


I also failed to install 10.04 Server 64 bit + VMware, but was successful with 11.04 Server 64 bit + VMware, due to the help given in this thread.  THANK YOU!!!!

I used [http://192.168.1.120:8222](http://192.168.1.120:8222) (my server's local static IP address) in Internet Explorer 8 to connect.  The other methods didn't seem to work.  ** EDIT ** Using the IP address : 8222 does start up in firefox 5.5 and 6, but some screens within the app. are blank, making firefox unusable at the moment.

You may want to change the root password when you are configuring your server.  I had to use the user root and the root password to log into the system the first time.

---

### Post by theprogrammer12 on 2011-09-11
When I try to run the script I get the following error:
```
In file included from include/linux/gfp.h:4:0,
                 from include/linux/kmod.h:22,
                 from include/linux/module.h:13,
                 from include/linux/miscdevice.h:3,
                 from /home/florian/Downloads/vmware/vmware-server-distrib/lib/modules/source/vmci-only/linux/driver.c:26:
include/linux/mmzone.h:1056:19: error: expected identifier or ‘(’ before ‘unsigned’
include/linux/mmzone.h:1056:19: error: expected ‘)’ before ‘<’ token
include/linux/mmzone.h:1076:0: warning: "pfn_to_nid" redefined
include/linux/mmzone.h:928:0: note: this is the location of the previous definition
make[2]: *** [/home/florian/Downloads/vmware/vmware-server-distrib/lib/modules/source/vmci-only/linux/driver.o] Fehler 1
make[1]: *** [_module_/home/florian/Downloads/vmware/vmware-server-distrib/lib/modules/source/vmci-only] Fehler 2
make: *** [vmci.ko] Fehler 2
There is a problem compiling the vmci module after it was patched. :(

```

---

### Post by halovivek on 2011-09-13
Hi 
I have successfully installed the Vmware server in ubuntu 11.04.
I could not able to install the windows.
I do have the ISO image stored in a separate partition.
I have given the file path location, and error message comes file not found.
I could not able to map it to use the image for installation.
can you please help me ?

---

### Post by chrisd. on 2011-09-16
i've been running into similar problems in 10.04 64 bit OS


root@ram:/home/chrisd/vmsrv/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce# ./vmware-server-2.0.x-kernel-2.6.3x-install.sh
You have VMware Server archive: 
	VMware-server-2.0.2-203138.x86_64.tar.gz
Checking for needed packages on Ubuntu
You do have the linux-headers-2.6.39.4 package...
You do have the build-essential package...
You do have the patch package...
Found .tar file for vmmon-temp module
Found .tar file for vmci-temp module
Found .tar file for vsock-temp module
Found .tar file for vsock module
Found .tar file for vmci module
Found .tar file for vmmon module
Found .tar file for vmnet module
Found .tar file for vmnet-temp module
Extracting .tar files in order to apply the patch...
Untarring /home/chrisd/vmsrv/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce/vmware-server-distrib/lib/modules/source/vmmon-temp.tar
vmmon-temp.tar tarball failed to extract in the directory vmmon-temp-only. :(

---

### Post by Kamzi on 2011-10-18
> **theprogrammer12 said:**
> When I try to run the script I get the following error:
```
In file included from include/linux/gfp.h:4:0,
                 from include/linux/kmod.h:22,
                 from include/linux/module.h:13,
                 from include/linux/miscdevice.h:3,
                 from /home/florian/Downloads/vmware/vmware-server-distrib/lib/modules/source/vmci-only/linux/driver.c:26:
include/linux/mmzone.h:1056:19: error: expected identifier or ‘(’ before ‘unsigned’
include/linux/mmzone.h:1056:19: error: expected ‘)’ before ‘<’ token
include/linux/mmzone.h:1076:0: warning: "pfn_to_nid" redefined
include/linux/mmzone.h:928:0: note: this is the location of the previous definition
make[2]: *** [/home/florian/Downloads/vmware/vmware-server-distrib/lib/modules/source/vmci-only/linux/driver.o] Fehler 1
make[1]: *** [_module_/home/florian/Downloads/vmware/vmware-server-distrib/lib/modules/source/vmci-only] Fehler 2
make: *** [vmci.ko] Fehler 2
There is a problem compiling the vmci module after it was patched. :(

```



I got same error, is there any solution available? :(

---

### Post by *cyber-charon* on 2011-10-24
Hey sirusdv!

I am quiet a noob and I like to thank you a lot for sharing your script! Very useful. And I guess it was a lot of work. Also I like to thank the other posters for sharing some more or less useful info.

So here's my mustard to the topic: 

raduco* 's script works perfectly for my system which is Ubuntu 11.04 64bit with all recent updates.  

I didn't use the attachment presented in this forum it, still installation works perfectly.

The contents of the raduco*.tar presented on: [https://help.ubuntu.com/community/VMware/Server](https://help.ubuntu.com/community/VMware/Server)  need to be in the same folder as your VMWare-Server-*.tar.gz in my case: VMware-server-2.0.2-203138.x86_64.tar.gz  

I think it's needed to have xinetd or a equal service installed BEFORE you start the installation. 
Also I used the following instructions I took from 
[http://blog.dixo.net/2006/06/05/installing-vmware-server-beta-on-ubuntu-606-dapper-drake/:](http://blog.dixo.net/2006/06/05/installing-vmware-server-beta-on-ubuntu-606-dapper-drake/:) 
I did so because I once had problems with the installer finding the kernel-headers (the *.h files, I think)

> sudo apt-get install build-essential
 The install wants inetd or xinetd, I went with xinetd…
 sudo apt-get install xinetd 
 Now get your kernel version with uname 
 uname -a
Linux hostname 2.6.15-23-server ...

Use that info to fetch the kernel headers you need
 sudo apt-get install linux-headers-2.6.15-23-server
 I found it useful to go and symlink the headers to the place the VMWare installer expects to find them
 cd /usr/src/
sudo ln -s linux-headers-2.6.15-23-server linux
So after that part I just continued the normal instructions given in raduco*.tar/README and VMServer is running:


```

/etc/init.d/vmware status
Bridged networking on /dev/vmnet0 is running
Host network detection is not running
Host-only networking on /dev/vmnet1 is running
DHCP server on /dev/vmnet1 is not running
Host-only networking on /dev/vmnet8 is running
DHCP server on /dev/vmnet8 is not running
NAT networking on /dev/vmnet8 is running
Module vmmon loaded
Module vmnet loaded

```So I hope this additions can help some of you a bit to get VMware-server running on a system like mine.

Greets,

*cyber-charon*

-----------------------------------------------------------------------
Bin ich schon drin?

---

### Post by casenvi on 2011-10-28
hello,

 I am trying to insBuilding the vmmon module.

Using 2.6.x kernel build system.
make: Entrando no diretório `/tmp/vmware-config2/vmmon-only'
make -C /lib/modules/3.0.0-12-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entrando no diretório `/usr/src/linux-headers-3.0.0-12-generic'
  CC [M]  /tmp/vmware-config2/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config2/vmmon-only/linux/driver.c:31:0:
/tmp/vmware-config2/vmmon-only/./include/compat_wait.h:78:13: erro: conflicting types for ‘poll_initwait’
include/linux/poll.h:72:13: nota: previous declaration of ‘poll_initwait’ was here
/tmp/vmware-config2/vmmon-only/linux/driver.c:39:28: erro fatal: linux/smp_lock.h: Arquivo ou diretório não encontrado
compilação terminada.
make[2]: ** [/tmp/vmware-config2/vmmon-only/linux/driver.o] Erro 1
make[1]: ** [_module_/tmp/vmware-config2/vmmon-only] Erro 2
make[1]: Saindo do diretório `/usr/src/linux-headers-3.0.0-12-generic'
make: ** [vmmon.ko] Erro 2
make: Saindo do diretório `/tmp/vmware-config2/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/go/unsup-linux-products" and 
"http://www.vmware.com/go/unsup-linux-tools".

Execution aborted.
tall ubuntu VMServer in 11.10, but stopped in the code below. I can not move, someone has a tip?

---

### Post by tmedtcom on 2011-12-17
> **kgb_hc said:**
> Edit:
Disregard this post, I will start my own thread for it. Sorry for unnecessarily bumping it. 


Hi,
I have been trying to install VMware server for a few days now, following various guides and using different patching solutions. But no matter what I try, I always get some error message at the end. Right now I get the error message described below.

I'm using the latest Ubuntu server LTS, 10.04.2, with Kernel 2.6.32-31-generic on x86_64. Trying to install VMWare server 2.0.2-203138. 

```
You have VMware Server archive:
        VMware-server-2.0.2-203138.x86_64.tar.gz
Checking for needed packages on Ubuntu
You do have the linux-headers-2.6.32-31-generic package...
You do have the build-essential package...
You do have the patch package...
Extracting the contents of VMware-server-2.0.2-203138.x86_64.tar.gz
Found .tar file for vmci module
Found .tar file for vmnet module
Found .tar file for vmmon module
Found .tar file for vsock module
Extracting .tar files in order to apply the patch...
Untarring /home/vm/vmware_server_package//vmware-server-distrib/lib/modules/source/vmci.tar
Untarring /home/vm/vmware_server_package//vmware-server-distrib/lib/modules/source/vmnet.tar
Untarring /home/vm/vmware_server_package//vmware-server-distrib/lib/modules/source/vmmon.tar
Untarring /home/vm/vmware_server_package//vmware-server-distrib/lib/modules/source/vsock.tar
Testing patch...
Creating some simlinks for the newer kernels...
ln: creating symbolic link `/usr/src/linux-headers-2.6.32-31-generic/include/linux/autoconf.h': File exists
ln: creating symbolic link `/usr/src/linux-headers-2.6.32-31-generic/include/linux/utsrelease.h': File exists
Applying patch...
Preparing new tar file for vmci module
Preparing new tar file for vmnet module
Preparing new tar file for vmmon module
Preparing new tar file for vsock module
Checking that the compiling will succeed...
Trying to compile vmci module to see if it works
Performing make in /home/vm/vmware_server_package//vmware-server-distrib/lib/modules/source/vmci-only
Using 2.6.x kernel build system.
Trying to compile vmnet module to see if it works
Performing make in /home/vm/vmware_server_package//vmware-server-distrib/lib/modules/source/vmnet-only
Using 2.6.x kernel build system.
/home/vm/vmware_server_package/vmware-server-distrib/lib/modules/source/vmnet-only/driver.c:121: warning: data definition has no type or storage class
/home/vm/vmware_server_package/vmware-server-distrib/lib/modules/source/vmnet-only/driver.c:121: warning: type defaults to âintâ in declaration of âDEFINE_SEMAPHOREâ
/home/vm/vmware_server_package/vmware-server-distrib/lib/modules/source/vmnet-only/driver.c:121: warning: parameter names (without types) in function declaration
/home/vm/vmware_server_package/vmware-server-distrib/lib/modules/source/vmnet-only/filter.c:82: warning: type defaults to âintâ in declaration of âDEFINE_SEMAPHOREâ
/home/vm/vmware_server_package/vmware-server-distrib/lib/modules/source/vmnet-only/filter.c:82: warning: parameter names (without types) in function declaration
/home/vm/vmware_server_package/vmware-server-distrib/lib/modules/source/vmnet-only/filter.c: In function âVNetFilter_HandleUserCallâ:
/home/vm/vmware_server_package/vmware-server-distrib/lib/modules/source/vmnet-only/filter.c:1089: error: âfilterIoctlSemâ undeclared (first use in this function)
/home/vm/vmware_server_package/vmware-server-distrib/lib/modules/source/vmnet-only/filter.c:1089: error: (Each undeclared identifier is reported only once
/home/vm/vmware_server_package/vmware-server-distrib/lib/modules/source/vmnet-only/filter.c:1089: error: for each function it appears in.)
make[2]: *** [/home/vm/vmware_server_package/vmware-server-distrib/lib/modules/source/vmnet-only/filter.o] Error 1
make[1]: *** [_module_/home/vm/vmware_server_package/vmware-server-distrib/lib/modules/source/vmnet-only] Error 2
make: *** [vmnet.ko] Error 2
There is a problem compiling the vmnet module after it was patched. :(
```I'm using the same script and patch as this guy did:




Also, a lot of guides tell me to use files in the  /usr/src/linux-headers-2.6.32-31-generic/generated/ directory but I  don't have that directory at all. 

Anyone have any ideas?

Thanks in advance!

[B]I have ubuntu 11.10
my problem when I do these steps:
> sudo su -
goto /usr/src/linux-headers-2.6.38-9-generic/include/linux
cat ../generated/utsrelease.h >> version.h
ln -s ../generated/autoconf.h
 it displays:[/B]
> What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] /usr/src/linux-headers-3.0.0-14-generic/include

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: entrant dans le répertoire « /tmp/vmware-config0/vmmon-only »
make -C /usr/src/linux-headers-3.0.0-14-generic/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: entrant dans le répertoire « /usr/src/linux-headers-3.0.0-14-generic »
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config0/vmmon-only/linux/driver.c:31:0:
/tmp/vmware-config0/vmmon-only/./include/compat_wait.h:78:13: erreur: conflicting types for ‘poll_initwait’
include/linux/poll.h:72:13: note: previous declaration of ‘poll_initwait’ was here
/tmp/vmware-config0/vmmon-only/linux/driver.c:39:28: erreur fatale: linux/smp_lock.h : Aucun fichier ou dossier de ce type
compilation terminée.
make[2]: *** [/tmp/vmware-config0/vmmon-only/linux/driver.o] Erreur 1
make[1]: *** [_module_/tmp/vmware-config0/vmmon-only] Erreur 2
make[1]: quittant le répertoire « /usr/src/linux-headers-3.0.0-14-generic »
make: *** [vmmon.ko] Erreur 2
make: quittant le répertoire « /tmp/vmware-config0/vmmon-only »
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/go/unsup-linux-products" and 
"http://www.vmware.com/go/unsup-linux-tools".

Execution aborted.


---

### Post by ppwsnower on 2011-12-30
I encountered same problem exactly. 
Any one has any hint about that please ?

> **tmedtcom said:**
> [B]I have ubuntu 11.10
my problem when I do these steps:

 it displays:[/B]

---

### Post by sanderhoppe on 2012-01-06
? Who could point me in the right direction here?

After jumping the hoops with the script I get this:

root@uvm:/home/sander/Install/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce# ./vmware-server-2.0.x-kernel-2.6.3x-install.sh
You have VMware Server archive: 
    VMware-server-2.0.2-203138.x86_64.tar.gz
Checking for needed packages on Ubuntu
You do have the linux-headers-3.0.0-14-generic package...
You do have the build-essential package...
You do have the patch package...
Extracting the contents of VMware-server-2.0.2-203138.x86_64.tar.gz
Found .tar file for vmnet module
Found .tar file for vsock module
Found .tar file for vmmon module
Found .tar file for vmci module
Extracting .tar files in order to apply the patch...
Untarring /home/sander/Install/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce/vmware-server-distrib/lib/modules/source/vmnet.tar
Untarring /home/sander/Install/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce/vmware-server-distrib/lib/modules/source/vsock.tar
Untarring /home/sander/Install/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce/vmware-server-distrib/lib/modules/source/vmmon.tar
Untarring /home/sander/Install/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce/vmware-server-distrib/lib/modules/source/vmci.tar
Testing patch...
Creating some simlinks for the newer kernels...
ln: creating symbolic link `/usr/src/linux-headers-3.0.0-14-generic/include/linux/autoconf.h': File exists
ln: creating symbolic link `/usr/src/linux-headers-3.0.0-14-generic/include/linux/utsrelease.h': File exists
Applying patch...
Preparing new tar file for vmnet module
Preparing new tar file for vsock module
Preparing new tar file for vmmon module
Preparing new tar file for vmci module
Checking that the compiling will succeed...
Trying to compile vmnet module to see if it works
Performing make in /home/sander/Install/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce/vmware-server-distrib/lib/modules/source/vmnet-only
Using 2.6.x kernel build system.
/home/sander/Install/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce/vmware-server-distrib/lib/modules/source/vmnet-only/driver.c:35:28: fatal error: linux/smp_lock.h: No such file or directory
compilation terminated.
make[2]: *** [/home/sander/Install/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce/vmware-server-distrib/lib/modules/source/vmnet-only/driver.o] Error 1
make[1]: *** [_module_/home/sander/Install/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce/vmware-server-distrib/lib/modules/source/vmnet-only] Error 2
make: *** [vmnet.ko] Error 2
There is a problem compiling the vmnet module after it was patched. :(
root@uvm:/home/sander/Install/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26

Thanks in advance

---

### Post by Heebie on 2012-01-20
No luck here.. I'm having a problem several others are as well, compiling the vmci.ko module is failing.  Perhaps it's because it's a 3.0.x kernel, and not a 2.6.x?

```
Performing make in /usr/src/vmware/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce/vmware-server-distrib/lib/modules/source/vmci-only
Using 2.6.x kernel build system.
/usr/src/vmware/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce/vmware-server-distrib/lib/modules/source/vmci-only/linux/driver.c:37:28: fatal error: linux/smp_lock.h: No such file or directory
compilation terminated.
make[2]: *** [/usr/src/vmware/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce/vmware-server-distrib/lib/modules/source/vmci-only/linux/driver.o] Error 1
make[1]: *** [_module_/usr/src/vmware/raducotescu-vmware-server-linux-2.6.3x-kernel-bb26dce/vmware-server-distrib/lib/modules/source/vmci-only] Error 2
make: *** [vmci.ko] Error 2
There is a problem compiling the vmci module after it was patched. :(
```

---

### Post by 4nubis on 2012-01-30
Has anyone got this running on a 3.2.0-12 ?
It seems patching the os (my bad) killed the vm server again.

it already begins at 
> Your kernel was built with "gcc" version "4.6.2", while you are trying to use
"/usr/bin/gcc" version "4.6". This configuration is not recommended and VMware
Server may crash if you'll continue. Please try to use exactly same compiler as
one used for building your kernel. Do you want to go with compiler
"/usr/bin/gcc" version "4.6" anyway? [no]if continuing with yes (after copying the autoconf.h into that repo)
> What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] /usr/src/linux-headers-2.6.35-32-server/include

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config2/vmmon-only'
make -C /usr/src/linux-headers-2.6.35-32-server/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-32-server'
  CC [M]  /tmp/vmware-config2/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config2/vmmon-only/./include/driver-config.h:35:0,
                 from /tmp/vmware-config2/vmmon-only/linux/driver.c:20:
include/linux/autoconf.h:4049:0: warning: "CONFIG_VERSION_SIGNATURE" redefined [enabled by default]
./include/generated/autoconf.h:4049:0: note: this is the location of the previous definition
In file included from /tmp/vmware-config2/vmmon-only/./common/vmx86.h:32:0,
                 from /tmp/vmware-config2/vmmon-only/linux/driver.h:29,
                 from /tmp/vmware-config2/vmmon-only/linux/driver.c:101:
/tmp/vmware-config2/vmmon-only/./include/x86msr.h:164:0: warning: "MSR_THERM2_CTL" redefined [enabled by default]
/usr/src/linux-headers-2.6.35-32-server/arch/x86/include/asm/msr-index.h:240:0: note: this is the location of the previous definition
In file included from /tmp/vmware-config2/vmmon-only/./include/driver-config.h:35:0,
                 from /tmp/vmware-config2/vmmon-only/linux/driver.c:20:
include/linux/autoconf.h:4049:0: warning: "CONFIG_VERSION_SIGNATURE" redefined [enabled by default]
./include/generated/autoconf.h:4049:0: note: this is the location of the previous definition
In file included from /tmp/vmware-config2/vmmon-only/./common/vmx86.h:32:0,
                 from /tmp/vmware-config2/vmmon-only/linux/driver.h:29,
                 from /tmp/vmware-config2/vmmon-only/linux/driver.c:101:
/tmp/vmware-config2/vmmon-only/./include/x86msr.h:164:0: warning: "MSR_THERM2_CTL" redefined [enabled by default]
/usr/src/linux-headers-2.6.35-32-server/arch/x86/include/asm/msr-index.h:240:0: note: this is the location of the previous definition
  CC [M]  /tmp/vmware-config2/vmmon-only/linux/driverLog.o
In file included from /tmp/vmware-config2/vmmon-only/./include/driver-config.h:35:0,
                 from /tmp/vmware-config2/vmmon-only/linux/driverLog.c:26:
include/linux/autoconf.h:4049:0: warning: "CONFIG_VERSION_SIGNATURE" redefined [enabled by default]
./include/generated/autoconf.h:4049:0: note: this is the location of the previous definition
  CC [M]  /tmp/vmware-config2/vmmon-only/linux/hostif.o
In file included from /tmp/vmware-config2/vmmon-only/./include/driver-config.h:35:0,
                 from /tmp/vmware-config2/vmmon-only/linux/hostif.c:29:
include/linux/autoconf.h:4049:0: warning: "CONFIG_VERSION_SIGNATURE" redefined [enabled by default]
./include/generated/autoconf.h:4049:0: note: this is the location of the previous definition
In file included from /tmp/vmware-config2/vmmon-only/./common/vmx86.h:32:0,
                 from /tmp/vmware-config2/vmmon-only/./common/hostif.h:32,
                 from /tmp/vmware-config2/vmmon-only/linux/hostif.c:73:
/tmp/vmware-config2/vmmon-only/./include/x86msr.h:164:0: warning: "MSR_THERM2_CTL" redefined [enabled by default]
/usr/src/linux-headers-2.6.35-32-server/arch/x86/include/asm/msr-index.h:240:0: note: this is the location of the previous definition
  CC [M]  /tmp/vmware-config2/vmmon-only/common/comport.o
  CC [M]  /tmp/vmware-config2/vmmon-only/common/cpuid.o
In file included from /tmp/vmware-config2/vmmon-only/./include/driver-config.h:35:0,
                 from /tmp/vmware-config2/vmmon-only/common/cpuid.c:21:
include/linux/autoconf.h:4049:0: warning: "CONFIG_VERSION_SIGNATURE" redefined [enabled by default]
./include/generated/autoconf.h:4049:0: note: this is the location of the previous definition
  CC [M]  /tmp/vmware-config2/vmmon-only/common/hashFunc.o
  CC [M]  /tmp/vmware-config2/vmmon-only/common/memtrack.o
In file included from /tmp/vmware-config2/vmmon-only/./include/driver-config.h:35:0,
                 from /tmp/vmware-config2/vmmon-only/common/memtrack.c:30:
include/linux/autoconf.h:4049:0: warning: "CONFIG_VERSION_SIGNATURE" redefined [enabled by default]
./include/generated/autoconf.h:4049:0: note: this is the location of the previous definition
  CC [M]  /tmp/vmware-config2/vmmon-only/common/phystrack.o
In file included from /tmp/vmware-config2/vmmon-only/./include/driver-config.h:35:0,
                 from /tmp/vmware-config2/vmmon-only/common/phystrack.c:38:
include/linux/autoconf.h:4049:0: warning: "CONFIG_VERSION_SIGNATURE" redefined [enabled by default]
./include/generated/autoconf.h:4049:0: note: this is the location of the previous definition
  CC [M]  /tmp/vmware-config2/vmmon-only/common/task.o
In file included from /tmp/vmware-config2/vmmon-only/./include/driver-config.h:35:0,
                 from /tmp/vmware-config2/vmmon-only/common/task.c:38:
include/linux/autoconf.h:4049:0: warning: "CONFIG_VERSION_SIGNATURE" redefined [enabled by default]
./include/generated/autoconf.h:4049:0: note: this is the location of the previous definition
  CC [M]  /tmp/vmware-config2/vmmon-only/common/vmx86.o
In file included from /tmp/vmware-config2/vmmon-only/./include/driver-config.h:35:0,
                 from /tmp/vmware-config2/vmmon-only/common/vmx86.c:29:
include/linux/autoconf.h:4049:0: warning: "CONFIG_VERSION_SIGNATURE" redefined [enabled by default]
./include/generated/autoconf.h:4049:0: note: this is the location of the previous definition
In file included from /tmp/vmware-config2/vmmon-only/common/vmx86.h:32:0,
                 from /tmp/vmware-config2/vmmon-only/common/vmx86.c:40:
/tmp/vmware-config2/vmmon-only/./include/x86msr.h:164:0: warning: "MSR_THERM2_CTL" redefined [enabled by default]
/usr/src/linux-headers-2.6.35-32-server/arch/x86/include/asm/msr-index.h:240:0: note: this is the location of the previous definition
  CC [M]  /tmp/vmware-config2/vmmon-only/vmcore/moduleloop.o
In file included from /tmp/vmware-config2/vmmon-only/./include/driver-config.h:35:0,
                 from /tmp/vmware-config2/vmmon-only/vmcore/moduleloop.c:29:
include/linux/autoconf.h:4049:0: warning: "CONFIG_VERSION_SIGNATURE" redefined [enabled by default]
./include/generated/autoconf.h:4049:0: note: this is the location of the previous definition
In file included from /tmp/vmware-config2/vmmon-only/./common/vmx86.h:32:0,
                 from /tmp/vmware-config2/vmmon-only/vmcore/moduleloop.c:35:
/tmp/vmware-config2/vmmon-only/./include/x86msr.h:164:0: warning: "MSR_THERM2_CTL" redefined [enabled by default]
/usr/src/linux-headers-2.6.35-32-server/arch/x86/include/asm/msr-index.h:240:0: note: this is the location of the previous definition
  LD [M]  /tmp/vmware-config2/vmmon-only/vmmon.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /tmp/vmware-config2/vmmon-only/vmmon.mod.o
  LD [M]  /tmp/vmware-config2/vmmon-only/vmmon.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-32-server'
cp -f vmmon.ko ./../vmmon.o
make: Leaving directory `/tmp/vmware-config2/vmmon-only'
Unable to make a vmmon module that can be loaded in the running kernel:
insmod: error inserting '/tmp/vmware-config2/vmmon.o': -1 Invalid module format
There is probably a slight difference in the kernel configuration between the
set of C header files you specified and your running kernel.  You may want to
rebuild a kernel based on that directory, or specify another directory.

For more information on how to troubleshoot module-related problems, please
visit our Web site at "http://www.vmware.com/go/unsup-linux-products" and
"http://www.vmware.com/go/unsup-linux-tools".

Execution aborted.
Think of switching to virtualbox (but on a headless server ... it's pro'lly more relax to pop one of my arteries)

---

### Post by EyeballGilbert on 2012-02-27
Hi

I know this is an old post and VMWare Server is no longer supported but i was hoping i might find some help.

I have Ubuntu 11.10 3.0.0 and VMWare Server 2.0.2

I am getting the following error when trying to install
- Unable to build the vmmon module

Can anyone help?

---

### Post by 4nubis on 2012-02-27
> **EyeballGilbert said:**
> I have Ubuntu 11.10 3.0.0 and VMWare Server 2.0.2I migrated to virtualbox - Headless - managed with phpvirtualbox.

Since Virtualbox4.1 is an aptitude package I really suggest you migrate too.
You can do all the dist-upgrades, upgrades & updates you want and it will keep working.

I was able to reuse all the vmdk files of my old vmware2 installation without much hastle.
If you're vm is build out of a single vmdk, you don't even have to go through the migration procedure.
You can just add the vmdk file as a disk to your virtualbox-vm and start it up.
(The only thing is that your MAC addresses will have changed and you might need to reconfigure your dhcp server if you had fixed addresses.)
I should have done this ages ago.

I'm not even mentioning the memory leak problems that VMWare server 2 has and all other issues. VMWare server 2 doesn't run the latest os's so if you want to experiment with W8 for example, you'll need to move on to vbox anyway.

edit : believe me, I've tried EVERYTHING to get vmware server working on ubuntu server 11, besides rewriting vmware server myself. If you should succeed anyway, please post it here.

---

### Post by vz90954 on 2012-03-09
every time i try to install the vmware or the update files it asks me for a c compailer location.
i tried the default - without luck
i treid /usr/bin/gcc (as explained) without luck.
can anybody help me?

---

### Post by ilyklinux on 2012-04-12
i am not able to run de script.i had downloaded vmware 2.0.0 in my home folder and tried to run the script from dere itself by giving de command sudo ./vmware-server-2.0.x-kernel-2.6.3x-install.sh.
but it is showing a msg like dis : 
"There is no archive containing VMware Server in the path you indicated!". And am using ubuntu 10.10 with kernel version 2.6.35-22-generic. am totally stuck here. now how i can install vmware on my machine?
someboby pls tel me wat to do?

---

### Post by zozy on 2012-04-17
> **ilyklinux said:**
> 
someboby pls tel me wat to do?

point the scrip to the directory where there is a file called (or similar, depending on version and architecture) "VMware-server-2.0.2-203138.x86_64.tar.gz"

It should be in the format: ./script.sh SOURCE  (or alternatively you could move the tar.gz file into the working directory of the script) Hope this helps!

---

### Post by ilyklinux on 2012-04-20
I am trying in dat way only. my script and archieve file is in same directory.both files i placed in home directory and then i tried these commands.
sudo ./vmware-server-2.0.x-kernel-2.6.3x-install.sh and i tried by 
putting the path also 

sudo ./vmware-server-2.0.x-kernel-2.6.3x-install.sh /home/ajith/      
and both ways failed and showing same message:-


There is no archive containing VMware Server in the path you indicated!

---

### Post by vlip on 2012-05-02
What about Ubuntu 12.04 whit kernel 3 
$uname -r
3.2.0-24-generic

---

### Post by weitau on 2012-10-29
Anybody get VMware server running on 12.04?

---


---
title: "gcc trouble: VMWare won't work on Breezy"
date: 2005-10-16
forum: Installation &amp; Upgrades
---

### Post by tag on 2005-10-16
I was using VMware with vmmon modules that i compiled myself on hoary. Now on breezy these didn't seem to work so I executed the vmware-config.pl script in order to compile a compatible vmmon driver. But apparently there is some confusion among the various gcc versions since it complains:

> Your kernel was built with "gcc" version "3.4.5", while you are trying to use
"/usr/bin/gcc" version "4.0.2". This configuration is not supported and VMware
Workstation cannot work in such configuration. Please either recompile your
kernel with "/usr/bin/gcc" version "4.0.2", or restart /usr/bin/vmware-config.pl
with CC environment variable pointing to the "gcc" version "3.4.5".

Can anybody help me out on what i should do now?
Below I posted the full output:

> tag@fry:~$ sudo /usr/bin/vmware-config.pl
Password:
Making sure services for VMware Workstation are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done
   Bridged networking on /dev/vmnet0                                   done
   Virtual ethernet                                                    done

Configuring fallback GTK+ 2.4 libraries.

***
* Updating MIME database in /usr/share/mime...
***
In which directory do you want to install the mime type icons?
[/usr/share/icons]

In which directory do you want to install the application's icon?
[/usr/share/pixmaps]

Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Workstation is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for
your system (you need to have a C compiler installed on your system)? [yes]

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

Your kernel was built with "gcc" version "3.4.5", while you are trying to use
"/usr/bin/gcc" version "4.0.2". This configuration is not supported and VMware
Workstation cannot work in such configuration. Please either recompile your
kernel with "/usr/bin/gcc" version "4.0.2", or restart /usr/bin/vmware-config.pl
with CC environment variable pointing to the "gcc" version "3.4.5".

For more information on how to troubleshoot module-related problems, please
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.


---

### Post by sjoh_64 on 2005-10-16
The Ubuntu Kernel for Breezy was not compiled with gcc 4, which is the standard compiler for breezy, but with gcc-3.4 which is by default unavailable in your breezy install.

You'll have to either rebuild your kernel -- without explicitly using gcc 3.4, gcc 4 will be used -- and reconfigure vmware, or build the vmware modules with gcc 3.4 explicitly.

To do so:
```
apt-get install gcc-3.4 g++-3.4
CC=gcc-3.4 /path/to/vmware-config.pl
```

If you don't want to work as root, use sudo instead:
```
sudo apt-get install gcc-3.4 g++-3.4
export CC=gcc-3.4
sudo /path/to/vmware-config.pl
```

Good luck.

---

### Post by jespo on 2005-10-16
In addition to last post you have to download 

[http://ftp.cvut.cz/vmware/vmware-any-any-update94.tar.gz](http://ftp.cvut.cz/vmware/vmware-any-any-update94.tar.gz)

And don't run the vmware-config.pl

decompress the tar.gz and go with runme.pl inside.

The vmware-config.pl generates boogy configuration.

---

### Post by msmeyer on 2005-10-17
[QUOTE=jespo]In addition to last post you have to download 

[http://ftp.cvut.cz/vmware/vmware-any-any-update94.tar.gz](http://ftp.cvut.cz/vmware/vmware-any-any-update94.tar.gz)
[/QUOTE]

Many thanks, that works for me, too! Just out of interest: What is that "vmware-any-any-update94.tar.gz" patch? Is it an official file from VMWare? It sure has the VMWare copyright notice on it :rolleyes: I mean I'm happy that VMWare now works again, but I'd prefer to download it from a more "trusted" source... :D 

> 
And don't run the vmware-config.pl

decompress the tar.gz and go with runme.pl inside.


Actually, this utility does run vmware-config.pl, but it seems to setup the environment in a proper way before doing that.

---

### Post by 11hjpphty76lkjj on 2005-10-17
I followed these steps:

sudo apt-get install gcc-3.4 g++-3.4
export CC=gcc-3.4
sudo /path/to/vmware-config.pl

then:

downloaded the vmware-any-any-update94.tar.gz
then tar xvfz vmware...
cd vmware...
sudo ./runme.pl

I'm getting this question, and I don't know how to answer it:

What is the location of the directory of C header files that match  your running
kernel? [/usr/src/linux/include]

The path "/usr/src/linux/include" is not an existing directory.

What is the location of the directory of C header files that match  your running
kernel? [/usr/src/linux/include]

How do I get around this?  

I have previously also installed the build-essentials and I can compile software, etc.

Thanks.

Aaron

---

### Post by zenwhen on 2005-10-17
[QUOTE=kalosaurusrex]I followed these steps:

sudo apt-get install gcc-3.4 g++-3.4
export CC=gcc-3.4
sudo /path/to/vmware-config.pl

then:

downloaded the vmware-any-any-update94.tar.gz
then tar xvfz vmware...
cd vmware...
sudo ./runme.pl

I'm getting this question, and I don't know how to answer it:

What is the location of the directory of C header files that match  your running
kernel? [/usr/src/linux/include]

The path "/usr/src/linux/include" is not an existing directory.

What is the location of the directory of C header files that match  your running
kernel? [/usr/src/linux/include]

How do I get around this?  

I have previously also installed the build-essentials and I can compile software, etc.

Thanks.

Aaron[/QUOTE]

Run this:

> uname -r

Then install the linux-headers package for your kernel. Your instructions worked PERFECTLY, as I had already done this.

---

### Post by feight on 2005-10-19
BUMP

I'd like to nominate this thread for a mini-sticky if it isn't already one, had to search a few minutes to find it.

---

### Post by aerials on 2005-10-20
vmware seems to refuse my kernel headers:(

I'm running kernel 2.6.12-9-686 and have therefore installed linux-headers-2.6.12-9-686

At this point:

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

I enter:

/usr/src/linux-headers-2.6.12-9-686/include

And get the following error message:

The directory of kernel headers (version 2.6.12) does not match your running
kernel (version 2.6.12-9-686).  Even if the module were to compile successfully,it would not load into the running kernel.


Why does vmware think that the headers are for 2.6.12 only?

uname -r returns 2.6.12-9-686 as well...

---

### Post by aerials on 2005-10-20
damn... sorry for bothering you guys.

A reinstall of linux-headers-2.6.12-9-686 did the trick. Looks like there went something wrong the first time.

---

### Post by zombie.daemon on 2005-10-20
i installed vmware, had that same problem with the different gcc version, but go those sorted out.  used defaults for the configs, but when i try to run vmare i get this message, any ideas?


vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.

---

### Post by aerials on 2005-10-20
Did you install the vmware-any-any patch?

Best thing to do would be following the guide in the wiki:
[https://wiki.ubuntu.com/InstallingVMWare?highlight=%28vmware%29](https://wiki.ubuntu.com/InstallingVMWare?highlight=%28vmware%29)

---

### Post by macewan on 2005-10-23
[quote=aerials]Did you install the vmware-any-any patch?

Best thing to do would be following the guide in the wiki:
[https://wiki.ubuntu.com/InstallingVMWare?highlight=%28vmware%29]("https://wiki.ubuntu.com/InstallingVMWare?highlight=%28vmware%29")[/quote]


This does work. Don't ignore what it says about the kernel.

---

### Post by jonathanhayward on 2005-11-22
VMware crashes when I try to make a VM.

I've downloaded VMware, tried to run vmware-config.pl independently and then ran the runme.pl file from vmware-any-any-update96. It compiles and begins to run; there is one error message displayed.

/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)

Then I am able to get through most or all of the wizard to create a new VM, then crashes after printing

NOT_REACHED /build/mts/release/bora-13124/bora/apps/vmuiLinux/sig_vmui.c:390

Has anyone else had problems with VMware crashing on trying to make a VM? Is there something else I should be installing?

TIA,
++ Jonathan Hayward, [email]jonathan.hayward@pobox.com[/email]
** To see an award-winning website with stories, essays, artwork,
** games, and a four-dimensional maze, why not visit my home page?
** All of this is waiting for you at [http://JonathansCorner.com](http://JonathansCorner.com)

** If you'd like a Google Mail ( gmail.com) account, please tell me!

---

### Post by jonathanhayward on 2005-11-22
Addendum:

I had a problem with filesystem permissions. VMware seems to be working now.

[QUOTE=jonathanhayward]VMware crashes when I try to make a VM.

I've downloaded VMware, tried to run vmware-config.pl independently and then ran the runme.pl file from vmware-any-any-update96. It compiles and begins to run; there is one error message displayed.

/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)

Then I am able to get through most or all of the wizard to create a new VM, then crashes after printing

NOT_REACHED /build/mts/release/bora-13124/bora/apps/vmuiLinux/sig_vmui.c:390

Has anyone else had problems with VMware crashing on trying to make a VM? Is there something else I should be installing?

TIA,[/QUOTE]
++ Jonathan Hayward, [email]jonathan.hayward@pobox.com[/email]
** To see an award-winning website with stories, essays, artwork,
** games, and a four-dimensional maze, why not visit my home page?
** All of this is waiting for you at [http://JonathansCorner.com](http://JonathansCorner.com)

** If you'd like a Google Mail ( gmail.com) account, please tell me!

---

### Post by mr.p on 2005-11-29
i installed vmware as per the wiki and now a kernel update has come through and it needs to be kinded be resetup so i can use vmware do i just run vmware-config.pl and let it do its thing? or do i re-run whats in the update-any-any-96?

---

### Post by carpy on 2005-12-16
News Flash!

I just installed VMWare 5.5 and the config script has ready-made modules for Breezy and Hoary!

./vmware-distrib/lib/modules/binary/bld-2.6.10-5-i386up-Ubuntu5.04
./vmware-distrib/lib/modules/binary/bld-2.6.10-5-i686smp-Ubuntu5.04
./vmware-distrib/lib/modules/binary/bld-2.6.10-5-i686up-Ubuntu5.04
./vmware-distrib/lib/modules/binary/bld-2.6.10-5-x86_64smp-Ubuntu5.04
./vmware-distrib/lib/modules/binary/bld-2.6.10-5-x86_64up-Ubuntu5.04
./vmware-distrib/lib/modules/binary/bld-2.6.12-9-i386k7smp-Ubuntu5.10
./vmware-distrib/lib/modules/binary/bld-2.6.12-9-i386k7-Ubuntu5.10
./vmware-distrib/lib/modules/binary/bld-2.6.12-9-i386up-Ubuntu5.10
./vmware-distrib/lib/modules/binary/bld-2.6.12-9-i686smp-Ubuntu5.10
./vmware-distrib/lib/modules/binary/bld-2.6.12-9-i686up-Ubuntu5.10
./vmware-distrib/lib/modules/binary/bld-2.6.12-9-x86_64generic-Ubuntu5.10
./vmware-distrib/lib/modules/binary/bld-2.6.12-9-x86_64k8smp-Ubuntu5.10
./vmware-distrib/lib/modules/binary/bld-2.6.12-9-x86_64k8-Ubuntu5.10
./vmware-distrib/lib/modules/binary/bld-2.6.12-9-x86_64xeon-Ubuntu5.10

---

### Post by deleric on 2006-01-31
[QUOTE=msmeyer]Many thanks, that works for me, too! Just out of interest: What is that "vmware-any-any-update94.tar.gz" patch? Is it an official file from VMWare? It sure has the VMWare copyright notice on it :rolleyes: I mean I'm happy that VMWare now works again, but I'd prefer to download it from a more "trusted" source... :D 



Actually, this utility does run vmware-config.pl, but it seems to setup the environment in a proper way before doing that.[/QUOTE]


This worked very good for the gcc-4 compiled kernel thanks! 

*mirror: [http://ftp.cvut.cz/vmware/?D=A](http://ftp.cvut.cz/vmware/?D=A)*

---


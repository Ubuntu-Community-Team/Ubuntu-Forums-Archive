---
title: "Can't install VMWare Server on Ubuntu 7.04 Server"
date: 2007-07-22
forum: Installation &amp; Upgrades
---

### Post by b0bby on 2007-07-22
Hey, I can't install VMWare Server (1.0.2-39867) on my fresh Ubuntu 7.04 Server.

I'v apt'd xinit,  build-essentials and C header files (w/ apt-get install linux-headers-`uname -r` )

And everything goes find until
'```
Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.20-15-server/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config1/vmmon-only'
make -C /lib/modules/2.6.20-15-server/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD
/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-server'
  CC [M]  /tmp/vmware-config1/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config1/vmmon-only/linux/driver.c:80:
/tmp/vmware-config1/vmmon-only/./include/compat_kernel.h:21: error: expected dec
laration specifiers or &#8216;...&#8217; before &#8216;compat_exit&#8217;
/tmp/vmware-config1/vmmon-only/./include/compat_kernel.h:21: error: expected dec
laration specifiers or &#8216;...&#8217; before &#8216;exit_code&#8217;
/tmp/vmware-config1/vmmon-only/./include/compat_kernel.h:21: warning: type defau
lts to &#8216;int&#8217; in declaration of &#8216;_syscall1&#8217;
make[2]: *** [/tmp/vmware-config1/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config1/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-server'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config1/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.
```

Please help..

---

### Post by Betelgeuse on 2007-07-22
uninstall everthing, enable canonical commercial repo on your sources.list and use this command :
sudo apt-get install vmware-server

that's it.

---

### Post by b0bby on 2007-07-22
Yeah, I did so accually.. But it didnt work either, and iv googled my brains out..

root@c3po:/home/b0bby# /etc/init.d/vmware-server start
Starting VMware services:
   Virtual machine monitor                                            failed
   Virtual ethernet                                                   failed
Module vmnet is not loaded.  Please verify that it is loaded before
running this script.

---

### Post by billstei on 2007-07-27
Apparently the problem is that line 21 of compat_kernel.h has two extra commas where they should not be:

static inline _syscall1(int, compat_exit, int, exit_code);

Should be:

static inline _syscall1(int compat_exit, int exit_code);

The source code can be found inside the vmmon.tar file either in

vmware-server-distrib/lib/modules/source

before you install, or in

/usr/lib/vmware/modules/source

after you try it and the installer copies the source there and then crashes out.  This post shows how to do it *before* you run the installer:

[http://ubuntuforums.org/showpost.php?p=2509584](http://ubuntuforums.org/showpost.php?p=2509584)

otherwise you need to do the same procedure, but go to /usr/lib/vmware/modules/source and change it there, then re-run /usr/bin/vmware-config.pl

Bill

---

### Post by BLTicklemonster on 2007-08-03
Still haven't fixed it, have they?

Okay, I followed your directions, but now I don't have a /usr/bin/vmware-config.pl any more.

I have old ones, but not one that works. So I opened the most recent one in root, and renamed it, and when I try to run it, I get this:

bill@bill-desktop:~$ sudo /usr/bin/vmware-config.pl
sudo: /usr/bin/vmware-config.pl: command not found

But it's there.

Now what?

Amazingly enough, I get vmware up, but when I try to run it, I get this, of course:

Unable to change virtual machine power state: The process exited with an error:
vmxvmdb: Index name being generated from config file
POST(no connection): Could not open /dev/vmmon: No such file or directory.
Please make sure that the kernel module `vmmon' is loaded.

POST(no connection): Failed to initialize monitor device.

Failed to initialize VM.
End of error message.

---

### Post by Vanish00 on 2007-08-03
I was just trying to install VMware Server but now I have the exact same problem as b0bby describes.  Anybody figure it out?

I tried to fix the problem is that line 21 of compat_kernel.h, but once I fix it I can't save it?

---

### Post by bengood24 on 2007-08-03
Here is what I did:
Open terminal window
sudo -i
cd /usr/lib/vmware/modules/source
tar xvf vmmon.tar
cd vmmon-only/include
Make changes to file mentioned above
cd ../..
mv vmmon.tar vmmon.tar.orig
tar cvf vmmon.tar vmmon-only

Then I reran vmware-config.pl and all is good.

---

### Post by Vanish00 on 2007-08-04
Thanks, bengood24!  I finally got VMware Server installed.  Sadly though once I got pass this hurdle now I can't get my virtual machine to read my Windows XP CD when I power on.  Any ideas?

---

### Post by Kilz on 2007-08-04
Thank you , thank you , thank you , thank you for this post!  :D

I finally bit the bullet and upgraded to Feisty because I upgraded a few things on my main box. It has been fun.

---

### Post by fridaystreet on 2007-11-24
Excellent :-)

Thanks this was just what I was looking for. I'm fairly new to Ubuntu, been great fun getting it all setup, a little frustrating at times but its posts like this in the forum that really help the newbies. Thanks for not assuming everyone just knows.

Cheers
Paul

---


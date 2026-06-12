---
title: "dist-upgrade on 11.04 breaks nvidia-current"
date: 2011-08-04
forum: Installation &amp; Upgrades
---

### Post by mbobak on 2011-08-04
Hi all,

I'm running Ubuntu 11.04 on x86-64.

I did 'sudo apt-get update' and 'sudo apt-get dist-upgrade' and when I did, it gave me kernel 3.0.  (3.0.0-7-lowlatency, to be specific.)

Problem is, it breaks nvidia-current, cause the nvidia kernel module build thinks that 3.0.0 is a development kernel, and errors out on compilation.

I was trying to hack the code a bit to get around the problem, but so far unsuccessful.

Anyone else have this problem?  Anyone found a valid workaround?

Thanks,

-Mark

---

### Post by dino99 on 2011-08-04
the easiest way is to purge the installed "nvidia" packages, install dkms and finally reinstall nvidia-current (can be easily done using synaptic)

---

### Post by coffeecat on 2011-08-04
To get the 3.0 kernel in Natty/11.04 you would have had to have enabled a ppa repository. If you enable a ppa repo for the kernel, the ppa kernel is not installed with "sudo apt-get upgrade", only with "sudo apt-get dist-upgrade", which is what seems to have happened in your situation.

What ppa repos do you have enabled?

---

### Post by mbobak on 2011-08-04
Yes, I have a ppa for the '-lowlatency' kernel.

Looking at /etc/apt/sources.list.d, the following ppas are installed:
```
mjb@mercury:/etc/apt/sources.list.d$ grep ppa *.list
abogani-ppa-natty.list:deb http://ppa.launchpad.net/abogani/ppa/ubuntu natty main
abogani-ppa-natty.list:deb-src http://ppa.launchpad.net/abogani/ppa/ubuntu natty main
mythbuntu-repos.list:deb http://ppa.launchpad.net/mythbuntu/0.24/ubuntu natty main
mythbuntu-repos.list:deb http://ppa.launchpad.net/mythbuntu/testing/ubuntu natty main
ubuntu-mozilla-security-ppa-natty.list:deb http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu natty main
ubuntu-mozilla-security-ppa-natty.list:deb-src http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu natty main
```

Thanks,

-Mark

---

### Post by mbobak on 2011-08-04
Just confirming, the abogani ppa is where I'm getting my lowlatency kernel from.

Thanks,

-Mark

---

### Post by mbobak on 2011-08-04
I'll work on this a bit more this evening when I get home from work.

I'll update the thread if I find a solution.

-Mark

---

### Post by CryptSphinx on 2011-08-04
Same problem , Same PPA , same issue with failure to build module for low latency kernel .

Let me know how it works out because its WAY over my head.

---

### Post by mbobak on 2011-08-05
Ok, I have a solution.

No doubt there's an easier way to do this, but, this will work.  If anyone can simplify my approach, I'd welcome that.

So, so, we need a copy of nvidia-current_270.41.06-0ubuntu1_amd64.deb.

That can be found in /var/cache/apt/archives.

(If you don't see it there, do 'sudo apt-get install --reinstall nvidia-current'.)

First, we need to unpackage the .deb, with this command:
```
dpkg-deb -x nvidia-current_270.41.06-0ubuntu1_amd64.deb my_tmp_dir
```

Now, we need to hack the code a bit, so that it thinks that the 3.0 kernel is ok.

First, cd to the 'src' dir:```

cd my_temp_dir/usr/src/nvidia-current-270.41.06
```

Then edit the nv-linux.h file:
```
vi nv-linux.h
```

Now, look for a chunk of code, starting at line 29, that looks like this:
```
#if LINUX_VERSION_CODE < KERNEL_VERSION(2, 4, 7)
#  error This driver does not support 2.4 kernels older than 2.4.7!
#elif LINUX_VERSION_CODE < KERNEL_VERSION(2, 5, 0)
#  define KERNEL_2_4
#elif LINUX_VERSION_CODE < KERNEL_VERSION(2, 6, 0)
#  error This driver does not support 2.5 kernels!
#elif LINUX_VERSION_CODE < KERNEL_VERSION(2, 7, 0)
#  define KERNEL_2_6
#else
#  error This driver does not support development kernels!
#endif

```

And modify it to look like this:
```
#if LINUX_VERSION_CODE < KERNEL_VERSION(2, 4, 7)
#  error This driver does not support 2.4 kernels older than 2.4.7!
#elif LINUX_VERSION_CODE < KERNEL_VERSION(2, 5, 0)
#  define KERNEL_2_4
#elif LINUX_VERSION_CODE < KERNEL_VERSION(2, 6, 0)
#  error This driver does not support 2.5 kernels!
#elif LINUX_VERSION_CODE < KERNEL_VERSION(2, 7, 0)
#  define KERNEL_2_6
#elif LINUX_VERSION_CODE < KERNEL_VERSION(3, 1, 0)
#  define KERNEL_3_0
#else
#  error This driver does not support development kernels!
#endif

```

Ok, almost there.  CD back to your temp directory:
```
cd ~/my_temp_dir
```

Now, we need to extract a control file, so, do this:
```
dpkg-deb --control ../nvidia-current_270.41.06-0ubuntu1_amd64.deb
```

Finally, repackage the .deb, and install it:
First repackage:```

cd <directory above tmpdir, where you originally put the .deb that was unpackaged>
dpkg -I name_of_your_new_package.deb
```

Now, finally, in the directory where name_of_your_new_package.deb exists, do:
```
dpkg -i name_of_your_new_package.deb
```

Ok, if I didn't miss any steps, and if you followed them all correctly, you should now have working nvidia-current on a 3.0 kernel.

Hope that helps,

-Mark

---

### Post by LowFidelity on 2011-08-05
Hey, I have the same problem. I tried following the steps that mbobak put up but I got stuck during the repackaging steps (i think). repackaging means doing
```

dpkg -b my_tmp_dir new_package.deb
```

right?

and then when you install the package THEN you use```

dpkg -i new_package.deb 
```
I think. When I did that, though, it returns this:

Error! Bad return status for module build on kernel: 3.0.0-7-lowlatency (x86_64)
Consult the make.log in the build directory
/var/lib/dkms/nvidia-current/270.41.06/build/ for more information.

I'm still having this problem.

---

### Post by mbobak on 2011-08-05
> **LowFidelity said:**
> Hey, I have the same problem. I tried following the steps that mbobak put up but I got stuck during the repackaging steps (i think). repackaging means doing
```

dpkg -b my_tmp_dir new_package.deb
```

right?
<....stuff deleted...>
I'm still having this problem.

Nope, you repackage with '-I'.  See steps below:
```
cd <directory above tmpdir, where you originally put the .deb that was unpackaged>
dpkg -I name_of_your_new_package.deb
```

Then try the install.  If you edited the nv-linux.h file correctly, it should work.

Hope that solves your problem,

-Mark

---

### Post by LowFidelity on 2011-08-06
> **mbobak said:**
> Nope, you repackage with '-I'.  See steps below:
```
cd <directory above tmpdir, where you originally put the .deb that was unpackaged>
dpkg -I name_of_your_new_package.deb
```

Then try the install.  If you edited the nv-linux.h file correctly, it should work.

Hope that solves your problem,

-Mark

when I try to do dpkg -I new_package.deb it returns this:

dpkg-deb: error: failed to read archive `name_of_your_new_package.deb': No such file or directory

---

### Post by mbobak on 2011-08-07
Wow, I'm really sorry.  I totally screwed up the directions.

For the 'repackage' step, you need to do:
```
dpkg-deb --build name_of_new_package.deb
```

Try that, then try installing the new package:
```
dpkg -i name_of_new_package.deb
```

Sorry for the screwup!

Let me know if that works for you.

-Mark

---

### Post by LowFidelity on 2011-08-08
When I built the package it returned this:

dpkg-deb: warning: 'my_tmp_dir/DEBIAN/control' contains user-defined field 'Modaliases'
dpkg-deb: warning: ignoring 1 warning about the control file(s)

am I supposed to modify the control file also?

---

### Post by MAFoElffen on 2011-08-08
Here's a fix for your original problem, installing nvidia drivers on the 3.0.x kernel from my sticky:
[http://ubuntuforums.org/showpost.php?p=10924650&postcount=306](http://ubuntuforums.org/showpost.php?p=10924650&postcount=306)

Oneiric has the first fix in this post, included in it already, Natty needs it, as I don't think it was included... Reason?  The 3.0.x kernel was not released for Natty, but is in the later Oneiric dev builds already.   These fixes we found while testing Oneiric when the kernel numbering schema changed. 

Hope this helped.

---


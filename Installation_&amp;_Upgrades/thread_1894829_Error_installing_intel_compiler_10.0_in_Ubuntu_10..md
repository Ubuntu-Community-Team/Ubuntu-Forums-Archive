---
title: "Error installing intel compiler 10.0 in Ubuntu 10.04"
date: 2011-12-13
forum: Installation &amp; Upgrades
---

### Post by cardogar on 2011-12-13
Hi all,

I've downloaded the intel fortran compiler 10.0 for intel64. However, I am not able to install it in my Ubuntu 10.04. 

I am forced to use the 10.0 release to compile a third party software.

Following the instruction of [http://software.intel.com/en-us/articles/using-intel-compilers-for-linux-with-ubuntu/](http://software.intel.com/en-us/articles/using-intel-compilers-for-linux-with-ubuntu/)

I have installed:
build-essential
gcc-multilib
rpm
openjdk-6-jre-headless
libstdc++5

But I still get the message:
architecture      = x86_64
kernel            = 2.6.32-37-generic
glibc             = unknown
operating system  = unknown

If I ignore this, I get the following:

The installation program was not able to detect the IA-32 version of the following libraries installed   :  
libstdc++
libgcc
glibc

Again I ignore the message, and finally the installation is interrupted by:

-----------------------------------------------------------------
Intel(R) Fortran Compiler for applications running on Intel(R) 64, Version 10.0 (10.0.026)
Installing...
Installation failed.
-----------------------------------------------------------------
RPM std error output is as follows:
-----------------------------------------------------------------
rpm: please use alien to install rpm packages on Debian, if you are really sure use --force-debian switch. See README.Debian for more details.
-----------------------------------------------------------------
This failure occured using the following RPM options:
    -U --replacefiles --force

No idea... I would really appreciate any help. 

First problem to download the product due to browser issues and now this.. it is taking ages to install it!

Thanks!
Carlos

---

### Post by BC59 on 2011-12-13
For the moment I can see 2 errors:

You are using 32bit application to install on a 64bit computer

and you are using Fedora packages .rpm on a Debian/Ubuntu OS.

For all of these are solutions.

From where you downloaded the packages to install? Are there any Debian packages to download?

---

### Post by cardogar on 2011-12-13
Thanks for you reply!

Well, I have downloaded the source from the intel website.

In principle, they should be for intel64, that's the name indeed:

l_fc_c_10.0.026_intel64.tar.gz

According to the description:

Product for Intel® 64 (File l_fc_c_10.0.026_intel64.tar.gz): Intel 64 architecture only compiler subset and Intel Debugger.

About Fedora and requirements... this is what is written in the README


Linux system with glibc 2.2.93, 2.3.2 , 2.3.3, 2.3.4, 2.3.5 or 2.5 and the 2.4.X or 2.6.X Linux kernel as represented by the following distributions. Note: Not all distributions listed are validated and not all distributions are listed.

    * Fedora* Core 6
    * Mandriva* Linux 2007
    * Red Flag* DC Server 5.0
    * Red Hat Enterprise Linux* 3, 4, 5
    * SGI* ProPack* 4, 5
    * SUSE LINUX Enterprise Server* 9, 10
    * TurboLinux* 10

# Linux Developer tools component installed, including gcc 3.2 or later, g++ and related tools.
# Linux component compat-libstdc++ providing libstdc++.so.5

---

### Post by BC59 on 2011-12-13
You have right, it's very complicated the guide!

I see that you have to install **alien**. Install it from Ubuntu Software Center.

Install 32bit libraries as well:

```
apt-get install ia32-libs
```

After that try again to see if you have less error messages.

---

### Post by cardogar on 2011-12-13
The ia32-libs were installed and tried installing alien...

Thanks... but again the same errors... not a single difference...

Running out of ideas :confused:

---

### Post by BC59 on 2011-12-13
you have to open the l_fc_c_10.0.026_intel64.tar.gz file and extract the .rpm then run

```
sudo alien -i [COLOR="Blue"]package_file[/COLOR].rpm
```

Then alien will produce a .deb file and try to install it with double click on it (it opens the Ubuntu Software Center).

---

### Post by N00b-un-2 on 2011-12-13
in my experience, using open-jdk for anything that specifically calls for the java-jdk will result in build failures.  i would recommend installing the proprietary JDK.

As for the rest of your issues, it's not impossible to install anything from source, given you satisfy the build prereqs.  Typically what I do when trying to install something from source is go through the ./configure and make commands, and use apt-file to search for dependencies when building spits out unsatisfied dependency errors.  It's a difficult and time consuming process, but in the end it's always worth it.  If all else fails, there is always google.

---

### Post by N00b-un-2 on 2011-12-13
> **BC59 said:**
> you have to open the l_fc_c_10.0.026_intel64.tar.gz file and extract the .rpm then run

```
sudo alien -i [COLOR="Blue"]package_file[/COLOR].rpm
```

Then alien will produce a .deb file and try to install it with double click on it (it opens the Ubuntu Software Center).

In this instance I would highly recommend using sudo dpkg -i *.deb to install.  It will give you a better idea of what is wrong if the package fails to install.  Ubuntu software center is buggy at best and very dumbed down for the computer illiterate masses.

---

### Post by BC59 on 2011-12-13
> **N00b-un-2 said:**
> In this instance I would highly recommend using sudo dpkg -i *.deb to install.  It will give you a better idea of what is wrong if the package fails to install.  Ubuntu software center is buggy at best and very dumbed down for the computer illiterate masses.

For many reasons it's highly recommended to use Ubuntu Software Center. One of them is that is much easier to uninstall. And we have to recommend to the new users to use GUI tools instead of terminal commands.

---

### Post by cardogar on 2011-12-13
Thanks for your kind replies and suggestions. I will carefully read and try them all tomorrow.

By the way, I made the same question in the intel forum and I got the following answer:

"That version of the compiler is old relative to your OS.  Current 12.1 should be much easier, not requiring any optional stuff from Ubuntu beyond the standard g++.
You would require the complete g++ development system installation for both 32- and 64-bit mode, if you want to install the 32-bit ifort.  You shouldn't need the entire 32-bit g++ for the 64-bit ifort on the x86_64 OS.
As the instructions you refer to indicate, you also need both the 32- and 64-bit libstdc++-33, even if you are installing only the 64-bit ifort. These libstdc++-5 requirements are gone since ifort 12.0."

Not really helpful though, since I have to install that version due to compilation constraints of the software that I need to compile. But maybe you could get some new ideas.

Thanks again and I will be back with my feedback.

---

### Post by N00b-un-2 on 2011-12-13
dpkg -l | grep *package name*
sudo dpkg -r *what grep returns*

I fail to see how that is different or more difficult than opening the software center, searching for the package and then uninstalling it.

---


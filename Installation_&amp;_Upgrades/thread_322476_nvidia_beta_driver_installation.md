---
title: "nvidia beta driver installation"
date: 2006-12-20
forum: Installation &amp; Upgrades
---

### Post by mendingo84 on 2006-12-20
can someone plz help me?
 i tried the following way:
 installed kernel-headers ( sudo apt-get install kernel-headers-$(uname -r) )
 downloaded beta driver from nvidia site
 stopped kdm
 entered sudo sh NVIDIA...
 but it gives me an error
 this is the log of nvidia-installer
 
 > 
 option status:
 license pre-accepted : false
 update : false
 force update : false
 expert : false
 uninstall : false
 driver info : false
 precompiled interfaces : true
 no ncurses color : false
 query latest version : false
 OpenGL header files : true
 no questions : false
 silent : false
 no recursion : false
 no backup : false
 kernel module only : false
 sanity : false
 add this kernel : false
 no runlevel check : false
 no network : false
 no ABI note : false
 no RPMs : false
 no kernel module : false
 force SELinux : default
 no X server check : false
 force tls : (not specified)
 X install prefix : (not specified)
 X library install path : (not specified)
 X module install path : (not specified)
 OpenGL install prefix : (not specified)
 OpenGL install libdir : (not specified)
 utility install prefix : (not specified)
 utility install libdir : (not specified)
 doc install prefix : (not specified)
 kernel name : (not specified)
 kernel include path : (not specified)
 kernel source path : (not specified)
 kernel output path : (not specified)
 kernel install path : (not specified)
 proc mount point : /proc
 ui : (not specified)
 tmpdir : /tmp
 ftp mirror : [ftp://download.nvidia.com](ftp://download.nvidia.com)
 RPM file list : (not specified)
 
 Using: nvidia-installer ncurses user interface
 -> License accepted.
 -> No precompiled kernel interface was found to match your kernel; would you li
 ke the installer to attempt to download a kernel interface for your kernel f
 rom the NVIDIA ftp site ([ftp://download.nvidia.com)?](ftp://download.nvidia.com)?) (Answer: Yes)
 -> No matching precompiled kernel interface was found on the NVIDIA ftp site;
 this means that the installer will need to compile a kernel interface for
 your kernel.
 -> Performing CC sanity check with CC="cc".
 -> Performing CC version check with CC="cc".
 -> Kernel source path: '/lib/modules/2.6.17-10-generic/build'
 -> Kernel output path: '/lib/modules/2.6.17-10-generic/build'
 -> Performing rivafb check.
 -> Performing nvidiafb check.
 ERROR: Unable to determine the NVIDIA kernel module filename.
 ERROR: Installation has failed. Please see the file
 '/var/log/nvidia-installer.log' for details. You may find suggestions
 on fixing installation problems in the README available on the Linux
 driver download page at [www.nvidia.com](www.nvidia.com).

 
i've been trying to install compiz on edgy kde with nvidia for a month now

---

### Post by _simon_ on 2006-12-20
> 
No precompiled kernel interface was found to match your kernel; would you li
ke the installer to attempt to download a kernel interface for your kernel f
rom the NVIDIA ftp site ([ftp://download.nvidia.com)?](ftp://download.nvidia.com)?)


I always answer NO to that...

Other than that I dunno?

---

### Post by po0f on 2006-12-20
mendingo84,

Did you even read the error message?
[quote=NVIDIA installer]... ERROR: Unable to determine the NVIDIA kernel module filename.
ERROR: Installation has failed. [b]Please see the file
'/var/log/nvidia-installer.log' for details[/b]. You may find suggestions
on fixing installation problems in the README available on the Linux
driver download page at [www.nvidia.com](www.nvidia.com). ...[/quote]
Bolded to make it stand out.

---

### Post by _simon_ on 2006-12-20
> **po0f said:**
> mendingo84,

Did you even read the error message?

Bolded to make it stand out.

I believe that's what they have posted ;)

---

### Post by po0f on 2006-12-20
_simon_,

Why would an error log refer to itself?

---

### Post by mannheim on 2006-12-20
I don't know if this is the issue, but with the 9631 insaller from nvidia's website there is a problem caused by the difference between the two shells bash and dash.

edgy links /bin/sh to "dash" not "bash", which causes nvidia's installer script to fail. The solution is to do this before running the installer:
```
sudo ln -sf /bin/bash /bin/sh
```
After running the installer, you can undo this by:
```
sudo ln -sf /bin/dash /bin/sh
```
This worked for me in a similar situation, but I can't remember if it was the same error message.

EDIT: It might have been the 9742 driver. (I have two machines, one has one driver, one the other.)

---

### Post by _simon_ on 2006-12-20
> **po0f said:**
> _simon_,

Why would an error log refer to itself?

I don't know, but they say "this is the log of nvidia-installer"

---

### Post by po0f on 2006-12-20
mannheim,

A much safer way of doing that would be to run:
```
[FONT="Courier New"]$ sudo dpkg-reconfigure dash[/FONT]
```


[EDIT]

mendingo84,

Which howto are you following to install the beta drivers?

---

### Post by mid_night gypsy on 2006-12-20
mendingo84,
 Maybe this link to envy (The easy nvidia installer script) will help...(answer "y" yes )to the two questions.
                                       [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by mendingo84 on 2006-12-20
oh well, i followed more than one...but this seemed to be the fair way...it is annoying because what i really am trying to do is to install compiz. it should be simple on edgy but it turns that there are two options:
1. either am i an idiot as i am trying to install it for a month
2. there is not one! good howto on installing compiz and not one! howto on installing nvidia beta...

oh, and one more thing, why the hell can i not remove compiz-plugins and compiz core? 
> 
Removing compiz-plugins ...
/var/lib/dpkg/info/compiz-plugins.prerm: 6: gconf-schemas: not found
dpkg: error processing compiz-plugins (--purge):
 subprocess pre-removal script returned error exit status 127
dpkg: compiz-core: dependency problems, but removing anyway as you request:
 compiz-plugins depends on compiz-core (= 1:0.3.3-0ubuntu2~git2006112~edgy1).
Removing compiz-core ...
/var/lib/dpkg/info/compiz-core.prerm: 6: gconf-schemas: not found
dpkg: error processing compiz-core (--purge):
 subprocess pre-removal script returned error exit status 127
Errors were encountered while processing:
 compiz-plugins
 compiz-core
E: Sub-process /usr/bin/dpkg returned an error code (1)


---

### Post by mannheim on 2006-12-20
> **po0f said:**
> 
A much safer way of doing that would be to run:
```
[FONT="Courier New"]$ sudo dpkg-reconfigure dash[/FONT]
```

Ah, thanks. I didn't know one could do that.

---


---
title: "nvidia-current not fully installed"
date: 2011-08-04
forum: Installation &amp; Upgrades
---

### Post by Jasev on 2011-08-04
Hi,

I ran a normal "apt-get upgrade" on my 11.04 mythbuntu system yesterday and nvidia-current didn't install properly.

Now I can only log into my box using ssh. When I try and run an upgrade I always get the error below:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up nvidia-current (270.41.06-0ubuntu1) ...
update-alternatives: error: alternative link /usr/share/man/man1/nvidia-xconfig.1.gz is already managed by i386-linux-gnu_gl_conf.
dpkg: error processing nvidia-current (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 nvidia-current
```

Reading various posts I have tried to remove the existing alternative-link by (although I don't really understand the alternative-link business): 

```
sudo update-alternatives --remove i386-linux-gnu_gl_conf /usr/share/man/man1/nvidia-settings.1.gz

```

I tried purging nvidia-current and reinstalling but that didn't help. Any suggestions?

Thanks

Jason

---

### Post by thefasterblueone on 2011-08-04
Run this command:

```
sudo dpkg --configure -a
```

---

### Post by Jasev on 2011-08-04
No luck. Same error.

```
jason@mini:~$ sudo dpkg --configure -a
[sudo] password for jason: 
Setting up nvidia-current (270.41.06-0ubuntu1) ...
update-alternatives: error: alternative link /usr/share/man/man1/nvidia-xconfig.1.gz is already managed by i386-linux-gnu_gl_conf.
dpkg: error processing nvidia-current (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 nvidia-current
```

Do I need to stop i386-linux-gnu_gl_conf 'managing' nvidia or something?

---

### Post by Duncan Williams on 2011-08-04
[I]dino99 stated:
the easiest way is to purge the installed "nvidia" packages, install [dkms]("ttp://en.wikipedia.org/wiki/Dynamic_Kernel_Module_Support") and finally reinstall nvidia-current (can be easily done using synaptic)[/I]

does this work?

I had same problem on last kernel update (as in it blew my nvidia drivers and forced me to re-install).
also this would have to be done from command-line as I couldn't get gui up.
what would the commands be?

---

### Post by jim.hansson on 2012-09-09
> **Jasev said:**
> 
```
sudo update-alternatives --remove i386-linux-gnu_gl_conf /usr/share/man/man1/nvidia-settings.1.gz

```I tried purging nvidia-current and reinstalling but that didn't help. Any suggestions?

Thanks

Jason

That did not work for me either, but this did
```

sudo update-alternatives --force --remove-all i386-linux-gnu_gl_conf

```After this I did get some warnings, but proceeded to install nvidia-current

```

Setting up nvidia-current (295.40-0ubuntu1.1) ...
update-alternatives: using /usr/lib/nvidia-current/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-alternatives: using /usr/lib/nvidia-current/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.

```I take that as the (two) alternative group(s) has been re-created by the install somehow.

---


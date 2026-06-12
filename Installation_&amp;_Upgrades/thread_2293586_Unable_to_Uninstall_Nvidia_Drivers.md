---
title: "Unable to Uninstall Nvidia Drivers"
date: 2015-09-06
forum: Installation &amp; Upgrades
---

### Post by jmarsz on 2015-09-06
So I'm currently having issues with my current Nvidia drivers (get a black screen when the computer comes up, but if I enter the password, it will log in).  When I try to run "sudo apt-get purge nvidia*" I get the following:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package nvidia-install.txt
E: Couldn't find any package by regex 'nvidia-install.txt'

Any idea why it thinks that the nvidia-install.txt is a package?  I'm guessing this file is somewhere it shouldn't be, just not too sure where exactly...

---

### Post by hansdown on 2015-09-06
Hi jmarsz.

Is this a virtual install?

---

### Post by efflandt on 2015-09-06
Which nvidia driver package do you have installed now. In other words what do you get for:```
dpkg-query -l nvidia* | grep ii
```Although, I got strange or no results for that when I had some file with nvidia in its name in my home directory. So maybe such a file in your home directory is tripping up apt-get with nvidia* wildcard.

---

### Post by jmarsz on 2015-09-06
This is not a virtual install, and this is what I got when I ran that command:

jmarsz@Sager:~$ dpkg-query -l nvidia* | grep ii
dpkg-query: no packages found matching nvidia-install.txt

---

### Post by MAFoElffen on 2015-09-06
efflandt & OP-- I think you might have hit it. 

I know in the past (about 3 years ago or so) , for about a 3-month period, where using an "nvidia*"  wildcard when trying to remove the nvidia packages didn't work as expected. During that period, we had to list the nvidia packages that were installed, then manually remove each package that was installed (use the name from that list). Don't remember why that was, but removing them individually by package_name worked back then, so...

---

### Post by Dale61 on 2015-09-08
As explained elsewhere, I have returned as an Ubuntu user, and when I tried to install restricted drivers, as instructed, all I got in return was a black screen; no cursor, no way of knowing what was happening.  All I could do was turn off the laptop, so I decided to reinstall from scratch.  I upgraded until I was current, but there is now no need to install restricted drivers as the replacement has been installed instead.

I have missed so much in the three years I have been away!

---

### Post by jmarsz on 2015-09-18
Even after removing all the Nvidia drivers, and installing them from the additional drivers section, I still get a black screen when I try to log in.  If I have the Noveau drivers loaded, I can see the login screen.  It's only when I'm running the nvidia drivers do I have this issue.  Any suggestions?

---

### Post by MAFoElffen on 2015-09-18
You started this out with "I can't purge nvidia drivers." You skipped a few step in letting us know what your main complaint is (that is in your last post)... and what you are working on (make & model, so we can look up the specs).

Please post the results of (from recovery root prompt):
```

lspci -vnn : grep -i VGA && lshw -n -c video

```
That would show us what the hardware is ID'ed by via linux.

Next is post your /etc/X11/xorg.conf file and your /var/logs/Xorg.0.log file that is where you tried to load the nvidia drivers. The "0" in that denotes current. "1" would be 1 times past. Xorg.2.log would be 2 times before current.  For instance, if load the nvidia driver and it frags, then reboot to recovery... copy over from a root prompt... or if you can boot it on another (via renaming the xorg.conf to anything else, then rebooting again... then it would be 1 past... 

Do you need any more info to be able to get those for us?

---

### Post by jmarsz on 2015-09-19
I kind of wrote the last post in a bit of a hurry, so let me give everyone and update:

Originally I wasn't unable to uninstall the Nvidia drivers due to it trying to uninstall the "nvidia-install.txt" file.  I found out that when I typed:

```
sudo apt-get purge nvidia*
```

It was trying to run against a file I had in my home directory.  Once I got rid of that file, I was able to uninstall and re-install the driver.  I am still having the issue though where when the computer (which is a Sager laptop with both an Nvidia card and the Intel graphics) come up to the login screen, I just get a black screen when I'm running the Nvidia card.  I can still enter my password and get logged in (and the screen does come back), it's only when I'm at the login screen on the Nvidia card does it display black.  When I'm on the Intel graphics, I can see it just fine...

---

### Post by MAFoElffen on 2015-09-20
You said you re-installed your nVidia driver, but have not installed nVidia Prime yet? Once you have your nvidia driver installed then:
```

sudo apt-get install nvidia-prime

```
You have hybrid graphics, so you need nVidia Prime to do your GPU and driver switches. Once that is installled, go into the nVidia control panel and configure your driver.

---

### Post by jmarsz on 2015-10-02
Sorry about the delay in responding, been a crazy week at work.  I believe the nvidia-prime is installed, as when I go into the Nvidia settings, change it to the Intel video driver, and then log out and back in, the login screen shows up.  It's only when I'm running the Nvidia card do I not see the login screen.

---

### Post by Bashing-om on 2015-10-02
jmarsz; Hello;

I refer you back to MAFoElffen's post # 8 . There is little to be done until the hardware is identified.

Once the correct driver for the hardware is installed properly, if problems continue, then it is time to consult the log files and see what the system reports.

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by jmarsz on 2015-10-02
I'll get that info for you guys this afternoon, and will post the results. :)

---

### Post by jmarsz on 2015-10-02
Here's my output:

```
root@Sager:/home/jmarsz# sudo lspci -vnn | grep -i VGA && lshw -c video
00:02.0 VGA compatible controller [0300]: Intel Corporation 3rd Gen Core processor Graphics Controller [8086:0166] (rev 09) (prog-if 00 [VGA controller])
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GK104M [GeForce GTX 680M] [10de:11a0] (rev a1) (prog-if 00 [VGA controller])
  *-display               
       description: VGA compatible controller
       product: GK104M [GeForce GTX 680M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:51 memory:f6000000-f6ffffff memory:e0000000-efffffff memory:f0000000-f1ffffff ioport:e000(size=128) memory:f7000000-f707ffff
  *-display
       description: VGA compatible controller
       product: 3rd Gen Core processor Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:47 memory:f7400000-f77fffff memory:d0000000-dfffffff ioport:f000(size=64)

```

---

### Post by Bashing-om on 2015-10-02
jmarsz; Welp;

Nvidia recommends the 352 version driver, what do you have installed ?
```

dpkg -l | grep -i nvidia

```
maybe a conflict in drivers ? Maybe a conflict in controllers ?.. the output will tale a tale.

[INDENT]seek and ye shall find
[/INDENT]

---

### Post by jmarsz on 2015-10-02
Here's that output:

```
root@Sager:/home/jmarsz# dpkg -l | grep -i nvidia
ii  bbswitch-dkms                                         0.7-2ubuntu1                                            amd64        Interface for toggling the power on nVidia Optimus video cards
rc  libcublas5.5:amd64                                    5.5.22-3ubuntu1                                         amd64        NVIDIA CUDA BLAS runtime library
rc  libcuda1-331                                          331.113-0ubuntu0.0.4                                    amd64        NVIDIA CUDA runtime library
ii  libcuda1-346                                          346.96-0ubuntu0~gpu14.04.2                              amd64        NVIDIA CUDA runtime library
rc  libcuda1-355                                          355.06-0ubuntu0~xedgers14.04.1                          amd64        NVIDIA CUDA runtime library
rc  libcudart5.5:amd64                                    5.5.22-3ubuntu1                                         amd64        NVIDIA CUDA runtime library
rc  libcufft5.5:amd64                                     5.5.22-3ubuntu1                                         amd64        NVIDIA CUDA FFT runtime library
rc  libcufftw5.5:amd64                                    5.5.22-3ubuntu1                                         amd64        NVIDIA CUDA FFTW runtime library
rc  libcuinj64-5.5:amd64                                  5.5.22-3ubuntu1                                         amd64        NVIDIA CUDA INJ runtime library (64-bit)
rc  libcurand5.5:amd64                                    5.5.22-3ubuntu1                                         amd64        NVIDIA CUDA Random Numbers Generation runtime library
rc  libcusparse5.5:amd64                                  5.5.22-3ubuntu1                                         amd64        NVIDIA CUDA Sparse Matrix runtime library
rc  libnppc5.5:amd64                                      5.5.22-3ubuntu1                                         amd64        NVIDIA Performance Primitives core runtime library
rc  libnppi5.5:amd64                                      5.5.22-3ubuntu1                                         amd64        NVIDIA Performance Primitives for image processing runtime library
rc  libnpps5.5:amd64                                      5.5.22-3ubuntu1                                         amd64        NVIDIA Performance Primitives for signal processing runtime library
rc  libnvtoolsext1:amd64                                  5.5.22-3ubuntu1                                         amd64        NVIDIA Tools Extension
rc  libnvvm2:amd64                                        5.5.22-3ubuntu1                                         amd64        NVIDIA CUDA Compiler NVVM runtime library
ii  nvidia-346                                            346.96-0ubuntu0~gpu14.04.2                              amd64        NVIDIA binary driver - version 346.96
ii  nvidia-opencl-icd-346                                 346.96-0ubuntu0~gpu14.04.2                              amd64        NVIDIA OpenCL ICD
ii  nvidia-prime                                          0.6.2                                                   amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings                                       355.11-0ubuntu0~gpu14.04.1                              amd64        Tool for configuring the NVIDIA graphics driver

```

---

### Post by Bashing-om on 2015-10-03
jmarsz; Humm ...

Getting above my skill level ? I see nothing amiss in what is installed. The 346 version driver I do expect to perform.
Grasping at straws here, the only thing I see that I can question is the support for " nvidia-opencl-icd-346 " .
What returns:
```

sudo apt update
sudo apt upgrade
sudo apt-get -f install
dpkg -l libc6
dpkg -l ocl-icd-libopencl1

```
As we have in the dependency tree:
> 
Depends: libc6 (>= 2.2.5), nvidia-libopencl1-346 | ocl-icd-libopencl1


Might be a good idea to look a new look at the log files and the config file:
```

cat /var/log/Xorg.0.log
cat ~/.xsession-errors
cat /etc/X11/Xorg.conf

```
see if that points us in  any direction.

At some point we can cleanup all those packages that have the mark 'rc' ( r-emoved but c-onfig files remain ). That is minor and more cosmetic .
--------------------
Whoa ! .. I have something !
```

apt-cache show nvidia-settings

```
Which shows to be Version: 331.20-0ubuntu8
So, where is that elevated version coming from ?
what returns:
```

apt-cache policy nvidia-settings

```

[INDENT][INDENT]another of those times
[INDENT][INDENT][INDENT]I do wonder
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---


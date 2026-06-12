---
title: "Unity Freezes are login : post upgrade"
date: 2015-04-11
forum: Installation &amp; Upgrades
---

### Post by Tim_Johnson on 2015-04-11
Just upgraded from 12.04 to 14.04 - using update manager, not a fresh install.
Unity freezes after logging in. Not in itself tragic as this is my wife's computer and she doesn't use unity, opting instead for gnome/metacity.
However, in case this is a "canary in the coalmine", I have tried the following as per [http://itsfoss.com/fix-unity-freezes-after-login-ubuntu-14-04/](http://itsfoss.com/fix-unity-freezes-after-login-ubuntu-14-04/)
```

sudo apt-get update
sudo apt-get install --reinstall ubuntu-desktop
sudo apt-get install unity
sudo shutdown -r now
```
Nothing changes. 
The content of the page above goes on to suggest reinstallaing graphics drivers.
I see the following command ```
sudo apt-get -purge nivia*
```
**but** I don't see the commands to re-install.
Here is some info from the system on dpkg and drivers ```

barbara@barbara:~$ lspci -vnn | grep VGA
00:0d.0 VGA compatible controller [0300]: NVIDIA Corporation C61 [GeForce 6150SE nForce 430] [10de:03d0] (rev a2) (prog-if 00 [VGA controller])
barbara@barbara:~$ dpkg -l nvidia*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                               Version                        Architecture                   Description
+++-==================================================-==============================-==============================-===============================================================================
ii  nvidia-173                                         173.14.39-0ubuntu3             i386                           NVIDIA legacy binary driver - version 173.14.39
rc  nvidia-96                                          96.43.23-0ubuntu0.1            i386                           NVIDIA binary Xorg driver, kernel module and VDPAU library
un  nvidia-96-modaliases                               <none>                         <none>                         (no description available)
ii  nvidia-common                                      1:0.2.91.7                     i386                           transitional package for ubuntu-drivers-common
un  nvidia-prime                                       <none>                         <none>                         (no description available)
ii  nvidia-settings                                    331.20-0ubuntu8                i386                           Tool for configuring the NVIDIA graphics driver
un  nvidia-settings-binary                             <none>                         <none>                         (no description available)
un  nvidia-vdpau-driver                                <none>                         <none>                         (no description available)
```
Please advise on how to procede (which commands to re-install drivers)
thanks
tim

---

### Post by Tim_Johnson on 2015-04-12
Maybe I should posted this under _Reinstalling Nvidia_ or something like that.

---

### Post by Tim_Johnson on 2015-04-12
No luck. Tried re-installing nvidia, based on lspci. Tried nvidia-304 and that just made things worse as far as unity goes.
Then tried nvidia-current, some result, but gnome/metacity remains fully functional and looks good.

The machine is a Compaq Presario CQ5320Y, at least 5 years old with 3 GB RAM. I have nothing against unity, but as far as an older machine goes,
gnome is just fine. In fact, if I were to do a fresh install, I'd probably go with Lubuntu. Works greats on the old netbooks we having laying around here.
I'm not going to mark this solved, but will try nothing further unless anyone else has an idea.

Too bad a thread can't be marked "unsolved" after a period of time, but I'd guess that would be a feature that some would abuse.

cheers
tim

---


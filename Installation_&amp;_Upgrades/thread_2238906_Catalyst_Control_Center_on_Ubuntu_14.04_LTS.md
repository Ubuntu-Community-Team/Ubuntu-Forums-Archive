---
title: "Catalyst Control Center on Ubuntu 14.04 LTS?"
date: 2014-08-10
forum: Installation &amp; Upgrades
---

### Post by Riothamus on 2014-08-10
I just upgraded to Ubuntu 14.04 LTS from 12.04. Previously, I had had Catalyst Control Center installed and working, but an error occurred during the upgrade which said that restoring the previously-installed packages failed, and I would need to install some of them manually. Catalyst Control Center is one package that is no longer installed.

My graphics card is an ATI Radeon 3000, which is no longer being supported on AMD's website, so I can't get the driver there. I Googled this problem a bit and came across [this post]("http://askubuntu.com/questions/450394/amd-catalyst-installation") but once I got to the part about typing "legacy catalyst control" into the Software Center, it didn't come up when I typed that. Catalyst Legacy also doesn't come up when I click "More."

So then I found [this page]("https://help.ubuntu.com/community/BinaryDriverHowto/AMD") and was getting ready to install follow the instructions under step 2 when I found [this Reddit post]("http://www.reddit.com/r/Ubuntu/comments/23gcr0/if_youre_using_1404_dont_install_the_radeon") which says that Catalyst Control Center will not work on the kernel that's being used by Ubuntu 14.04. Another interesting thing is that there's no xorg.conf file in my /etc/X11 directory.

So now I'm not sure if I should continue with this or not, as I'm afraid I might mess something up without knowing what I'm doing. Hoping someone who knows more about this can advise me on whether there is a way to get my old Catalyst Control Center working for my graphics card. Or maybe I shouldn't have upgraded from 12.04? Hoping someone can help. Thanks.

---

### Post by grahammechanical on 2014-08-10
> [COLOR=#000000] there's no xorg.conf file in my /etc/X11 directory.[/COLOR]

Not on my system either. Ubuntu Utopic Unicorn. That is standard

> [COLOR=#333333][FONT=Ubuntu Beta]Today's X rarely requires manual configuration. X now automatically configures itself with reasonable defaults. Both GNOME and KDE provide GUI utilities for customizing settings beyond these defaults if you like.

[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu Beta]Most systems don't ship with an X config file any more, but sometimes you need one.[/FONT][/COLOR]

[https://wiki.ubuntu.com/X/Config](https://wiki.ubuntu.com/X/Config)

Search in the software centre for fglrx catalyst and that might get you somewhere.

Regards.

---

### Post by Riothamus on 2014-08-11
Thanks for the response.

Unfortunately, it seems that I did screw something up while I was trying to follow the instructions on one of the links I posted before. Now, my graphics card is not working at all, and whenever I try to start Ubuntu, I get an error that it detected a system error and gives me an option to report the problem, but nothing else is displayed. The screen is completely dark except for the mouse cursor, which looks like an X. Sometimes, it gives me the option to start in low-graphics mode, but then when I choose that option it just sits there with the dark screen again. (I'm now writing this to you from my Windows partition.)

I've tried inserting the Ubuntu installation disc to try to repair the installation, but it doesn't have that option. The only options available are to remove Ubuntu Completely, remove it completely and reinstall, or "Something Else" which takes me to a screen for resizing my partitions. I've also tried loading Ubuntu in recovery mode, which works, but again, the graphics don't work, so I can only access the recovery mode menu options or the shell. I've tried removing and installing the fglrx, fglrx-updates, and fglrx-dev packages and rebooting, but I'm still getting the same error.

Worse yet, I didn't backup before upgrading to 14.04. I know, stupid stupid me, but I honestly did not expect for there to be this many issues, or for the graphics driver to stop working completely. So, short of trying to remember every file I need, manually copying them to a flash drive, and then doing the remove Ubuntu and then reinstall option, do you have any other ideas how I can get my system working again? Would it make more sense to try to install 12.04 again (if that's even an option)? Any help? Thanks.

---

### Post by Mark Phelps on 2014-08-11
Try following the instructions in the link for removing the fglrx drivers -- the default Radeon drivers will be installed in their place and should work: [https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

---

### Post by Riothamus on 2014-08-11
Unfortunately, still no change. To be clear, what I did was I followed the link to [https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection#Problem:_Need_to_purge_-fglrx](https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection#Problem:_Need_to_purge_-fglrx) and then entered the commands:

```

sudo apt-get remove --purge xorg-driver-fglrx fglrx*
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo dpkg-reconfigure xserver-xorg

```

And then rebooted. When I ran  dpkg --get-selections|grep libgl1-mesa it said both libgl1-mesa-glx and libgl1-mesa-dri were :amd64 so I also tried specifically specifying them in the sudo apt-get install --reinstall command. Although, I don't think that was necessary, because it listed the :amd64 specification while it was installing them the first time.

---

### Post by QIII on 2014-08-11
Hello!

Your Reddit article is utterly wrong.  The fglrx driver and Catalyst Control Center do work in 14.04.  I use them.

Your problem is that ATI no longer supports your card in any version beyond 12.04.1.   With that card, you will need to use the default open source Radeon driver (which you have been trying to re-install).  So don't be tempted to try to install fglrx again.

Would you please check to see if you have any bits of the fglrx driver lying around.  Please issue the following commands and post the results back (get a picture with your cell phone if needed.)

```
dpkg -l '*fglrx*'
```

(that's a lower case L)

and then

```
locate fglrx
```

---

### Post by Riothamus on 2014-08-11
Thanks, and sorry for the delay in getting back to you. I had a bit of trouble getting my hands on a phone today, unfortunately, and finally just realized I could mount my Windows partition and then echo the output to a file there, to copy and paste to you here.

This is the output of dpkg -l '*fglrx*':
```

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                                  Version                                             Architecture Description
+++-=====================================================-===================================================-============-===============================================================================
ii  fglrx                                                 2:13.350.1-0ubuntu2                                 amd64        Video driver for the AMD graphics accelerators
ii  fglrx-amdcccle                                        2:13.350.1-0ubuntu2                                 amd64        Catalyst Control Center for the AMD graphics accelerators
un  fglrx-amdcccle-updates                                <none>                                              <none>       (no description available)
un  fglrx-control                                         <none>                                              <none>       (no description available)
un  fglrx-control-qt2                                     <none>                                              <none>       (no description available)
un  fglrx-driver                                          <none>                                              <none>       (no description available)
un  fglrx-glx                                             <none>                                              <none>       (no description available)
rc  fglrx-updates                                         2:13.350.1-0ubuntu2                                 amd64        Video driver for the AMD graphics accelerators

```

And here is the output of locate fglrx:

```

/etc/apt/sources.list.d/makson96-fglrx-trusty.list
/etc/apt/trusted.gpg.d/makson96-fglrx.gpg
/etc/apt/trusted.gpg.d/makson96-fglrx.gpg~
/home/arlo/.cache/software-center/rnrclient/reviews.ubuntu.com,reviews,api,1.0,reviews,filter,en,ubuntu,natty,any,fglrx-amdcccle,page,1,,753c579cc12b883c7a5c49f351400067
/usr/share/app-install/desktop/fglrx-driver.desktop
/usr/share/apport/package-hooks/source_fglrx-installer-experimental-9.py
/usr/share/apport/package-hooks/source_fglrx-installer-updates.py
/usr/share/apport/package-hooks/source_fglrx-installer.py
/usr/src/fglrx-8.840
/usr/src/fglrx-8.970
/usr/src/fglrx-8.840/2.6.x
/usr/src/fglrx-8.840/dkms.conf
/usr/src/fglrx-8.840/drm.h
/usr/src/fglrx-8.840/drmP.h
/usr/src/fglrx-8.840/drm_compat.h
/usr/src/fglrx-8.840/drm_os_linux.h
/usr/src/fglrx-8.840/drm_proc.h
/usr/src/fglrx-8.840/fglrxko_pci_ids.h
/usr/src/fglrx-8.840/firegl_public.c
/usr/src/fglrx-8.840/firegl_public.h
/usr/src/fglrx-8.840/kcl_acpi.c
/usr/src/fglrx-8.840/kcl_acpi.h
/usr/src/fglrx-8.840/kcl_agp.c
/usr/src/fglrx-8.840/kcl_agp.h
/usr/src/fglrx-8.840/kcl_config.h
/usr/src/fglrx-8.840/kcl_debug.c
/usr/src/fglrx-8.840/kcl_debug.h
/usr/src/fglrx-8.840/kcl_io.c
/usr/src/fglrx-8.840/kcl_io.h
/usr/src/fglrx-8.840/kcl_ioctl.c
/usr/src/fglrx-8.840/kcl_ioctl.h
/usr/src/fglrx-8.840/kcl_osconfig.h
/usr/src/fglrx-8.840/kcl_pci.c
/usr/src/fglrx-8.840/kcl_pci.h
/usr/src/fglrx-8.840/kcl_str.c
/usr/src/fglrx-8.840/kcl_str.h
/usr/src/fglrx-8.840/kcl_type.h
/usr/src/fglrx-8.840/kcl_wait.c
/usr/src/fglrx-8.840/kcl_wait.h
/usr/src/fglrx-8.840/libfglrx_ip.a
/usr/src/fglrx-8.840/make.sh
/usr/src/fglrx-8.840/patches
/usr/src/fglrx-8.840/2.6.x/Makefile
/usr/src/fglrx-8.840/patches/add-compatibility-with-2.6.36-kernels.patch
/usr/src/fglrx-8.840/patches/fglrx-2.6.37.patch
/usr/src/fglrx-8.840/patches/rt_preempt_28.patch
/usr/src/fglrx-8.840/patches/rt_preempt_31.patch
/usr/src/fglrx-8.840/patches/use-cflags_module-together-with-modflags.patch
/usr/src/fglrx-8.970/2.6.x
/usr/src/fglrx-8.970/dkms.conf
/usr/src/fglrx-8.970/drm.h
/usr/src/fglrx-8.970/drmP.h
/usr/src/fglrx-8.970/drm_compat.h
/usr/src/fglrx-8.970/drm_os_linux.h
/usr/src/fglrx-8.970/drm_proc.h
/usr/src/fglrx-8.970/fglrxko_pci_ids.h
/usr/src/fglrx-8.970/firegl_public.c
/usr/src/fglrx-8.970/firegl_public.h
/usr/src/fglrx-8.970/kcl.c
/usr/src/fglrx-8.970/kcl.h
/usr/src/fglrx-8.970/kcl_acpi.c
/usr/src/fglrx-8.970/kcl_acpi.h
/usr/src/fglrx-8.970/kcl_agp.c
/usr/src/fglrx-8.970/kcl_agp.h
/usr/src/fglrx-8.970/kcl_config.h
/usr/src/fglrx-8.970/kcl_debug.c
/usr/src/fglrx-8.970/kcl_debug.h
/usr/src/fglrx-8.970/kcl_io.c
/usr/src/fglrx-8.970/kcl_io.h
/usr/src/fglrx-8.970/kcl_ioctl.c
/usr/src/fglrx-8.970/kcl_ioctl.h
/usr/src/fglrx-8.970/kcl_iommu.c
/usr/src/fglrx-8.970/kcl_iommu.h
/usr/src/fglrx-8.970/kcl_osconfig.h
/usr/src/fglrx-8.970/kcl_pci.c
/usr/src/fglrx-8.970/kcl_pci.h
/usr/src/fglrx-8.970/kcl_str.c
/usr/src/fglrx-8.970/kcl_str.h
/usr/src/fglrx-8.970/kcl_type.h
/usr/src/fglrx-8.970/kcl_wait.c
/usr/src/fglrx-8.970/kcl_wait.h
/usr/src/fglrx-8.970/libfglrx_ip.a
/usr/src/fglrx-8.970/make.sh
/usr/src/fglrx-8.970/patches
/usr/src/fglrx-8.970/2.6.x/Makefile
/usr/src/fglrx-8.970/patches/rt_preempt_28.patch
/usr/src/fglrx-8.970/patches/rt_preempt_31.patch

```

My main need for Catalyst Control Center is that I have a widescreen monitor, and when running older software, I need to be able to set the graphics card to send the data to the monitor as-is, without having the monitor stretch it (I'm using the HD cable for that, rather than the standard VGA one). Is this something which is possible to do with the generic driver? If not, then I will need to look into a way to downgrade back to 12.04. Maybe you can tell me whether it's worth the trouble trying to fix the 14.04 installation, if I'm just going to have to downgrade anyway?

Thanks again!

---

### Post by QIII on 2014-08-12
Hi again!

It is clear that you still have a number of pieces of fglrx scattered around.  It is also clear that you installed that from the makson96 PPA at least once in the past -- a route I have been recommending against for two years for just such reasons.  I don't know how to tell you how to undo the changes that PPA made, since it effectively broke your installation -- which I have also been saying for a couple of years.  You might have a look at the instructions that led you to use that PPA and see if there are instructions to back out the changes made.  

You probably won't be able to make any headway until you can remove all of that.  Using that PPA, also locks the X Server to an out-dated version.

Unfortunately, I don't think I can help much with this at the moment.  Going back to a fresh installation 12.04.01 is an option for using the fglrx driver available in the repo for that version.  Another option is a fresh installation of 14.04 using the open source Radeon driver.

As for your other concerns ...

I am able to use a three head HD 5870 to run three wide screen monitors (two by DVI, one by Display Port) using the Radeon driver.  I can't say for sure how your setup would work, but I would be very surprised if you cannot run multiple wide-screen monitors if your card is capable.

I use the fglrx driver only because some of the scientific applications I run require it and because I can only get temperature, fan and activity feedback for monitoring the card with the fglrx driver.  But I have removed it on any number of occasions, used the Radeon driver and had output to all three widescreen monitors without any trouble at all.  The current Radeon driver is very capable and I recommend it for those who don't need the gaming performance or application-specific features.

---

### Post by Riothamus on 2014-08-12
Thanks anyway for the help. Interestingly, doing sudo apt-get remove --purge fglrx again got it working enough that the graphics on Ubuntu now work again. When I first startup, it's always dark and I can only see a message saying that an error was detected and asking if I want to report it. But once I click cancel, the screen comes alive. I also randomly get an error that a system error was detected while I'm doing work. So clearly, my installation is still broken. But at least now I can use Ubuntu somewhat again.

Not sure how to proceed from here. I assume doing a backup at this point would also cause the broken stuff to be backed up? So maybe it makes more sense to manually copy everything to my Windows partition and then do a clean install and copy it all back? Hoping someone with knowledge about this will answer and give me some advice.

EDIT: Since doing the upgrade, another interesting thing is that I've found a file in /media called Ubuntu 12.04 LTS and another one called Ubuntu 14.04 LTS" Is it possible this is a backup I could use to recover the old installation, or anything like that?

---


---
title: "new install of ubuntu 14.X to USB harddrive results in corrupt filesystem after patch"
date: 2015-03-03
forum: Installation &amp; Upgrades
---

### Post by john372 on 2015-03-03
I am trying to install ubuntu or kubuntu 14.x on a USB harddrive drive (not flash) for portability, and it install fine and reboots with no issues but if I do an "apt-get update" and then install all the patches available, the OS becomes corrupt on the next boot. I have tried this with 14.04 and 14.10 and it is consistent. I also went back and installed 13.X and tried and patched and it had no issues. The reason I am trying to intall on a portable USB harddrive is so I can take the OS with me to different areas in our network without having to install on a dedicated workstation or laptop. It is slightly slower when used off of the USB drive, but provides the mobility I need for doing vulnerability scans in different subnets. 
    After patching and booting, I always get "errors were found while checking the disk drive for /". I have tried both SATA and EIDE drives in a multiple types of USB drive enclosures and also on multiple workstation type, but they were all different Dell models.
I have also tried multiple ways of installing including using LVM and not using LVM. They all result in a corrupt filesystem structure.
Ideas?

---

### Post by grahammechanical on 2015-03-03
You have not described the form of "corruption."

---

### Post by john372 on 2015-03-03
Besides consistently getting the "errors were found while checking the disk drive for /" message after the first patch, it appears the underlying filesystems are no longer found. Even choosing to try and fix the filesystems at the "errors were found while checking the disk drive for /" screen, doesn't fix anything and the system is no longer bootable.

---

### Post by john372 on 2015-03-03
So after doing some searching and finding others who are getting the "errors were found while checking the disk drive for /" error after rebooting, I changed the "ro" entries to "rw" in the grub.cfg file and it appears the problem is solved. What's odd is that after patching with all available patches after the initial install, and then doing a reboot, the OS doesn't seem to correctly go through a clean shutdown and reboot. The reason I say this is because after issuing a "reboot" command, I would expect to see the OS sequentially shutting down services but the workstation almost instantly powers off and reboots without all of the normal "shutting down xxxxx" messages.

---

### Post by sudodus on 2015-03-03
Welcome to the Ubuntu Forums :-)

Please tell us about the patches! Maybe they were made for your 13.x system, and do not work well in 14.04 LTS and 14.10.

A correct way to update a system is to use the two command lines

```
sudo apt-get update
sudo apt-get dist-upgrade

```
See the explanation in the manual

```
man apt-get
```

You can also use the ***update-manager*** with a graphical user interface (it does the same thing under the hood).

---

### Post by john372 on 2015-03-03
Just so we are clear, I did not upgrade to 14.10. I started with the 14.10 x64 boot CD and installed it on a USB harddrive. After the initial reboot, I did "apt-get update" and then "apt-get install aptitude" and then "aptitude full-upgrade" which after a reboot, resulted in the corruption.

---

### Post by sudodus on 2015-03-03
I'd recommend safe-upgrade instead of full-upgrade. See ```
man aptitude
``` but normally full-upgrade should work too. Have you got any PPAs or packages that are separately installed (compiled by you or installed from deb-files)?


```
       safe-upgrade
           Upgrades installed packages to their most recent version. Installed
           packages will not be removed unless they are unused (see the
           section “Managing Automatically Installed Packages” in the aptitude
           reference manual). Packages which are not currently installed may
           be installed to resolve dependencies unless the --no-new-installs
           command-line option is supplied.

           If no <package>s are listed on the command line, aptitude will
           attempt to upgrade every package that can be upgraded. Otherwise,
           aptitude will attempt to upgrade only the packages which it is
           instructed to upgrade. The <package>s can be extended with suffixes
           in the same manner as arguments to aptitude install, so you can
           also give additional instructions to aptitude here; for instance,
           aptitude safe-upgrade bash dash- will attempt to upgrade the bash
           package and remove the dash package.

           It is sometimes necessary to remove one package in order to upgrade
           another; this command is not able to upgrade packages in such
           situations. Use the full-upgrade command to upgrade as many
           packages as possible.

       full-upgrade
           Upgrades installed packages to their most recent version, removing
           or installing packages as necessary. This command is less
           conservative than safe-upgrade and thus more likely to perform
           unwanted actions. However, it is capable of upgrading packages that
           safe-upgrade cannot upgrade.

           If no <package>s are listed on the command line, aptitude will
           attempt to upgrade every package that can be upgraded. Otherwise,
           aptitude will attempt to upgrade only the packages which it is
           instructed to upgrade. The <package>s can be extended with suffixes
           in the same manner as arguments to aptitude install, so you can
           also give additional instructions to aptitude here; for instance,
           aptitude full-upgrade bash dash- will attempt to upgrade the bash
           package and remove the dash package.

               Note
               This command was originally named dist-upgrade for historical
               reasons, and aptitude still recognizes dist-upgrade as a
               synonym for full-upgrade.

```

---

### Post by john372 on 2015-03-03
No. The only thing that was installed outside of the default packages, was aptitude. Absolutely nothing else was installed outside of the default build.

---

### Post by sudodus on 2015-03-04
Then I suspect that there is some [of the upgraded] drivers, that are not compatible with your computer hardware.

I would try the LTS version 14.04 LTS. Try also the point versions live: 14.04.1 and 14.04.2. You may need to pin some version of the kernel (and not upgrade beyond it).

```
sudo apt-get upgrade
```

does not upgrade the kernel. I'm not sure if aptitude's 'safe-upgrade' is corresponding exactly to that apt-get command.

Other people may be able to give you a more advanced method to pin the kernel or a particular driver, if you can identify it.

Please chip in and help the OP, if ***you*** know :-)

---

### Post by john372 on 2015-03-04
I'm pretty sure it isn't driver related as after more experimentation (post #4), changing all of the "ro" entries in the menu.lst for grub to 'rw' solved the issue. It reboots cleanly now.

---

### Post by sudodus on 2015-03-04
Sorry I missed post #4. Maybe I was editing post #5 at the same time, and never looked back. I think you are right about the conclusions. But I don't understand why it would happen.

Maybe you can try different methods to shutdown and reboot, and check if some method will flush the buffers and close processes better than other methods.

---


---
title: "Major difficulty installing Ubuntu"
date: 2008-07-04
forum: Installation &amp; Upgrades
---

### Post by kerplatz on 2008-07-04
This is a long post. And I may ramble at times. Please bare with me.

I have been at this for days and weeks and I still seem to be no further in getting this thing installed on my hard drives. I have 2 laptops; I want Ubuntu 8 installed on. Both of them have been headaches since I started this process.

The first laptop is a Toshiba 1955 Satellite. It is a few years old, but it still works for most of the things I need it to do. Sometime ago I tried to install version 8 from a live cd. It would crash and report errors with the CD. This CD installed fine in a new HP laptop which I will get to later. I suspected that the problem was with my CD drive not being able to read the boot disk/sectors of the CD properly. Old drive meets new software. So, I downloaded version 6.10 and after several failed attemps to get it to install, I now have Windows XP and Ubuntu 6.10 dual booting using Grub. Yeah!

Not so fast. I don't want to use version 6.10 -- I want to use the latest and greatest, version 8. When I run the Update Manager all I ever get is Authentification Failure. I looked that problem up and I found out that I have the wrong version of Update Manager. I believe I have version 4.5 and I need version 4.5.2. The number I just cited may be wrong, but I do know I don't have the correct version. Everything I do to get it ends in failure.

So my question is, Can I download and install just the correct version of Update Manager? Is it on one of the Ubuntu CDs, and I can install only the Update Manager? Is there another way to upgrade to version 8? I will take all credible responses.

The second laptop have Vista, XP (when I get it installed), and Ubuntu 8. I kept having issues with all three residing on this computer, but I think I have the installation order (Vista, XP, Ubuntu) worked out, and the way I have my hard drive partitioned should be good to go also. The verdict is still out on this one. I believe I will be more fortunate with how well all the installs go on this computer.

The frustrations I have are:

1. Information on the order of installing the OS's was not good. I figured out, by trial and error, that Windows should be installed first, then Ubuntu. It was a MBR thing. Which leads to
2. Boot Managers suck, Grub does not. It seems that no matter which Boot Manager I tried it would inverably screw up one of the OS installs that I would have to partition, format, and reinstall everything again. When I left Grub alone and used it, I never had a problem. Go Grub!
3. How you lay out the partitions on the HD were a problem also. Windows likes to be the first partitions on the drive, while Ubuntu was happy at the end. Windows needed Primary partitions and Ubuntu liked Extended partitions.

Thats my story. If anyone has some helpful advice to my problem, I would appreciate it very much. Thanks.

---

### Post by logos34 on 2008-07-04
> **kerplatz said:**
> wrong version of Update Manager. I believe I have version 4.5 and I need version 4.5.2. The number I just cited may be wrong, but I do know I don't have the correct version. Everything I do to get it ends in failure.

So my question is, Can I download and install just the correct version of Update Manager? Is it on one of the Ubuntu CDs, and I can install only the Update Manager? Is there another way to upgrade to version 8? I will take all credible responses.

What about opening synaptic and upgrading the pkg there? 

You can try to dl it directly here:
[http://packages.ubuntu.com/edgy/](http://packages.ubuntu.com/edgy/)

But even if you manage to straighten that out, be aware that you cannot upgrade directly from edgy to hardy.  You'll have to go one release at a time: ->feisty->gutsy->hardy.  (if only you had installed dapper--you CAN go directly from one LTS to another!)

 On the triple boot stuff, yes, it can be pain.  Sometimes grub can't chainload vista, so you have to do it the other way round using [EasyBCD.]("http://neosmart.net/wiki/display/EBCD/Linux")  But in your case, if you install xp after vista, either 'hide' the vista partition during install (so you an chainload each windows separately from its own partition, or let it go normally, in which xp will place the boot files on the vista partition, and grub will load that (i.e. a windows selection screen where you will choose either vista or xp).  You'll have to [reinstall grub]("http://ubuntuforums.org/showthread.php?t=224351") to the mbr afterwards.

[http://apcmag.com/how_to_dual_boot_vista_and_xp_with_vista_installed_first__the_stepbystep_guide.htm](http://apcmag.com/how_to_dual_boot_vista_and_xp_with_vista_installed_first__the_stepbystep_guide.htm)

---

### Post by kerplatz on 2008-07-04
Thanks logos34.

I tried the synaptic route. I got the same result. The problem seems to be that the Update Manager cannot find the files it needs to be able to get the updates. I think I know why.

You gave this website [COLOR="Red"]http://packages.ubuntu.com/edgy/[/COLOR] for me to download the package I need. Well it does not seem to exist. The version before Dapper 6.06 LTS and version 7.04 are there, but Edgy is not.

I think I will trash this install of Ubuntu and install Dapper 6.06 LTS from a CD and see if I can do what you say. Go from 6.06 to 8.04.

As fas a triple booting goes, I think I can get EasyBCD and Grub to not fight each other.

Thanks for the help. I will keep my progress updated.

---

### Post by logos34 on 2008-07-04
> **kerplatz said:**
> You gave this website [COLOR=Red]http://packages.ubuntu.com/edgy/[/COLOR] for me to download the package I need. Well it does not seem to exist. The version before Dapper 6.06 LTS and version 7.04 are there, but Edgy is not.


When I tried it last night I thought it wasn't responding because the server was temprarily down...But it looks like they completely removed Edgy:
> **Browse through the lists of packages:**

  
[LIST]
[*][dapper]("http://packages.ubuntu.com/dapper/") (6.06LTS)
[*][dapper-updates]("http://packages.ubuntu.com/dapper-updates/")
[*][dapper-backports]("http://packages.ubuntu.com/dapper-backports/")
[*][feisty]("http://packages.ubuntu.com/feisty/") (7.04)
[*][feisty-updates]("http://packages.ubuntu.com/feisty-updates/")
[*][feisty-backports]("http://packages.ubuntu.com/feisty-backports/")
[*][gutsy]("http://packages.ubuntu.com/gutsy/") (7.10)
[*][gutsy-updates]("http://packages.ubuntu.com/gutsy-updates/")
[*][gutsy-backports]("http://packages.ubuntu.com/gutsy-backports/")
[*][hardy]("http://packages.ubuntu.com/hardy/") (8.04LTS)
[*][hardy-updates]("http://packages.ubuntu.com/hardy-updates/")
[*][hardy-backports]("http://packages.ubuntu.com/hardy-backports/")
[*][intrepid]("http://packages.ubuntu.com/intrepid/")
[/LIST]
  There is also a list of [packages recently added to intrepid]("http://packages.ubuntu.com/intrepid/main/newpkg").
  It was there the last time I checked.

Anyway, good luck with dapper-hardy route and EasyBCD.

---

### Post by bahnted on 2008-08-14
I am a frustrated newbie.

FAILURE of Ubuntu 7.11 upgrade to Ubuntu 8.x
IBM ThinkPad T30

Upgrade went well until I answered the question: replace configuration file.

The update went through the following:

  Preparing to upgrade
  Setting new software channels
  Getting new packages

At: Installing the upgrades

The progress meter showed 14 minutes remaining.

It hung there for several hours.
Re-started.

Ubuntu start bar started, then stopped, then executed.

Message: Internal error: failed to initialize HAL!
Hit Close

Have different desktop "look" now.
1. Do not have networking...wifi or network.
2. No network icons.
3. Firefox icon disabled.  Tried restart through Apps/internet/firefox.  No joy.
4. Looks like most other apps (evolution, fstop, moneydance, amarok, etc) that I have do work and start.  

Please let me know if you can help, or have other contacts who can.

Thanks
Ted

---


---
title: "My installation failed horribly - Suggestions for fixing it"
date: 2005-05-25
forum: Installation &amp; Upgrades
---

### Post by vbertola on 2005-05-25
Hello,

I am a happy user of Ubuntu since the 4.10 version. I have just received the CDs and tried to install 5.04 (in Italian language) on my home PC... and I had some problems. I think I can solve them alone (I am a sysadmin) but I wanted to post them so that maybe the developers can address them in future releases.

I think that the root of the problems is that my motherboard (ASUS P5-GD1) has an integrated giga ethernet card that is not supported yet by the standard Linux ethernet driver. As a result, during the installation, it will not find the network card. 

The installation rightly stops, but the message I get at that stage is "you should get back to the hardware detection phase", which is quite confusing, because there is no such phase in the phases list and in any case it will not work. All of this can be terribly confusing for an average user.

Anyway, I forced the installation to proceed by hand-selecting the following installation phase. It finished, but it gave a number of errors, as it cannot connect to the Internet to setup package sources etc. Also, when I booted the system after installation, before the prompt, I received an error message such as "I cannot solve the name of the local machine".

I booted up again the machine with the pre-existing Win XP installation, and I searched the Internet for a solution. I found a marvelous guide by a guy who already had my same problem:

[http://ta.twi.tudelft.nl/DV/Staff/Lemmens/linux_p5gd1.html](http://ta.twi.tudelft.nl/DV/Staff/Lemmens/linux_p5gd1.html)

that points to the right driver to install, and also a message in these forums:

[http://ubuntuforums.org/showthread.php?p=169932#post169932](http://ubuntuforums.org/showthread.php?p=169932#post169932)

This brings me to more problems: I can download the file elsewhere and bring it to the Ubuntu installation via a floppy or USB stick, but then... I cannot install it, because I am not root, and because I miss all the packages that the answer to the forum post above mentions.

For what regards the packages (which, basically, include gcc and various development libs): yes, I can get them from the installation CD through Synaptic... but when I clicked on Synaptic in the menu, it stayed there loading for a while, and then it disappeared. No way to start Synaptic from there! (Perhaps this is due to the absence of the network and the deriving installation problems?) 

I am skilled enough to know that I could open a shell and type 'sudo synaptic' - that way, it worked and I could install the packages. But, again, an average user would be lost.

The second problem is that I cannot run the installation script for the driver without being root... and you can't be root in Ubuntu, can you? (Yes, I know you can, but not the average guy and not even the skilled guy who comes from using another distribution.)

I think that the sudo approach in Ubuntu is nice, but is being pushed too much onto users. It is so frustrating to have a problem like mine, type 'su' and being asked for a password you don't know and you weren't asked for. I felt like Ubuntu had stolen my PC!!

I also tried to see whether I could enable the root account via the "Users and Groups" menu item... but that wouldn't load either. (Same problem as for Synaptic?)

So, now I know that I can use 'sudo passwd root' to change the root password, or 'sudo -i' to run a root shell. Nonetheless, sudo is not really in use in all other distributions, so even skilled admins would not think at that at a first glance, and would stay there puzzled... or, more likely, throw the Ubuntu CDs in the dustbin and install Mandrake or Fedora.

This is why, in my opinion, the Ubuntu installation procedure conceptually needs a fix in the following three points:

1) You should ensure that everything works fine if the network isn't found or initialized properly. No error messages (just a warning), no broken stuff, just install and boot nicely without the network (at most, there could be a warning at boot such as 'your network card isn't correctly installed yet').

2) You should consider installing gcc and all the 'build-essentials' by default. All non-Ubuntu-packaged installations out there expect to find them, and without them will fail horribly and leave the user puzzled. As a minimum, you should ask the user whether he/she wants to install them or not, during installation.

3) During the installation, you should ask the user whether he/she wants to use the sudo approach, or whether he/she wants to set the root password and enable the root account. It's the USER'S machine, not yours - so show all the good reasons you want to convince him/her to use sudo, but then let him/her choose. Also, it would be good to have a modified version of 'su' that (in case the root password was never changed since installation) shows a message explaining how to set it to enable the root account (i.e. 'sudo passwd root') or how to live without it (i.e. 'sudo -s' or 'sudo -i'). Otherwise, you risk letting the user in the middle of a big mess, yelling insults at you :-)

Ah, and of course, please include the updated drivers in the distribution asap - my motherboard is getting quite common out there.

Thanks!

[I now realize that perhaps this message should better go to the feature request section, wherever that is... does anyone know how to contact developers to discuss this kind of proposals?]

---

### Post by vbertola on 2005-05-27
Whoops! Now I have a real problem: in fact, the driver refuses to compile.

First, I installed the linux-headers package, and I had a problem with that: it was hard to find (why doesn't it have "kernel" in its name? if you search for "kernel" inside synaptic, you get another "kernel-headers" package which is the wrong one - that's confusing!) and once found, it installed but it did not create the /usr/src/linux symbolic link, so the driver installation script could not find the kernel headers until I manually added the symlink.

Then... the compilation of the driver crashes with an unknown error. 

Is there anyone else who has had this problem?

Thanks,

---


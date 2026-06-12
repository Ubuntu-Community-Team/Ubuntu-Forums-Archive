---
title: "Server Install STUCK - Requests to insert disc that's already loaded - Grub boot load"
date: 2013-12-12
forum: Installation &amp; Upgrades
---

### Post by ubuforum3 on 2013-12-12
Hi,

Thank you for viewing this.

I'm attempting Ubuntu Server install for the first time on new hardware and stuck on the following prompt:

[!!] Install the GRUB boot loader on a hard disk
Please insert the disc labeled: 'Ubuntu-Server 13.10 _Saucy Salamander_ - Release amd64 (20131016)' in the drive...

From what I can tell this is the disc already in the drive... i downloaded and burned again to be sure - ubuntu-13.10-server-amd64.iso

I can't proceed from here.

Thanks for your help!

Peace

ps: the installation went smoothly except for problems installing some of the software modules... I repeated that section and ended up not clear on their status... but, it sounds like these can be installed at any time... some instructions i ran across suggested skipping all of the "install software" section.

pss: Hardware
Lenovo Thinkserver TS140
[COLOR=#333333][FONT=Arial]3.40 GHz Intel Core i3

[/FONT][/COLOR]

---

### Post by ubuforum3 on 2013-12-12
The problem is MOSTLY RESOLVED

I tried the install twice again... it appears the part i was stuck on was how to proceed after selecting software modules to install.  I'm still not sure what was supposed to be done - 
q - quit
g - install/update/remove

NOTE: This section was not mentioned in any of the installation guides I ran across and the name of the tool running flashed quickly... something beginning with A... Adaptive?

There was a list of things installed, not installed... and, lots of errors,, many related to "connect to socket failed".  So, I'm not sure they installation is really complete... I just get a login prompt and the familiar $

Previously the attempts must have only installed parts of a few selections... this last time I only selected the "Manual Package Selection".

Any tips on how to use the software install area of the installation?

Maybe this should be closed and opened with a new thread?

Thanks for any input...

---

### Post by oldfred on 2013-12-13
I do not know server, but it sounds like you may not have a working Internet connection?

I really only know how to do repairs from a live installer, and the server install is not a live version.
I might download the same 13.10 desktop and see if you get Internet. You then can use that for repairs if need be later.

Are you installing in UEFI mode or BIOS boot mode?

---


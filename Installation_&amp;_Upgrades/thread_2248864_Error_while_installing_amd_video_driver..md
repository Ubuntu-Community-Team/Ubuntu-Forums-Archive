---
title: "Error while installing amd video driver."
date: 2014-10-17
forum: Installation &amp; Upgrades
---

### Post by robgeek on 2014-10-17
Hello!
I'm using Ubuntu 14.4 Trusty in a notebook with videocard integrated. Here, my video card.
> root@robgeek:/home/rob# lspci -nn | grep VGA
01:05.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] RS880M [Mobility Radeon HD 4225/4250] [1002:9712]

In my notebook is written "Raedon HD 4200 Series". So, i downloaded the newest version of the driver because i think my system very slow. The same thing happened with Windows 8.1 and after install the video driver my system became much more fast. When i went to amd website i choose:
> Step1: Integrated Motherboard Graphics
Step2: Raedon Integrated HD Series
Step3: Raedon HD 4200  Series
Step4: Linux x86_64
And i downloaded the "amd-driver-installer-catalyst-13.1-legacy-linux-x86.x86_64.run" file. But when i run him, after choose "Install driver 8.97.100.7 on X.Org6.9 or later 64bit" i get the following error message:
> One or more tools required for installation cannot be found on the system.
Install the required tools before installing the fglrx driver. Optionally, run the installer with --force option to install without the tools. Forcing install will disable AMD hardware acceleration and may make your system unstable. Not recomended.
See /usr/share/ati/fglrx-install.log for more details.

Here what is written in "/usr/share/ati/fglrx-install.log" file.
> Check if system has the tools required for installation.
fglrx installation requires that the system have kernel headers.  /lib/modules/3.13.0-37-generic/build/include/linux/version.h cannot be found on this system.
One or more tools required for installation cannot be found on the system. Install the required tools before installing the fglrx driver.
Optionally, run the installer with --force option to install without the tools.
Forcing install will disable AMD hardware acceleration and may make your system unstable. Not recommended.

So, what can i do to solve this problem? I'm very, very newbie in Linux.

---

### Post by Bashing-om on 2014-10-17
robgeek; Regretfully;

It is not a linux problem:
> 
IF its an HD 2x/3x/4x then you are out of luck as AMD announced <last> summer that it is relegating these chipsets to legacy status and will not be developing new drivers for them. Existing restricted drivers from AMD won't work either, because they require X-server v1.12 and Ubuntu 12.10 uses X-server v1.13.
That's because, starting with Ubuntu 12.04.2, the X-server version was updated to a newer version that is now incompatible with the HD 2x/3x/4x series AMD cards. Terminal command -> X -version to determine the x-server version.
(Mark Phelps)


Blame AMD for not supporting the ATI ( they bought out ATI) cards, 

It is a shame
[INDENT][INDENT][INDENT]but that is the way it is
[/INDENT][/INDENT][/INDENT]

---

### Post by robgeek on 2014-10-17
Bashing-om

Thank you anyway!

---

### Post by Bashing-om on 2014-10-17
robgeek
 Quite welcome :)

Thankfully our developers maintain support for that series of cards.

[INDENT]make do with what we got
[INDENT][INDENT][INDENT]and keep on keep'n on
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by robgeek on 2014-10-17
I have two more questions about this, please.

1- If AMD is not developing new drivers for my videocard, why they are avaliable in amd website like the one i downloaded?

2- If i install Debian Wheezy, can i install correctly this driver?

---

### Post by Vladlenin5000 on 2014-10-17
1. They're still available as *legacy* and for *legacy* X-server v1.12 and older only.

2. Probably not -> Read #1.

---


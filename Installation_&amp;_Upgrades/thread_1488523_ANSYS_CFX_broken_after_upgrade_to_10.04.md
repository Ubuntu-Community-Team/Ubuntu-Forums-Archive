---
title: "ANSYS CFX broken after upgrade to 10.04"
date: 2010-05-20
forum: Installation &amp; Upgrades
---

### Post by shas3n on 2010-05-20
On my 64bit Ubuntu desktop, upgrade from 9.10 to 10.04 has broken ANSYD CFX Pre and CFX solver tools. (ANSYS CFX is a popular computational fluid dynamics tool).
I did contact ANSYS support but unfortunately they do not support Debian distros.

There is a description of the problem [here ]("http://www.cfd-online.com/Forums/cfx/75829-ubuntu-10-04-cfx5pre-problem.html") by another user.

The software launches alright (hence it is not a GT problem), the graphics work fine (hence not a OpenGL problem).
The software fails with an error whenever it is trying to read/extract CCL files. CFX uses Perl to handle text extraction etc. so I suspect this might be a problem with the version of perl that came with 10.04.

Can someone guide me to the root of the problem? How do I roll-back to an earlier version of Perl to start with? 
Are they any other Ubuntu users who have experienced the problem?
Any help will be appreciated.

---

### Post by TurbilentFluid on 2010-06-08
Hullo...

I have the same unnerving issue rolled back on PERL, ended up being quite easy - download the desired version from their site, compile it (make install) into some folder other than the default perl folder, then copy all the files over to where your default perl files are and paste over them. 

I don't know if this is the correct procedure, but it did work for me - I had the 5.8.8. version as a reply to **perl -v** in konsole...

However, it did not get ansys up and running. anymore ideas!? I'm lost!

---

### Post by shas3n on 2010-06-08
I did not have any further luck either. (Although I did not try downgrading PERL).
Ended up installing Open Suse on a separate partition just to be able to run Ansys. Getting GRUB to recognise both Ubuntu and OpenSuse was quite tricky (they did not identify one another) but in the end figured out how to do it.
So while no direct solution to this problem has been found, I have worked around it by installing another OS.

---

### Post by TurbilentFluid on 2010-06-08
> **shas3n said:**
> I did not have any further luck either. (Although I did not try downgrading PERL).
Ended up installing Open Suse on a separate partition just to be able to run Ansys. Getting GRUB to recognise both Ubuntu and OpenSuse was quite tricky (they did not identify one another) but in the end figured out how to do it.
So while no direct solution to this problem has been found, I have worked around it by installing another OS.

I was thinking of the same sollution myself! About to try it in virtualbox, could you please tell me which version of OpenSuse did you use? :)

---

### Post by shas3n on 2010-06-08
I ended up using OpenSuse 11.2 (64bit) with GNOME which does work very well.
I also got it to work in Windows XP inside Virtualbox on Ubuntu, but it is not ideal for running large-memory runs.
BTW, I am using Ansys 64 Bit 12.1 version.
Good luck! Backup your Ubuntu files if you decide to use Suse on a partition. Grub will get messed up and you might not be able to boot into Ubuntu without hacking Grub a bit.

---

### Post by TurbilentFluid on 2010-06-09
Thanx for the reply! I still haven't went ahead with SuSe - I just... don't like it. I said I'll give it a bit more fight... ;)

And now I'm confused... I installed Ansys on Kubuntu x64 in Virtualbox and it works no problem...? Quite awkward! I'm using 12.1 Development version for Linux. HOWEVER, I did strip it naked and installed only CFX components... 

I will try it again with an Ubuntu guest and post results. 
This is weird...?

---

### Post by TurbilentFluid on 2010-06-09
Here I am after a few attempts, to report more weirdness.

I have installed the "stripped" ansys 12.1 Development x64 on a fresh Ubuntu x64 virtualbox guest, and it works fine.
I then updated the system, and it still works fine. 

I have then re-installed the guest Ubuntu x64, installed full  ansys 12.1 Development x64, and it works fine. 
I then updated the system, and it still works fine. 

Now I'm confused throughoutly.
It shouldn't be the nVidia drivers, because I used the same card with the same drivers on Karmic and it worked fine.
Any ideas...?

---


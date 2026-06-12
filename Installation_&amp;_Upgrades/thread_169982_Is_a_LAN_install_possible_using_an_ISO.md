---
title: "Is a LAN install possible using an ISO?"
date: 2006-05-03
forum: Installation &amp; Upgrades
---

### Post by Brinstar on 2006-05-03
I have 2 laptops (currently running W2K and XP) linked with a crossover cable. I want to put Linux on one and leave XP on the other so I can use MS Office 2003 (need it for work). 

I have a Dapper Drake ISO (6.06 beta 2) and basically want to know if it's possible to install it from one machine to the other using the LAN connection? I'm not certain but I think both are able to use PXE. 

Is it possible to use Windows to 'host' the ISO and for the other machine to copy the files from it? I don't have access to a good internet connection, so let's assume I can't use that. Only one machine (the one I want to install Ubuntu on) has a floppy drive.

---

### Post by tonyr on 2006-05-03
There is apparently a way to do it, but it is not straightforward. It requires that
one of the machines  is set up as a TFTP and DHCP server.  Look at:

[URL="https://wiki.ubuntu.com/Installation/Netboot"]
https://wiki.ubuntu.com/Installation/Netboot[/URL]
for the gory details. There are a couple of other references that I saw:

[http://gridpt1.fe.up.pt/mlopes/blog/index.php/ubuntu-network-install/](http://gridpt1.fe.up.pt/mlopes/blog/index.php/ubuntu-network-install/)

[http://ubuntuforums.org/showpost.php?p=2493&postcount=2](http://ubuntuforums.org/showpost.php?p=2493&postcount=2)
but these pretty much say the same thing as the wiki document.

The wiki article talks specifically about using a Windows box as the server.

---

### Post by Brinstar on 2007-09-02
sorry to dig up this old thread, but i have recently decided to give this another shot after hearing that people have got this working and thought i should be next...

What I'm using:

* A Toshiba laptop running XP connected to a cheapo Netgear switch, this is the DHCP/TFTP server

* A Dell laptop, also with XP on it, this is the one that is hopefully going to have Ubuntu Feisty on it

* TFTPD32 by Phil Jounin, a good DHCP/TFTP server that 'just works'

* A decompressed ISO of Ubuntu Feisty *Alternate ISO* on the C drive of the Toshiba machine in a folder named 'ubuntu'

* The 'netboot' files, if you have tried a similar install before, you'll know what i mean



I have got TFTPD32 working, the PXE boots and grabs the pxelinux.0 file and starts the Ubuntu install process, this all works...

The installer has reached the point where it shows a list of world mirrors to choose from, and at the top where it lets you 'enter the information manually' i don't know what to put? I don't have a reliable internet connection to use (though i am able to download the iso from a public library computer), so am i out of luck?

I am sure I have done something wrong, but wonder if it will still work somehow if i feed the installer the correct information? 

I think taking the 'netboot' route and expecting the installer to be able to pick the install files from the ubuntu folder was expecting too much from the installer. 

Reading a few posts on this forum, I am starting to think i should have used the files from the following link to bootstrap the install:

[http://archive.ubuntu.com/ubuntu/dists/feisty/main/installer-i386/current/images/hd-media/](http://archive.ubuntu.com/ubuntu/dists/feisty/main/installer-i386/current/images/hd-media/)

One thing i am not sure about is what file would i bootstrap off instead of pxelinux.0?

Anyone have any input on this?

---

### Post by southernman on 2007-09-02
I can't help alot brinstar. Currently looking to do this by installing from another linux (ubuntu) sytem.

Just wanted to suggest that the installation files are not supposed to be uncompressed, but rather in their original .iso format. AFAIAmAware anyway.

good luck.

---

### Post by ravingmad on 2007-09-03
[http://ubuntuforums.org/showthread.php?t=541365](http://ubuntuforums.org/showthread.php?t=541365)

---

### Post by Brinstar on 2007-09-03
> **southernman said:**
> I can't help alot brinstar. Currently looking to do this by installing from another linux (ubuntu) sytem.

Just wanted to suggest that the installation files are not supposed to be uncompressed, but rather in their original .iso format. AFAIAmAware anyway.

good luck.

no, the files would have to be uncompressed, there is no way the bootstrap could open the iso if you understand what i'm getting at...

ravingmad, i guess what you did is the closest to what i'm attempting to do, though i think there is an easier solution out there that involves using more appropriate install files such as the ones in the 'hd-media' folder.

---

### Post by guess.who on 2007-09-06
Hi all,
I am an ubuntu user.I tried to install ubuntu in 4 computers(same architecture) with a  minimum effort.So,I did network installation.It was going fine in ubuntu 5.1 distro.But when i tried with ubuntu 7* distro it is not getting over.When i am selecting my local repo. path (mounted iso image in the local server),it is giving the following error...
"The specified ubuntu archive mirror is either not available,or doesnot have a valid Release file on it.Please try a different mirror."
But at the same time when i am selecting official ubuntu mirror it is going fine..
Once again i am mentioning that i am using the same procedure that i followed during ubuntu 5.1 distro network installation.and it worked fine.
My intention is to install ubuntu from (mounted install cd) local server without using the internet.
I followed the PXE local network installation procedure.In my server i am using dhcp3 server,tftpd-hpa for tftp,and apache2 for http.
Another thing i want to ask is that is it a problem of ubuntu-installer?As i found that in ubuntu 5.1 distro netboot option is there in the install cd itself (/install/netboot) and it is mandatory for PXE net installation but in ubuntu higher versions they are not providing this option in the install cd (or in the iso image) so i downloaded the netboot.tar.gz package from the official ubuntu repo and untar it inside my tftp root directory(/var/lib/tftpboot).So that my computers are now booting from the server but the ubuntu-installer fails in that stage what i mentioned above.

---

### Post by logos34 on 2007-09-06
> **Brinstar said:**
>  though i think there is an easier solution out there that involves using more appropriate install files such as the ones in the 'hd-media' folder.

[https://help.ubuntu.com/community/Installation/FromWindows](https://help.ubuntu.com/community/Installation/FromWindows)
(-->'**The CD image approach**')

---


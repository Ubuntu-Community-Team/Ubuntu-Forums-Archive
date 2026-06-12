---
title: "Recovery Mode with Networking gone . .Upgrade Woes . . KarmicNBR -&gt; Lucid"
date: 2010-06-08
forum: Installation &amp; Upgrades
---

### Post by pete_m on 2010-06-08
In the hope that my observations may be of use to others and that others may have insights to offer . .

I optimistically started my upgrade process with Lucid, Debian Sid and EB4 reposiitories in my /etc/sources.list.
The( evidently misguided )  rationale for this was my wish to benefit from the  the LTS status of  Lucid while simultaneoulsy being able to plug-in to the latest ( Sid ) versions of packages relating to the ( graphics) sofware I am interested in developing

After apparently passing sucessfully past a  safe upgrade using Squeeze snapshots, things went ( horribly ) wrong when i came up against " unable to migrate to dependency-based boot .. 
I tracked this down to problems with insserv and sysv-rc, and after struggling with this i decided to 
downgrade these two to the Lucid packages. this appeared to break the logjam and aptitude safe-upgrade seemed t go smoothly enough that I plucked up courage to re-boot my system.
Alas - since then I have been unable to boot my system except from the USB sticks I had prepared prior to embarking on this journey.
Whlie grappling with the LSB-boot stuff i discovered the mediahacks ppa which had seemed to promise some help in the area of mountall/ plymouth which were also implicated - unfortunately I removed this from my sources.list when attempting the upgrade as I had read somewhere that such a ' hack' was unadvisable.

My system is now unable to boot except to a command shell. . and i do not know how to enable networking to try to fix things . .any ideas ?

 In my Karmic system there used to be a safe-mode with networking option which allowed me to continue to tinker with apt-get/ aptitude and to access these forums and other Web resources to track down and resolve problems. 
What has happened to this option ?
This had served me well after a bad physical HD problem had left me with a badly-broken system. I had managed to rebuild the system and install Karmic NBR starting from an old USB stick with 8.04 on it.  .

Prior to my upgrade i was working with Grub 1.97 and had a fair degree of success in creating bootable USB sticks accesssing a variety of Linux flavours . .
I allowed the upgrade process to re-configure my GRuB and the sysntax in the grub.cfg menus has now changed considerably . ..


What hope for Ubuntu and the mass-market Linux desktop market when even someone with some experience such as myself gets caught out.  . . . ..

):P - is it time for me to wave bye-bye to Ubuntu and go diretl to Debian-based systems ? I am writing this on  an EB4 system which is SID-based.

---


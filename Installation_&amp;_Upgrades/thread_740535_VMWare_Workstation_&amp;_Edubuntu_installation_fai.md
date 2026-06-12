---
title: "VMWare Workstation &amp; Edubuntu installation failing"
date: 2008-03-30
forum: Installation &amp; Upgrades
---

### Post by JordanH on 2008-03-30
Hi Edubuntu fans,

A friend of mine is interested in implementing an Edubuntu lab at her school next fall and asked me to give her a demo.  Thinking it'd be quick and easy to load up Edubuntu on two VMWare workstations, I downloaded the CD last night.

The installation consistently freezes at the "Compressing Thin Client image..." once it reaches 89% - no error message, but no progress either.  The Windows XP host workstation shows 50% CPU usage but VMWare shows no disk, CPU or network activity.  The VMWare guest machine is configured with 2 NICs, one through NAT and the other as Host-Only networking.

Any suggestions on what to try or how to change the setup/config to get past this screen so I don't have to build an LTSP system from scratch?

J.

---

### Post by zvacet on 2008-03-31
If [md5sum](https://help.ubuntu.com/community/HowToMD5SUM) is O.K. and you checked CD for errors and that is fine,maybe you should look how much ram you give to the guest (Edubuntu).I´m just guessing but that can be reason( low ram for guest).

---

### Post by pbcartwright on 2008-03-31
I'm not sure myself, but I know there are some linux users in our local user group that helped implement a linux solution in the Cobb County schools in Georgia. You might join ale.org the local Atlanta Linux group, or maybe try your local ( or closest) Ubuntu Loco. Or look for a Linux User group ( Google) in your area, most are very helpful!

[https://wiki.ubuntu.com/LoCoTeamList](https://wiki.ubuntu.com/LoCoTeamList)

---

### Post by JordanH on 2008-03-31
@zvacet:  Thanks.  Indeed I did check the CD for errors and the guest Edubuntu server is allocate 1.5GB of RAM so I'm afraid those weren't the cause.

Having said that, I did get the installation to complete.  5th time's a charm?  The only change I made was switching the external NIC to bridged networking rather than the NAT networking.  Edubuntu server installed without problems after that - mind you, I only tried it once.

So to make sure this post isn't left open ended...

Symptom
Installation of Edubuntu 7.10 in VMWare 6 froze at the "Compressing Thin Client Image" screen

Problem
undetermined

Resolution
Changed VMWare configuration from 1xHost-only NIC and 1xNAT NIC to 1xHost-only NIC and 1xBridged NIC.  Then restarted the installation from scratch.

edit: Furthermore, I had difficulty with the Edubuntu DHCP competing with the VMNat DHCP compounded by VMWare switching both NICs each time I rebooted.  :-/

---


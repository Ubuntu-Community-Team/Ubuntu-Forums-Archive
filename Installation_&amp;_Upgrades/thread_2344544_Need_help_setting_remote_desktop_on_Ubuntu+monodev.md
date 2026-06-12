---
title: "Need help setting remote desktop on Ubuntu+monodevelop VM on Azure"
date: 2016-11-26
forum: Installation &amp; Upgrades
---

### Post by ziphnor2 on 2016-11-26
Hi,

I would like to set up a development workstation (meaning with a desktop environment) on Azure for easy access, but i have been having some problems (actually i also tried local Hyper-V, but had exactly the same issues). The problem boils down to not being able to resize the resolution. I am either stuck on 1024x768 or 1152xsomething, which is then also reported by xrandr as the max resolution. This is in both Hyper-V locally and on Azure.

I have tried to use NoMachine as remote desktop, but it is also limited by the "physical" resolution.  

Any tips would be appreciated.

---

### Post by TheFu on 2016-11-26
What is the resolution set to by the remote desktop?  You have to control both and real resolution from the client display AND the virtual resolution inside the VM.

I've never used hyper-v or azure, but use x2go daily for the last 2+ yrs as my primary desktop into a KVM VM from across the room or around the world. Only used NoMachine clients for about a year. Never used their servers (wanted F/LOSS). With x2go (which is fast like NX), you set the resolution on the client, then set the resolution inside the VM to what you need.  The only trick is that the VM virtual-hardware setup needs to have sufficient video-RAM allocated to support whatever resolution you need. 9MB isn't sufficient for most desktops.

BTW, it would probably be easier to get it working locally than remotely, then move it remote. 

The other tricks are  - 
* don't use Unity
* use XFCE or LXDE. Those are well supported. 
* stay with only LTS releases
* use the PPA for both the x2go client and x2go server

---


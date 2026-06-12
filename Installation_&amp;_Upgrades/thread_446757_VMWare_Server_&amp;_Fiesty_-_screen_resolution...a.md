---
title: "VMWare Server &amp; Fiesty - screen resolution...again"
date: 2007-05-17
forum: Installation &amp; Upgrades
---

### Post by speedway on 2007-05-17
Hi all

I am helping a friend get VMWare working on Fiesty. He is running Windows XP Pro. 

The story. I converted him to Ubuntu with a wonderful Dapper install. Then we upgraded to Edgy and installed VMWare Server (v 1.02 I think). All was sweet in the hybrid world with Ubuntu running at 1024x768 / 85hz via an ATI Radeon 9200 Pro / 256 Card. VMWare Server quite happily ran fullscreen in this configuration as well.....

Then we upgraded to Fiesty and all went wrong. VMWare would not run anymore, so I searched here and found some solutions. I removed the previous install and installed a shiny new version of VM Server, this time 1.03. I installed the patch as instructed. All was sweet again....so I thought. Remember, the machine is set to run @ 1024x768 / 85Hz. BUT! VMWare Server flatly refuses to work in this mode. While it *says* it is in 1024x768 / 85hz, it is really in something else. It is "squashed" vertically, squeezes out the side of the monitor and has terrible scan lines all over it. Switch back to Ubuntu and the screen is crispy clear, filling the screen. No matter what I do (in my limited knowledge), I cannot get the thing to display correctly at the needed resolution. I have trying to "fit" it every which way as well...

So, I am hoping some kind soul will come along as say "Hey, that's easy. You need to do XYZ and all shall be well again in the hybrid world...".

If you are that person, pray do tell me your little secret...

Cheers
Bruce

---

### Post by veloce on 2007-05-17
Hopefully some one else can answer your actual question.  I have ceased using vmware console (or full screen versions of the same) to run virtual machine.  What I do is get vms up and running then connect to them with rdp (gnome-rdp is my preference) over the host only network.  I find the performance and functionality much improved.

---

### Post by veloce on 2007-05-17
Oh, and btw, vmware server is now in the Feisty repositories - specifically the commercial one.

Makes installation and upgrades so much easier.

---

### Post by speedway on 2007-05-18
Thanks Veloce

RDP sounds interesting. I will see what I can find on the subject...

As for VM in the repos, I did try that but it failed to install. 

> 
License could not be presented; aborting
dpkg: error processing /var/cache/apt/archives/vmware-server_1.0.3-1_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 2


I suspect it has something to do with remnants of the old install. I'll try again before abandoning this path...

Cheers
Bruce

---


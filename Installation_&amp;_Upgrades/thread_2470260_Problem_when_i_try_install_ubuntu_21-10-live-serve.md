---
title: "Problem when i try install ubuntu 21-10-live-server-amd64"
date: 2021-12-23
forum: Installation &amp; Upgrades
---

### Post by elpedrop on 2021-12-23
hi everyone, 

I have a Problem when i try install ubuntu 21-10-live-server-amd64 on vmware. When I am installing on a VMware virtual machine, the screen of -> Snap does not appear, on this screen I could choose to install docker but since it does not appear, I do not know how to solve it

Does anyone know why they don't give me the option?
Why doesn't that screen appear?

the screen that does not appear is ->  FEATURED SERVER SNAPS 




thanks for the help, i'm desperate


Regards,
Peter

---

### Post by TheFu on 2021-12-23
A) exactly which VMware hypervisor?  Player, Workstation, Fusion, ESXi?  Something else?  Please don't make people guess.
B) does the VMware product you use actually list support of Ubuntu 21.10?  Often, the newest releases aren't supported by VMWare for a few months.

Start by checking those 2 things.

After you determine that 21.10 is officially supported (or not) by VMware, you'll be able to decide if asking for support directly from VMware would be the best route for help. That's a main reason for using commercial software - support by the company.

Best to ask 1 question per thread.  Snaps and Docker are different skills than hypervisors.

BTW, hypervisor-related questions/threads should be placed into the Virtualization sub-forum.

---

### Post by ActionParsnip on 2021-12-24
What settings do you have in the VM? RAM? Video RAM? CPU? NIC type...... and so on. Please give as many details as possible. What version of VMWare are you using?
Did you verify the ISO is complete and consistent?

---

### Post by MAFoElffen on 2021-12-27
Also of note... The latest/current version (for example, if you downloaded it now) of that 21.10 Server Live Installer ISO has a branch in it where it says:

Quote:
> 
Installer Update Available.
Version 21.12.2 of the installer is now available (21.10.3 is currently running).
You can read the release notes for each version at"
                             https"//github.com/canonical/subiquity/releases
If you choose to update, the update will be downloaded and the installation will continue
Which version did you choose?

Because at that panel, if I choose to upgrade, it then downloads the new installer, flashes a very quick message about snaps, then goes on to the keyboard configuration for the installer...

Next would be... If it got that far, the LiveCD enviroment booted the Linux Kernel and is running... If you <shift><tab> back up to "Help" and Select... Then you can select "Shell" and get to a Shell Prompt, where you can check the syslog and installer log to see what happened and what failed. Those write realtime, so even if the system is locked up, you can do a hard shutdown... Boot that VM from a LiveCD ISO and check those logs. Just as what you would do if it was on Metal... 

Just saying. You didn't give much information, but there is a lot you can do to be able to provide that detailed information also...

---


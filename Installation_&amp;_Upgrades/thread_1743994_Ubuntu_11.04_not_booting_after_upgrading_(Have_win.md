---
title: "Ubuntu 11.04 not booting after upgrading (Have windows 7 installed alongside))"
date: 2011-04-30
forum: Installation &amp; Upgrades
---

### Post by coolvishesh on 2011-04-30
I have Windows 7 installed on my system along side ubuntu. 
So,last night I thought of upgrading  my Ubuntu to version 11.04 (via distribution upgrade through internet)
Got no error during installation... Restarted system to complete the installation.. Found that system froze at booting screen and ubuntu is not booting..Left system for half an hour it still was on the same booting screen.
Previous versions of ubuntu is also not booting.
Please provide a solution to this problem so that i can get it working.

---

### Post by cariboo on 2011-04-30
Can you start in recovery mode, and select failsafeX from the menu to get to your desktop?

---

### Post by coolvishesh on 2011-04-30
Yes i m able to access my desktop by the way you told me but it opened with very low graphics.. i have nvidia 8400 GM on my laptop.. And got a message saying that i dont have the necessary hardware to run unity.. 
Please let me know what to do next so that i may be able to access it the normal way.

Thanks much in advance...

---

### Post by Rubi1200 on 2011-04-30
You need to check if your hardware is supported for 3D Unity:
[https://wiki.ubuntu.com/DesktopExperienceTeam/UnityHardwareRequirements](https://wiki.ubuntu.com/DesktopExperienceTeam/UnityHardwareRequirements)

Can you login using the Classic Desktop mode?

---

### Post by coolvishesh on 2011-04-30
Yes my system satisfies the requirement to run unity..

---

### Post by peternickson on 2011-04-30
I get the same issue.  I have WinXP installed alongside.  Upgraded through the upgrade manager.  Installation completed and I restarted system.  Freeze on ubuntu load screen.

I tried recovery mode, failsafeX.  I get an error message "Your screen, graphics card...... you'll need to configure these yourself."  I tried to reconfigure graphics settings and restarting.  It's different this time.  These messages appear:
"Starting load fallback graphics devices [fail]"
* jetty is not installed

NVidia8800GTX

---

### Post by peternickson on 2011-04-30
xserver log file includes this:
> [  20.429](II) Module nvidia: vendor="NVIDIA Coperation"
[  20.429]     compiled for 4.0.2, module version = 1.0.0
[  20.429]     Module class: X.Org Video Driver
[  20.432](EE) NVIDIA: Failed to load the NVIDIA kernal module. Please check your
[  20.432](EE) NVIDIA:    system's kernel log for additional error messages
[  20.432](II) UnloadModule: "nvidia"
[  20.432](II) Unloading nvidia
[  20.432](EE) Failed to load module "nvidia" (module-specific error, 0)
[  20.432](EE) No drivers available
[  20.432]
Fatal server error:
[  20.432] no screens found

In the startup errors everything is fine except for the same errors as above.  Strange thing is that from the first load screen if I select previous versions of linux, it works fine with Unity & everything

---

### Post by WarholsGhost on 2011-05-02
i'm getting this error as well, its being very odd.

---

### Post by danbhala on 2011-05-03
me too :(

---

### Post by treasonvoice on 2011-05-03
Nvidia drivers. Apparently they suck. Or do they?

Ok. here's what I **THINK** you guys need to do. 

Boot into failsafe X as you did before

Open additional drivers.

If it says you are using an Nvidia driver, REMOVE it.

Next step (order is important): if there is an option for the experimental 3D driver, select it and activate/install. 

If there is no option in Jockey/additional drivers, go into Synaptic Package Manager and search for xserver-xorg-video-nouveau, which is the in-house driver for Nvidia cards. Trust me, it works better than Nvidia drivers.

Install it.

Reboot, Log in, see how it goes.

Next step (just in case): Somewhere along the line Ubuntu blacklisted a few cards. My one, the Geforce 7400 Go, was blacklisted because of the above situation. Then they released an update which disables Unity for those cards and sends you into the backup.

There is a fix for it if you still want to try Unity. Let me know if that happens.

I might be COMPLETELY off the mark but there really is no harm in doing what I say. It worked for me when my system would just hang completely after logging in.

---

### Post by treasonvoice on 2011-05-03
Welcome to the forums. Now get some beans. :)

---


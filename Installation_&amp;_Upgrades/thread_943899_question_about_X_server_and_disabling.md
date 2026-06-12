---
title: "question about X server and disabling"
date: 2008-10-10
forum: Installation &amp; Upgrades
---

### Post by zero7404 on 2008-10-10
i'm pretty sure with the popularity of this OS, someone might have posted about this before, but searching for my answer hasn't been easy (at least on this forum)....

i'm new to Linux, as i did my own research and managed to install it on an external hdd and it runs fine with i start up from the hdd, i'm good.

however, i've downloaded nvidia's latest linux driver package for my machine, and after trying to execute the installer it tells me i need to exit the X server. when i use CTRL+ALT+BACKSPACE (i think that's the exit X server command) and i log into ubuntu and try to install the same package, i get the same message.

i'm a complete linux novice, so I have no idea what's going on here, anyone have suggestions ?

this is the latest ubuntu (8.1) and i have not yet installed all the update packages when prompted (it has found some 260+ packages)...

thanks

---

### Post by Pumalite on 2008-10-10
Install all your updates first

---

### Post by zero7404 on 2008-10-10
> **Pumalite said:**
> Install all your updates first

i figured that might have something to do with it...thanks

---

### Post by sokopok on 2008-10-10
Dont install the drivers from the nvidia website. Use Package Manager to install/upgrade the drivers shipped by Ubuntu (nvidia-glx if I'm not mistaken). This will save you many headaches...

---

### Post by zero7404 on 2008-10-10
> **sokopok said:**
> Dont install the drivers from the nvidia website. Use Package Manager to install/upgrade the drivers shipped by Ubuntu (nvidia-glx if I'm not mistaken). This will save you many headaches...

nvidia's driver package was not installing after updating ubuntu, same message (exit x server)...

is the package manager you're referring to the 'Synaptic Package Manager' ? doing a search for Nvidia doesn't return anything with the '-glx' term, but there are others listed. regardless, the manager shows that i have the latest version installed already.

---

### Post by sokopok on 2008-10-11
Synaptic is the one.
You will need the glx variant of the driver. Maybe the "restricted" repository is not enabled. Enabled it in Synaptic via Settings/Repositories

---

### Post by zero7404 on 2008-10-11
> **sokopok said:**
> Synaptic is the one.
You will need the glx variant of the driver. Maybe the "restricted" repository is not enabled. Enabled it in Synaptic via Settings/Repositories

i got the restricted (non-ubuntu) latest driver to install (177)...
thanks for your help.

although i've been having wifi issues since install, it's prompting multiple times to enter my key to get on my wpa2 network. sometimes it works, sometimes it doesn't....not sure where the problem is...

---

### Post by cariboo on 2008-10-11
You might have better luck getting your wifi question answered here:

[http://ubuntuforums.org/forumdisplay.php?f=346](http://ubuntuforums.org/forumdisplay.php?f=346)

Add the output this command:

```
sudo lshw -C network
```

This command has to be entered in a Applications-->Accessories-->Terminal and post it along with your question.

Jim

---

### Post by zero7404 on 2008-10-11
> **cariboo907 said:**
> You might have better luck getting your wifi question answered here:

[http://ubuntuforums.org/forumdisplay.php?f=346](http://ubuntuforums.org/forumdisplay.php?f=346)

Add the output this command:

```
sudo lshw -C network
```

This command has to be entered in a Applications-->Accessories-->Terminal and post it along with your question.

Jim

thanks, will do, however your link points to a forum, could you tell me which thread to post this info in ?

---

### Post by ByteJuggler on 2008-10-14
Hmm, when I click on that forum link I'm redirected to the Intrepid Testing and discussion forum, that can't be right.  The poster must've meant the [Networking & Wireless forum]("http://ubuntuforums.org/forumdisplay.php?f=336") instead.

Aside: Wireless, although a lot better than before, can still be a bit hit and miss, depending on the chipset you're using.  The command the previous poster posted will help identify which chipset you're using, and consequently how best to fix your problems.  Aside2:  I for example have a broadcom chipset in my laptop, and while there's a native driver for it, it's not yet complete and it works relatively poorly with my access point (due to not having support for low signal compensation stuff yet.)  As a result I'm using NDisWrapper with the Windows driver with mostly no problems now, even though that took a little while to set up.  Be patient and you'll get there!

---

### Post by Pumalite on 2008-10-14
I can recommend to anyone using Hardy or Intrepid the D-Link Wireless G USB Adapter DWA-110

---


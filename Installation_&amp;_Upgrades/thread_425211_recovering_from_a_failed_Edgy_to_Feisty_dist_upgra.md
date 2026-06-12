---
title: "recovering from a failed Edgy to Feisty dist upgrade..."
date: 2007-04-27
forum: Installation &amp; Upgrades
---

### Post by c_martini on 2007-04-27
I had it all working the way I wanted it. All set up and configured just about perfectly ...  Sometimes I forget my hard learnt lessons about not doing a complete backup before trying these new bells and whistles. I am referring of course to the dist upgrade from Edgy to Feisty.

Well now i've run the dist upgrade over an Edgy installation with twin Nvidia cards running in SLI and a kernel mode Nvidia driver installed, also with Beryl. Not a smart thing to do.

With the new kernel (2.6.20.11 i think), it doesn't get to x. After the shiny new Kubuntu startup splash screen, it drops back to a blank screen with a blinking cursor. No login prompt, nothing. It sits there for as long as I can stand to wait for it.

If I restart and then load the previous kernel for which the Nvidia kernel mode driver was installed, it boots without a problem, KDE desktop and all.

I first assumed this was because I had the Driver installed in Kernel mode and had to reinstall it for the new kernel. No problem, I knew this procedure from the last kernel update. Went through the steps, rebooted, same problem... Blank screen blinking cursor, nada.

The system still works fine with the previous kernel, 2.6.17.15 i believe. I just cannot start the system with the new kernel.

I am not a total newb at this, but certainly no expert either. I'm no stranger to the command line, but from a Windows background previously. I rely on things like Automatix and such packages to install and configure most things for me as I just don't have that much time to learn every byte of code and command under the hood of this nice operating system. That's why these forums are priceless with the help and info they encourage.

So now i'm faced with a dilemna. Do I backup my data, wipe and reinstall Feisty from scratch? Do I try and fix the problem? Is it a legitimate bug?


:confused:

---

### Post by zvacet on 2007-04-27
[http://www.psychocats.net/ubuntu/nox]("http://www.psychocats.net/ubuntu/nox")

---

### Post by pheitman on 2007-04-27
I had a similar problems. I'm using the nvidia driver (for beryl). IIRC I had to boot with the previous kernel, use synaptic to install the restricted drivers for the latest kernel (search for nvidia and install the linux-restricted-modules-2.6.20-15 (either 386 or generic or both depending on which kernel you use). Then rebooting using the newer kernel worked...

Peter

---

### Post by c_martini on 2007-04-28
> **pheitman said:**
> I had a similar problems. I'm using the nvidia driver (for beryl). IIRC I had to boot with the previous kernel, use synaptic to install the restricted drivers for the latest kernel (search for nvidia and install the linux-restricted-modules-2.6.20-15 (either 386 or generic or both depending on which kernel you use). Then rebooting using the newer kernel worked...

Peter

thanks for the suggestion Peter. I wil try this now...

:)

---

### Post by c_martini on 2007-04-28
Peter,
That worked well enough to get me logged in with the 2.6.20-15 generic kernel, where I was able to reinstall the 1.0.9755 Nvidia driver in kernel mode. All fixed!

Many thanks to both you and zvacet!
:)

---


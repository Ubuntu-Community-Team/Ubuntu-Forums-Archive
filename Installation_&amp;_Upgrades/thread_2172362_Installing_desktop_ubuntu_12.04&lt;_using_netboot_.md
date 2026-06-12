---
title: "Installing desktop ubuntu 12.04&lt; using netboot (PXE)"
date: 2013-09-04
forum: Installation &amp; Upgrades
---

### Post by Sakrecoer on 2013-09-04
Hi!

I hope i post this in the right place.

There seem to be "netboot" and "netboot". where one is about booting a mini.iso and downloading the rest from internet, and then there is the PXE netboot (PXE is what i want) my search queries tell me there are almost no threads covering the subject in this forum (if i'm wrong feel free to merge me to another thread), and  while #ubuntu #ubuntu-server on IRC have been very kind and helpfull, none seemed to be able to give me light. In average, the documentation is very poor and unconsolidated on the subject of booting a client configured to boot on PXE. I understand it moves fast? Perhaps this thread could help make it more sollid? I hope so...

Enough wineing. :)

I have spent the last few weeks trying to set up a server running bootp, tftpd-hda and apache2 in order to install ubuntu 12.04 on two tabletPC. These two clients are old but work fine with PAE and have ok specs. Unfortunately, in my scenario, there is no internet available.

I have miserably failed.

The closest i have got, was using this howto: [https://help.ubuntu.com/community/Installation/LocalNet](https://help.ubuntu.com/community/Installation/LocalNet) which is dating quite a bit. Everything works fine, the target/client boots up the installer. But when i get to chose a custom mirror. It complains about wrong kernel versions.  Now, I have tried absolutely EVERY .iso there is for 12.04.1-2-3 on  [xkl]ubuntu, twice and the message persists. I tried the netboot 13.04 but that one wouldn't even recognize the mounted .iso in apache a valid one, no matter what version (of course, the 13.04.1-2-3 iso's)

If i execute the install anyways, i end up with a prefectly operational ubuntu 12.04 server terminal. YAY! but since i can't get internet on them, no possible apt-get desktop :(

So my questions are: 
- How do i get the kernels to match? Or, what iso in combination to what netboot do i need?
- The server i run bootp tftpd.hda and apache2 on. Has it got to have a matching kernel as well? i've used a quite powerfull laptop with ubuntustudio12.04 installed on it, where i have added the required software for this operation?
- Do you know of any detailed but not toooooo hightech howto, hidden by the "United SearchEngines against Sakrecoer" that could help me out? :)

However, if i'm still stuck in 6 months i might abandon, but not even such failure could shake my steady ubuntulove.

Thankfull for any hints,
Set H. AKA Sakrecoer

PS.
Now for a happydream break:
Somehow all this has led me to dreama bout a usb-creator-common, called LAN-creator-common, that would allow me to inject any iso into any PXE capable machine. Which seems to have been suggested in the past, but not taken forward: [https://wiki.ubuntu.com/NetbootManagement](https://wiki.ubuntu.com/NetbootManagement)

---

### Post by newbie-user on 2013-09-04
Forget the .iso, that just creates problems because the mirrors have newer versions of everything. That's why you're getting the kernel errors. To prevent that, you either have to install fully from the cd or set up your own Ubuntu mirror with the most current netboot files. Here's a step-by-step tutorial that works without any .iso, though it requires an Internet connection: [http://techblog.glendaleacademy.org/blog/pxebootnetworkinstallrepositoryserver%E2%80%93ubuntu1004](http://techblog.glendaleacademy.org/blog/pxebootnetworkinstallrepositoryserver%E2%80%93ubuntu1004)

But to clarify, you don't have an Internet connection at all? If that's the case, you're kinda stuck installing from a cd or from a bootable usb. Otherwise you'd have to create a local mirror, which would still require an Internet connection.

---

### Post by Sakrecoer on 2013-09-04
Thank you very much.

The internet problem is a missing hardware issue. -edit- The router wants internet from dsl, and won't share the mobile broadband i have acces to on the laptop -edit- I guess i was hopeing i would be able to by-pass that.

I've been advised to use apt-cache-ng to store the packages localy and set up my own little microcosmubuntu :). I intend to. But i can already tell it will take me further time to get a hold on all that process. And until then i will have solved the hardware issue that got me here in the first place.

---

### Post by Sakrecoer on 2013-09-04
i should perhaps add, I have this poetic vision, of enabling. Pentium3, and Ethernet being a very comon standardized interface today on the second hand market. 
[NetbootManagement]("https://wiki.ubuntu.com/NetbootManagement") seems like a very interesting sollution. I am curious about what made it irrelevant.
I shall contact the project maintainer.
I will probably keep the thread posted.

*sakrecoer

---

### Post by Sakrecoer on 2013-09-10
Ok,

I followed the delicious [suggestion]("http://ubuntuforums.org/showthread.php?t=2172362&p=12778949#post12778949") given by newbie-user. But for some reason my apt-mirror could not be detected. I suspect this to be due to my n00biness.

So i finally decided to take the hardware way and get a router that would allow to redistribute a WAN. And **I realised how amazaingly simple and perfect the netboot option is when having internet available!!!!!!!!**

Actualy, when no internet is available, you can persue the installation without mirror. The installer will warn you about not being able to boot without a kernel. But (at least mine) the computer booted perfectly into a terminal where apt-get works and eth0 gets configured automaticaly. So basically, depending on your machine, once you've booted it with the netboot image. you could take it somewhere you can plugg it to internet and apt-get the distro you fancy!

I still intend to learn how to set up my own mirror. But it will take some more time. Until then: THANK YOU AWSOME DEAR BELOVED SUPER DEVS FOR MAKING THIS SUPER EASY NETBOOT THING!!!!!!!!! <3 <3 <3 <3

---


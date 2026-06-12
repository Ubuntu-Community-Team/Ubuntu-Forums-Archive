---
title: "Seriously considering going back to Windows..."
date: 2017-05-18
forum: Installation &amp; Upgrades
---

### Post by Boosh007 on 2017-05-18
This WiFi glitch is knutz... It has disabled my older laptop for good. I've tried at least a dozen EASY fixes, but they've only been temporary at best. Each time it works, the next time it becomes immune to its effect. I recently tried just installing a completely new system (17.04) on a wiped laptop, but the glitch has followed me. At the beginning of the download I had a working WiFi and internet connection, but just before the finally download, the system shut it off, and now claims it needs files from Ubuntu to finish the process. It's left me with one giant terminal screen. The only thing I can do is type in my username and password. Since it's not yet downloaded completely, any attempt to find hardware on the system is rendered useless, so I can't open the WiFi or any other components. I even tried connecting a hard line cable to the system for the WiFi, but since the system isn't fully downloaded the system connection isn't recognized. Any other ideas of what I might try?...

---

### Post by LastDino on 2017-05-18
Not the actual solution to your problem as it has me stumped too, but is the option to download full setup ISO and installation not attractive?

If I was in your place, I would probably try that out as it is more easy.

On the actual issue>
What WiFi card does your old lappy have? Make of lappy and few more hardware details might as well help here if you want someone who has knowledge of this to help on the issue

---

### Post by Bucky Ball on 2017-05-18
Did you tick 'Install updates while installing' or 'add third-party software' (something like that) during the install? If so, there is a good chance it's hanging there. Untick those things during install as you need to be online for that to happen and it appears you're not.

Prepare an ethernet cable because once your system is installed, you will probably need to plug it in and get online and update to get your wireless working.

If you want better support with this you might have a better chance if you change the title of the thread to something that reflects the issue you are having. ;)

* Good, just noticed you have an ethernet cable. As above, if you have the update and third-party software options ticked during install, untick them. Once you get to the end of the install, plug the ethernet cable in when you are asked to reboot and reboot.

---

### Post by Boosh007 on 2017-05-18
It was a full setup, 685 megabytes worth. The files from the internet were to confirm setup of the operating system. The old one has been tossed. It had other issues besides that, what with Windows 7 Pro stuck in a reboot loop, among other things...

---

### Post by Boosh007 on 2017-05-18
Didn't get that far. Mind you the system never came up. In was in the last field of setting up 17.04, before the main screen would appear. There was no updates or third party software to install. I got the disc copy direct from the ubuntu website (ubuntu 17.04 server amd64.iso) As with the cable, it's not recognized as a port by the system, since it didn't get that far in the download. I just tried to bring up the WiFi component for the new system, after entering the commands to do so after the force restart of network manager, but it comes up with no such component. hmm...

---

### Post by ajgreeny on 2017-05-18
> **Boosh007 said:**
> Didn't get that far. Mind you the system never came up. In was in the last field of setting up 17.04, before the main screen would appear. There was no updates or third party software to install. [COLOR="#FF0000"]I got the disc copy direct from the ubuntu website (ubuntu 17.04 server amd64.iso)[/COLOR] As with the cable, it's not recognized as a port by the system, since it didn't get that far in the download. I just tried to bring up the WiFi component for the new system, after entering the commands to do so after the force restart of network manager, but it comes up with no such component. hmm...
You do realise that the server version does not have any GUI when installed?  The server version is command line only and will need commands issued to set up any wifi connection.

Do you really need a server version or do you want the full Ubuntu (or other DE version, eg Xubuntu, Lubuntu, etc etc) with a complete GUI desktop environment?

---

### Post by Bucky Ball on 2017-05-18
As above. Why the server??? If you have no specific reason, don't bother. Do you want all the server stuff that comes with it? Will you ever use that software?

If you answered no, then stick to the desktop version of Ubuntu or the flavour of your choice. If you are looking to do a minimal install, then go for the [minimal install]("https://help.ubuntu.com/community/Installation/MinimalCD") or a core version, Xubuntu-core or Lubuntu-core. I think there is a Ubuntu-core as well, though don't quote me.

The minimal install will give you the kernel only. You install whatever else you want.

---


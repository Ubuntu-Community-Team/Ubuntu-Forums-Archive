---
title: "Force boot after improper shutdown"
date: 2010-03-12
forum: Installation &amp; Upgrades
---

### Post by PlymWS on 2010-03-12
Hi all,

I've installed xUbuntu on a machine I will be using as a file server.  Everything is fine except one thing.  If the server suffers an improper shutdown such as a loss of power the next time the machine boots it gets to the GRUB2 boot menu and then waits for a keyboard input.

As this machine runs headless with nothing connected other than a network cable and power lead and is tucked away under the stairs it's quite an inconvienience to go to the machine and plug in a keyboard so I can press enter.

Is there some way I could force the machine to boot as normal without stopping at the menu ?

TIA for any help.

---

### Post by akand074 on 2010-03-12
hmm, you can try this: 

```
sudo apt-get install startupmanager
```

Then go to System > Administration > StartUp-Manager and play around there, they have a feature to set a default OS, wait time before boot to the OS, etc, pretty much a GUI to play around with the Grub file. When I have improper shut-downs it still auto-boots into my Ubuntu (I put it as my default and wait time as 0s, its my only OS on this computer).

---

### Post by Jose Catre-Vandis on 2010-03-12
Have you edited the grub config files to "miss out" the grub menu and just boot?

---

### Post by PlymWS on 2010-03-12
> **Jose Catre-Vandis said:**
> Have you edited the grub config files to "miss out" the grub menu and just boot?
Not yet.  What would I have to do to achieve this ?  The only file I've looked at is not to be edited :)

---


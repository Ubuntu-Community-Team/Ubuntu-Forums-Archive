---
title: "Discover complains about a software source"
date: 2023-05-22
forum: Installation &amp; Upgrades
---

### Post by Tom_ZeCat on 2023-05-22
I'm busy getting a new Dell desktop set up with Kubuntu 22.04 LTS.  If you need details about this PC, it's this one: 

[INDENT]Dell Optiplex 7040 Tower, i7-6700 Quad Core upto4.2 Ghz, 1TB SSD, 16GB RAM[/INDENT]

Things are going okay, except that I keep getting the following error message when I bring up Discover Software Center: 

[IMG]https://i.postimg.cc/0270YWdB/discover-error-message-final.png[/IMG]

I thought I must have accidentally installed some unauthorized PPA of Flatpak, so I went into Muon Package Manager and purged my install of Flatpak, but the error persisted.  I then purged anything related to Flatpak.  It was some program named "backend."  I restarted the PC, but that error message still persists.  As near as I can tell, I must have installed this Alex Larsson PPA for Flatpak, but Kubuntu doesn't trust it.  Is that what's going on?  How do I get rid of this thing.  

I haven't done any Flatpak-based installs yet on this new PC.  I'll reinstall Flatpak when I need it, but, first, how do I get rid of this untrusted PPA?

---

### Post by MAFoElffen on 2023-05-22
If you go to the PPA: [https://launchpad.net/~alexlarsson/+archive/ubuntu/flatpak](https://launchpad.net/~alexlarsson/+archive/ubuntu/flatpak)
...and look at the releases there are packages built for that PPA, it does not have any packages built for release Jammy (22.04). The last release files were built for Focal. It has also not been updated in over 80 weeks. So it should be removed from your sources...

It seems to be a mystery how it would have gotten into your sources list without you putting it in yourself, but it has. No matter.

You have two options to correct this this... 
Option #1 -- Open 'Software & Updates'. Go to the Other Software Tab. Look for the PPA and select it with your mouse. Either uncheck the checkbox, or Select the "remove" button.

Option #2 -- Please run the [UbuntuForums 'system-info' Script]("https://github.com/UbuntuForums/system-info"). Check for FlatPak app's in the Installed FlatPak Applications Section. Check the Apt Source Section to look for the PPA address and see if the line for it is in the /etc/apt/sources.list file, or a separate file in folder /etc/apt/sources.list.d/. If in the sources.list, edit it and either comment it out or remove those lines. If a separate file in the /etc/apt/sources.list.d/ folder, rename or remove it.

---

### Post by Tom_ZeCat on 2023-05-23
> **MAFoElffen said:**
> If you go to the PPA: [https://launchpad.net/~alexlarsson/+archive/ubuntu/flatpak](https://launchpad.net/~alexlarsson/+archive/ubuntu/flatpak)
...and look at the releases there are packages built for that PPA, it does not have any packages built for release Jammy (22.04). The last release files were built for Focal. It has also not been updated in over 80 weeks. So it should be removed from your sources...

It seems to be a mystery how it would have gotten into your sources list without you putting it in yourself, but it has. No matter.

You have two options to correct this this... 
Option #1 -- Open 'Software & Updates'. Go to the Other Software Tab. Look for the PPA and select it with your mouse. Either uncheck the checkbox, or Select the "remove" button.

Option #2 -- Please run the [UbuntuForums 'system-info' Script]("https://github.com/UbuntuForums/system-info"). Check for FlatPak app's in the Installed FlatPak Applications Section. Check the Apt Source Section to look for the PPA address and see if the line for it is in the /etc/apt/sources.list file, or a separate file in folder /etc/apt/sources.list.d/. If in the sources.list, edit it and either comment it out or remove those lines. If a separate file in the /etc/apt/sources.list.d/ folder, rename or remove it.

That fixed the problem.  Thank you so much.  It's not such a big mystery how that ended up on my computer.  I installed it by mistake.  I keep an organized CherryTree database record of everything I've ever installed in Kubuntu, going back to version 13.04.  I have it organized into the nodes "high," "medium," and "low" priority, and I often include info on how I installed it.  Flatpak was a high priority item.  I must have gotten ahead of myself, and installed it exactly how I did for a previous Kubuntu version without checking if it was good for this version yet.  I've learned my lesson.  

I've saved your info in my database in case I ever need it again, though I plan to look more closely at my install notes from here on out.  Your help is extremely appreciated.  Thank you.

---

### Post by MAFoElffen on 2023-05-23
You are welcome. Glad I could help.

If solved-- Please use the link on the upper right "Thread Tools" to mark this thread as "Solved" so that other Users can find your solution to help resolve their own similar problems.

---


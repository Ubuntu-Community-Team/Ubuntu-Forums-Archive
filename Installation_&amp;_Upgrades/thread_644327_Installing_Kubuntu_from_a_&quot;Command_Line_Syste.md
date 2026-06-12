---
title: "Installing Kubuntu from a &quot;Command Line System&quot;"
date: 2007-12-18
forum: Installation &amp; Upgrades
---

### Post by Ubiquitous1980 on 2007-12-18
**The reason why I make this post is for those who own a Ubuntu disk and want to install Kubuntu without the added GNOME elements.  The method to do this is as  follows:**


Boot either a LiveCD or an Alternate CD and install the command line system.  Some people may find kernel panic when they do this or any other install for that matter.  The best way to avoid this kernel panic (if it is caused by ACPI) is F6 at "Install a Command Line System" and add the acpi=off entry in the kernel line.


[LIST]
[*][I]When the command line system has been installed you will be presented with a user prompt.  
[/I]
[*]Type sudo su; and log in with your user password.



[*]Now type apt-get install kubuntu-desktop.

[*]For those whose repositories were not set correctly on installation, you will have to edit the /etc/apt/sources.list file and remove any deb repositories that have been commented out with a #.

[*]To edit the sources.list file type: nano /etc/apt/sources.list


[*][Exit and type the following to update apt for the added repositories: apt-get update.



[*][Once apt is updated type: apt-get install kubuntu-desktop
[/LIST]


[I]Depending on your connection, you can expect the download and install process to take approximately 45 minututes.

Notice on boot that the splash screen and shutdown splash screen are not at the correct resolution.  This can be resolved, but is outside the subject area of this tutorial.[/I]

---

### Post by sethfc on 2007-12-18
i'm new to linux...

but would this also be a completely "clean" install?  as in, there are no additional programs, like rhythmbox, etc etc?

I'm trying to do this, because I hate some of the pre-loaded programs that come with ubuntu (like rhythmbox), and i'd just like to have an install where I know exactly whats on the computer, and it's exactly what i need.

---

### Post by Ubiquitous1980 on 2007-12-18
Yes, this is a completely clean install.  You get a baseline kubuntu install.  There is only one more basic setup than this, and because I don't recommend it, I won't be posting it. :)

---

### Post by sethfc on 2007-12-19
sa-weet!
i'll come to you if i have questions =p

---


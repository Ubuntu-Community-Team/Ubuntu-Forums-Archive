---
title: "Gnome Shell installation problem in ubuntu 11.10"
date: 2012-03-13
forum: Installation &amp; Upgrades
---

### Post by ldhankey on 2012-03-13
I am trying to install Gnome shell in Ubuntu 11.10. I have tried to install it both with the software center and with a terminal. My updates are all up to date. I get the following message.
```
 The following packages have unmet dependencies:
 gnome-shell : Depends: gir1.2-clutter-1.0 but it is not installable
               Depends: gir1.2-cogl-1.0 but it is not installable
               Depends: gir1.2-folks-0.6 but it is not installable
               Depends: gir1.2-gee-1.0 but it is not installable
               Depends: gir1.2-json-1.0 but it is not installable
               Depends: gir1.2-mutter-3.0 but it is not going to be installed
               Depends: gir1.2-telepathyglib-0.12 but it is not installable
               Depends: gir1.2-telepathylogger-0.2 but it is not installable
               Depends: gjs (>= 1.29.18) but it is not going to be installed
               Depends: libclutter-1.0-0 (>= 1.7.6) but it is not installable
               Depends: libcogl5 (>= 1.7.4) but it is not installable
               Depends: libgjs0c (>= 1.29.18) but it is not going to be installed
               Depends: libmozjs185-1.0 (>= 1.8.5~hg20110306r6) but it is not installable
               Depends: libmutter0 (>= 3.2.1) but it is not going to be installed
               Depends: caribou but it is not going to be installed
               Depends: gir1.2-gkbd-3.0 but it is not installable
               Depends: gir1.2-polkit-1.0 but it is not installable
               Depends: gir1.2-upowerglib-1.0 but it is not installable
               Recommends: gnome-themes-standard but it is not going to be installed
               Recommends: gnome-session-fallback but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```
]I am at a loss as to what to do now. Please help! I had no idea how hard it would be to install Ubuntu and get Gnome running. It is taking me weeks!

---

### Post by zvacet on 2012-03-13
```
sudo apt-get -f install
```

---

### Post by ldhankey on 2012-03-14
[SIZE=2]I have tried sudo apt-get -f install, numerous times. All I get is:[/SIZE][INDENT]Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 87 not upgraded.

[/INDENT][SIZE=2]I'm not really getting any clues from that.

Just to clarify - just did another update, I now get:
 
~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

But I still get all the dependency errors when I try installing Gnome Shell.


[/SIZE]

---

### Post by ldhankey on 2012-03-14
This may be related to my problem? Although my gearwheel (sorry, don't know the proper name for that) indicates that my software is up to date, a discrete red triangle with an exclamation mark suggests I should check for updates again to check for failed repositories. When  I do this, the Update Manager gives me the following error message:
[INDENT]Failed to download repository information

[/INDENT]If I check the details, it says:
[INDENT]W:Failed to fetch gzip:/var/lib/apt/lists/partial/ie.archive.ubuntu.com_ubuntu_dists_oneiric_main_binary-i386_Packages  Hash Sum mismatch
, W:Failed to fetch gzip:/var/lib/apt/lists/partial/ie.archive.ubuntu.com_ubuntu_dists_oneiric_main_i18n_Translation-en  Encountered a section with no Package: header
, E:Some index files failed to download. They have been ignored, or old ones used instead.

[/INDENT]I am instructed to check my Internet connection, but it is fine. Could this be where the missing dependencies for Gnome Shell are? How can I resolve this?

---

### Post by ldhankey on 2012-03-14
> **zvacet said:**
> ```
sudo apt-get -f install
```
Thanks, but this doesn't help me. Please check my new replies on the subject if you think you can help...

---

### Post by bcarlowise on 2012-03-15
Try the following:

sudo apt-get install --reinstall gnome-session gnome-shell

Let us know what happens.

---

### Post by ldhankey on 2012-03-16
Hi, I tried that - no joy.[FONT=Arial] I am reproducing the full transcript of the terminal session below, in case I am leaving out important inform[/FONT]ation.
[FONT=Courier New][COLOR=RoyalBlue]
[/COLOR][/FONT][INDENT][FONT=Courier New][COLOR=RoyalBlue]~$ sudo apt-get install --reinstall gnome-session gnome-shell
[sudo] password for lucie: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 gnome-shell : Depends: gir1.2-clutter-1.0 but it is not installable
               Depends: gir1.2-cogl-1.0 but it is not installable
               Depends: gir1.2-folks-0.6 but it is not installable
               Depends: gir1.2-gee-1.0 but it is not installable
               Depends: gir1.2-json-1.0 but it is not installable
               Depends: gir1.2-mutter-3.0 but it is not going to be installed
               Depends: gir1.2-telepathyglib-0.12 but it is not installable
               Depends: gir1.2-telepathylogger-0.2 but it is not installable
               Depends: gjs (>= 1.29.18) but it is not going to be installed
               Depends: libclutter-1.0-0 (>= 1.7.6) but it is not installable
               Depends: libcogl5 (>= 1.7.4) but it is not installable
               Depends: libgjs0c (>= 1.29.18) but it is not going to be installed
               Depends: libmozjs185-1.0 (>= 1.8.5~hg20110306r6) but it is not installable
               Depends: libmutter0 (>= 3.2.1) but it is not going to be installed
               Depends: caribou but it is not going to be installed
               Depends: gir1.2-gkbd-3.0 but it is not installable
               Depends: gir1.2-polkit-1.0 but it is not installable
               Depends: gir1.2-upowerglib-1.0 but it is not installable
               Recommends: gnome-themes-standard but it is not going to be installed
               Recommends: gnome-session-fallback but it is not going to be installed
E: Unable to correct problems, you have held broken packages.[/COLOR][/FONT]

[/INDENT]Any more ideas? How about the repository that I can't update I mentioned earlier?

---

### Post by bcarlowise on 2012-03-16
Ok, try this next. If you have any 3rd party repositories enabled in Software Sources disable them. Only have the "Canonical Partners" and "Independent" repositories enabled.

ext, let's remove Gnome completely so we can then install it again fresh:

sudo apt-get remove --purge gnome-session gnome-shell
sudo apt-get autoremove

Next, you will need to reinstall the ubuntu-desktop package since it gets uninstalled in the first step:

sudo apt-get install ubuntu-desktop

Now reboot your machine. When it comes back up, ctl-alt-f3 to get to the terminal window. Login using your credentials. Now we will reinstall Gnome:

sudo apt-get install gnome-session gnome-shell

Hopefully everything will install correctly this time. If so, just reboot and when it comes back up try and log into both Unity and Gnome to make sure both work correctly.

I performed these steps on my working system and I am able to log into both Unity and Gnome3 just fine. If Gnome still will not install correctly then my next recommendation is to just back up your data and do a fresh install. Once the install is complete, log into Unity and perform an update. Once the update is done, install gnome-session from the Ubuntu Software Center. It will install all the needed packages.

Let me know how it goes.

---

### Post by ldhankey on 2012-03-16
Thanks. Plan A didn't work either. However, before resorting to Plan B (a reinstall) I did a bit more delving into ubuntu problems. What I ended up doing is changing my server for software updates from one in Ireland to one in the UK. This seemed to solve all my problems. So I presume there are faulty files sitting on the Irish server. Who would I let know about this?

Thanks everyone for your suggestions. It's been a steep learning curve!

---

### Post by bcarlowise on 2012-03-16
Glad you were about to get it figured out!

---

### Post by fubofo on 2012-03-28
Can I continue this on instead of creating another thread about the same issue?

My machine (Ubuntu 11.10 64bit) was running perfectly with gnome-shell 3.2.1 for months but as of an update yesterday my entire display is gone.

I managed to SSH into my machine (was only showing black/powered off monitor - yet with power on) and noticed a lot of issues with dependencies, so I installed gnome-shell-extensions which allowed me to reboot and get a login prompt.

Now I cannot reinstall gnome-shell (I can load Gnome Classic) and am having the same errors as previously posted.

```
kaipee@zoostorm-ubuntu:~$ sudo apt-get install gnome-session gnome-shell
[sudo] password for kaipee: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gnome-session is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 gnome-shell : Depends: gir1.2-mutter-3.0 but it is not going to be installed
               Depends: libcogl5 (>= 1.7.4) but it is not going to be installed
               Depends: libmutter0 (>= 3.2.1) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
kaipee@zoostorm-ubuntu:~$ 

```

Any help with this would be MUCH appreciated

---


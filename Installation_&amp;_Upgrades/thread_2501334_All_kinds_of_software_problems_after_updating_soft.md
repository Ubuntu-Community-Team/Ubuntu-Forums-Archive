---
title: "All kinds of software problems after updating software / Kernal"
date: 2024-10-02
forum: Installation &amp; Upgrades
---

### Post by pdxwebdev503 on 2024-10-02
[COLOR=#0C0D0E][FONT=-apple-system]I am currently using Ubuntu 22.04 LTS.[/FONT][/COLOR]
[COLOR=#0C0D0E][FONT=-apple-system]this morning I tried to update my system's software. I started by using the GUI (Ubuntu dialog that says "these updates are ready, do you want to install?"[/FONT][/COLOR]
[COLOR=#0C0D0E][FONT=-apple-system]This produced a black screen, and after some time, forced a restart by unplugging my machine. Upon restart, I entered straight into a GRUB prompt.[/FONT][/COLOR]
[COLOR=#0C0D0E][FONT=-apple-system]After some debugging, I realized I had to boot into an older kernal to get into the OS, then I was able to fix the new kernal.[/FONT][/COLOR]
[COLOR=#0C0D0E][FONT=-apple-system]Now that I can boot into the OS, Apps like Brave Browser, Sublime, and BitWarden are all unreesponsive. Google Chrome, VS Code, and Sublime merge seem to be working just fine.[/FONT][/COLOR]
[COLOR=#0C0D0E][FONT=-apple-system]I have no idea what SnapD is, or Apt, or gnome.... i'm guessing one or all of those are corrupt?[/FONT][/COLOR]
[COLOR=#0C0D0E][FONT=-apple-system]sudo apt update && sudo apt upgrade && sudo apt-get dist-upgrade all report everything is up to date.[/FONT][/COLOR]
[COLOR=#0C0D0E][FONT=-apple-system]attempting to restart snapd results in a hanging terminal (ref: [Cannot communicate with server: Post [http://localhost/v2/apps:](http://localhost/v2/apps:) dial unix /run/snapd.socket: connect: no such file or directory]("https://askubuntu.com/questions/1258137/cannot-communicate-with-server-post-http-localhost-v2-apps-dial-unix-run-sn"))[/FONT][/COLOR]
[COLOR=#0C0D0E][FONT=-apple-system]I then tried to just update to 24.04 (ref: [https://www.cyberciti.biz/faq/how-to-upgrade-from-ubuntu-22-04-lts-to-ubuntu-24-04-lts/](https://www.cyberciti.biz/faq/how-to-upgrade-from-ubuntu-22-04-lts-to-ubuntu-24-04-lts/)) but terminal stalls when trying to continue the upgrade (sudo do-release-upgrade)[/FONT][/COLOR]
[COLOR=#0C0D0E][FONT=-apple-system]Immediately I need my Apps like Brave Browser to work. I thought i had installed these apps via the snapd store but i really have no idea why there is snap and gnome and whatever the new one it :/

I have no idea how to go about diagnosing this. The only option I can think of is to put 24.04 on a bootable usb and hope that will fix everything. Still, this problem seems stupid and I'm curious to understand more and how to avoid this in the future[/FONT][/COLOR]

---

### Post by pdxwebdev503 on 2024-10-02
It seems the problem is that all of my apps inastalled with Snap were broken. i purged my snap installs with this command:

sudo apt autoremove --purge snapd

I had to rename the Firefox folder because it had some read-only files. After a couple attempts, I was able to empty out my snap folder and reinstall all my apps using apt

---

### Post by Rick St. George on 2024-10-04
So ... its fixed now? 
If so,  please mark thread as "solved".
Thanks!

---

### Post by grahammechanical on 2024-10-04
> [COLOR=#0C0D0E][FONT=-apple-system]but i really have no idea why there is snap and gnome and whatever the new one it :/[/FONT][/COLOR]

Please, let us not start an argument.

Software has to be packaged. Ubuntu is built on Debian which uses the debian package format (deb). To install or remove installed deb packaged software we need a package manager. Ubuntu uses apt. Read about it.

```
man apt
```

Gnome is an organisation that develops the gnome3 desktop environment and the gnome3 shell user interface. There are other kinds of desktop environment. But Ubuntu uses Gnome.

For years now there have been moves to create package formats that are more secure than the Debian (deb) and the Redhat package formats (rpm). There are two available. Flatpak and Snap (which is developed by Ubuntu's sponsor - Canonical).

Because Debian has software called SystemD (developed by Redhat) to start and stop processes, Ubuntu also has SystemD. To blend snap packaged applications into SystemD Ubuntu uses some software called snapd. Remove snapd and snap packaged applications cannot run. I am not sure if they can be installed.

Flatpak applications cannot run on Ubuntu without the installation of special software. Why have software such as Flatpak and Snap?

Software packaged in these formats is said to be confined. It cannot access system files. With the right additional software Flatpak and Snap can run on any Linux distribution. Debian package applications cannot run on Fedora. It runs rpm packaged applications. Likewise, rpm packaged applications cannot run on Debian based distributions. They use the deb package format. So, software developers see an advantage to having a package format that can run on any Linux distribution regardless of the original package format that the distribution used.

Regards

P.S. Yes, I do know about Appimage. I cannot confirm if these applications use confinement.

[https://appimage.org/](https://appimage.org/)

---

### Post by 1fallen on 2024-10-04
Just to fill in the Blanks

AppImage features

[list]
    
[*]Distribution agnostic: Can run on various different Linux distributions
    
[*]No need of installing and compiling software: Just click and play
    
[*]No need for root permission: System files are not touched
    
[*]Portability: Can be run anywhere including live disks
    
[*]Apps are in read-only mode
    
[*]Software is removed just by deleting the AppImage file
    
[*]Applications packaged in AppImage are not sandboxed by default.
[/list]

---


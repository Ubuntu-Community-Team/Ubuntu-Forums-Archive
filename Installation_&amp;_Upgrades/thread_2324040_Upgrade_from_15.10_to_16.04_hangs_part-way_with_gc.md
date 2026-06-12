---
title: "Upgrade from 15.10 to 16.04 hangs part-way with gconf2 problem"
date: 2016-05-10
forum: Installation &amp; Upgrades
---

### Post by Christopher_Waldon on 2016-05-10
I'm upgrading from 15.10 to 16.04, and the process appeared to be going smoothly for a while. The updater made it through the "Preparing to upgrade," "Setting new software channels," and "Getting new packages" steps without issue. However, about a quarter of the way through the "Installing the upgrades" step, an error dialog popped up with the following:

Could not install 'gconf2'
The upgrade will continue but the 'gconf2' package may not be in a working state. Please consider submitting a bug report about it.
dependency problems - leaving triggers unprocessed

I figured that something small had gone wrong, so I didn't worry about it. I clicked the "Close" button on the dialog box, and the dialog closed. Sadly, it immediately reopened. Every time I close it, it opens itself again. In the background, the upgrade appears to be frozen. Beneath the progress bar it says "Configuring dbus (amd64)" and the last thing in the Terminal at the bottom of the upgrade window is "Preparing to unpack .../libe-book-0.1-1_0.1.2-2ubuntu1_amd64.deb ..."

I can open other applications still (I've only tried it with the terminal), but I'm not really sure how to proceed. I imagine that rebooting partway through an upgrade would break something, and there doesn't seem to be an easy way to cancel or revert the process, so I came here hoping that someone had some suggestions for moving past this in the upgrade process.

---

### Post by Christopher_Waldon on 2016-05-14
In case anyone else encounters this issue, it was a problem with unconfigured packages. I'm no expert on the package system that underlies apt, but something was broken. To fix it, I ran:
[FONT=courier new]sudo apt full-upgrade -f
sudo dpkg --configure -a
sudo apt-get dist-upgrade
sudo apt-get install -f[/FONT]
Those steps, combined with running the software updater application upgraded me to 16.04. However, I now get dozens of warnings whenever I login that read "System program problem detected." All of them are because the system tried to install a package that was already configured. I'm not sure how to get the system to stop complaining about them, but at least it works. Any advice on getting rid of those popups would be appreciated.

---

### Post by g1g133 on 2016-05-29
I've just had the same issue. For anyone else that encounters this, to get past the roadblock continue to click on the "close" button on the dialog boxes (or keep hitting the return key), it looks like the boxes keep coming back because it's many instances of the error that are reported but eventually they will go away and the upgrade process resumes.

In my case it got to the end and then it said that some errors were encountered and my system may be unusable. I had to manually reboot and the shut down hang so I had to long press the power button. However then the system booted and I could log on okay without having to run any apt-get or dpkg commands. The only problem was that the launcher and the windows title bars weren't there but a 'unity --reset' fixed that.

---

### Post by michaelaquilina on 2016-07-18
Just FYI, the installation does not hang. If you had the Terminal section open you will see that the installation is proceeding as normal. Clicking on close multiple times will eventually make it stop. It is rather scary to see this as a user during an upgrade though :(

---


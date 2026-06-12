---
title: "DPMS Power save problems"
date: 2008-09-21
forum: Installation &amp; Upgrades
---

### Post by BobvanderPoel on 2008-09-21
I've recently upgraded my Gutsy to Hardy. A few minor problems, but the DPMS screen savings have been nothing but a problem.

The system I have is a desktop using the Nvidia binaries. Kubuntu is installed over top of the standard Ubuntu stuff. I'm running kde-3.

The problem is that the power saving options selected via the system settings->monitor/display don't save. I can set them as user or admin, but each time I log in I need to redo it.

I thought I'd be clever and add the line:

   xset dpms 600 1200 1800

to a file in my .kde/Autostart. But, that doesn't work. I think it takes, but then get overridden.

Getting kpowersaver running does solve the problem. But, only if it is running. If I stop it and don't set it to run on login, my dpms is disabled.

I traced this earlier to the gnome-power-manager program running in the background. Removing this program via apt-get solved the problem. But, that also disabled any login to a gnome desktop session. Not the end of the world, but a pain.

So, what I have ended up doing is to install the gnome-session and power-manager programs and deleted /usr/bin/gnome-power-manager. Now, when I log in to K my local script sets the dpms. I assume that the setting in my xorg.conf file is also taking effect, but I'm getting too tired to check.

Question: some process is starting the program gnome-power-manager ... which? I've spent too much time looking/tracing startup scripts and can't figure it out. I think that the problem I'm having is just a result of updates PLUS the fact that kubuntu appears to be a poor cousin of ubuntu :)

I'd like to have the proper fix for this. Deleting gnome-power-manager seems a bit extreme!

---


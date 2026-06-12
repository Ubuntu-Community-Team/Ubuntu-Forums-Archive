---
title: "Installing for a disconnected (from Internet) environment"
date: 2014-02-11
forum: Installation &amp; Upgrades
---

### Post by richard36 on 2014-02-11
Hi

I need to setup a small network of Ubuntu Desktops (with 1 Ubuntu Server) in an environment where they will never be connected to the Internet (difficult to believe I know).

I will be able to do the initial setup whilst connected, but once the installation is complete they will not be anywhere near a working network connection.

I intend to build a apt-mirror of the packages that I think I might need on the system during it's lifetime.

I would like to remove (or disable) any applications or services that expect to be able contact the Internet (i.e. social networking, search lenses etc.). I don't care to much about the disk space (or CPU) that they consume, but I don't want my network to be cluttered up with lots of failed connections.

Is there a list of packages anywhere that I could use as a starting point for removal, alternatively, are there any instructions for disabling any such applications?

Many thanks

Richard

---

### Post by Kirboosy on 2014-02-11
Welcome to the forums! 

I have found [Synaptic Package manager]("https://help.ubuntu.com/community/SynapticHowto") to be very simplistic and easy to use. It has the ability to show all installed packages and their descriptions. You can most likely figure out what packages will do you no good on your secluded enviroment. Also with Synaptic you can export the configuration before you apply it. That would enable you to only have to sort through the packages once, save it, and then with a thumbdrive you could carry the file to the next computer. That should make your life easier on setup.

Hope that helps!
~Caboose

---


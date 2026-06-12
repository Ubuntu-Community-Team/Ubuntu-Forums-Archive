---
title: "Hardy a bit buggy!"
date: 2008-07-24
forum: Installation &amp; Upgrades
---

### Post by Piddell on 2008-07-24
I've just moved from 6.06 to Hardy and its much nicer, but has a number of "features" which might be described as bugs:
1.  Network vanishes.
50% of the time I boot up the network is not available, and I have to run sudo dhclient to restore it
2.  update manager hangs (just before you enter your password) and I have to xkill it and run sudo apt-get update (twice) to restore it.
3.  It will not auto detect my camera, I have to run gThumb manually to import my pictures.
These features are all new since my upgrade.  Looking through the support forums I don't think I'm the only one with these issues?

I love the new multimedia support.

Phill

---

### Post by althequick on 2008-07-24
Same issue:
I tried to upgrade from version ... (dunno, sorry) to 8.04 LTS Hardy. The update manager stalled at moment as he tried to install the locals. I interrupted the update process (bad, i know, but nothing happened anymore) and restarted. After that, ubuntu is not starting any more. That means:
1) Press start button
2) Ubunutu logo with progress bar appears
3) Progress bar completes
4) Ubuntu is loading Gnome
5) Mousepointer appears, screen stays unicolor fawn.
6) Nothing seem to happen anymore
7) if i now press the start button, ubunto shuts down with the following error message: I made a camshot of the errormessage. the flash reflection prevented me from decoding the xxxxxxxxx in xxxxxxxxx_logs_days without

> 
Starting web server apache 2 [OK]
/etc/rc2.d/S50mysql: ERROR xxxxxxxxx_logs_days without log_bin crashes the server. See README.Debian.gz
Starting ftp server proftpd [OK]
Starting anac(h)ronistic cron anacron [OK]
Starting deferred execution scheduler atd [OK]
Starting periodic command scheduler crond [OK]
Starting additional executable binary formats binfmt-support [OK]
Checking battery state... [OK]
Running local boot scripts (/etc/rc.local) [OK]
NetworkManager: <WARN> nm_signal_handler(): Caught signal 15, shutting down nor mally

NetworkManager: <info> Caught termination signal

NetworkManager: <debug> [1216885578.967090] nm_print_open_socks(): Open Sockets
List:

NetworkManager: <debug> [1216885578.967249] nm_signal_handler(): nm_print_open_socks(): Open Sockets
List Done.



I think its worth to recemmend that, during the update process the update manager told me (while updating locals) that he has no connection any more. At this time he told me, that 8 minutes of updating are left...

What can i do now? All data lost? Reinstallation?

Greetings,
Alexander

---

### Post by Piddell on 2008-07-25
> **althequick said:**
> 
What can i do now? All data lost? Reinstallation?


With Ubuntu you don't normally need to start from scratch (that's the old windows world), the trick is to figure out what the problem is and re-work that bit of code.  The hard bit is figuring out the problem, unless your a bit of a command line expert.

---

### Post by althequick on 2008-07-25
Hi,
problem solved!

The bug, i came across, is discussed here: [https://bugs.launchpad.net/ubuntu/+source/langpack-locales/+bug/249340](https://bugs.launchpad.net/ubuntu/+source/langpack-locales/+bug/249340)

In brief:

Bug: Updating from Edgy to Hardy results in a stalling GUI-Update-Manager when he tries to install the OS-Locales.

Solution:
1) Interrupt the installation process
2) reboot
3) start with a kernel in a prvious version (not in recovery mode, the current one seems to habe problems with the locale-gen process)
4) get into a console and type: dpkg --configure -a to restart updateprocess
5) locales should now installed correctly
6) reboot with the current kernel

Thats it.

---


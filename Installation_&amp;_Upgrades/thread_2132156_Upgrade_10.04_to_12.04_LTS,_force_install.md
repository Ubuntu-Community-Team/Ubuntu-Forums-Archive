---
title: "Upgrade 10.04 to 12.04 LTS, force install?"
date: 2013-04-03
forum: Installation &amp; Upgrades
---

### Post by agnewton on 2013-04-03
[COLOR=#232323][FONT=Verdana]I am a relative newbie who searched the forum for posts to solve my problem, but I have either not hit on the right combination of terms or just don't quite have the jargon/ understanding to get it right.  Please bear with me if the solution is really obvious.  [/FONT][/COLOR]
[COLOR=#232323][FONT=Verdana]
[/FONT][/COLOR]
[COLOR=#232323][FONT=Verdana]The terminal use of "apt-get" suggests I force install, but I was under the impression that using "-f" is a somewhat dangerous practice for the uninitiated (I am uninitiated).  With the description of the symptoms below, what are the risks of a force install and what packages should I force install?  It's a loaded question, I realize.  Is there another work around that would preserve my partitions and built-from-scratch applications? Can I just install the boot/ OS partition from DVD (it's on a separate partition) without losing the integrity of my /opt/, /usr/local/, and /home/ directories (they are on separate partitions; they all contain applications and packages built from scratch)?[/FONT][/COLOR]
[COLOR=#232323][FONT=Verdana]
[/FONT][/COLOR]
[COLOR=#232323][FONT=Verdana]**Description of Symptoms:** I used the Software Update/ Upgrade to upgrade my OS to 12.04 LTS.  During the process, I began receiving messages about available disk space. Dialogs with what appeared to be font issues (Multiple small boxes, instead of characters, where the sentences would be and two blank "buttons" that functioned as "OK" and "Cancel") would appear.  The "OK" option opened up a "Disk Usage"-type dialog window. Without fear, I just kept clicking through these dialogs.[/FONT][/COLOR]
[COLOR=#232323][FONT=Verdana]
[/FONT][/COLOR]
[COLOR=#232323][FONT=Verdana]On re-boot, the OS desktop will not start (surprise?).  The sequence of screen messages and dialogs are as follows:[/FONT][/COLOR]
[COLOR=#232323][FONT=Verdana]
[/FONT][/COLOR]
[COLOR=#232323][FONT=Verdana]1) I get a notification of three errors a) no module specified b) no suitable mode found and c) unknown command "terminal".  Then...[/FONT][/COLOR]
[COLOR=#232323][FONT=Verdana]2) The low-fi splash screen flashes and then a higher-res dialog "The system is running in low-graphics mode."  "Your screen, graphics card, and input device settings could not be detected correctly.  You will need to configure these yourself."  I press "Enter".[/FONT][/COLOR]
[COLOR=#232323][FONT=Verdana]3) I next get the "What would you like to do?" dialog to select: a) Run in low-graphics mode for just one session b) Reconfigure graphics c) Troubleshoot the error or d) Exit to console login.  This whole dialog is unresponsive (no mouse, no keyboard).  I cannot change the options, select "OK", or "Cancel".  So, I use the "Ctrl-Alt-F2" option.[/FONT][/COLOR]
[COLOR=#232323][FONT=Verdana]
[/FONT][/COLOR]
[COLOR=#232323][FONT=Verdana]At this point, I have a "Ubuntu 12.04.2 LTS" terminal login.  Logging in, I see "E: Error: BrokenCount > 0run-parts: /etc/update-motd.d/90-updates-available exited with return code 255"  "Welcome to Ubuntu 12.04.2 LTS (GNU/Linux 3.2.0-39-generic x86_64).[/FONT][/COLOR]
[COLOR=#232323][FONT=Verdana]
[/FONT][/COLOR]
[COLOR=#232323][FONT=Verdana]I log into the terminal and then run "sudo apt-get update && sudo apt-get upgrade".  It stops (or the final output message occurs) when packages with unmet dependencies are found and suggests that I run 'apt-get -f install' to correct them.  In more detail, the unmet dependencies are:[/FONT][/COLOR]
[COLOR=#232323][FONT=Verdana]libxine1: Depends: libxine1-plugins (=1.1.20-2build1) bit it is not installed or[/FONT][/COLOR]
[COLOR=#232323][FONT=Verdana]libxine1-misc-plugins (=1.1.20-2 build1) but 1.1.17-1ubuntu3 is installed[/FONT][/COLOR]
[COLOR=#232323][FONT=Verdana]libxine1-console: Depends: libxine1-bin(=1.1.20-2 build1) but 1.1.17-1ubuntu3 is installed[/FONT][/COLOR]
[COLOR=#232323][FONT=Verdana]libxine1-ffmpeg: Depends: libxine1-bin(=1.1.20-2 build1) but 1.1.17-1ubuntu3 is installed[/FONT][/COLOR]
[COLOR=#232323][FONT=Verdana]libxine1-x: Depends: libsine1-bin(=1.1.20-2 build1) but 1.1.17-1ubuntu3 is installed[/FONT][/COLOR]
[COLOR=#232323][FONT=Verdana]E: Unmet dependencies. Try using -f[/FONT][/COLOR]
[COLOR=#232323][FONT=Verdana]
[/FONT][/COLOR]
[COLOR=#232323][FONT=Verdana]I have been under the impression that using "-f" to force installations is a somewhat dangerous practice for the uninitiated.  [/FONT][/COLOR]
[COLOR=#232323][FONT=Verdana]
[/FONT][/COLOR]
[COLOR=#232323][FONT=Verdana]My OS is on a 12 GB partition that appears to be approaching full.  My important data [/opt/; user/local/; and /home/] are on separate disk partitions of 12, 12, and 950 GB, respectively.  All the data on these partitions appears intact.  I do not yet have a backup, but assume that the command line and other forum discussions would satisfy that need if I needed to do a clean install.[/FONT][/COLOR]
[COLOR=#232323][FONT=Verdana]
[/FONT][/COLOR]
[COLOR=#232323][FONT=Verdana]My thanks for your responses.[/FONT][/COLOR]
[COLOR=#232323][FONT=Verdana]
[/FONT][/COLOR]
[COLOR=#232323][FONT=Verdana]Aric[/FONT][/COLOR]

---

### Post by ibjsb4 on 2013-04-04
In terminal enter:

```
man apt-get
```

And you will find this:

-f, --fix-broken
           Fix; attempt to correct a system with broken dependencies in place.
           This option, when used with install/remove, can omit any packages
           to permit APT to deduce a likely solution. If packages are
           specified, these have to completely correct the problem. The option
           is sometimes necessary when running APT for the first time; APT
           itself does not allow broken package dependencies to exist on a
           system. It is possible that a system's dependency structure can be
           so corrupt as to require manual intervention (which usually means
           using dselect(1) or dpkg --remove to eliminate some of the
           offending packages). Use of this option together with -m may
           produce an error in some situations. Configuration Item:
           APT::Get::Fix-Broken.

---

### Post by ManamiVixen on 2013-04-04
Usually, it isn't a good idea to upgrade straight from 10.04 - 12.04. You are supposed to to do it in increments. Going through each version till you hit the one you want. Thing is that is time consuming and tends to break things. If you are using a very old version of Ubuntu and need a newer one, it's best to do a fresh install.

---

### Post by ibjsb4 on 2013-04-04
> **ManamiVixen said:**
> Usually, it isn't a good idea to upgrade straight from 10.04 - 12.04. You are supposed to to do it in increments. Going through each version till you hit the one you want. Thing is that is time consuming and tends to break things. If you are using a very old version of Ubuntu and need a newer one, it's best to do a fresh install.

Where are you getting this information?  Links please :)

You can only do this kind of upgrade with LTS.  Its built into the system.

---

### Post by agnewton on 2013-04-04
Thank you both for your quick replies.

I think my description of the problem was less than clear. I am upgrading from 10.04 LTS to 12.04 LTS.  Sorry for the ambiguous description.

The man apt-get description was most useful- and the obvious solution, please forgive my newbieness.  The "attempt" part of the description was re-assuring.  I did simply run "sudo apt-get -f install" and have a desktop login screen.  There appear to be a long list of upgrades to pursue, but I should be able to wade into it all from here.  Thank you for your help ibjsb4.

Post closed.

Aric

---

### Post by claracc on 2013-04-04
> **ManamiVixen said:**
> Usually, it isn't a good idea to upgrade straight from 10.04 - 12.04. You are supposed to to do it in increments. Going through each version till you hit the one you want. Thing is that is time consuming and tends to break things. If you are using a very old version of Ubuntu and need a newer one, it's best to do a fresh install.

I do have upgraded some months ago my 10.04 ubuntu dual boot with win vista to 12.04 and everything was ok. Upgrading from LTS to LTS can be done and it is not harmful, it is one of the ways to do the upgrading straightforward without going through releases step by step.

---

### Post by fantab on 2013-04-04
> **agnewton said:**
>  I am upgrading from 10.04 LTS to 12.04 LTS.  Sorry for the ambiguous description.

If you want my advice, the do a CLEAN INSTALL of Ubuntu 12.04LTS. I find upgrades to be time comsuming (than a clean install) and can be messy, especially from 10.04 to 12.04 because Ubuntu has undergone some massive upgrades since 10.04. 

Back up all your DATA and do a clean Install.

For more on how to back up and restore after a clean install, [See Here]("http://ubuntuforums.org/showthread.php?t=1748541&p=10765330#post10765330").

My two cents...

---

### Post by ibjsb4 on 2013-04-04
To close a post

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---


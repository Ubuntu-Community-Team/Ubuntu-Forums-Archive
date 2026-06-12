---
title: "Installation on an early model PowerMac G3, continued"
date: 2005-09-11
forum: Installation &amp; Upgrades
---

### Post by John Azelvandre on 2005-09-11
Hi everyone.  I had a glitch that required me to install with the option "video=ofonly."  The first part of the install seemed to work, and then, in the second part of the install it went into unpacking and installing all of the packages.  I left it running (I'm installing ubuntu on an old G3 PowerMac at work) and have just come back to it today.

The install hung up at "setting up xlibs (6.8.2-10)."  

I rebooted.

Upon boot-up and log-in, it put me into aptitude, saying that not all packages had been installed.

**First question:**  It was not readily apparent which packages did not install.  It has been awhile since I've used aptitude (been using synaptic on my Sarge machine at home
for awhile), so it was kind of hard to navigate.  **How can I determine which [crucial] packages were not installed?** 

I closed out of aptitude without doing anything.

**Second question and a BIG PROBLEM:**  When I did the initial install, I was never asked to set up a root password (!!).  I thought that was mighty peculiar.  I have a user account and password.  Now, I cannot become root to make necessary adjustments to the system.  (For example, I cannot use aptitude to do anything meaningful, since I must be root to run 'apt-get update' etc.)

So, before I tackle the absence of a GUI, I need to find out what the root password is (or how to set the root password).

Can anyone help?

---

### Post by John Azelvandre on 2005-09-11
I can't run base-config without root privileges either (of course).  So what happened?  Why didn't the installation program ask me to set the root password?  Did I somehow miss it?  Is there a default root password that I'm supposed to know and then change later?  This is really odd.

I'm hoping someone can clear up my confusion.,..

---

### Post by John Azelvandre on 2005-09-11
Ok,

I figured out how to set up the root password.  I was able to finish the install.  Now, for the fun stuff:

I rebooted, and at the conclusion of booting up, the system goes into GUI mode, but the monitor is not cooperating and so I get a blank screen, and, if I turn the monitor on and off the message "H. V frequency over range."  So I guess I need to tweak the settings (where exactly, I'm not sure) manually.

Problem is, how do I switch back into commandline mode so I can see what I'm doing?

The monitor I'm using is an old one: It is a "View Sonic" E70fb.

Thanks in advance.

---

### Post by Hairy_Palms on 2005-09-11
to go back to the cline i believe u press ctrl+alt+f1

---


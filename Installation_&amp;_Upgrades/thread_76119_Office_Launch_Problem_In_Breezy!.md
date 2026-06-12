---
title: "Office Launch Problem In Breezy!"
date: 2005-10-14
forum: Installation &amp; Upgrades
---

### Post by chhimed.w on 2005-10-14
I downloaded Breezy using synaptic which was successful and then I installed it, also using synaptic.

Now when I boot up, I get a no entry sign, with an error message which says:

[center]Configuration is not correct

The configuration file contains an invalid command line for the login dialog, so running the default command. Please fix your configuration.[/center]

So what does all that mean and how do I fix it? 

Also, I'm unable to launch any of the office programs. I get a window that says:

[center]OFFICE Error

Cannot launch entry


Details: Failed to execute child process "/usr/bin/oowriter" (no such file or directory).[/center] 

](*,) 


Previously (before the install), I was using Hoary with no problems at all!

Can anyone help please?

---

### Post by chhimed.w on 2005-10-15
Everything sorted now. :-D

---

### Post by taygan on 2005-10-15
What did you do to fix it?  (In case someone else has the same problem..)

---

### Post by chhimed.w on 2005-10-17
[QUOTE=taygan]What did you do to fix it?  (In case someone else has the same problem..)[/QUOTE]


Let me rephrase your question. It is not so much what did I do to fix it, but what did I do that caused the problem in the first place?

Being somewhat new to computers in general and even newer to Linux and Ubuntu, I was not entirely clear on how to do an upgrade. Looking at the information available on these threads, I figured I could give it a try and upgrade from Hoary to Breezy without too much difficulty. 

First I tried downloading Breezy and burning it to a CD to install it, but there is a problem with my CD burner, so the burn wasn't a complete and flawless one. So, when I tried to do the install, I figured that doing it with synaptic would probably be the easiest was to go about it, but because the CD didn't have all the data burned onto it correctly, it wouldn't do the install and upgrade. 

I then decided to try doing the upgrade using synaptic to download the data and install it. Looking at these threads, I found this page. 

 [https://wiki.ubuntu.com/BreezyUpgradeNotes](https://wiki.ubuntu.com/BreezyUpgradeNotes)

The relevant section is as follows: 

[indent]Through Synaptic Package Manager
1.Open up Synaptic Package Manager 
2.Change your repositories to look for Breezy[/indent] 
[center]From 
         URI: [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
         Distribution: hoary
         Sections: main restricted
To 
         URI: [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
         Distribution: breezy
3.         Sections: main restricted[/center]
[indent]
4.Click on "Reload" 
5.Click on "Mark All Upgrades" 
6.Click on "Apply"[/indent] 

Where I went wrong, was that it did not occur to me, that it meant all the repository distributions had to be changed from Hoary to Breezy. So I only changed one of them, leaving the rest of them alone. This meant that part of the package was trying to upgrade from Hoary to Breezy and the rest of it was trying to get hoary updates. 

The result of this was that Office would not launch.

The solution, was to change all the distributions, so that they upgraded to Breezy.

A further complication was that the sources had previously been set up with a Debian format. Changing them all to the Ubuntu layout meant that even more packages were available for upgrade.

What seemed like a major headache, was actually quite a simple problem with a simple solution, it just took a little while to correct, by making all the appropriate changes.

As far as I can tell, everything is working fine now.

---

### Post by cdravi on 2005-11-29
Hi, 
    I have the same problem of "Configuration not correct" warning, but everything is working perfectly.  However, **chhimed.w** seems to be lucky to solve his.  I used apt-get to upgrade from hoary to breezy, using the same link [https://wiki.ubuntu.com/BreezyUpgradeNotes](https://wiki.ubuntu.com/BreezyUpgradeNotes) 
and changed the sources.lst EXACTLY as shown there. Everything went fine, but each time I log in, the X-login shows "Configuration not correct"  warning.  

   I tried dpkg-reconfigure gdm, (even -a) a couple of times, but no success met. 

   I checked my Synaptec settings also, and obviously (apparantly) all are set correctly to breezy.
Any idea how to solve?

---


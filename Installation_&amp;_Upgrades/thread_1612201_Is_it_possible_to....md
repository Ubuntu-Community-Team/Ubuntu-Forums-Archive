---
title: "Is it possible to..."
date: 2010-11-02
forum: Installation &amp; Upgrades
---

### Post by nolag on 2010-11-02
I want to have a few linux distros installed on my comp.  I know that I won't use a lot of diskspace with any of them.  I also know that all the distros I want to use all use the same kernel version.  I am wondering if it is possible to install 2+ versions of linux on the same partition with the same settings (ie /home) for all of them?  Also I am wondering if it is possible for them to share common apps?

The linuxes I have in mind are (all 64-bit):

Ubuntu
Linux Mint
Cent OS

maybe more later.

Ideally Grub would let me pick at boot (or if possible I can change at log in although I doubt that one?)

---

### Post by dabl on 2010-11-02
The good news:  YES, it is possible.

The bad news:  Your shared /home partition will soon be a hopeless wreck of commingled and conflicting settings files and folders -- all the hidden "dot" files and folders will never be 100% consistent across multiple OS's.

A better approach, to have 3 different Linux OS's, would be:

(a) make a common (shared) /boot partition -- 512MB is way plenty of space

(b) each OS gets its own modest partition --  8GB - 10GB is plenty for each, and including the /home directory

(c) your user data should be on separate partition(s), mounted in the /etc/fstab file for each OS.

Then when you set up each OS, use symlinks to your user data directories, i.e. symlink "DOCS" in to the /home folder for each Linux OS.

---

### Post by snowpine on 2010-11-02
The good news is that Ubuntu and Mint are basically the same distro, so you only really need to install one of them. :)

CentOS on the other hand is very different and deserves its own separate partition. (Not sure who told you "CentOS uses the same kernel as Ubuntu"!)

I like the suggestion above to use a separate partition for your data. I do this myself. ;)

---

### Post by nolag on 2010-11-03
> **dabl said:**
> The good news: YES, it is possible.
 
The bad news: Your shared /home partition will soon be a hopeless wreck of commingled and conflicting settings files and folders -- all the hidden "dot" files and folders will never be 100% consistent across multiple OS's.
 
A better approach, to have 3 different Linux OS's, would be:
 
(a) make a common (shared) /boot partition -- 512MB is way plenty of space
 
(b) each OS gets its own modest partition -- 8GB - 10GB is plenty for each, and including the /home directory
 
(c) your user data should be on separate partition(s), mounted in the /etc/fstab file for each OS.
 
Then when you set up each OS, use symlinks to your user data directories, i.e. symlink "DOCS" in to the /home folder for each Linux OS.
 
Interesting, but then I would still need to have applications seperate right?  I guess my main goal was to only need to install the apps once.  I don't know why I included CentOS, I know its not debian based and that it is very different but I was under the impression that they all still used the most recent linux kernel?
 
I guess the purpose of what I wanted to do was to try many linuxes using as little disk space as possible and as little time setting them up (since I was hoping that at least some would share apps).  I guess for now I will stick to VMs to test other distros.
 
Thanks for all the advice :).

---

### Post by dabl on 2010-11-03
> **nolag said:**
> 

what I wanted to do was to try many linuxes using as little disk space as possible



Disk space?  Disk space costs what -- 3 cents per Gigabyte?  And a typical Linux distribution like Ubuntu needs 6 or 8GB for the OS?  What are you thinking of saving -- 18 cents?

>  but then I would still need to have applications seperate right?  I guess my main goal was to only need to install the apps once. 



Here's your problem - each Linux _distribution_ is a package of OS + Applications.  The development team for each distribution has worked out the dependencies and needed libraries for the applications in their distribution, so it all hangs together and works as they intended.

So, if you start trying to dump different distributions into the same filesystem, you'll have a train wreck in no time.  For example, just take a look at the version information in any three different distributions that you're thinking of, for key libraries like libc6, libgcc1, libgtk*, libncurses*, etc. etc.  You can't "mix 'n match" different versions of these files -- they have to support the rest of the OS and applications that they belong to.

---

### Post by nolag on 2010-11-04
I guess I am not as worried about saving disk space, more that I did not want a lot of partitions sitting there.  I don't know why it would be a big deal, but I guess its the way to go.  I was thinking the application settings (and installed apps) would be the best thing to share, but it sounds like that could be a bad thing in the end so I guess I will stick to VMs for now, at least until I find other distros I like.

---


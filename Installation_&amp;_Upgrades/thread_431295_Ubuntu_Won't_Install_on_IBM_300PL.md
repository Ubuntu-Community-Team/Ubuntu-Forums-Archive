---
title: "Ubuntu Won't Install on IBM 300PL"
date: 2007-05-02
forum: Installation &amp; Upgrades
---

### Post by km4hr on 2007-05-02
Xubuntu installation won't write anything to the hard drive. Installation gets to disk partitioning step. Disk size is correctly displayed. I select default partitioning. The computer hangs after starting to write files to disk. I'm using an installation file I downloaded this week. 7.0.4 I think is the version. 
The computer is IBM 300PL, 500 Mhz PIII, 192Meg RAM. I've had Freespire running on it.
Any ideas? Thanks!

---

### Post by jfinkels on 2007-05-02
> **km4hr said:**
> Xubuntu installation won't write anything to the hard drive. Installation gets to disk partitioning step. Disk size is correctly displayed. I select default partitioning. The computer hangs after starting to write files to disk. I'm using an installation file I downloaded this week. 7.0.4 I think is the version. 
The computer is IBM 300PL, 500 Mhz PIII, 192Meg RAM. I've had Freespire running on it.
Any ideas? Thanks!

You may not have enough RAM for Xubuntu...I think the minimum is 256MB.

---

### Post by km4hr on 2007-05-02
> **jfinkels said:**
> You may not have enough RAM for Xubuntu...I think the minimum is 256MB.

From the Ubuntu web site:
=====================================================================================
Memory and Disk Space Requirements

You must have at least 32MB of memory and 190MB of hard disk space for a minimal installation of the base system. For the full default installation, you must have at least 128MB of memory and 2GB of hard disk space. 
=====================================================================================

I have 192MB and 13GB.

---

### Post by TransitMan on 2007-05-03
Is Freespire still installed on this computer?
Were the partitons setup differently than what you want to do now?
Have you tried setting the partitions manually instead of letting the OS install do it? If not, try this approach, as the partitoner may be choking on the automatic wipe and install.
I have always found that by setting the partitions manually that installs go fairly easy.

As for your system specs, you seem to be good to go.

---

### Post by km4hr on 2007-05-04
I finally got Xubuntu to load on the 300PL. I'm not sure what finally enabled the copying of files to the hard drive. It must have been a setting I found in the BIOS that configures the hard drive to run in "compatibility" mode.  But I'm seeing some really strange stuff during and after installation. First, it took what seemed like an excessively long time for Xubuntu to copy it's files to the hard drive, like a hour or more. When copying first started a message appeared saying I didn't have enough privileges to mount something (I don't recall what). But the install process continued. I later noticed a "lost+found" directory had a red "X" attached to it's icon. What's up with that?

The installation process puts up a screen that inquires about transferring old files to the new system, or something like that. What's that about?

After installation I couldn't bring up an xterm window at all. I tried several times but each time Xubuntu would abruptly kill the X server and log me out of the system. 

Is 7.0.4 a final version? If so, I sure hope Ubuntu gets it right before Dell starts installing it on their new PC's. It will be a disaster if Ubuntu doesn't measure up. Maybe I'll try the regular Ubuntu instead Xubuntu. I tried Xubuntu first because of statements on the web site indicating Xubuntu might be easier on the older PC's resources. 

Perhaps I shouldn't mention this here but another thing I noticed as I was trying different OS's was that PCLinuxOS installed in like 15 minutes. Even though I don't use PCLOS normally (I use Centos because that's what we have at work) I might have to give it a try. I don't mean to create a fire storm here but PCLOS is really slick! As a workstation distro it makes everthing I've seen lately look like they are 5 years old.

---

### Post by recto on 2007-07-30
Hi,

I had thesame problem with my IBM 300PL (500Mhz), 192 ram etc. What I did was I upgraded the ibm firmware [http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=JBAR-3TYSNA](http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=JBAR-3TYSNA) after the upgrade, I formatted the HD, created the typical primary/ logical partitions. 

After that, booting from the live cd and installation didnt give any problem.

Im now enjoying Ubuntu 7.04 version in my ibm 300PL machine.

Hope it helps.

recto

---


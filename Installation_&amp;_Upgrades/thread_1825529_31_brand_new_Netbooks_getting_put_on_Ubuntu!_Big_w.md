---
title: "31 brand new Netbooks getting put on Ubuntu! Big week for me &amp; our company..."
date: 2011-08-15
forum: Installation &amp; Upgrades
---

### Post by ajmctaggart on 2011-08-15
Hey all,

We are a small organization will be providing after school tutoring through the Boys & Girls Clubs around town.  

My main concern is to get the system installed, updated, and then lock it into place for the school year.  I would only considering doing updates if absolutely necessary.

These machines will be used for a very simple purpose - to connect to a web-based curriculum - essentially, Google Chrome will be our main application installed.  I could (and may) strip everything other than LibreOffice, Chrome, and Firefox - but that has yet to be decided.

I purchased all netbooks (Acer Aspire One AOD255E - Intel Atom N455, 1 GB ram, 160GB HDs) at once, same model, so there should be no difference between each machine.  

I've never done a customized system and then re-imaged to 30 machines - so I wanted to get the community's blessing on this one first - I am no expert, but far from a newb.  

I assume the process will go something like :

1.  Install Ubuntu on 1st Netbook, customize accordingly.
2.  Once everything is how I want it, use USB-Creator to make an image of this system.
3.  Use USB drive to install onto 30 others...

I guess I'm a bit nervous about usernames, passwords, etc.  so if anyone has anything to add before I venture out, I'd greatly appreciate it.  In the next few days, I'll be mulling over previous posts as well to make sure I'm prepared.  Since this isn't the usual install for me, I'm taking a proactive approach with the forums.  Please don't bash me for not trying and then posting - this is one of those times where I think I get a "pass."  

Thanks!  I'll post my results and issues (if any) here as well...

*Edited to cut the fluff*

---

### Post by ajmctaggart on 2011-08-16
Kind of surprise I've had views but no responses.  Is this a dumb question - or does no one have any experience cloning systems with different users, etc.?

---

### Post by uRock on 2011-08-16
Once you get your first system set up the way you want it with all issues ironed out. You can the use remastersys to make an installable copy of the system, which can be used on all of the other systems.

I have not used remastersys before, so I can't advise on how to use it, but these tutorials look promising. [http://www.psychocats.net/ubuntu/remastersys](http://www.psychocats.net/ubuntu/remastersys) & [http://www.geekconnection.org/remastersys/ubuntu.html](http://www.geekconnection.org/remastersys/ubuntu.html)

---

### Post by ajmctaggart on 2011-08-17
Thanks for the reply URock!

I'll read up and try this on Friday - 25 have arrived :)

Cheers and Beers indeed!

---

### Post by wandalalakers on 2011-08-18
Remastersys is nice but if you use an Nvidia proprietary driver, you will have to reinstall it after cloning with Remastersys.  Also, if your image is bigger than 4gb it won't work.

---

### Post by wagb278 on 2011-08-19
Maybe - Maybe Not of some help.

I supported a similar activity - setup one Ubuntu, clone it, and install on other machines. We had only four total.

This is what we did (and it worked fine).

The new machines came with Windows XP.
We installed from the Ubuntu (10.04) live CD; wiping the whole HD; set Computer Node name to XXX-1 (as the first one) this we altered on each machine after installing the cloned system so each machine got a number (XXX-n) pick a meaningful acronym for your suite of machines. We had to set and configure Network Proxy and verified we could connect to the Network. 

Then we used Update Manager to update Ubuntu for changes since the Live CD was created - there were about 200. 

Use Software Manager to install applications that we wanted (we wanted SSH, Adobe Reader, SQLite3, MySQL, Wireshark, Eclipse (java programming); and configured Eclipse adding features desired. You probably don't want these but you basically want to get the first machine exactly how yo want the others with whatever applications you desire. 

Create users/group - we established a user group with our project name and established user accounts for each user with a basic password configured.  We did this because we knew the few project members up front and wanted each to be able to logon to any machine. 

Created a new directory at /project-name giving our user group write access - so project related files on any machine could be saved there. You may not need this. We intended to use a script the backup project files between each machine into a sub-directory using a cron job.

Downloaded "Clonezilla ISO" and wrote that to a CD. Read instructions carefully for its use. We used a 8-Gig memory stick as the repository for the clone image.  It took about 5 minutes per machine to load the clone image.

After installing the clone - login and change the machine name in /etc/hostname and /etc/hosts (if you want /etc/hosts setup to know of the others on your network).  Each machine got a unique sequential number appended to a short project name acronym).

Afterwards we discovered the Ethernet port number had gotten changed so we had to go in and alter eth0 and eth1.  Also we later discovered one of the tools we where using required the NVidia graphics driver to be installed, so we had to do that on each machine. (We didn't know about that dependency before we built the image).  Another configuration change was to alter the display settings to show black screen when the Laptop cover was closed. (we used large monitors connected to the Laptops) We saved the image file to a couple of machines just so we had a copy.  We needed to re-use the memory stick. 

Clonezilla was recommended to us, none of us had done this before.  There are other clone tools.  I found this one confusing at first, but it worked well. 

Good Luck; hope something in this reply helps;
Jim

---

### Post by ajmctaggart on 2011-08-19
wagb278 - this totally helps! Thank you!!!

Starting this over the weekend, will report my process and success (or failures...).

Thanks to everyone that posted!

---

### Post by ajmctaggart on 2011-08-24
Everyone that made suggestions to me - 

I'm not there yet, still trying to nail down how to "roll" the first netbook...deciding on something like a Chromebook on the Cheap...Im calling it ChromeBuntu...lol


See current thread here:
[http://ubuntuforums.org/showthread.php?t=1831488]("http://ubuntuforums.org/showthread.php?t=1831488")

---

### Post by ajmctaggart on 2011-09-07
Just to put an end to this mission of mine:

I ended up using Ubuntu 10.04 LTS and Clonezilla - absolutely amazing tool.

Each clone took 10-12 minutes and not one of them gave me issues.

I did need to change the computer name in a few places:
/etc/hostname
/etc/network/hosts

I also needed to remove a file for Google Chrome in ~/.config/google-chrome/ called Singleton Lock, since it apparently uses the machine name in some way.  It recreates it on next open, however.

Thanks to everyone that helped make this possible- all your suggestions got me here!

Oh and just for humor - it took approximately 2-4 gigs of space for the Ubuntu Cloned OS (not sure since I used an 8 gig USB drive).  Guess what it takes to clone the Windows 7 Starter OS?  23 Gigs!  23 gigs to get it back to manufacturer OEM - crazy!

---

### Post by uRock on 2011-09-07
I am happy it worked out for you. Sounded like a fun project.

---


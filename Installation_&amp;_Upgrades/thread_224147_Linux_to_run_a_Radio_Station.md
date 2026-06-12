---
title: "Linux to run a Radio Station?"
date: 2006-07-27
forum: Installation &amp; Upgrades
---

### Post by shane2peru on 2006-07-27
Let me explain what I would like.  I would like to use Linux to run all the programming for a radio station.  I'm a missionary working in Peru, and the last computer that was used at this radio station became infected with over 30+ viruses, and I would like to setup a Linux box to run the station instead - for the obvious virus problem, and carelessness that was taken in running the computer.  And I believe I can do it on Linux with far less cost.  This is not my station, and I really don't know all that is involved in this, but this is what I believe we would need:

1.  MP3 capabilities (leagally - according to US standards)

2.  or ability to convert MP3 to OGG and run everything in OGG - although this solution creates much more work.

3.  Ability to edit MP3/OGG - (BTW - Audacity is ok, but I don't care for the quality of its output.  I have never used it with OGG, but I have used it on Windows, and it's MP3 ability is very poor.)

4.  Run a set program (maybe a playlist) for a couple of hours.

5.  Be installed without an internet connection - they don't have internet. (and still had 30+ viruses??? I know, very careless.)

6.  I really like Ubuntu, and that is what I use, however I'm not limiting myself to Ubuntu, if there is another distro setup better for Audio, I'm more than willing to learn, and teach.

Thanks in advance for help!

Shane

---

### Post by catlett on 2006-07-27
[http://www.campware.org/en/camp/livesupport_news/](http://www.campware.org/en/camp/livesupport_news/)
I do not have any personal knowledge. I got that link from this article [http://www.linuxjournal.com/article/7168](http://www.linuxjournal.com/article/7168)

---

### Post by Kyran on 2006-07-28
A few days ago I went to a radio station for such and such a reason and I noticed that their computers in studio two were using the GNOME desktop, (don't know which distro) one of the guys there clicked on an icon at the top of the screen, typed in a password and Windows with a very low colour depth came up.

You shouldn't have any problems playing audio in Ubuntu, unless you have an older non-PCI soundcard.

---

### Post by hw-tph on 2006-07-28
Check out the [Ubuntu Studio](http://ubuntustudio.com/wiki/index.php/Welcome,_Musicians!) project. While it is aimed towards musicians most of the features you are looking for you have in common with computer musicians.

It is not too difficult to set up Ubuntu as a professional digital audio workstation, and if you enable the Universe repository you will have access to some very high quality applications for multi-tracking ([Ardour](http://ardour.org)), mastering ([JAMin](http://jamin.sourceforge.net/en/about.html)) and more audio file editors (read [this LinuxJournal article](http://www.linuxjournal.com/article/7274) for a primer) than you can shake a stick at.

Ubuntu comes with the kernel configured as a low latency desktop already so it is usually not necessary to build a low latency kernel.


Håkan

---

### Post by shane2peru on 2006-07-28
Thanks for the info!!!  I will certainly look at those links and read up on this info.  I appreciate the help.

Shane

---

### Post by shane2peru on 2006-07-28
> **catlett said:**
> [http://www.campware.org/en/camp/livesupport_news/](http://www.campware.org/en/camp/livesupport_news/)
I do not have any personal knowledge. I got that link from this article [http://www.linuxjournal.com/article/7168](http://www.linuxjournal.com/article/7168)

Ok, this is  a great site, and it really looks just like what I am looking for.... However, couldn't install it on Ubuntu Dapper.  It appears that it worked great on Breezy, but here is the problem I get when trying to install the libraries:```
sudo apt-get install livesupport-libs
Password:
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  livesupport-libs: Depends: xlibs (>= 4.1.0) but it is not installable
                    Depends: libboost-date-time1.32.0 (>= 1.31) but it is not installable or
                             libboost-date-time1.33.0 (>= 1.31) but it is not installable

```
I emailed their support, but haven't heard anything yet.  If anyone else knows how to do this that would be great!

Shane

---

### Post by catlett on 2006-07-28
Try using aptitude instead of apt-get. I mention this because apt-get will just give you an error, like what just happened.
Aptitude will try to resolve the issue. What might happen in this case is aptitude may use a lower version of the library you need, instead of saying it can't install the new version.
Anyways, it couldn't hurt.
```
sudo aptitude install livesupport-libs
```

---

### Post by shane2peru on 2006-07-28
Well, it was a thought.  Thanks for the idea, didn't work though: ```
 sudo aptitude install livesupport-libs
Password:
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done
The following packages are BROKEN:
  livesupport-libs
The following packages are unused and will be REMOVED:
  amarok amarok-engines amarok-xine
0 packages upgraded, 1 newly installed, 3 to remove and 0 not upgraded.
Need to get 17.3MB of archives. After unpacking 29.7MB will be used.
The following packages have unmet dependencies:
  livesupport-libs: Depends: xlibs (>= 4.1.0) which is a virtual package.
                    Depends: libboost-date-time1.32.0 (>= 1.31) which is a virtual package. or
                             libboost-date-time1.33.0 (>= 1.31) which is a virtual package.
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
livesupport-libs [Not Installed]

Score is -1


```

Any other ideas?

Shane

---

### Post by catlett on 2006-07-28
The only other thing I can think of is...
Find a distro that supports the package.
Or get rid of Dapper and install Breezy. It is stil a great OS and you can still get the download [http://releases.ubuntu.com/5.10/](http://releases.ubuntu.com/5.10/)

Hopefully the next release, due in 4 months or so, Edgy Eft will have support for it and you can upgrade to the latest version of Ubuntu.

---

### Post by christooss on 2006-07-28
try downloadinfg official deb packages and than install them with

sudo dpkg -i  package,deb

---


---
title: "Installing VLC"
date: 2005-04-22
forum: Installation &amp; Upgrades
---

### Post by Goober on 2005-04-22
Hello,

I just installed Ubuntu recently, after my WinXP crashed, and I was wondering if I can find a Video Program to play .avi movie files, but, more importantly, DVDs.  I have downloaded and got working RealPlayer version 10 for Linux, and there is this Totem Video Player, but that doesn't seem to useful.  Neither can play my .avi movie files, nor my DVDs.  

On Windows, I used VLC, which can play like anything.  [Here](http://www.videolan.org/vlc/) is the Link to the site.  Now, I want to install VLC on my Ubuntu Linux to play .avi files and DVDs.  Which version of Linux should I chose to download from that site?  It doesn't have Ubuntu as one of the options.

If not, can anyone reccomend or point my out a Video Playing program that play .avi and DVDs?

And, I assure you, my .avi movie files are NOT illegally downloaded.  They are legitimate clips of family events and that kind of stuff.  I am NOT a Pirate.  Well, except in my imagination  ;-) 

Thanks in advance for your help!

---

### Post by SGC on 2005-04-22
To install VLC:

Add the following lines to your /etc/apt/sources.list:

deb [http://download.videolan.org/pub/videolan/debian](http://download.videolan.org/pub/videolan/debian) sid main
deb-src [http://download.videolan.org/pub/videolan/debian](http://download.videolan.org/pub/videolan/debian) sid main

from the terminal do the following:

   # sudo apt-get update
   # sudo apt-get install wxvlc libdvdcss2

---

### Post by Goober on 2005-04-22
Hmm, umm, SGC, I don't quite understand what you intend for me to do there.  From what I can tell, both of thiose links lead to the same place.  Do you want me to go to the link, and download the code, and then compile it?

I don't understand your instructions, could you please explain in more detail?

Thanks :)

---

### Post by SGC on 2005-04-22
Don't click on the links, those links are used by apt-get program to download and install VLC. I hope the following detailed instructions will help you. 

1 - type the following command in the terminal
(you can find the terminal in applications > system tools > terminal)

**sudo gedit /etc/apt/sources.list**


2 - add the following lines to the end of the opened file:

[B]deb [http://download.videolan.org/pub/videolan/debian](http://download.videolan.org/pub/videolan/debian) sid main
deb-src [http://download.videolan.org/pub/videolan/debian](http://download.videolan.org/pub/videolan/debian) sid main[/B]


3 - save the file and open the terminal again, the type the following:

**sudo apt-get update**

4 - after the update finish type the following inthe terminal to download the VLC and the  ability to playback DVDs:

**sudo apt-get install wxvlc libdvdcss2**


**PS:** If you found a download site that does not have Ubuntu package, download the debian package. it will work since ubuntu is based on debian.

---

### Post by Goober on 2005-04-22
Ok, I followed your instructions (Very helpful, thanks!), and, well, I am not sure if the right thing happened.

I got this after I typed in the last line 

```
Reading Package Lists... Done
Building Dependency Tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  wxvlc: Depends: vlc (= 0.7.0-1) but it is not going to be installed
         Depends: libwxgtk2.4 (>= 2.4.2.4) but it is not installable
E: Broken packages

```

Then, well, nothing seemed to happen.  No VLC opened up, and I can't find a VLC saved anywhere.  Did I do something wrong?

I did find this site:

[http://www.videolan.org/vlc/download-debian.html](http://www.videolan.org/vlc/download-debian.html)

That is for Debian.  Also, they have it for almost every other Linux version (except Ubuntu) here:

[http://www.videolan.org/vlc/](http://www.videolan.org/vlc/)

I am going to try the upper Link now, maybe that will work.

Thanks for your continued help, though, much appreciated!

---

### Post by SGC on 2005-04-22
I think you may need to add extra repositories to your apt-get source file:
[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

after that, do the following: 
sudo apt-get update
sudo apt-get install vlc wxvlc libdvdcss2

alternatively you can add codecs and the ability to play DVDs to totem:

**How to install Multimedia Codecs?**
[http://ubuntuguide.org/#codecs](http://ubuntuguide.org/#codecs)

**How to install DVD playback capability?**
[http://ubuntuguide.org/#dvdplayback](http://ubuntuguide.org/#dvdplayback)

---

### Post by Goober on 2005-04-22
Hmm, I think it would be much simpler to just install the Codecs and such for Totem.

My Linux abilities are just not good enough for VLC at this stage.

Now, the links you pointed me to for the Totem Codecs did not work.  I believe that is because you gave me the Links for Ubuntu 5.4, the Hoary edition.  I am using Ubuntu 4.10, the Warty Edition.  Are there links for the Codecs and such in the 4.10 edition?

---

### Post by SGC on 2005-04-22
Sorry Goober, I don't relize this is the Warty Warthog forum

The links for Warty are:
**Codecs:**    [http://ubuntuguide.org/4.10/index.html#codecs](http://ubuntuguide.org/4.10/index.html#codecs)
**DVD playback:**     [http://ubuntuguide.org/4.10/index.html#dvdplayback](http://ubuntuguide.org/4.10/index.html#dvdplayback)

The above are exactly the same instructions for hoary what differnt is you need to add the extra repositories from here:
[http://ubuntuguide.org/4.10/index.html#extrarepositories](http://ubuntuguide.org/4.10/index.html#extrarepositories)

---

### Post by Goober on 2005-04-22
Ok, I got my .avi Movie Files to work.  Thanks a lot!!!  :)  :)  :) 

However, my DVD Playback seems to not be working.  I did the Repository thing.  Then I installed the DVD Playback.  Any suggestions?  Or any other proghrams available that play DVDs for Linux?

---

### Post by SGC on 2005-04-22
I'm glad that you can play avi files.

For DVD in totem, I think you need to restart the system so that totem can recognize what you add (just gusseing)

You may find the following usefull, it explains in details how to install and make DVDs playable in VLC for warty:
[http://ubuntuforums.org/showthread.php?t=12988](http://ubuntuforums.org/showthread.php?t=12988)

---


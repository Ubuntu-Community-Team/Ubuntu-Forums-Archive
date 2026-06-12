---
title: "Problems Installing Wine and with Repositories"
date: 2005-05-24
forum: Installation &amp; Upgrades
---

### Post by cinematography on 2005-05-24
[http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb)

The instructions look pretty easy, right? When I go to Synaptic and select Settings->Repositories, I get this window: 

[http://img.photobucket.com/albums/v611/tsharpfilm/Screenshot.jpg](http://img.photobucket.com/albums/v611/tsharpfilm/Screenshot.jpg)

Which looks nothing like the window in the tutorial. ](*,) These "repositories" have been holding me back from installing a lot of software. If you have any suggestions on how I could fix this problem, where I could go, or how I could install all the repositories I need, they would be greatly appreciated.

Edit: And I've tried installing it manually and I get nothing but errors: 
> W: Couldn't stat source package list [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Package s (/var/lib/apt/lists/wine.sourceforge.net_apt_binary_Packages) - stat (2 No suc h file or directory)
W: Couldn't stat source package list [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Package s (/var/lib/apt/lists/wine.sourceforge.net_apt_binary_Packages) - stat (2 No suc h file or directory)
W: You may want to run apt-get update to correct these problems
E: Could not open file /var/lib/apt/lists/wine.sourceforge.net_apt_source_Source s - open (2 No such file or directory)

---

### Post by mjbeam on 2005-05-24
Well, I'm far from an expert but this is how I installed wine:

1. Uncomment the following lines in your **/etc/apt/sources.list** file:

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

2. execute the following 2 commands:

sudo apt-get update
sudo apt-get install wine winesetuptk


-Mike

---

### Post by cinematography on 2005-05-24
[QUOTE=mjbeam]Well, I'm far from an expert but this is how I installed wine:

1. Uncomment the following lines in your **/etc/apt/sources.list** file:

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

2. execute the following 2 commands:

sudo apt-get update
sudo apt-get install wine winesetuptk


-Mike[/QUOTE]
Oh wow! That worked! I think it did. It's going now, which is more than what I had before. Hopefully no errors will come up when it finishes. Thank you for the suggestion. I'll post updates when it's done.

Edit: It worked. :) Now I'm off to setting it up. ](*,)

---

### Post by logan2004 on 2005-05-24
please do

---

### Post by cinematography on 2005-05-24
[QUOTE=logan2004]please do[/QUOTE]
I got it to work with those command lines. 

**To open that list file I entered the following in the root terminal: **
nano /etc/apt/sources.list

**I scrolled down to the bottom of the file and pasted these lines:**
deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/

**And pressed Ctrl-O to save the file. **

**From there I entered these lines in the root terminal:**
sudo apt-get update
sudo apt-get install wine winesetuptk

**I then right clicked the .exe file, left clicked 'open with other', and entered the following in the 'use a custom command space': **
wine


Woo hoo! :roll:

---


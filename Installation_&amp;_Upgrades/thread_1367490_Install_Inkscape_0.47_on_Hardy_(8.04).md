---
title: "Install Inkscape 0.47 on Hardy (8.04)"
date: 2009-12-29
forum: Installation &amp; Upgrades
---

### Post by aer0usa on 2009-12-29
Hi, I think I'm missing an important step. I'll try to keep this concise.

I want to upgrade Inkscape from version 0.46 to version 0.47 under Hardy Heron (8.04).

I started with these instructions: [http://wiki.inkscape.org/wiki/index.php/CompilingUbuntu#Hardy.2C_Intrepid_and_Jaunty]("http://wiki.inkscape.org/wiki/index.php/CompilingUbuntu#Hardy.2C_Intrepid_and_Jaunty")

...Which refers to this: [https://help.ubuntu.com/community/Repositories/Ubuntu]("https://help.ubuntu.com/community/Repositories/Ubuntu")

...and this: [https://launchpad.net/~inkscape-nightly/+archive/ppa]("https://launchpad.net/~inkscape-nightly/+archive/ppa")

So I added the [Inkscape Nightly Build]("https://launchpad.net/~inkscape-nightly/+archive/ppa") repository and the [Signing Key]("https://launchpad.net/+help/soyuz/ppa-sources-list.html").

Then I did:```
sudo apt-get update
```, and that seemed to go all right.

But when I do ```
sudo apt-get install inkscape
```, it tells me the following:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
inkscape is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

And in Inkscape's "About Inskscape" box, it claims still to be version 0.46.

What have I missed? Thanks!
Eric

---

### Post by aer0usa on 2010-01-04
Happy New Year! Giving this a Bump since I posted it when many were away over the holidays. 

I see that Inkscape 0.47 is included with 9.04 and 9.10, so I will likely just stick with Inkscape 0.46 until the next LTS release of Ubuntu, but if anyone can share with me why I can't get the update in 8.04, I'm quite curious.

Thanks!
Eric

---

### Post by Stuart Rackham on 2010-01-14
I've got exactly the same problem.

---

### Post by ZYV on 2010-02-13
Hi guys!

I've just rebuilt the latest Lucid package for Hardy at it seems to work well for me:

[https://launchpad.net/~zyv/+archive/ppa](https://launchpad.net/~zyv/+archive/ppa)

However, it seems that new Inkscape requires new Poppler. Popples is almost impossible to backport without major modifications, so I just bumped this dependency. I am not sure what implications this might have on PDF export. 

It would be nice if someone could test my packages and report back if they are broken in any way.

---

### Post by Francewhoa on 2010-03-12
Thanks ZYV :) Your package works. Find attached TERMINAL log and screenshot.

---

### Post by Francewhoa on 2010-03-12
**Installing the latest Inkscape on Ubuntu 8.04 LTS Desktop edition**

Step 1: Visit the PPA's overview page in Launchpad at [https://launchpad.net/~zyv/+archive/ppa]("https://launchpad.net/%7Ezyv/+archive/ppa") Look for the heading that reads Adding this PPA to your system and click the Technical details about this PPA link.

Step 2: Click on 'Technical details about this PPA' link.

Step 3: You'll see that the text-box directly below reads something like this:
```
deb http://ppa.launchpad.net/zyv/ppa/ubuntu hardy main
deb-src http://ppa.launchpad.net/zyv/ppa/ubuntu hardy main
```Copy those lines.

Step 4: Open a terminal and type:
```
sudo gedit /etc/apt/sources.list
```This will open a text editor containing the list of archives that your system is currently using. Scroll to the bottom of the file and paste the lines you copied in the step above.

Save the file and exit the text editor.

Step 5: Back on the PPA's overview page, look for the Signing key heading. You'll see something like:
```
1024R/F82FBD49
```Copy the portion after the slash but not including the help link; e.g. just F82FBD49.

Step 6: Now you need to add that key to your system so Ubuntu can verify the packages from the PPA. In your terminal, enter:
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys F82FBD49
```Replace F82FBD49 with whatever you copied in the step 5.

This will now pull down the PPA's key and add it to your system.

Step 7: Now, as a one-off, you should tell your system to pull down the latest list of software from each archive it knows about, including the PPA you just added:
```
sudo apt-get update
```Now you're ready to start installing software from the PPA. Type in the following command in TERMINAL.
```
sudo apt-get install inkscape
```The latest version of Inkscap can be found under APPLICATION > GRAPHICS > INKSCAPE.

Enjoy,

---

### Post by ZYV on 2010-03-13
Hey! 

You're welcome, thanks for the step-by-step guide, I was too lazy to write anything like this.

By the way, I have some other updated Hardy packages in this PPA, e.g. mc & vte / planner and rabbitvcs. Please be sure to disable the PPA after you install Inkscape to avoid replacing system packages with my backports if this is not what you want.

Z.

---


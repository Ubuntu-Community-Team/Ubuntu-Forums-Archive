---
title: "[SOLVED] Problem with Synaptic: msttcorefonts"
date: 2008-11-25
forum: Installation &amp; Upgrades
---

### Post by davidbilla on 2008-11-25
OK. You'll already have a pretty much good idea of what this problem is. Every time I try to install something, Synaptic tries various different servers for downloading msttcorefonts and fails. I've tried to get the exe's separately and install but it didn't work out. I've tried many things that pop up in a normal 'google' search (and even some roundabout google searches!) but nothing has worked so far. I still have the problem. Is there any place where I can go and edit so that synaptic does no more checks for 'msttcorefonts'? The package is not properly installed and I can't even uninstall it.

Waiting...

---

### Post by renzokuken on 2008-11-25
do you have the multiverse repos enabled?

---

### Post by davidbilla on 2008-11-25
> **renzokuken said:**
> do you have the multiverse repos enabled?

Yes,  of course.

---

### Post by aheckler on 2008-11-25
Have you tried downloading the package from [here]("http://packages.ubuntu.com/intrepid/msttcorefonts") and installing it manually?

You mentioned trying to install "exes", but those are Windows installers that wont work on Ubuntu IIRC.

---

### Post by davidbilla on 2008-11-25
This is what happens. It tries many such servers and fails ultimately.

```
Resolving surfnet.dl.sourceforge.net... 130.59.138.20
Connecting to surfnet.dl.sourceforge.net|130.59.138.20|:80... failed: Connection timed out.
Giving up.
--21:40:21--  http://mesh.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving mesh.dl.sourceforge.net... 213.203.218.122
Connecting to mesh.dl.sourceforge.net|213.203.218.122|:80... failed: Connection timed out.
Giving up.
```

---

### Post by aheckler on 2008-11-25
Try downloading it (in your browser) from any one of these: [http://packages.ubuntu.com/intrepid/all/msttcorefonts/download](http://packages.ubuntu.com/intrepid/all/msttcorefonts/download)

---

### Post by davidbilla on 2008-11-25
> **aheckler said:**
> Try downloading it (in your browser) from any one of these: [http://packages.ubuntu.com/intrepid/all/msttcorefonts/download](http://packages.ubuntu.com/intrepid/all/msttcorefonts/download)

Yeah. That's what I did! And...

```
Resolving surfnet.dl.sourceforge.net... 130.59.138.20
Connecting to surfnet.dl.sourceforge.net|130.59.138.20|:80... failed: Connection timed out.
Giving up.
--21:40:21--  http://mesh.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving mesh.dl.sourceforge.net... 213.203.218.122
Connecting to mesh.dl.sourceforge.net|213.203.218.122|:80... failed: Connection timed out.
Giving up.
```

...that's what I got!

---

### Post by renzokuken on 2008-11-26
i think the deb from the repos downloads the files directly from the sourceforge site automatically.

in that case its an issue with sourceforge and not the repos or ubuntu. maybe they are just down and trying again later when its been fixed will solve it

---

### Post by davidbilla on 2008-11-26
> in that case its an issue with sourceforge and not the repos or ubuntu.

Of course.

> maybe they are just down and trying again later when its been fixed will solve it 

It has been down for at least four months. I didn't even want these fonts at all. I just thought I would check them out and now I want to remove them but since they're not properly installed, I'm not able to remove them. 

Any ideas? Is there anywhere I can go and edit some file that would prevent synaptic from trying to setup msttcorefonts everytime I install anything?

---

### Post by forkandles on 2008-11-27
davidbilla,

Sorry, I have just realised that you wanted to get rid of msttcorefonts, not install them.
Ignore the rest of this, but it might be a useful alternative for somebody else.

Go to The Linux Box and download a tar.gz file for msttcorefonts:

[http://thelinuxbox.org/?page_id=3](http://thelinuxbox.org/?page_id=3)

Then go to your Downloads directory and extract the file (right click on file, click on extract, select home folder) to your home directory:

 /home/myusername/msttcorefonts

The existing truetype folder lives here:    /usr/share/fonts/truetype

Open terminal.
Move the msttcorefonts into the truetype folder by typing (better to copy and paste):

sudo mv /home/myusername/msttcorefonts /usr/share/fonts/truetype

Press Enter. 

Next open OOO Writer.
Tools > Options > click on (+) next to OOO Writer > Basic Fonts Western.
Then select your new default msttcorefont and size.
Job done!

---

### Post by forkandles on 2008-11-28
davidvilla,

Come to think of it, I had a similar problem. The download of the msttcorefonts from sourceforge stalled.
The solution is to go to terminal and type:

sudo dpkg --configure -a

This should install them correctly.

If you then wish to remove them use:

sudo apt-get remove msttcorefonts

---

### Post by davidbilla on 2008-11-28
Hi forkandles,

First I did what you'd told in your first post and then I ran 'dpkg'. It worked like a charm! Thanks.

---


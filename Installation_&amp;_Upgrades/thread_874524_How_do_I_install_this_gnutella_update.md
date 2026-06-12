---
title: "How do I install this gnutella update?"
date: 2008-07-30
forum: Installation &amp; Upgrades
---

### Post by Isakmo on 2008-07-30
I just installed Gnutella as my p2p client, but every time I run it it tells me that there is a newer version I need to update to. I followed the link I was given and downloaded the 'update.' Unfortunately I don't know what the next step is.

...and just so you understand where I am coming from:

I just completely switched over to Ubuntu because Windows no longer runs on my laptop... long story ... so basically I know nothing about Ubuntu. That being said, if you do post an answer please be as detailed as you can. I am not computer illiterate, just Ubuntu illiterate :-D

Thank you!

---

### Post by SkonesMickLoud on 2008-07-30
To update Gnutella (as well as everything else that needs updating), copy/paste this into a terminal:

```
sudo aptitude update && sudo aptitude safe-upgrade
```

Generally, you'll want to answer yes to what it asks you.

What's a terminal and where do you get it you ask?  Simple.  A terminal, aka a console, let's you enter text commands that work the same (or better) than commands issued in a GUI.  You can get a terminal by going to Applications >> Accessories >> Terminal.

If you're more comfortable in a GUI setting, you can open up Synaptic and search for gnutella, (synaptic has it as gtk-gnutella) right click and select "Mark for Upgrade".  If Synaptic doesn't show gnutella as installed, simply click on the box, then click apply.

---

### Post by Isakmo on 2008-07-30
Ok, I pasted that in the terminal and let it finish and then closed the terminal and tried again to start gtk-gnutella, but the same "Ancient Version Detected" message popped up.

Like I said before, when I run the program the message pops up and displays a link to [http://gtk-gnutella.sourceforge.net/](http://gtk-gnutella.sourceforge.net/) I followed the link and downloaded the bz2 file like it instructed me to. I then extracted it to a new folder, but I don't know what to do with it now :-/

---

### Post by SkonesMickLoud on 2008-07-30
Did you try upgrading through Synaptic?

---

### Post by Isakmo on 2008-07-30
Yes, it says that version '0.96.4 stable' is the newest version available for download, but the program continues to display the update message.

Is there a command that will allow me to run a file that is in a folder on my computer from a terminal? I am asking because there is an 'install.sh' file in the folder that was downloaded as the 'update.'

---

### Post by SkonesMickLoud on 2008-07-30
> **Isakmo said:**
> I am asking because there is an 'install.sh' file in the folder that was downloaded as the 'update.'

In a terminal, navigate to the folder that holds the install.sh file and enter:

```
sh install.sh
```

---

### Post by Isakmo on 2008-08-08
How do I navigate to the folder in a terminal?

---

### Post by SkonesMickLoud on 2008-08-08
Use "cd".  For instance:

```
cd /home/username/install
```

---

### Post by mikjp on 2008-08-09
You have to wait for Ubuntu 8.10. New versions of software come with new releases.

There are several other p2p software available. You could try them (transmission, azureus, amule, limewire,  etc)

mikko

---

### Post by Isakmo on 2008-08-10
It's not working.

It won't go past the /home directory.

All I am getting are "bash" notices.

Once I navigate to the /home directory how do actually navigate to my folders?

I tried just putting the files in the /home folder but it gives me an error message saying that I'm not the owner and that I do not have permission to do so :-/

---

### Post by mikjp on 2008-08-10
> **Isakmo said:**
> Once I navigate to the /home directory how do actually navigate to my folders?

cd foldername

This might be worth reading: [http://ubuntu-tutorials.com/2006/12/17/basics-for-the-command-line-for-newbies-ubuntu-510-6061-610/](http://ubuntu-tutorials.com/2006/12/17/basics-for-the-command-line-for-newbies-ubuntu-510-6061-610/)

---

### Post by orethrius on 2008-09-29
> **mikjp said:**
> You have to wait for Ubuntu 8.10. New versions of software come with new releases.

There are several other p2p software available. You could try them (transmission, azureus, amule, limewire,  etc)

mikko

It's probably more worthwhile to actually check the included README, as in [this post](http://ubuntuforums.org/showpost.php?p=5332268&postcount=3) in [this thread](http://ubuntuforums.org/showthread.php?t=851388&highlight=gtk-gnutella+0.96.5).  Seems to work on my end now that I've done all that. ;)

EDIT: If anyone cares enough to IM me, I'm considering making a quick BASH script to handle this, and I'd appreciate someone verifying the code integrity on 8.04 once that's done - perhaps a backport is in order for people still running Gutsy?

---


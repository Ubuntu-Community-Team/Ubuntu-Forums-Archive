---
title: "Ran out space on /root while upgrading"
date: 2012-03-14
forum: Installation &amp; Upgrades
---

### Post by DarthTeufel on 2012-03-14
Hi all,

First, I'm not the most savvy linux user, but I have been happily using Ubuntu for about 1.5 years now.  I was recently attempting to update my version of Ubuntu to either 10.04 or 10.10.  I can't really remember. Either way,  during the update, I received a message that I was running low on disk space on /root, and to run
```

sudo apt-get clean
```

which I did.  The install continued... then when it was under a minute remaining, it said I ran out of space.  Unfortunately, I cannot remember what I ended up doing, but I then reboot the system.

It boots fine, but when I try to login with the graphical login, I get an error message that says

> The Configuration defaults for GNOME power manager has not been installed correctly

I can login via the terminal.  Basically, I just wanted to copy the contents of my home directory to a NAS box... unfortunately, I can't figure out how to do this via terminal.

Once the data is copied, then I was just going to reformat and install the latest version of ubuntu.  Thanks for any help in advance

---

### Post by Bucky Ball on 2012-03-14
Boot from a LiveCD and copy your data to the external device. Then reformat and reinstall as you were going to do.

If you have a separate /home partition (not folder) you could do this by choosing 'Something Else' at the partitioning part of the install and unticking the existing /home partition so it doesn't get formatted. The data would then be untouched and the system would install to existing / and use the existing /home as its /home (and /swap also).

PS: 10.04 LTS has longer support than 10.10 (April 2013 as opposed to a few more months for 10.10) and will also be a one click upgrade to the next LTS, 12.04 LTS, but wait a couple of months after that is released always a good idea. ;)

---

### Post by DarthTeufel on 2012-03-14
> **Bucky Ball said:**
> Boot from a LiveCD and copy your data to the external device. Then reformat and reinstall as you were going to do.

If you have a separate /home partition (not folder) you could do this by choosing 'Something Else' at the partitioning part of the install and unticking the existing /home partition so it doesn't get formatted. The data would then be untouched and the system would install to existing / and use the existing /home as its /home (and /swap also).When I try to boot from a LiveCD, it freezes (pretty sure its a graphics driver issue as its freezing the same way it did when I first installed Ubuntu).

Rather than trouble shoot why I can't get the LiveCD to boot, I figured I'd see if I could just backup the data I want, then reformat (with a much larger /root directory)

---

### Post by Bucky Ball on 2012-03-14
Can you get to the screen with options to 'Try Ubuntu' 'Install Ubuntu' etc with the LiveCD? 

If so, hit F6 and choose 'nomodset' then 'Try Ubuntu' and see if it freezes. 

To copy through a terminal you are going to need to do something like:

```
sudo cp /path/to/your/files /path/to/external/device
```You need to find the path to your files and external device, naturally, and replace them with what I have here. You will also need to make sure you have the external device mounted somewhere by:
```

sudo mount /external/device /media
```... for example, if you want to mount your external device to the directory /media, which is fine for this. With any luck the external will be auto-mounted when plugged in (maybe plug it directly into your box rather than router for this).

---

### Post by DarthTeufel on 2012-03-14
I tried doing that during the LiveCD install, but got a 
> 
stopping system v runlevel compatibility

error.  I started researching ways to fix it, but then I just figured to post a thread since these forums were so helpful in the past.

Thanks for the help.  I'm actually browsing through my /home directory now, and looking to see if there is really anything there I need.  I store the majority of my files on the NAS box, so.... I think I might just go the clean install method.

Question for you though.  My live CD is 11.10.  Any thoughts on using this distro?  I don't really use this computer for very much besides web browsing and some office applications.

---

### Post by DarthTeufel on 2012-03-14
Now, when I try to install from the LiveCD, it freezes too.... back to the search bar !!!!

---

### Post by whiskers751 on 2012-03-15
You can try the Ubuntu Minimal distros....
They install via command line

---

### Post by Bucky Ball on 2012-03-15
> **DarthTeufel said:**
> Question for you though.  My live CD is 11.10.  Any thoughts on using this distro?  I don't really use this computer for very much besides web browsing and some office applications.

I would go for the most stable release which is currently the long-term support release, 10.04 LTS if that is all you do. Xubuntu would also be a good choice (slicker, speedier). 

I need my machine(s) to be stable/reliable so I stick with the current LTS release generally, have a couple of partitions on the laptop for newer release hopping and tweaking which I don't mind breaking. 

12.04 LTS is out end of April (but would give it some time after that before hitting 'Upgrade' or install on a different partition until stable) and the Ubuntu release has five years support like the server releases have always had (used to be three years for desktop). 

My mottos? If it ain't broke don't fix it and the latest ain't always the greatest! ;)

---


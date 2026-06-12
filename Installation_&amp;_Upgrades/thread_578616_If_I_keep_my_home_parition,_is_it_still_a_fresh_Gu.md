---
title: "If I keep my /home parition, is it still a fresh Gutsy install?"
date: 2007-10-17
forum: Installation &amp; Upgrades
---

### Post by bobbob1016 on 2007-10-17
I read somewhere that I should do "upgrade-upgrade-install".  I started with dapper, so I think I should reinstall.  I have my /home in a separate partition (a habit someone who got me into RH9 got me into), but everything else is in /.

I read this [http://ubuntuforums.org/showthread.php?t=572910](http://ubuntuforums.org/showthread.php?t=572910) but I am still a little confused on he says to do.

He basically makes a list of what is installed, and then copies the actual debs from the apt-archive, and puts them back, after installing Gutsy and reinstalls from the list?  When he says take out anything "Linux* and gnome*" does he mean remove the app, or the program entirely?  I'd assume program since the kernels fall under Linux*.

Would I have to do the /home things in the directions since I have a separate home partition?  Do I have to tell the programs where to find the old settings?

---

### Post by reckless2k2 on 2007-10-17
by "fresh" do you mean "clean"?

---

### Post by bobbob1016 on 2007-10-17
Yes, I mean clean.  One that is as close to a normal Gutsy install as can be, apart from my programs.  I want to clear up anything lurking that might be broken and hurt me down the road, or anything extra I don't need anymore, I tried wireless on this computer, but then I discovered networking over the powerlines, so all the things I did for wifi could be removed in a fresh/clean install.

---

### Post by gOLdenHaWK3D on 2007-10-17
> **bobbob1016 said:**
> I read somewhere that I should do "upgrade-upgrade-install".  I started with dapper, so I think I should reinstall.  I have my /home in a separate partition (a habit someone who got me into RH9 got me into), but everything else is in /.

I read this [http://ubuntuforums.org/showthread.php?t=572910](http://ubuntuforums.org/showthread.php?t=572910) but I am still a little confused on he says to do.

He basically makes a list of what is installed, and then copies the actual debs from the apt-archive, and puts them back, after installing Gutsy and reinstalls from the list?  When he says take out anything "Linux* and gnome*" does he mean remove the app, or the program entirely?  I'd assume program since the kernels fall under Linux*.

Would I have to do the /home things in the directions since I have a separate home partition?  Do I have to tell the programs where to find the old settings?

No problem at all. 
But all the softwares/packages and the Gnome itself stores its settings/configurations in the */home* folder, and these files are named starting with a Dot (.). For example, there will be *.gnome* and *.gnome2* for gnome settings, *.audacity* file for audacity settings etc.
If you really want a Clean install, then remember to delete these files by mounting the hard disc and deleting them using the *rm -r .** command from your home folder, when you boot thru the LiveCD. Then *umount* the hard disc, and continue the installation as usual.
This will ensure that you really get a clean install, otherwise the programs will tend to use the configuration files from your previous installation. [:)]

---

### Post by GlennW on 2007-10-17
Interesting reading, a bit over my head my I think somewhat related. I'm very much looking forward to Gutsy. However, I've had Feisty for only a little while and broke it to the point where I can only get to the console. X will start but screen has nothing but artifacts. It's a long and sordid story. I'm sure it's fixable from the console but my questions are these: 

How can I uninstall 7.04 without getting to the desktop?

Can I download Gutsy and install "over" Feisty with no repercussions?

I'm quite a newb so dumb it down quite a bit.

Thanks...

---

### Post by bobbob1016 on 2007-10-17
It is my configurations that I want to keep.  I want to get rid of anything broken in the / partition, but keep my settings.  If I do a complete wipe of the / partition, and keep the same /home, and use the same username and password, will I still have rw on it?  And if I follow the directions in the link I have in my first post, will the programs I have installed via apt be gutsy compatible?

---

### Post by renato_rosa on 2007-10-17
I also have a separate */home* partition.

How do I keep my website and */etc* conf files, like samba and other daemons?

Thanks!

Renato.

---

### Post by bobbob1016 on 2007-10-18
So far everything is working.  Pidgin picked up Gaim's settings, and Firefox is working.  I followed the directions in the link in my first post.  I am still re-installing my programs via apt, since they weren't all in the archive I guess.  I'll post with an update later.

---

### Post by bobbob1016 on 2007-10-21
I did this on my Desktop and one Laptop, it works well so far.  Had to manually reinstall virtualbox, but only because it isn't in the repos.

---

### Post by Jimlas53 on 2007-10-21
Add this line to your /etc/apt/sources.list file:
deb [http://www.virtualbox.org/debian](http://www.virtualbox.org/debian) gutsy non-free

Now you will be able to get the updates as they come through the repos.
Go to the website [www.virtualbox.org](www.virtualbox.org) and download the gpg signing file.  I think you need to right-click and "Save Target As".  It is the security signature you will need.  It can be saved in your /home folder.  Go to Software Sources (System>Administration>Software Sources) and select Authentication.  Select "Import Key File", then browse to the .asc file you downloaded from virtualbox.
Now you're all set!

As an aside, to address your initial question - I always maintain a separate /home partition, and I make it as large as possible.  I've upgraded one computer from Dapper all the way to Gutsy, all with the same /home.  It saves lots of pain and all my settings, bookmarks, mail etc. are preserved.

Hope this helps!

-Doug

---


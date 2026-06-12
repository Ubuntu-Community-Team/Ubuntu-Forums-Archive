---
title: "Minimal, but nice usable Ubuntu for my mother."
date: 2010-05-08
forum: Installation &amp; Upgrades
---

### Post by Linkert on 2010-05-08
Hello.

I've used Ubuntu in the past around version 7.04 and I was the typical user running from Windows, then I got a Mac with OS X and I do not see the need for Ubuntu for my own personal use. 

I'm gonna try and get my old Windows machine running for my mother, but I want to avoid Windows at all costs, so I thought Ubuntu would do the trick.

I got a Minimal CD and installed a basic Ubuntu installation. Some of you might wonder, "why not install the full ubuntu from the live cd for your mother?". Basically I think it's cluttered as hell with loads of packages which nether me or my mother will ever use or ever think about. So I thought I would make a totally custom Ubuntu installation.

Here's where you guys come in. I'm a commandline-retard, I know very little or second to none about typing in commands and such. I can follow instructions, you guys say "type sudo apt-whatever flip flop", I go "OK" and start typing. 

My goal is to achieve something that..

.. looks like this (gnome, lucid lynx, new wave theme):
[http://grab.by/4h4O](http://grab.by/4h4O)

.. works just like regular Lucid Lynx Ubuntu desktop, with all the preferences and administration tools.

BUT..

.. no preinstalled software like rythmbox, firefox, OpenOffice, Et Cetera..
.. no additional spacehogging stuff in general.

Ok, sure a browser would be nice. How about getting Google Chrome preinstalled?

__

Sorry about the vague description. I hope you understand.

What do I need to type? (I make it sound so simple, don't I?)

[http://grab.by/4h5g](http://grab.by/4h5g) (experimenting in VMware Fusion on Mac OS X)

---

### Post by Naitsirhc Hsem on 2010-05-08
Google Chrome can be installed via a download at chrome.google.com

What else do you want to install/uninstall?

---

### Post by cybrsaylr on 2010-05-08
> **Linkert said:**
> 

.. no preinstalled software like rythmbox, firefox, OpenOffice, Et Cetera..
.. no additional spacehogging stuff in general.

Ok, sure a browser would be nice. How about getting Google Chrome preinstalled?

Ubuntu is hardly a spacehogging OS. Ubuntu only usues <5 GB of space. Windows 7 takes up ~30 GB!

The full version of Ubuntu doesn't take up much space.
How much space does OS X use?
Just don't use the apps not needed but at least they are there if some else needs them. 

Chrome or even other browsers can easily be added. Along with any other app you may desire.

---

### Post by Naitsirhc Hsem on 2010-05-08
the new software Center is excelent for getting the software you need

---

### Post by Linkert on 2010-05-08
> **cybrsaylr said:**
> Ubuntu is hardly a spacehogging OS. Ubuntu only usues <5 GB of space. Windows 7 takes up ~30 GB!

The full version of Ubuntu doesn't take up much space.
How much space does OS X use?
Just don't use the apps not needed but at least they are there if some else needs them. 

Chrome or even other browsers can easily be added. Along with any other app you may desire.

I'm not trying to make comparisons between the OSes.. (yeez..) I'm calling the unnecessary packages "spacehogging stuff" as that is all these packages will do, hog space. 

Sure i could install a full version of Ubuntu and remove them manually, but i sure would like to just install Ubuntu without all of these unnecessary applications and packages..

---

### Post by Linkert on 2010-05-08
> **Naitsirhc Hsem said:**
> the new software Center is excelent for getting the software you need

I think you need to read everything again.

---

### Post by cybrsaylr on 2010-05-08
How big is your HDD?
All those unwanted apps may take ~1 GB of space, which most would not consider "spacehogging stuff" as you state. Believe you can easily remove the "spacehogging stuff" if desired with out hurting Ubuntu performance.

Just seems not worth the trouble unless the HDD is very small.

Ubuntu takes about as much space as XP.
Just curious? How much space does OS X take?

---

### Post by candtalan on 2010-05-08
Remember to create a non privileged account for your mother to use. The account which does the install is able to use admin rights (sudo). An extra account set to restricted privileges will save a lot of problems, and also it is worth locking the panels (to stay in the fixed position).
It is also very easy to remove unwanted items from the menus (they do not need to be actually un installed)

Good luck

you might enjoy this:
Shopping delivered to Great Grandma, by Ubuntu Linux
[http://dnc.digitalunite.com/2009/03/31/shopping-delivered-by-ubuntu-linux/](http://dnc.digitalunite.com/2009/03/31/shopping-delivered-by-ubuntu-linux/)

---

### Post by ugm6hr on 2010-05-08
This is written for 8.10, but I think should still apply:
[http://distrowatch.com/weekly.php?issue=20081215#feature](http://distrowatch.com/weekly.php?issue=20081215#feature)

But I agree with others - if you want *all* the services / GUI / auto-configuration without the apps - it would actually be easier to install the standard Ubuntu and then remove the apps you don't want.

This can be done from synaptic, Software Centre, or from commandline.  Just beware not to remove Evolution, which I presume is still somewhat integrated into Gnome.

If you actually want* just* a browser - then that is different...  You could do without Gnome in that case.

---

### Post by Linkert on 2010-05-09
I do not care about the space it self, the machine got plenty. I just don't want it being on the HDD at all, that's it really.

The inspiration for this little "project" or whatever you would like to call it, is this tutorial:
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

Just installing the basic Ubuntu installation, then adding what you want and need. 

I believe you could reduce the 1304 installed packages from the liveCD by almost 30% (% from anus) without reducing the quality of the OS and usability.

OS X uses less then 5 GB as i understand it. The minimum requirements for OS X Snow Leopard says "5GB of available disk space".  (for those who wanted to know)

Great link **ugm6hr**! That's what I'm looking for.  Will try it out.

---

### Post by ugm6hr on 2010-05-10
> **Linkert said:**
> OS X uses less then 5 GB as i understand it. The minimum requirements for OS X Snow Leopard says "5GB of available disk space".  (for those who wanted to know)


The Ubuntu Netbook Remix can be installed on under 4GB (or at least could be for 9.04).

That may be worth considering - and just removing the netbook-launcher would return you to the normal desktop.

---

### Post by Herman on 2010-05-10
> The Ubuntu Netbook Remix can be installed on under 4GB (or at least  could be for 9.04).I can confirm that the full Ubuntu Lucid Lynx standard installation can fit inside 4 GB and still have room for adding my favorite softwares like googleearth, quantum gis and a few other things because I have an ASUS 4 G and have been running Ubuntu in it for a long time now. There isn't room for very many files, but it will fit, and files can always be stored in flash memory sticks.  I recently installed Lucid Lynx in it and I decided to start using a picture card in the camera card drive as a separate /home, to give me room for files without the protrusion of a flash memory stick, but Ubuntu would have been able to fit inside 4 GB without doing that. I don't think Lucid takes up very much more room (if any) than earlier releases.  

Ubuntu One is a godsend to people with small hard drives or SSDs, we're allowed 2 GB of free storage in cyberspace, and we have the option to rent 50 GB for about $10 a month I think, and also there are many other benefits that come with having a Ubuntu One.
I'm still learning about it myself, so for more info it would be best to read for yourself. I started from the [Ubuntu One]("http://ubuntuforums.org/forumdisplay.php?f=367") section of Ubuntu Web Forums.

My mother uses Ubuntu too, she's extremely smart, but she's a new Ubuntu user. I must agree with you about one thing, there is a bewildering array of (to a person who has been using Windows since Windows 95)  strange sounding names for applications. It can be a little daunting to be suddenly dropped into this strange new world for some people, although for others it's exciting and fun. 

Did you know you can prevent programs from appearing in the menus by right-clicking on your top panel in the menus area and selecting 'edit menus'?
All you need to do is remove the checkmarks from the checkboxes for items you don't want to show up in your mother's menus.
That might make things a lot simpler for her, and if later you decide there's an application you want after all, you can simply re-enable it. (Although installing and un-installing programs is also easy).

I have to admit there are some programs I never use, (but I guess other people do), and I'm not interested in being presented with in my menus, it is nicer to see just the programs we want.
Now that you've got me thinking about this, I think I'll go and hide some programs I never use in some of my computers, and especially in my EeePC, to make better use of the smaller screen. (I still like the full Ubuntu install as opposed to netbook remix, probably just because I'm familiar with it.)

Uninstalling programs you don't want or installing minimal Ubuntu, (with the 'Alternate Installation' CD), can be useful for computers with a shortage of RAM. Ubuntu can run in as little as 32 MB of installed RAM, (command line only.) You can add a Desktop and just the apps you want. That would be an extreme step to take though.
There are a few apps you might want to keep, like rhythmbox music player, for use with Ubuntu One. There are three music stores available through rhythmbox via Ubuntu One, and even mothers like music too, my mother does anyway. So think things over well before you go uninstalling too many things. It's also nice to leave some things for people to explore. We don't want to be pre-judging people just because they're older than us or for any other reason. My mother often teaches me things about computers I didn't know before, and she's an expert in fields I haven't dabbled in yet. If you leave things there to be explored, you just might be in for a surprise some day when you come home and she has found out how to use some app from the software center that you have never even heard of! (LOL). :)

---


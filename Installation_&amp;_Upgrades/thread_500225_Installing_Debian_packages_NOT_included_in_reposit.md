---
title: "Installing Debian packages NOT included in repositories"
date: 2007-07-13
forum: Installation &amp; Upgrades
---

### Post by Xoldie on 2007-07-13
Hi there,
This post was previously presented at the Absolute Begginers Talk (where I do belong !!, by the way, as long as I’m 100% debutant in Linux with less than two weeks coming out from the “dark side”). 
No solutions were found there at beginners Talk, probably because the topic is a little to tough for strict beginners. Then, I´m taking the liberty to repost the subject here. 
Furthermore, I think that it is going to be an interesting subject fo many fellow members, as so few info is available on forums and the web on this matter of installing software NOT included in repositories.
Point is that software gathering and installation is one of the first tasks to accomplish when setting up a new OS, Xubuntu in my case. 
Being a novice to Xubuntu, or to Linux anyhow, if by any chance you need to go beyond what is the content of software repositories, then you will be rapidly needing to leave the beginners’ level arena (Synaptic, dpkg, or Debian Package Installer) being forced –notwithstanding that you are just a beginner– to get into deeper waters (Debian package downloading from websites or torrents, dependencies coordination, installation and, hopefully final, running your new application) well beyond the recently acquired (semi-acquired? Loosely tied?) very basic know how on the new OS and its operating procedures.      
After Xubuntu was painlessly set up and repository available soft was installed (excellent experience, very smooth and clean) I start to search for a 3D-CAD program to run on Xubuntu and did not find anything adequate neither in main nor in universe nor in multiverse repositories. 
So, the next step was to download Debian packages (GraphiteOne and FreeCAD were the downloads in this case I'm telling about) directly from the applications websites. Then in both cases the packages were installed using dpkg's GUI. After resolving dependencies issues (libraries had to be searched, downloaded as .deb archives, and installed using dpkg GUI as well) both applications were installed (apparently) OK in accordance with the post installation report from dpkg. 
But none of them made an appearance on the application menu, and none of then run when convoked from de command line or from a luncher created in the panel or the desktop. So one may think that the executables might be ended in a location out of PATH. 
Next spep was, then, to search for the executables, trying to fetch their location. 
Unfortunately, I was not able to find the executables anywhere in the file system.
Controlling in Synaptic, both application are shown registered as "installed". Right clicking on the item to open de "properties" dialogue, selecting the tab "installed files", a long list of files are listed as filed in /usr/bin/freecad, but said directory is not found and the listed files and filing locations does not exist. 
Just in case you ask, the route shown in Synaptic is absolute and dpkg was run with root privileges (the password to empower root rigths was asked at the time of running the order).
According to Synaptic the program is installed. So, we must assume that all the requisites to install were fulfilled at the time of running dpkg. The point is that what is shown in Synaptic apparently does not correlate to what actually happened. Somehaow, what Synaptic registered did not occur or did not get completed.
Believe it or not, the directories reported by Synaptic does not exist. 
I imagine that during the installation process the directory structure for the new installation is somehow designed and said design (written down in a configuration file?) is taken by Synaptic as done, but the actual creation of the filing structure takes place AFTER said step, and -who knows why- get truncated and/or incompleted. Please be aware that this is only imagination and deduction from the findings and facts, pure theorization. Actually, I don't have the knowledge of how the installation process goes on and why what's shown by Synaptic is not materialzed in the file system, either because it was never implemented or because it gets deleted at the finalization of the installation process. 

Let's hope a forum colleague member be there with an answer or, better, a solution to the problem, or at least with directions to a tutorial or paper on the subject.

Sorry for the lengthy speech. Thanks a lot.

---

### Post by Xoldie on 2007-07-13
After I posted my comments on installation of Debian packages NOT included in repositories, I came across to the superlative guide posted under: [http://ubuntuforums.org/showthread.php?t=500020&highlight=debian+packages](http://ubuntuforums.org/showthread.php?t=500020&highlight=debian+packages) ,now rightly converted to Sticky.
Its an excellent guide, but ONLY FOR REPOSITORY CONTAINED SOFTWARE.
See what I said before in my previous post -as a very beginner's impression- that very little is found out there on how to proceed when you need to go off repositories limits to fetch the software you need.
Is that Linux software coverage and availability abruptly ended and/or deteriorated off the boundaries of repositories? Is it like medieval times, with civilization well kept within cities or monasteries walls and wild forsaken grounds out of walls?
Please, I would like to know what is felt in the community on said issues.
Best regards and tks in advance.

---

### Post by fenario on 2007-08-29
Yes Xoldie, you have a good point there. 

When you cross the floor from Windows to Linux it is all one big field to gather and learn.
I'm already thinking of trying a redhat system, like the new Fedora, after a few frustrations with Ubuntu. It has promise to make my printer work.

There are reasons why one gets other software like tarballs and as I found out there are a lot more rpm files to be had and sometimes, as in Lexmark, an rpm file is the only option. You may find a file on a CD or DVD from a computer mag and extract it from there.

Dreaded Dependency Defuncts and Defects

As so many tell you the same problems. Dependencies are installed but not recognized outside the synaptic helper. That's were the obscurity starts. Info on the problems is hard to find. I'm wasting weeks of my life just to install a printer...grrrr...I still have windows thanks god. I need a printer to print out the text on how to install a printer.....so I can print out.....etc

It seems that there is camps and medieval fortresses. For me but it is the world. Good on you Xoldie; keep the world thinking.
Fen

---


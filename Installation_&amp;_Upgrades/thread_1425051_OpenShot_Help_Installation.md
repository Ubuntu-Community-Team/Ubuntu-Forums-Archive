---
title: "OpenShot Help Installation"
date: 2010-03-08
forum: Installation &amp; Upgrades
---

### Post by splosh5 on 2010-03-08
Hey guys i am very new to ubuntu i have only used it for 3 days now :(. anyway i came across this great program called Openshot now i downloaded the (DEB Installer) for version 9.10 witch i am running right now. Anyway when i try and rune the Package Installer it says at the top:

>  
Error: Dependency is not satisfiable: python-mlt|python-mlt2|openshot-mlt
Any Suggestions? 

Many Thanks
   Splosh5

---

### Post by blur xc on 2010-03-08
> **splosh5 said:**
> Hey guys i am very new to ubuntu i have only used it for 3 days now :(. anyway i came across this great program called Openshot now i downloaded the (DEB Installer) for version 9.10 witch i am running right now. Anyway when i try and rune the Package Installer it says at the top:

Any Suggestions? 

Many Thanks
   Splosh5

If you are running 9.10 you should add their ppa (personal package archive) and install it from the software center, or synaptic, or the command line, whichever you prefer.

here are command line instructions- [http://www.openshotvideo.com/2008/04/ppa-instructions.html](http://www.openshotvideo.com/2008/04/ppa-instructions.html)

This way it will grab and install the dependencies automatically.

As a little FYI (in case you don't know, you did say you have been using Ubuntu for only 3 days)- the preferred method for installing software in Linux is to use the repositories.  Repositories  are like the apple app store.  Just with a less pretty storefront (apple has "pretty" dialed).  You can add extra repositories in your software sources.  If you install software from the repos you get the latest versions, and you get automatic updates when new versions come out.  
  
BM

---

### Post by splosh5 on 2010-03-08
> **blur xc said:**
> If you are running 9.10 you should add their ppa (personal package archive) and install it from the software center, or synaptic, or the command line, whichever you prefer.

here are command line instructions- [http://www.openshotvideo.com/2008/04/ppa-instructions.html](http://www.openshotvideo.com/2008/04/ppa-instructions.html)

This way it will grab and install the dependencies automatically.

As a little FYI (in case you don't know, you did say you have been using Ubuntu for only 3 days)- the preferred method for installing software in Linux is to use the repositories.  Repositories  are like the apple app store.  Just with a less pretty storefront (apple has "pretty" dialed).  You can add extra repositories in your software sources.  If you install software from the repos you get the latest versions, and you get automatic updates when new versions come out.  
  
BM

Ahh thanks alot ive downloaded it and it works great BUT. there is one big issue. when i come to render my videos the program just crashes for i get logged out. any ideas?

---

### Post by blur xc on 2010-03-08
> **splosh5 said:**
> Ahh thanks alot ive downloaded it and it works great BUT. there is one big issue. when i come to render my videos the program just crashes for i get logged out. any ideas?

For that I have no idea.  I just started playing around with it over the weekend as well, so I'm for from an expert, and it crashed on me a few times too.  Maybe check out their forums...

BM

---

### Post by splosh5 on 2010-03-08
> **blur xc said:**
> For that I have no idea.  I just started playing around with it over the weekend as well, so I'm for from an expert, and it crashed on me a few times too.  Maybe check out their forums...

BM


Ahh ok will do.. thanks :)

---

### Post by jsmnuk on 2010-03-16
Python-mlt2 is definitely the magic bullet here. Attempts to run openshot from Terminal will repeatedly result in either a failure to import bindings message or a line error message which locks up both Synaptic and the Terminal. Mine was line 53 of /etc/apt/source.list. I did:

$ cd /etc/apt/(whatever directory that source.list is in)

$ gksudo gedit source.list

I then manually deleted line 53, and Voila!: I could use Synaptic and "apt-get install" again. However, line 53 **had** listed the lucid source where I got the python-mlt2 install, and attempting to download and install it again led to dependency hell.

Lucid Lynx, we have a problem....

(PS, plz don't take my scripting seriously, but gksudo gedit did work for me)

---

### Post by shipp on 2010-04-02
I am getting the failed to retrieve python bindings message and want to do whatever it is that you did to fix the problem.  You said "mine was line 53"  line 53 of what?  I don't really know how python works, or even the repositories for that matter, since I just started on ubuntu and am trying to figure it out.  So, where or how do i find the line that is preventing me from running open shot, and how do I change it, and what should i change it to?  

Any suggestions?  Thanks.

---

### Post by jsmnuk on 2010-04-12
> **shipp said:**
> I am getting the failed to retrieve python bindings message and want to do whatever it is that you did to fix the problem.  You said "mine was line 53"  line 53 of what?  I don't really know how python works, or even the repositories for that matter, since I just started on ubuntu and am trying to figure it out.  So, where or how do i find the line that is preventing me from running open shot, and how do I change it, and what should i change it to?  

Any suggestions?  Thanks.

Openshot's got a problem: NO SOUND. I got bumped up to Lucid 10.04, and Openshot is installed. It readily opens, but.... I ran sudo apt-get update and sudo apt-get upgrade, and, if I observed the process correctly, the latest python-mlt2 was downloaded and installed. Still no sound. 

The official release of Lucid is due out the 29th, and Openshot will have competition from VideoLAN's new media editor --- AND VLC Media Player will play Blu-Ray. Somebody out there in Ubuntuland better wake up and smell the coffee!

As for you, Mr. Shipp, you might want to wait until the official release for a solution to your problems, if it fixes them at all. BTW, line 53 is in etc/apt/source[COLOR=Red]s[/COLOR].list (sorry for the mistake). It was the very last line for me, but I just checked the file and if line 53 says "deb [http://mirrors.kernel.org/ubuntu](http://mirrors.kernel.org/ubuntu) lucid main", I wouldn't touch it.

---

### Post by jsmnuk on 2010-04-14
> **shipp said:**
> I am getting the failed to retrieve python bindings message and want to do whatever it is that you did to fix the problem.  You said "mine was line 53"  line 53 of what?  I don't really know how python works, or even the repositories for that matter, since I just started on ubuntu and am trying to figure it out.  So, where or how do i find the line that is preventing me from running open shot, and how do I change it, and what should i change it to?  

Any suggestions?  Thanks.

UPDATE, UPDATE! I've got sound now. 

                 What I did:
 1. open Synaptic;
 2. select and mark for installation libsdl1.2debian-all (which will  remove libsdl1.2debian-pulseaudio);
 3. above, click apply;
 4. I don't know how it happened, but Openshot has got sound now.
 No guarantees, I'm a noob. Sorry I was such a crab.

[https://bugs.launchpad.net/openshot/+bug/440721](https://bugs.launchpad.net/openshot/+bug/440721)

---

### Post by Bob2893 on 2010-04-27
I had openshot running fine on 9.10 for a few weeks, then it began to loose sync with voice / video and took ages to load. Now it will not open at all, either in terminal or menu. I did a 'complete removal' via synaptic, then a reload  via ppa but still won't open. .(I notice that there are still openshot program files in the var/cache/apt/archive which cannot be deleted????........why so?

I installed the current repository file via ppa on another computer, which has the same 9.10 config and it works fine. Seems like there is something disrupted in the first machine which is preventing me doing a clean install??

Help appreciated........just a Ubuntu learner but enjoying the journey.

---

### Post by Cresho on 2010-08-22
> **jsmnuk said:**
> UPDATE, UPDATE! I've got sound now. 

                 What I did:
 1. open Synaptic;
 2. select and mark for installation libsdl1.2debian-all (which will  remove libsdl1.2debian-pulseaudio);
 3. above, click apply;
 4. I don't know how it happened, but Openshot has got sound now.
 No guarantees, I'm a noob. Sorry I was such a crab.

[https://bugs.launchpad.net/openshot/+bug/440721](https://bugs.launchpad.net/openshot/+bug/440721)

this worked perfectly.  thsnks

---

### Post by NoBugs! on 2010-12-05
How did you install Openshot in 10.04? Whenever I try to install, it only gives "The following packages have unmet dependencies:
  openshot: Depends: python-mlt but it is not installable or
                     python-mlt2 but it is not installable
E: Broken packages"

I have all standard repositories checked, updated, it seems there is no "python-mlt" in Lucid packages.

---

### Post by NoBugs! on 2010-12-20
It looks like python-mlt, and also jpilot, are unavailable on the main server. Going to System -> Admin -> Software Source, changing the download server, and reloading, fixed the problem.

---

### Post by wolfen10 on 2011-07-05
hello, i have tried to install Open shot as well but with no luck...
whenever i enter the code for installing it via terminal it gives me this error message:

E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

any suggestions?

P.S.: I am using Ubuntu version 11.04


-wolfen10

---

### Post by NoBugs! on 2011-07-05
> **wolfen10 said:**
> 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

any suggestions?


Do you have more than one Software Center / Synaptic package manager open? Have you tried restarting?

---

### Post by Keizgon on 2011-09-28
> **wolfen10 said:**
> hello, i have tried to install Open shot as well but with no luck...
whenever i enter the code for installing it via terminal it gives me this error message:

E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

any suggestions?

P.S.: I am using Ubuntu version 11.04


-wolfen10

Close out of Synaptic Package Manager, it's preventing you from getting the package lists from your terminal through 'sudo apt-get update'.

I been researching how to fix my problem after an update in 11.04 natty  (shame on me for not paying attention to what was being upgraded and  removed). I had openshot 1.4 installed and working before I executed  this update. Now I recreated getting back both 1.3 and 1.4.

Now here's the solution for openshot versions 1.3 and 1.4.

**1.3** (currently default version in ubuntu package repository)

- uncheck openshot's ppa 'http://ppa.launchpad.net/jonoomph/openshot-edge/ubuntu' in your software sources (via Ubuntu Software)
- install openshot (via terminal or Synaptic).

You might end up removing a couple packages, which is ok if you want version 1.3. However, if you want the latest stable (1.4), ignore these steps and read on for 1.4.

**1.4** (latest stable in openshot's ppa)

- Add and check ppa 'http://ppa.launchpad.net/jonoomph/openshot-edge/ubuntu' (if you haven't already) for openshot's latest stable.
- Now add ppa 'http://ppa.launchpad.net/sunab/sunab2/ubuntu'. This will update you with the latest mlt (0.7.4 currently) dependencies that require openshot 1.4 to run. 
- Check for updates and install or upgrade (if 1.3 is installed) to openshot 1.4
- Note there might now be some useless packages leftover so be sure to remove them through 'sudo apt-get autoremove' when all done

I hoped this helped. I noticed another thread on this from back in May 2011 which didn't help me originally. I wasn't aware I didn't have the latest stable of mlt framework, and apparently, nobody else here has realized this for 1.4 so far. Some responses were "reinstall Ubuntu", but I fail to see that as a viable solution for an easy problem.

Also, please note future releases of openshot will likely be removing the mlt framework, which might prevent some of this confusion in the future.

---


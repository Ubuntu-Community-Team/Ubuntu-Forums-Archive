---
title: "Updating multiply pc's on limited bandwidth"
date: 2011-04-22
forum: Installation &amp; Upgrades
---

### Post by Dis-appointed on 2011-04-22
------------Quick Info------------

I'm new to Ubuntu. 3 days ago I successfully installed maverick on 2 machines.(initially via wubi now dual booting to seperate partitions). Quite a bit of "windows" experience and not scared of the CLI, but know very little apart from what I've been reading the last few days about ubuntu/*nix. This has been mostly been MAN pages/howto's about updating my systems, including APT, dpkg, etc. Some things I can't seem to find answers to though.

-------------------Questions------------------------

What is update-manager actually doing? 
a) Where is it looking and how is it deciding which packages/updates to suggest.
I thought I'd be able to use synaptic to reproduce the results via it's filters etc. This would at least give me a starting point for further investigation. But I have had no luck so far getting the totals the same. Closest result was same number of files but the size differed by 40mb+. This is on my "virgin" installation of ubuntu 10.10 on my laptop with nothing else installed and no updates done yet.

b) I assume maverick-security and maverick-updates has something to do with how it's deciding what to offer. How does it work? Is it a field or something in the packages themselves? How do I access it so that I can make APT look there too. Is it just "apt-get upgrade" (or dist-upgrade)? If so what is apt-get looking at in order to decide what packages? ideally I'd like to have apt run in a simulation mode (-s switch IIRR) and have it show the same list/totals as update-manager.

c) My objective here is to recreate locally(on USB) what's on the official source so that update-manager can use it to decide what's available/needs to be on the system. Irrespective of where the packages actually are. (An initial update of the sources in update-manager after installing was more than 15mb. Even this amount of bandwidth becomes significant with multiple installs for me.) 
This looks possible by using only the Packages.bz2, Packages.gz, Release, Release.gpg, etc files, but something hasn't clicked into place for me yet, despite all the documentation I've read so far. I haven't found what i'm looking for in Ubuntu docs which refer to APT docs/man pages which are supplied by Debian. So Identifying the specific case for Ubuntu inside the general info is proving impossible for me with my current wet-ware installation :P

A "you need ###these.files.from.sever###" on your usb (added to sources.list) for apt to update properly" type answer for this question be great :D

This is similar to what synaptic offline, apt-medium, etc do, but they don't quite fit with what I'm trying to achieve. So I need a way to replicate what they do, which I haven't found in the docs yet.

Any comments or references that you think might help would be most welcome. As well as any problems you see in my "thinking aloud" below. 




------------Background info------------

I made a long, long post about why ubuntu seem to be a chocolate covered dog turd to me. (based on the fact that it looks good, smells good, but tastes like sh*t. looks =looks, smell = use, taste = keeping up to date on a low speed/data capped connection. updates = 300mb immediately after install. Which belies what I was led to believe on whyuseubuntu page.)

Anyway after writing out my rant I felt better and didn't post it. I've just moved on to trying to find a solution. Luckily, due to the "openness", a solution seems to be possible for me to achieve, with my limited skill-set and a bit of effort. Tasting better already, or maybe i'm just getting use to the flavour, hehehe.

So here's my problem

I have 3 machines I need to upgrade after installing (+ re-installs once I've mucked it up with fiddling :D ) + offline update for mom on a regular basis. Internet is capped at 1g per month. So automatic update via ubuntu's update manager is not feisable out the box. I can't afford to have no internet for the rest of the month after I update the 3. The solution should be easy download updates once and re-use the packages (just like i've done for years on windows).

Handbrake!!! No easy (i.e. couple of clicks in a gui) way to do this.
So here I am wading through dozens of help topics/howto/man pages. 
eg. [https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)
    
All of which seem focused on;
1) single system updates/upgrades by using a 2nd system to do the downloading with a broadband unlimited connection. (STFU 3rd world you don't need upgrades :P ). 
OR
2) Alternatively mirror the entire repository. (I'd never finish, it would continually update before I completed a fraction). I could buy the dvd set, but this would only solve the problem temporarily. And ongoing it would soon outstrip the cost of windows.

All is not lost however I have discovered various things after hours of reading through doc's and feel I'm almost where I need to be in order to actually trying to get this working. 

Objective 1: A local(USB/CD/Network) non-"machine specific" cache of packages I can use to update various machines from by default. If not available download and/or request them to be added to cache. 
Objective 2: Make it work via update-manager with minimal user input (for non-techsavy family and friends)
(Example: I send a cd of windows updates to my mother regularly (she has a very low bandwidth connection so auto-update is disabled). She runs a simple batch file on the cd which then installs all the updates, using silent switches. I'd have her using ubuntu in a flash if I had a easy way of doing similar with it)
Objective 3: Solutions need to be as simple as possible so I don't have to go through an extensive learning curve again in 6 months, just to figure out what I was up to now :P

The software chain seems to be;
dpkg -> APT -> synaptic -> update manager (as it shares settings with synaptic)

Seems using APT directly is the way to go as it's refered to as the back-end tool for the others. So this has been my base point for research and plan of action. Focusing on the suggested updates for a system as this is my primary area of concern (and by comparison installing specific packages from a local folder will be a breeze.)
Rough outline of process: 
a) editing apt's source.list (probably copy + replace it with Internet neutered one) and config on-the-fly . apt-update 
b) run update-manager (or apt-get or install) using a USB with a dpkg-scanpackages produced file + packages and/or a "copy of latest official packages available".
c) Then either install whats available locally and/or make a list of whats needed. 
d) cleanup on-the-fly changes. apt-update
e) Either immediately or at some other time and/or place. Download the required files without installing. Update "copy of latest official packages available" if needed.
f) dpkg-scanpackages update to include downloaded packages.
g) goto a)
At the moment I'm planning to use a USB flash drive to transfer files around. A switch to using a network share(or cd) seems easy enough afterwards, but I haven't opened the networking can-of-worms yet :P

I could update my current system and then simply copy the packages from the apt cache (/var/cache/apt/archives), to the other systems and add the packages via apt or synaptic, etc manually. This would only be a very temporary solution, as soon each system will have different packages on to suit there functions/users. I don't have the experience to make decisions about what upgrades to install or not install. So it would probably soon cause dependency issues, etc. So my solution has to work with update-manager or at least simulate what it does. 

Since bandwidth conservation is one of my primary concerns and I don't know enough about the packages "on offer" to be selective atm. I need to have some certainty of the route i will take and that the packages will be re-usable, before I start downloading. Other than that I'll happily break my system and re-install in my efforts to get this right.

So I've spent a couple of days reading up what I can.
e.g. [https://help.ubuntu.com/community/Repositories](https://help.ubuntu.com/community/Repositories)
[https://help.ubuntu.com/community/Repositories/Personal](https://help.ubuntu.com/community/Repositories/Personal)
None of which directly resolves my problem. So I have a few questions I haven't been able to discover answers to. Since I'm a noob to *nix I think i'm probably not asking the right questions or looking in the right places. Also I'm suffering from an exponentially increasing list of documents to read (usually just to find a single snippet of info that is relevant atm.) I'm not looking for elegant yet. Just something that I can understand and uses the most basic commands

e.g I plan to use "apt-cdrom -d" to mount my cache folder.
Why? cos I can remember the command easily :D
To do it right I'd need to edit sources.list. I'm not ready yet to do that via a script/CLI. it's proably as easy as using >> to the end of the file. But thats a whole nother investigation which can wait.
So for now i'm familiar enough with mount, umount and blkid -o from my wrestlings with sysresccd.org for data recoveries. So easy to read blkid -o and umount last entry (the usb that will have just been plugged in) then mount it to floppy0 so that it fulfills the fstab condition of the -d switch for apt-cdrom. (don't ask me what fstab is :P i just read the file in gedit on 2 machines and floppy0 was in both, so seems like a likely candidate for me to maul.)

-------------------------- End Background ------------------------------

---

### Post by sanguinoso on 2011-04-22
You can use apt-cacher-ng to cache the downloads so that each identical package will only download once, and then all the other computers can download from that one. There's a tutorial on how to set it up here:
[http://linuxexpresso.wordpress.com/2011/02/13/howto-apt-cacher-ng-on-ubuntu/](http://linuxexpresso.wordpress.com/2011/02/13/howto-apt-cacher-ng-on-ubuntu/)

---

### Post by Dis-appointed on 2011-04-22
> **sanguinoso said:**
> You can use apt-cacher-ng to cache the downloads so that each identical package will only download once, and then all the other computers can download from that one. There's a tutorial on how to set it up here:
[http://linuxexpresso.wordpress.com/2011/02/13/howto-apt-cacher-ng-on-ubuntu/](http://linuxexpresso.wordpress.com/2011/02/13/howto-apt-cacher-ng-on-ubuntu/)


Many Thanks for this info. Looks like a fast way for me to get all my installs upgraded. 

And maybe even abuse it a little to get a offline install updated. Also I see potential to use it to answer some of my other questions, if there is a way for me to read a log file of the requests made via ACNG, but that's a whole new thing for me to investigate.

---

### Post by dino99 on 2011-04-24
[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

[http://ubuntuguide.net/update-ubuntu-off-line-via-another-windowslinux-pc-using-keryx](http://ubuntuguide.net/update-ubuntu-off-line-via-another-windowslinux-pc-using-keryx)

---

### Post by Dis-appointed on 2011-04-24
> **dino99 said:**
> [https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

[http://ubuntuguide.net/update-ubuntu-off-line-via-another-windowslinux-pc-using-keryx](http://ubuntuguide.net/update-ubuntu-off-line-via-another-windowslinux-pc-using-keryx)

Thanks for the reply but they don't really help. I've read those pages before and they don't give me the info i think i need :P

I'm currently working on using one of the APT proxy applications for downloads on an initial machine (as suggested by sanguinoso) . And then using a local copy of ftp.ubuntu.com 's package information (maybe with the links to a local pool edited if i have too.) Not quite there yet, but working on it.

What I really need is info on the relationships between APT (synaptic, update-manager) and the sources (as per my other post [http://ubuntuforums.org/showthread.php?t=1737891](http://ubuntuforums.org/showthread.php?t=1737891)). This is the bit that is still unclear to me, even though I've read; the debian policy documentation on packages, everything ubuntu docs has to offer on the subject. the various apps man pages. So at this point I can't check the results of what I plan to try compared to what update-manager does.

---

### Post by Elfy on 2011-04-24
Not quite sure why you need to know "the relationships between APT (synaptic, update-manager) and the sources" other than knowing.

However I know when I used apt-cacher-ng it worked well. The only time the 'client' machines will need to go to elsewhere for a package is if it's no available on the 'server' machine.

It worked well when I had 4 machines here all running the same OS.

Update-manager on the clients worked as expected and pulled the packages from the server - obviously you need to ensure that's updated first.

---

### Post by Dis-appointed on 2011-04-24
> **forestpiskie said:**
> Not quite sure why you need to know "the relationships between APT (synaptic, update-manager) and the sources" other than knowing..

Since I can't seem to get the "underlying" APT programs (apt-get, synaptic) to agree with update-manager. As per my unanswered post
[http://ubuntuforums.org/showthread.php?t=1737891](http://ubuntuforums.org/showthread.php?t=1737891) , I having a difficult time trying to find a way to check that the results will be the same after doing things a different way. 

Since I've spent less than a week with ubuntu (or any linux) I can't make intelligent decisions about what packages need to be install. Hence my pre-occupantion with upgrade-manager, working on the basis that "ubuntu" knows best what I need right now.

If i can get equivalence between synaptic and update-manager, I can then compare synaptic and apt-get. these 2 at least have a function whereby I can create a list to compare with.

> **forestpiskie said:**
> 
However I know when I used apt-cacher-ng it worked well. The only time the 'client' machines will need to go to elsewhere for a package is if it's no available on the 'server' machine.

It worked well when I had 4 machines here all running the same OS.

Update-manager on the clients worked as expected and pulled the packages from the server - obviously you need to ensure that's updated first.

Thanks for the +1 recommendation of apt-cacher-ng. It's the keeping the server updated bit that is concerning me. I need to have a firm control over where and when the new packages are downloaded. At the same time I want automate the process so I don't have to  continually manage it. All of which looks possible and more. But I need a reference point to compare back too. i.e. a list of the things update-manager wants to do!

Thanks again for your post.

---

### Post by Elfy on 2011-04-24
> **Dis-appointed said:**
> If i can get equivalence between synaptic and update-manager, I can then compare synaptic and apt-get.  From memory (atm I don't have a working debian machine) while both update manager and synaptic deal with and from the same packages, and synaptic would show the packages that update-manager installs as being installed, I do not think that the history in synaptic shows what update-manager has done. I'm quite probably wrong or at least wrongish - memory is not what it was.

> It's the keeping the server updated bit that is concerning me. I need to have a firm control over where and when the new packages are downloaded. At the same time I want automate the process so I don't have to  continually manage it. All of which looks possible and more. But I need a reference point to compare back too. i.e. a list of the things update-manager wants to do!Once the cacher is setup then update-manager will work just as it is now - the only difference being that the clients will take packages from the server when they are available from the local server or from over the internet when they are not.

---


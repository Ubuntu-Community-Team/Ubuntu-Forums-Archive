---
title: "Net install - How to use CD or network as archive?"
date: 2005-10-24
forum: Installation &amp; Upgrades
---

### Post by khansen on 2005-10-24
Ok, here is the situation.

I teach Multimedia in a high school in the US and I am ready to completely convert my lab over from windoze to Linux.  I am looking for a way to install Breezy on all 40 of my machines (1 year old dells) without having to put the install CD in each one. 

I have considered:
1 - Using partimage (and partimaged) from the  SystemRescue CD to clone one master machine onto every other machine.  The one disadvantage to this is that I still have to sit at every machine and run some sort of script to do this.  I've done this in the past, but it is still somewhat tedious with 40 machines.

2 - Using LTSP to boot each maching and do the partimage cloning.  The advantage here is that if I can figure out how to gain access to the local harddrive, I could setup up a script to run as soon as the system is running that would do the cloning.

3 - Using Net Install/LTSP which comes built-in to breezy and edubuntu (which I plan to use).  

I have managed to get a LTSP server running and I installed one machine using it, but I noticed that it fetched the kernel and all the debbootstrap stuff from an archive on the internet.  

I would like to have it fetch that information from a local network resource/archive but I don't know how to set that up or change the location it looks to download that information.  I was able to setup apt later on to look for the cdrom, which was nice, but I'd like it to get everything from the local network.

4 - Using SystemImager to do the cloning.  This seems to be a good, long-term option.  It would simplify periodic reimaging.

Question 1: Which would  be the best way to go about installing ubuntu on the entire lab?

Question 2: How do I change the location the netboot image looks for the installation archive?

Question 3: Have any of you successfully used SystemImager to create and use a netboot image?
-----------------------------------
OK, I found an answer to my own question.  I followed the instructions [ here ]("https://wiki.ubuntu.com/Installation/LocalNet?highlight=%28localnet%29") and I was successfully able to launch the installation from any client using netboot.  It turns  out there is an option to manually enter in the archive URL used when doing a net install.  I feel sheepish not looking more into it before posting this here.  I still have to setup the install on each machine, so the next step is getting a hands-off install up and going.  The link above has instructions for this too.  I'll work on getting that working tomorrow.

---

### Post by scottie4442 on 2005-11-08
Ok, I am lost. I looked all over that page and I cannot find where it tells you how to manually enter the archive location.  I do want to do an interactive install using a local archive, I am teaching a *NIX class, using Ubuntu linux for lab projects, and I cannot uses internet repositories to do the initial install, I have 24 lab machines and doing an internet install would load up the schools T1 line, which would get me in trouble with the IT department. Please let me know where you found the manual setup for the archive, or just how you did it.  Thanks

Scott Adams
Computer Network Instructor
Southeast Arkansas College
Pine Bluff, AR

Converting the world to Linux one pissed off Windows user at a time

---

### Post by imagine on 2005-11-08
I have never done anything like that, but did you dig around in the wiki a bit? I found [https://wiki.ubuntu.com/UbuntuOnCluster](https://wiki.ubuntu.com/UbuntuOnCluster). Apparently he used a caching proxy to prevent packages from being downloaded multiple times.

---


---
title: "Unmounting Weak file system-Error?"
date: 2010-09-19
forum: Installation &amp; Upgrades
---

### Post by dmurphy787 on 2010-09-19
Upon shut down I have noticed that my system says "Unmounting Weak file system".  I have taken steps to check that all software is installed correctly and up to date but I am quite new to Linux and I am still learning.  
Does warning at shutdown mean that there is a problem with my file system?  
Is there anything I can do to fix this?

---

### Post by simong6 on 2010-10-14
i have the exact same problem, i had a 1-00gb hdd that i knew was failing, replaced it with a brand new 160gb drive on tuesday and upgraded to 10.10 at the same time, upon restarting the new install, recieved countless read write errors which haven;t appeared since, and now get Unmounting Weakfile system upon shutting the laptop down.
 
i've also noticed that since the updates on Tuesday night, the machine is now running really quite slow compared to what i'm used to with ubuntu

---

### Post by dmurphy787 on 2010-10-14
Hi thanks for reply, my system is about 5 years old and does have some hard drive issues, like over heating problems etc.  I managed to fix mine by reinstalling Ubuntu straight over the top again and the weak file system warnings have disappeared and not returned.  I think that the system hardware issues possibly caused some issues on installation and a reinstall when my machine was feeling better fixed it.
Give it a go and let me know if you experience the same.

---

### Post by dino99 on 2010-10-14
dont worry about that, but some cleaning could help. You have the usual "sudo apt-get clean", autoclean, autoremove

and gconf-cleaner
and bleachbit (use as admin but set carefully the prefs)

if nothing help, then do a reinstall from scratch if things become weird.

---

### Post by dmurphy787 on 2010-10-14
I love the community of Ubuntu, it really does allow all of us to share and give to others as we should in life.
Thank you dino99 for your excellent info.

---

### Post by simong6 on 2010-10-14
> **dino99 said:**
> dont worry about that, but some cleaning could help. You have the usual "sudo apt-get clean", autoclean, autoremove

and gconf-cleaner
and bleachbit (use as admin but set carefully the prefs)

if nothing help, then do a reinstall from scratch if things become weird.

I've given all these things a go, with the exception of bleachbit and none of it has gotten rid of the weak filesystem message on log off, also the boot is still slow, and after paying attention to it gives me a blank screen rather than any slash screen.

---

### Post by dmurphy787 on 2010-10-14
Have you reinstalled straight over the top again? This has worked for me but we need to wait for a reply or place the question to Ubuntu directly.:(

---

### Post by efflandt on 2010-10-14
That flashes by too quickly to read in detail, but I never gave "Unmounting weak filesystems" another thought.  I just figured that was listing the normal sequence of events as it was powering down, and maybe just unmounts auto mounted and/or non-Linux file systems first.  I could be wrong, but I always took it as an informational thing, not a warning.

I am not currently running any drives with any issues.

---

### Post by dmurphy787 on 2010-10-14
Hi,
It not should be unmounting any other non-linux file systems, you know because its linux and the mounting system only relates to linux.  Which works totally different from windows or other and it would be impossible for another type of mount.
In relation to my issue I also had the Warnings about "Weak file system" and I did not have any other issues either but I believe it is a File system warning that indicates something on the system needs addressing.  I have 2 systems running Ubuntu and my other system does not have any issues at all.  My second system is only about 3 months old and has no hardware or other issues either but the system that was reporting the "Weak file system" does have some hard drive integrity issues and I believe that this is possibly the cause.  I managed to fix mine with a reinstall of that system and it does not display the warning anymore.

---

### Post by simong6 on 2010-10-15
I'll give the reinstall a try once i finish work this evening, and i'll let you know the progress, it could be that i've got a duff new hard drive and may need to contact the supplier.

---

### Post by simong6 on 2010-10-15
installed again straight over, however i'm still getting the message when shutting down. Haven't even bothered installing the updates this time (yet)

---

### Post by Gary_inNYC on 2010-10-20
I'm no expert, but perhaps you can run:

sudo touch /forcefsck 

and see if the problem persists?
Hope that helps.

- Gary_inNYC

---

### Post by dmurphy787 on 2010-10-20
Hi Gary,
I appreciate your suggestion and help but do you know what that command does?  If you are not %100 sure yourself its not advisable to give out commands that could not be suitable for another persons computer.  A further explanation of this command and why it will help would be more suitable.
Thank you.

---

### Post by vdubhack on 2010-11-06
all that command does is tell your system to run fsck then next time it boots then once done removes the file. 

Always research any command given before running it even if they explain what its "suppose" to do. Just cause I said thats what its does, does not mean it really does 

I have the same messages coming up on my laptop. Brand new drives multiple reinstalls always this warning. All tests run on my disks in either linux or winblows say my disk is fine with no issues at all as I would expect with a new drive. I think there is another cause for this. I think it has to do with the SATA plug on the drive as my drive remounts lots of times during and after reboot. I dont think linux likes the sata plugs as of yet or there is a bug in acpi maybe not really sure.

---

### Post by werty2010 on 2011-02-07
did anyone found out the exact reason for this message after all?
if yes could you please reply for the rest of us?

---

### Post by Ragmuffin on 2011-02-10
> **dmurphy787 said:**
> Upon shut down I have noticed that my system says "Unmounting Weak file system".  I have taken steps to check that all software is installed correctly and up to date but I am quite new to Linux and I am still learning.  
Does warning at shutdown mean that there is a problem with my file system?  
Is there anything I can do to fix this?
Boot from the live CD and select try Ubuntu.  At the top left hand corner where the programs are click on Administration and then click on Disk Utility.  Find your hard drive on the left panel and click on it.  Click on the icon near the bottom that says "Check File System."  After clicking on it, it says your file system is up to date.  I don't know what it did but after the next reboot into the system on the hard drive and shutting down the error message was no more.

---


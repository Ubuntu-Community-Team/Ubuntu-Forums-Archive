---
title: "feisty -&gt; gutsy upgrade problems, help!"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by xtlosx on 2007-10-19
Hey everyone, some upgrading problems.... Let me introduce the problem and walk through everything.... I have a ubuntu box at my work, laptop.. it was feisty, upgraded this morning, downloaded it followed the standard way from the website, no issues!

Now my fiancee's laptop... this is where the bad things happen.... So go to the upgrade manager, and looks for the distribution upgrade, and nothing... We tried the method on the console gksu "update-manager -d" and update-manager -c , to no avail.... nothing is working...

I went into the synaptics package manager, and made sure the distribution was set to the highest, I have been on IRC poking around asking, and everyone is just telling me it should be as easy as upgrade manager.. which I tried.... apt-get dist-upgrade , and all possible combinations, they just say, no packages to update..


erin@erin-laptop:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
erin@erin-laptop:~$ sudo apt-get dist-upgrade -d
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
erin@erin-laptop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
erin@erin-laptop:~$ 


I really don't want to reinstall this box, surely someone has to know what could be happening..... Thanks for any help in advance..

---

### Post by mgmiller on 2007-10-19
Since Gutsy was released, you don't want to use -d or -c.  All you should need to do is to run update manager from System>Preferences>Update Manger.  It should see the update as available and offer to install it.

Failing that, try opening Syanptic Package manger and go to Settings > Repositories.

Once there, in the first tab "Ubuntu Software" click to open the drop down window next to Download From:  and then select "Other".

From the window presented, click the "Select Best Server" button and be patient.  It will check every server in the world and find the best one for you.  after it is done it will prompt you to click the reload button in the upper left of synaptic.  let it reload all the info, then exit synaptic and rerun the Update manager.  See if it now gives the option to upgrade.

If that doesn't work, I don't know what else to try.

---

### Post by xtlosx on 2007-10-19
yup, it found a new mirror, but it didn't do anything for me.. maybe downloading the iso, burning it, and doing the upgrade that way... or after i burn the cd, set the repo to the cdrom and go from there?  What is the best way you think..


has this happened to anyone yet?

---

### Post by mgmiller on 2007-10-20
I had forgotten about using the CD for an upgrade.  After burning the iso, if you insert the CD in the already booted system (don't boot from the CD, boot normally first), I think it may just discover the newer system and offer to upgrade.  

I have 2 Ubuntu machines and my son has 1. I upgraded one of mine last night.  It went very smoothly and the only problem I had was not Ubuntu related.  My image was shifted 1 inch to the left on my monitors screen.  All I had to do was hit the "Auto adjust" button on my monitor to fix it.

I will be upgrading my other machine in the next day or 2 and if that goes well, my sons machine will follow.

---


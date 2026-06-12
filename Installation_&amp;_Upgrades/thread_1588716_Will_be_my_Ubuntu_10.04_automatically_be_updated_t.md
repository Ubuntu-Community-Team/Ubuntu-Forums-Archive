---
title: "Will be my Ubuntu 10.04 automatically be updated to 10.10 ?"
date: 2010-10-05
forum: Installation &amp; Upgrades
---

### Post by pstein on 2010-10-05
I am currently running successfully Ubuntu 10.04
When I execute an update through UpdateManager new updates will be downloaded and applied.
 
Will there be also an update to the next Ubuntu 10.10 (when final) through this channel?
 
Or are updates here only supplied for Ubuntu 10.04 bot not for any new major releases?
In this case the users must perform a "major" update manually be a new installation?
 
Peter

---

### Post by oldfred on 2010-10-05
After 10/10/10 the update screen should have a new entry at the top that says new version available do you want to update. You can either ignore it if you do not want to update or click on it to update. 

If you do update make sure you have good backups. While usually things work, sometimes there can be an issue and it is much better to have a good backup.

I prefer to do clean installs of just the system into another 20-25GB partition. (I keep 3 in rotation, old, current & next). I did do updates from about 6.06 to 9.04. But after a clean install of Karmic I liked that so much I now do clean installs. You do have to have separate /home or /data and backup any system settings and a list of installed programs, but then do not have any left over old stuff. I found some files from my 6.06 still there.

---

### Post by TBABill on 2010-10-05
+1! One of the things I think that makes upgrades to a new version problematic is all the additional software installed outside the repos. Particularly, video drivers, wireless drivers, software apps like Adobe Flash and Java. They install and work fine until you get to an update or upgrade that breaks things because the system does not take into account those externally installed apps. If you keep your machine clean of those you would probably have a more successful upgrade than someone whose requirements rely on those newer sources than what is contained in the repos.

---

### Post by plucky on 2010-10-05
!0.04 is a LTS (Long Term Support) so you won't get the offer to upgrade unless you change the release to **Normal Releases** in Software Sources > Updates > Release Upgrade box.That is because you can update from one LTS to the next LTS

Good Luck

---

### Post by Cavsfan on 2010-10-05
Or you can just enter "update-manager -d" in a terminal.
I did it yesterday and everything went so well I still cannot believe it! :P

The one thing I did was untick all of the software sources except the top 2 before hand.
I have an nVidia card and NVIDIA Driver Version: 260.19.06. And have Compiz, Cairo 
Dock, Emerald and everything just upgraded! I didn't even backup anything! I didn't loose 
any applications, documents, even cookies in Firefox! I will be sticking with that method in 
the future! :P

---

### Post by garvinrick4 on 2010-10-05
[LEFT]open terminal and copy and paste and done:
[/LEFT]

```
sudo sed -i 's/lucid/maverick/g' /etc/apt/sources.list && sudo aptitude update &&
sudo aptitude dist-upgrade 
```

---

### Post by Cavsfan on 2010-10-05
> **garvinrick4 said:**
> [LEFT]open terminal and copy and paste and done:
[/LEFT]

```
sudo sed -i 's/lucid/maverick/g' /etc/apt/sources.list && sudo aptitude update &&
sudo aptitude dist-upgrade 
```

I do not doubt that will work as you appear to have been doing this a while, but a GUI is better in my opinion.
You can see what's going on just like a regular install. It goes through steps and it took over 2 hours.
You would not see the progress via a terminal would you?

---

### Post by garvinrick4 on 2010-10-06
> **Cavsfan said:**
> I do not doubt that will work as you appear to have been doing this a while, but a GUI is better in my opinion.
You can see what's going on just like a regular install. It goes through steps and it took over 2 hours.
You would not see the progress via a terminal would you? You see everything via terminal, what you are going to download, what repository it is coming from, how big it is in size, what speed it is downloading at and what packages are being held back for time being. You will not make a partial upgrade, which is most of the time the problems you see in the Forums that say "recent upgrade borked my system". You can just about bet they upgraded from GUI and ignored partials. Also you have the option of not doing the upgrade after reading what it is going to be upgraded, will ask you yes or no.
 If you are doing a dist-upgrade it can be up towards 700 to 1000 packages or so to go out and fetch and install and every once in a while it just flat does not work. Not very often for me but once in a while. I use the same large  /home for all installs and have 10 gig partitions for the /root file systems. Doing a clean install is faster than upgrading, I keep one that is a dist-upgrade and one Wubi just because I want to see how they are working.
 But do keep a separate /home to keep all your personal info and will make your Linux just so much nicer to use. You see if you start goofing around with your config files and more and screw up your
install and you will sooner or later it only takes 30 minutes or so to be back where you were with fresh install and your /home is not affected.

---

### Post by Sef on 2010-10-06
If you do upgrade, 1) back up your files and 2) remove all proprietary drivers.

---

### Post by Dustin2128 on 2010-10-06
I'd recommend waiting a few weeks after the problems start rolling in though ;).

---

### Post by Cavsfan on 2010-10-06
> **garvinrick4 said:**
> You see everything via terminal, what you are going to download, what repository it is coming from, how big it is in size, what speed it is downloading at and what packages are being held back for time being. You will not make a partial upgrade, which is most of the time the problems you see in the Forums that say "recent upgrade borked my system". You can just about bet they upgraded from GUI and ignored partials. Also you have the option of not doing the upgrade after reading what it is going to be upgraded, will ask you yes or no.
 If you are doing a dist-upgrade it can be up towards 700 to 1000 packages or so to go out and fetch and install and every once in a while it just flat does not work. Not very often for me but once in a while. I use the same large  /home for all installs and have 10 gig partitions for the /root file systems. Doing a clean install is faster than upgrading, I keep one that is a dist-upgrade and one Wubi just because I want to see how they are working.
 But do keep a separate /home to keep all your personal info and will make your Linux just so much nicer to use. You see if you start goofing around with your config files and more and screw up your
install and you will sooner or later it only takes 30 minutes or so to be back where you were with fresh install and your /home is not affected.

I never use Update Manager except to view the updates. I have a script setup that is called "ud" that does **sudo apt-get update && sudo apt-get upgrade** 
Also have "ud2" that does **sudo apt-get dist-upgrade**. I used to just type in those commands and I know not to do a partial upgrade. I just wait until the partial goes away and then update.
I did enjoy the GUI letting me know what was being done and what step it was on though. I don't get pre-released or unsupported updates.

> **Sef said:**
> If you do upgrade, 1) back up your files and 2) remove all proprietary drivers.

I agree with you! But, this one time I didn't backup anything and just unticked everything except the top 2 software sources and the update to 10.10 RC went flawlessly!
I had to take the grub2 font command out of my /etc/default/grub as they have greatly improved the default font that comes with it!
I have everything I had on Lucid now on Maverick. But, you are absolutely right and don't try this at home.

---

### Post by jimbo99 on 2010-10-06
I have attempted the update 2 times once on a late beta and the other on the release candidate.  Both times the update completely and utterly borked my install.  After investigating some it seems that Canonical is aware of some of these problems.  They were aware of them in the beta.  I would have expected them to have resolved them in the release candidate, but they have not.

So, be weary.  Be forewarned.  I would not try the update until many weeks after it has been out.  And, as a response to your question, the answer would be, no, because you do NOT want updates to occur where you haven't made the decision in the front of your mind.

---

### Post by el_heffe on 2010-10-06
Being as I am currently using an internet connection that at *BEST* gives me 8k/s I will be holding off on the update until I go on mid-tour in January.  Personally, I couldn't care less if I lose my install, as whenever I have problems I generally reinstall the OS.  I have been trying to figure out how to fix it and have been more successful as of late with the fixing vs. the replacing.  We shall see though.

---


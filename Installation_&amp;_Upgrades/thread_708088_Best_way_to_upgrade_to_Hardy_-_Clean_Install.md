---
title: "Best way to upgrade to Hardy - Clean Install?"
date: 2008-02-26
forum: Installation &amp; Upgrades
---

### Post by MountainX on 2008-02-26
I am new to Linux. On Windows, I always did a clean install when upgrading the OS. I see many people do the same on Ubuntu.

I keep almost all of my data on a NAS appliance, so I'm not worried about my data during an OS upgrade. However, the installed apps, customizations, hardware drivers, keys, etc. represent a significant investment of time.

Is there any strategy under Linux that will minimize the time cost of an upgrade (such as from Gutsy to Hardy) and maximize the chances of the new OS running its best? 

On Windows I used a roaming profile and this really helped a lot at upgrade time.

With Ubuntu, is there a strategy that would let me avoid redoing all the work to set up the OS from scratch the first time, yet still get the good performance and stability that comes with a clean install?

I'm open to any suggestions. Under Windows, I went so far as to set up a NAS that held all my data and my complete profile. I would be willing to do something just as extensive with Ubuntu if it would prevent me from having to spend all those hours redoing work when I upgrade. I appreciate any suggestions.

---

### Post by Partyboi2 on 2008-02-26
You could use the upgrade option that comes with the update manager to upgrade your machine to the next distro, this should keep your current settings and save you doing a clean install. Personally I think a clean install is the best, but in saying that I have done a couple of upgrades via the net and have not run into much problems and have pretty much the same performance as I think as I should if I had done a clean install.

---

### Post by wolfen69 on 2008-02-26
i have heard too many things going wrong with upgrading. i realize that many people do not have problems, but then again, ive never had a problem with fresh installs. a clean install is definitely the safer way IMO, but is a little more work.

---

### Post by housam on 2008-02-26
I agree (regarding the number of posts about upgrading problems) , fresh install is better ,although you'll spend time resetting the new distro.

---

### Post by MountainX on 2008-02-26
> **housam said:**
> I agree (regarding the number of posts about upgrading problems) , fresh install is better ,although you'll spend time resetting the new distro.

Well, I will have to find a solution for the amount of time it requires to set up the new OS. I have been working for weeks to get the issues sorted out with Gutsy. There was the multimedia stuff, the fingerprint reader, the suspend/resume, the video drivers, and so many other things. There is no way I can spend that much time every time I upgrade the OS. I need a better solution - any ideas anyone?

---

### Post by housam on 2008-02-26
> **MountainX said:**
> Well, I will have to find a solution for the amount of time it requires to set up the new OS. I have been working for weeks to get the issues sorted out with Gutsy. There was the multimedia stuff, the fingerprint reader, the suspend/resume, the video drivers, and so many other things. There is no way I can spend that much time every time I upgrade the OS. I need a better solution - any ideas anyone?

Let us go for the upgrade but with a fast internet connection as it may reduce the possibility of download desturbances and hope for a safe one without troubles.any way backup your data and settings before doing any thing .

---

### Post by housam on 2008-02-26
I've an idea. if you have enough space on your HDD or have another PC , create a small partition and install ubuntu and setup only one of your favorit programs and go for the upgrade and afterwards test the effects on that particular programs . if it goes well you can apply the upgrade for your main OS.

---

### Post by Carl H on 2008-02-26
I invariably install loads of programs to try them out and then don't use them, so I always do a clean install when I'm going to a newer version of the OS. 

If you have your /home on a seperate partition and don't reformat it during your fresh install, then your application settings will be preserved - you don't have to reconfigure all your apps again. 

HTH.

---

### Post by OmahaVike on 2008-02-26
is that really true?  

for instance, the config files in my ~ directory for dapper might be different than the config files for hardy, thus not transferrable.

furthermore, there are customizations, say for ssh/apache/etc, which are not stored in /home.

i totally see what this person is referring to, as i'm facing the same dilema with a dapper -> hardy upgrade in the coming months.  EEK.

---

### Post by MountainX on 2008-02-26
With WIndows upgrades the registry can become a mess & so can other obscure parts of the OS. With Linux, do we not have the ability to more easily fix any upgrade problems so that the upgrade can be made to function just as well as a clean install?

If so, then the decision should just come down to which path takes less time. 

With Windows I eventually learned a bunch of tricks such as exporting all my IIS sites, app pools, etc. as XML and using a roaming profile. I would do a clean install, reinstall my apps, apply all my saved settings (such as IIS) and then assign my prior profile to my new user account. It was still a lot of work, but it was an organized & efficient approach. Plus I had no choice because upgrading never worked as well as a clean install.

With Ubuntu, I would imagine that a knowledgeable person could fix any upgrade issues to make the OS perform just as well as a clean install. Is that true?

---

### Post by Ardrias on 2008-02-26
As long as you keep /home on a separate partition, any option should be fine. In case upgrade fails, just do a clean install. Doesn't take long.

Also you could always boot to a live-cd of the next release before upgrading, to see if any problems you previously had to fix manually, are working from the get-go.

---

### Post by MountainX on 2008-02-26
> **Carl H said:**
> I invariably install loads of programs to try them out and then don't use them, so I always do a clean install when I'm going to a newer version of the OS. 
HTH.

Your approach is the opposite of mine. I use a virtual machine for testing new apps and doing other stuff that might be temporary or might mess up my system. I try to keep my actual system much more stable.

My computer needs to be a productivity tool. I customize it highly and I tune it to work exactly like I want it to work. Doing all that customization and tuning can be a very time consuming process. Repeating it for an upgrade is very impractical.

Some people use a generic OS install that isn't highly tweaked or highly customized. And other people don't mind experimenting with changes and doing a new set up tweaks on an OS upgrade. I suspect these are the people for whom a clean install is always preferred.

But as OmahaVike said, for many of us, we don't want to throw away the work we have done to get a system customized exactly as it needs to be.


> **Carl H said:**
> 

If you have your /home on a seperate partition and don't reformat it during your fresh install, then your application settings will be preserved - you don't have to reconfigure all your apps again. 

HTH.

I will set up my /home on a separate partition. I'm thinking about putting it on a file server (with RAID) on my LAN. Thanks for the suggestion.

---

### Post by Herman on 2008-02-26
When each version of Ubuntu is officially released, or maybe a little before time, I always notice a large number of posts for help with operating systems that have failed because people have tried to upgrade and things have not gone well.
When we see a lot of problems of a particular type, it's worth remembering that there are quite a lot of Ubuntu users now, and the number of reported problems could be small in proportion to the number of probable successful outcomes. 
People don't usually type in to Ubuntu Web Forums to report a successful outcome, so it can seem as if a lot of people have trouble upgrading when that may not be entirely true.
I have read that upgrading should be no problem if we have used only software from the official Ubuntu repositories, and probably that would be correct.

Nevertheless I'm another one who prefers to install the new operating system beside the old one and transfer my files across to the new /home/username directory rather than use the upgrade method. 
That gives me two Ubuntu installations and I usually don't bother deleting the old one as I have plenty of hard drive space and the operating system itself actually only uses about 1.8 GB anyway.

The new installation will mount the existing installation of Ubuntu automatically, and  when we know what we are doing it's very quick and easy to transfer the files that contain the important settings. Some settings need to be made again, but that doesn't take long. 
In Ubuntu that can be done a lot faster than in Windows. We don't need to keep rebooting all the time and most of the software we need is all in the one CD, instead of ten or more different ones.
There are a few files in the /home/username folder of the old installation to be copied to the new installation and most of it is done in a matter of a few minutes. Most of those files are in invisible files in your /home/username directory, so just click 'View'-->'Show Hidden Files'. Once you know what files to look for and copy across it's really simple.
It might take a little while to re-download new software, depending on the amount of software you need and your internet connection speed. It probably doesn't take any longer than upgrading though, and may even be quicker, because the new software for the upgrade comes through the internet too.

I don't like the idea of having /home on a separate partition, I prefer to have everything in one / (root) partition. That way it's easier to multi boot. 
As I already mentioned, the operating system files only need about 1.8 GB of hard disk space. When you divide things up into separate partitions you are fencing yourself in, and stopping things from being able to expand and contract as needed. You lose flexibility. You need to allow some extra room in each partition to allow for added software or files, but how much? The extra room you need to allow for that is less then the amount of space you need for another copy of Ubuntu.

I had an experience following the release of Gutsy Gibbon when I decided to make a presentation CD for some people I wanted to impress at work who use Windows.  I made a presentation CD apparently successfully in Gutsy Gibbon but luckily I tested it first in a Windows OS to make sure it would work and it didn't.  The CD was invisible in Windows. It took me a while to find out what I was doing wrong. Actually I was doing everything correctly, but the CD writing software had changed. When I booted into my old Feisty installation and made the CD it worked perfectly.  I was certainly glad that time that I still had my old Feisty installation to fall back on when the new release failed to perform as expected on that particular occasion.

I think it's best to play it safe and install the new Ubuntu beside the old one and transfer the files and settings at my leisure, and have two Ubuntu installations instead of only one.

Regards, Herman  :)

---

### Post by Pumalite on 2008-02-26
I maintain a Feisty, 2 Gutsy's: one 32 bit and another 64 bit, and 2 Hardy Heron's: one a clean install and another that I got from a Gutsy upgrade with the upgrade manager to test the upgrade. No problems with the upgrade.

---


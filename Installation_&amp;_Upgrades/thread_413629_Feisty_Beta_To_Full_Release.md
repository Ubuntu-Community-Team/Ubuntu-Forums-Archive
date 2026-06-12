---
title: "Feisty Beta To Full Release?"
date: 2007-04-19
forum: Installation &amp; Upgrades
---

### Post by residualbit on 2007-04-19
i know the final release of ubuntu feisty 7.04 came out today, and i have been running the beta for about a month or so. i noticed that i haven't gotten any updates for beta in about the last three days or so, maybe more. anyway, my question is...do i have the full release? how do i check? i get nothing from update manager, apt-get update, or apt-get upgrade...thanks for any help!

---

### Post by jiaz1 on 2007-04-19
Same question here.

I ran update but got no notice.

---

### Post by Podex on 2007-04-19
I think it is normal since there were no more changes since April 15th

---

### Post by Spinalcracker on 2007-04-19
I have been wondering the same thing.  If you get all the updates is that as good as a fresh final install?  I have read where it is the same and also where it is not the same.

---

### Post by Podex on 2007-04-19
I didn't do a fresh final install for Edgy either at the time it came out and all worked out fine for me ;). I've been running Feisty since the beta.

---

### Post by thinkdreams on 2007-04-19
I too have a similar question. It will be interesting to find out. I suspect that if we're all running the beta version, the repos are the same as the full release, and we already have the latest, but hopefully someone in the know will post what they know.

:)

---

### Post by Phyrexicaid on 2007-04-19
I too have the Feisty beta running.  My question is this: Why is the manual command line upgrade *not* recommended.

I was a new Ubuntu user, downloaded 6.10 and immediately searched on how to upgrade.  I followed the following steps:
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

Flawless upgrade to 7.04 beta.  Now, every once in a while I'd repeat the process (whenever apt informed me that packages were being kept back).  I've never used the graphical installer or upgrader, I found the command line apt perfect (and quicker).

Now 8 packages are being kept back, and if I choose to run dist-upgrade it's going to install kernel *.20-15.  Should I carry on with the method I've been using (blissfully unaware that it's not recommended) or should I switch to the graphical installer?

---

### Post by residualbit on 2007-04-19
i guess i will feel better if i start seeing updates soon...i know during the end of the beta i was getting well over 25 a day...i guess we'll see what happens

---

### Post by Podex on 2007-04-19
It doesn't really make much difference if you do it graphically or in a terminal. I prefer the terminal too, but I often use Synaptic and Add/Remove as well.
You should get the new kernel. But it is strange that it wouldn't just upgrade normally (sudo apt-get upgrade). My kernel got updated somewhere last week.

---

### Post by Drunner611 on 2007-04-19
> **nkirk1 said:**
> i guess i will feel better if i start seeing updates soon...i know during the end of the beta i was getting well over 25 a day...i guess we'll see what happens

I know what you mean, I haven't had an update in 3 days, lol.  Makes me nervous.

---

### Post by residualbit on 2007-04-19
so if the kernel got upgraded is it the final version? i just would like to know one way or the other. does it say somewhere if i am running beta or stable(full)?

---

### Post by residualbit on 2007-04-19
i expected to turn my computer on today, run update manager and be able to click on the distribution upgrade like all of the pictures on the website. didnt happen. i don't consider this to be a problem, i really haven't had any with ubuntu...just more of an inconvenience

---

### Post by dragnazz5.0 on 2007-04-19
ive been wondering the same thing as you guys.  apt-get dist-upgrade does nothing so i guess its the full version with all the updates.

---

### Post by socomoddjob on 2007-04-19
> **Drunner611 said:**
> I know what you mean, I haven't had an update in 3 days, lol.  Makes me nervous.

Im in the same boat as you.

Im assuming what i have here is the final product and until im told otherwise im not messing with anything.

---

### Post by dspari1 on 2007-04-19
I'm in the same boat; I go to update to find out that there isn't anything to upgrade. I somehow doubt that we've been running the non-beta version for the last 3 days. Anybody here try the DVD or Alternate CD?

---

### Post by duchamp.fitz on 2007-04-19
I hope it's a big boat.

---

### Post by ckkoba on 2007-04-19
For the Fiesty Beta Server users, I've been having the same problem where it wouldn't update.  
I tried: 
```
sudo apt-get update
```
then 
```
sudo apt-get upgrade
```
and it was saying that 3 packages were held back.  

But it seems if you do a ```
sudo apt-get dist-upgrade
```, it goes ahead and updates those 3 packages that are held back. (For me, the packages were linux-image-server linux-server & netbase)

Hopefully that helps for those people upgrading from Server Beta to Final!  (Oh and yeah, this is my first time upgrading so please don't lambast me!)

---

### Post by midnightracer on 2007-04-19
I guess the boat is getting bigger. I came to this forum with the same question in hand.:confused:

---

### Post by jorgerosa on 2007-04-19
**Boat! Wait for me!... ** How can i know if im running beta or the full ubuntu version? [-o<  Thx.

---

### Post by residualbit on 2007-04-19
well im glad im not the only one in this huge boat...we should see about getting another one, or at least a bigger boat...any official word yet?

---

### Post by residualbit on 2007-04-19
great, now it won't even let me check for updates. i get this:


nate@nate-laptop:~$ sudo apt-get update
E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory

anyone else having this problem?

---

### Post by residualbit on 2007-04-19
also, it throughs me this, when i use the regular update manager rather then the console:


Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences

---

### Post by init6 on 2007-04-19
postcount++


Interested to know the answer to this myself.

---

### Post by Podex on 2007-04-19
As I said earlier, there have not been any changes since 15th of April. If you look at the [releases page]("http://releases.ubuntu.com/feisty/") you can see that the images are dated 15-Apr-2007. So if you were already running Feisty before today it is perfectly normal not to get any updates. I'm pretty sure you all have the "final version".

Also nkirk1 just do 
```
sudo rm /var/lib/apt/lists/lock
```
and try again. You won't get any updates though, cause there are none. (Unless you have different repositories enabled than me of course)

---

### Post by tubasoldier on 2007-04-19
Yes, you are running the final release. The stop updating packages a few days before the actual release so they can make the iso files and get it ready for downloading.

---

### Post by blamecanada on 2007-04-19
Ok I was curious about this today too, I wasn't sure if there were no updates or if all the Ubuntu servers were just getting hit too hard. 

BTW what does it mean when you update and when if checks the repo it says "Hit" instead of "Done"

---

### Post by jimz on 2007-04-19
This may be the wrong place for this ...but if I have been running fiesty for a month and gotton all updates and upgrades why is dhelp still broken and no php5-mysqli extension?  Is there no mysqli support in the final version?:confused:

---

### Post by thinkdreams on 2007-04-20
After a quick search of the Launchpad forums, I found the answer to the question for everyone in this "boat" (to continue the boat metaphor).

[https://answers.launchpad.net/ubuntu/+question/5268](https://answers.launchpad.net/ubuntu/+question/5268)

It is not necessary to perform any sort of upgrade from beta to full. If you have done regular updates, we all should have the final version without having to do anything.

---

### Post by sethvath on 2007-04-20
To those wondering about their ubuntu version, do "lsb_release -a" in terminal. Everyone on beta should see "development branch" because there's no updates since april 15.

---

### Post by socomoddjob on 2007-04-20
Nice, i think this is my stop....im getting off this vessel.

---

### Post by dspari1 on 2007-04-20
> **sethvath said:**
> To those wondering about their ubuntu version, do "lsb_release -a" in terminal. Everyone on beta should see "development branch" because there's no updates since april 15.

mine says:
No LSB Modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 7.04
Release:        7.04
Codename:       feisty


I don't see where it says "development branch"

---

### Post by drewcoll on 2007-04-21
In the same boat... I'll feel better when I get some kind of update...

I have to say though that Fiesty is a great improvement.  My computer has been more stable on this than any other release.

---

### Post by old_geekster on 2007-04-21
I didn't read every post, so I appologize if this has been said previously.

If you have been running Feisty Beta and downloaded the updates, you have the "Final" version already.  It should be Kernel 2.6.20.15 generic.  You can run this command in the Terminal: uname -a or uname -r.

I had 15 updates last evening.  I couldn't receive any on the 19th because all of the servers were swamped.

---


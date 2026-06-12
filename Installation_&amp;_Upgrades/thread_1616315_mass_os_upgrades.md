---
title: "mass os upgrades"
date: 2010-11-08
forum: Installation &amp; Upgrades
---

### Post by Paper Pusher on 2010-11-08
I am the reluctant administrator of a house with a dozen PCs, all connected to our 100mb/1gb LAN.  
All boot some flavor of Ubuntu (DTE, NBR, Studio, 32-bit or 64-bit depending on the capabilities of the CPU).  Most also run some flavor of Microsoft Windows 32 bit. 
The Ubuntu upgrades every six months are driving me crazy!  Is the 2-year LTS for me?  What's the best way to do upgrades of 12 machines?

---

### Post by zvacet on 2010-11-08
In your case I will choose LTS,because it is 3 years support.For updating comps see [https://help.ubuntu.com/community/Apt-Cacher-Server](https://help.ubuntu.com/community/Apt-Cacher-Server)

---

### Post by TBABill on 2010-11-08
+1 for LTS. The 3 year support cycle is great if you just want to install it and let them run without constant installs or upgrades.

---

### Post by Grenage on 2010-11-08
Absolutely use LTS in your case.

---

### Post by Paper Pusher on 2010-11-08
Thank you for your unanimous endorsement of LTS.  How then do I do the upgrades when the LTS expires?  I understand that I have one year to complete this every two years.  

Is there also unanimous endorsement of [https://help.ubuntu.com/community/Apt-Cacher-Server?](https://help.ubuntu.com/community/Apt-Cacher-Server?)
Thank you zvacet for the pointer.

Where is the best documentation for it?  It seems rather daunting and it doesn't work for all LTS releases according to the link.

---

### Post by Paper Pusher on 2010-11-08
For additional information on "my" installation, the census is:
Ubuntu [there is no other Linux distro]
DTE-32 x3
NBR-32 X1
DTE-64 X7
Studio-64 x1
=12

For MS Windows, it is:
XP Pro-32 x1
XP Home-32 x2
Vista-32 x1
XP MCE-32 X1
S7SE-32 X2
=7

All 7 MSW computers dual-boot Ubuntu.
5 computers boot Ubuntu only.

---

### Post by zvacet on 2010-11-08
> How then do I do the upgrades when the LTS expires?

You can always upgrade from one LTS to another. ):P

---

### Post by Paper Pusher on 2010-11-08
Is it best to upgrade from the update manager or from the CD?

---

### Post by Paper Pusher on 2010-11-08
The reason for my OP was to increase SA productivity in an environment of a  dozen PCs. 

As I review this thread, switching to LTS distributions increases my productivity by a factor of four because I would upgrade my PCs every two yeas instead of every six months.  Am I understanding this correctly?

Switching to [https://help.ubuntu.com/community/Apt-Cacher-Server](https://help.ubuntu.com/community/Apt-Cacher-Server) instead of direct download lowers the load on Canonical's Ubuntu distribution computers. I download UDTE-64 once and then redistribute it to my seven 64-bit machines. Am I understanding this correctly?

What's more, I am already reducing Ubuntu distribution by a factor of four through my switch to LTS. Local caching would increase my workload because I would have to set up the caching infrastructure and maintain it across LTS distributions.  The link provides details.  I'll leave setting up distro caching to those more experienced than me and stick to LTS.

---

### Post by Grenage on 2010-11-09
For a dozen PCs, I probably wouldn't bother with a cached apt server, either.

---

### Post by Paper Pusher on 2010-11-09
Thank you very much for your generous advice.  I have reviewed this thread, its links, and this forum.  Here is my new SA policy:
 
1. current Ubuntu LTS only.  I'll upgrade all 12 PCs to 10.4 LTS.
2. next upgrade is June 2012.  This gives 12.4 LTS time to settle.
3. upgrades via update manager.
4. start the upgrades with a non-vital PC so I can gain experience with 12.4.
5. rinse and repeat every two years. ++LTS ++LTS.

Any comments?

---

### Post by Grenage on 2010-11-09
Sounds good.  If the users aren't admins, then you might want to set update manager to not check for updates.  That way, you can go round and manually process them.

If they are admins, you don't have to worry about that.

---

### Post by Paper Pusher on 2010-11-09
How much skill does it take to be an admin?
update manager looks as easy as Microsoft Windows updates.

---

### Post by Grenage on 2010-11-09
If the user has admin rights (via prompt or sudo), they can do whatever they like - install software, delete system files, et cetera.

Only you can decide whether or not that is a problem.

---

### Post by Paper Pusher on 2010-11-09
my users do NOT have sudo rights.

---

### Post by Grenage on 2010-11-09
Ok then; I'm assuming then, that they cannot install updates themselves manually - but they could be installed automatically.

---

### Post by Paper Pusher on 2010-11-09
Thank you for explaining this.
How do I set up automatic updates?

---

### Post by Paper Pusher on 2010-11-09
I just changed the settings in update manager to show LTS upgrades only and to install security updates without confirmation.  Is that what you mean?

---

### Post by Grenage on 2010-11-09
The option should be listed as *'Install security updates without confirmation'*, that's correct.

---

### Post by Paper Pusher on 2010-11-11
What I described above worked with one PC, but does not work with my personal desktop and laptop.  Both are running U9.10DTE-64.

Update Manager does not prompt me to upgrade to 10.4LTS. Why?

---

### Post by Grenage on 2010-11-11
That's odd, you don't get the option after pressing *update*?  You can always push it through via the terminal:

[https://help.ubuntu.com/community/LucidUpgrades](https://help.ubuntu.com/community/LucidUpgrades)

---

### Post by gordintoronto on 2010-11-11
If you do that many upgrades online, there's a good chance that your internet connection will drop during one of the upgrades, which is a total disaster. You can upgrade using an "alternate CD," which eliminates this risk.

Upgrading itself seems to be error-prone. I have always done a new install, which takes a bit longer. Having root (/), swap and home partitions helps a lot, but you also have to record what applications are installed, 
(dpkg --get-selections "*" > Desktop/applications)
then re-install them:
sudo apt-get update
sudo dpkg --set-selections < Desktop/applications
sudo apt-get -u dselect-upgrade

I always go through the "applications" text file and remove any applications I no longer need...

---

### Post by Paper Pusher on 2010-11-12
Toronto,

Thanks for the insightful message.  I had heard that online updates are problematic, but I could find no posts verifying that. Your post is the first.  Thank you.  

You use the alternate installer.  Its claim to fame is that it's text-based, not graphical.  Why?  What's wrong with the graphical installer? 

You reinstall all applications, but do you protect user data?

---

### Post by gordintoronto on 2010-11-13
> **Paper Pusher said:**
> Toronto,

You use the alternate installer.  Its claim to fame is that it's text-based, not graphical.  Why?  What's wrong with the graphical installer? 

You reinstall all applications, but do you protect user data?

Actually, I don't use the Alternate installer. It's my understanding that it can do an upgrade -- but I have never done an upgrade.

Yes, I protect user data in two ways: I have a separate /home partition, which I am very careful to preserve when I install the new version. But just in case, I back it up to an external drive first. (Or to DVD. Or both.)

I actually have multiple hard drives which I swap in and out of my external drive. Sometimes, I will try a new version (such as Lubuntu) by installing it on the external drive. For something like that, even an old 10 GB drive is useful.

---

### Post by i.r.id10t on 2010-11-13
> **Grenage said:**
> For a dozen PCs, I probably wouldn't bother with a cached apt server, either.

I certainly would.  Or rather, I have.  And believe me, it is nice seeing all those machines getting updates at 100mb speed.

---


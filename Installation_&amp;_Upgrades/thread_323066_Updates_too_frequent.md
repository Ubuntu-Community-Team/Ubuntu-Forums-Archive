---
title: "Updates too frequent"
date: 2006-12-21
forum: Installation &amp; Upgrades
---

### Post by RichLouth on 2006-12-21
Hi everyone,

Is it just me or am I the only one that thinks that Ubuntu asks to update itself too frequently?

It seems like every week the update icon pops up and doesn't go away until I allow it to download MB's of data. Today I've had to update Open Office for the second time this month (both of which were of considerable size). I have a broadband connection but it's one that has a download limit. I can't afford to download every single update but at the same time I don't appreciate the way the update icon hangs around until you've downloaded everything.

Is there any way of setting synaptic so that it only updates essential things like security fixes? Surely those are the only kind of updates that are really important.

Thanks

---

### Post by dannyboy79 on 2006-12-21
well of course there is. haven't you tried opening up synaptic and looking at the preferences tab??? it should be in there. there is also another spot you can check but I am not in front of my box right now so I can't tell ya, i'll repost when I get home. it basically is a setting that either upgrades to the latest and greatest, or only upgrades security, or only upgrades blah blah  etc etc. but for now, open synaptic, then within one of the pull downs at the top, there should be pref's, then within there, you'll see a place that talks about updating and upgrading. good luck

---

### Post by RichLouth on 2006-12-21
Thanks bud.

---

### Post by wpshooter on 2006-12-21
Here's my recommendation.

Apply all available updates as soon as possible.  I think this will give you a better chance of have a good smooth running O/S.

Get an unlimited DSL connection such as Verizon's $17.99 per month deal.

Good luck.

---

### Post by dannyboy79 on 2006-12-21
> **wpshooter said:**
> Here's my recommendation.

Apply all available updates as soon as possible.  I think this will give you a better chance of have a good smooth running O/S.

Get an unlimited DSL connection such as Verizon's $17.99 per month deal.

Good luck.


no true, this all depends on what he has added to his repos. if he uncommented the backport, he could update something that could cause headaches for a novice user. he's already telling you that he only wants security updates.

---

### Post by wpshooter on 2006-12-21
IMO, the repositories should be controlled by marking and unmarking parameters in Software properties or Synaptic and NOT by editing/uncommenting lines in a configuration file.  I think if he would practice this, he would have no problems, I never have.

---

### Post by dannyboy79 on 2006-12-21
> **wpshooter said:**
> IMO, the repositories should be controlled by marking and unmarking parameters in Software properties or Synaptic and NOT by editing/uncommenting lines in a configuration file.  I think if he would practice this, he would have no problems, I never have.

ok, have it your way, if he "marked the backport box in Software properties or Synaptic" he would still get updates to packages that could cause headaches. just so you know, using the GUI (marking and unmarking parameters in Software properties or Synaptic) has no different effect than commenting and uncommenting your /etc/apt/sources.list file. also, he isn't saying he is having problems, he is simply saying that he would only like to get security updates instead of every update under the sun. some people are on dial-up and don't have the resources to update every other day as he is describing. You should also know more about what you are talking about before you say stuff and also don't try to tell people how to do stuff, there are always more than one way to skin a cat.

---

### Post by TheWizzard on 2006-12-21
> **wpshooter said:**
> IMO, the repositories should be controlled by marking and unmarking parameters in Software properties or Synaptic and NOT by editing/uncommenting lines in a configuration file.  I think if he would practice this, he would have no problems, I never have.
this is a very strange statement. you basically discourage people to understand how linux works. 
i'm very happy with the improvements in gui's in linux because this makes it easier for new users, but i'd also encourage people to understand their system. people who know how the system works under the hood are needed to help other people with solving problems.

---

### Post by dannyboy79 on 2006-12-21
> **TheWizzard said:**
> this is a very strange statement. you basically discourage people to understand how linux works. 
i'm very happy with the improvements in gui's in linux because this makes it easier for new users, but i'd also encourage people to understand their system. people who know how the system works under the hood are needed to help other people with solving problems.

thank you for the support thewizzard. 

also, to RichLouth, you can also go under system, admin, the software properties and change the amount of time that your system will check for updates. mine is at daily due to having broadband, but there is also weekly, monthly etc etc. so the 2 places are what I just stated and also, unde system, admin, synaptic, then under settings, then prefs, then you can change whether you want the system to ask you to upgrade, do a smart upgrade, or default upgrade. then on another tab. you can set youre distro so that is always has the highest cversion possible, or to prefer the installed version or you can prefer the version from a certain repo, check it out. good luck. remember though, this is lts, long term support so you're probably ok saying ok to all the updates and your system will be fine, it just gets messy (i should say it can get messy) when you enable the backport repo, what this does is allow software that is only tested for feisty or other versions past dapper so that you can install using apt-get or synaptic onto dapper which can cause dependencies issues but most of the time they aren't serious.. good luck. like the thewizzard says, don't be afraid to roam around, learn about waht files do what behind the scenes, you'll learn much faster if you dive into the terminal and don't count on only the guis.

---

### Post by wpshooter on 2006-12-21
> **TheWizzard said:**
> this is a very strange statement. you basically discourage people to understand how linux works. 
i'm very happy with the improvements in gui's in linux because this makes it easier for new users, but i'd also encourage people to understand their system. people who know how the system works under the hood are needed to help other people with solving problems.

Not if the properly GUI tools would be written to perform these tasks and eliminate the possibility of say an accidental typing mistake causing problems where this could NOT happen when using a GUI tool.

---

### Post by wpshooter on 2006-12-21
> **dannyboy79 said:**
> ok, have it your way, if he "marked the backport box in Software properties or Synaptic" he would still get updates to packages that could cause headaches. just so you know, using the GUI (marking and unmarking parameters in Software properties or Synaptic) has no different effect than commenting and uncommenting your /etc/apt/sources.list file. also, he isn't saying he is having problems, he is simply saying that he would only like to get security updates instead of every update under the sun. some people are on dial-up and don't have the resources to update every other day as he is describing. You should also know more about what you are talking about before you say stuff and also don't try to tell people how to do stuff, there are always more than one way to skin a cat.

He may not now, but if he goes into that file and makes a typing mistake or accidentally deletes needed information, and then does not know what he did wrong and/or how to fix it.

I don't need a system that I know every in and out of, I need a system which is reliable and that can get work done not make me a Linux O/S guru.  I don't see that as the purpose of using a computer and/or an O/S.

---

### Post by dannyboy79 on 2006-12-22
> **wpshooter said:**
> He may not now, but if he goes into that file and makes a typing mistake or accidentally deletes needed information, and then does not know what he did wrong and/or how to fix it.

I don't need a system that I know every in and out of, I need a system which is reliable and that can get work done not make me a Linux O/S guru.  I don't see that as the purpose of using a computer and/or an O/S.


agreed, that's why I always suggest to people to make a backup of a file they are manually editing. Also, i never once said you should become a guru. my point is that if you don't learn how the system works in and out you're dependent on others for help instead of being able to troubleshoot it yourself. just because only uses the gui's to make changes to his/her system doesn't mean nothing can go wrong, hence why it's beneficial to learn about your os and not simply "use" it.

---

### Post by MrHorus on 2006-12-22
> **RichLouth said:**
> Surely those are the only kind of updates that are really important.


Personally I prefare software that is stable, efficient and up to date - that's 'important' to me.

---

### Post by TheWizzard on 2006-12-22
> **wpshooter said:**
> Not if the properly GUI tools would be written to perform these tasks and eliminate the possibility of say an accidental typing mistake causing problems where this could NOT happen when using a GUI tool.

typo's are indeed a disadvantage of using the command line and edditing manually. however, there are also benefits of using the latter. 1) works on both gnome and kde, 2) works on different releases, and 3) is more accurate then 'click this and then that'.

basically, in many aspects it is more user friendly. see also: 
[http://ubuntuforums.org/showthread.php?t=59334](http://ubuntuforums.org/showthread.php?t=59334)

---

### Post by RichLouth on 2006-12-23
It's sorted now. I selected the check box that says security updates only.

Under: System -> Administration -> Synaptic Package Manager -> Settings -> Repositories -> Internet Updates.

I didn't think about uncommenting the appropriate bar in the sources.list. I thought that might restrict me in what I could install from synaptic.

wpshooter: Can't get an American isp I'm in England;)

I have BTBroadband. I totally recommend that you **never** go with BT for anything. Download anything significant one day and the next they cap your download to something similar to a 56k connection. I have to sit and watch images download](*,) 

Thanks for the support:)

---

### Post by dannyboy79 on 2006-12-25
> **RichLouth said:**
> I didn't think about uncommenting the appropriate bar in the sources.list. I thought that might restrict me in what I could install from synaptic.
 
i think you may be misinformed! what do you mean that uif you uncomment a line in your sources.list that'll restrict what you can get in synaptic, it's actually just the opposite. the more you have uncommented in your sources.list, the more programs you;ll have available to you! all the sources.list is is a list of servers that contain .deb packages and when when you do a update through synaptic or sudo aptitude update or sudo apt-get update, the sources.list is looked at by the system and the system goes out and reads the available packages from each one of the servers (this is an example:  deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse) and then your packages available to you thru synaptic will be updated so you can see what you can all download. this is a very basic explaination of what happens but I believe it to be true. if I am wrong, someone please correct me.

---


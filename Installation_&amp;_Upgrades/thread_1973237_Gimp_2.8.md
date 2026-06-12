---
title: "Gimp 2.8"
date: 2012-05-04
forum: Installation &amp; Upgrades
---

### Post by jimbo99 on 2012-05-04
Gimp 2.8 would never install on my system.  

Via Synaptic there are no unmet dependencies and no broken packages.  

I fear the suggestions listed below will result in seriously disabling my system.  I'm not inclined to perform those choices suggested in the output (see below) just for Gimp 2.8.

We can't encourage others to use Linux if we are going to have these types of issue, issues that should not exist.

Gimp 2.8 install attempt, via the ott-kesselgu PPA repository, results in getting unmet dependencies.

In order to resolve these it was recommended that the ppa-purge command be installed and issued.  You can see the command below.  Can anyone explain what's happening and the route I should take.  

I'm purposefully not upgrading to Ubuntu 12.04 because I actually use my computer and what I do is important enough to not be saddled with weeks of re-installation and reconfiguration.  (Note:  yes, I have a separate home partition (drive) for my user stuff, but I actually use my computer and do not just tinker, so spending weeks re-installing and putting things back in order isn't something I'm interested in--and any suggestions about compiling it will be met with great disdain by me).


I had to use pastebin because THIS WEBSITE thinks there are 12 images embedded in that output and won't post.  So, forgive me and follow the link to see what I'm asking.

****** ***** *********** ******

[http://pastebin.com/eWJbpvzH](http://pastebin.com/eWJbpvzH)

****** ***** *********** ******


The solution seems HUGELY dangerous.  I have a system I use.  I know many of you are in the same boat.  You use your system.

The first entry is acroread.  No biggy. I can resolve that at any time.

But some of those others are seriously important, such as the ia32 libs.

And the list is long.

Any help would be appreciated.  Thanks in advance.

---

### Post by fooman on 2012-05-04
> **jimbo99 said:**
> 
We can't encourage others to use Linux if we are going to have these types of issue, issues that should not exist.


sorry i understand your frustration,  but at the top of the otto-kesselgulasch PPA repository page,  it clearly states:

*CAUTION!*
 *This PPA could break your installed OS. There are dependency issues  especially for Oneiric (11.10). Only use it if you know what you do! I'm  working with others on a stable and reliable solution.*
 *Regards*


i also tried to install via this method earlier today,  and although gimp seemed to work,  i don't think it was working quite right.... i used the following command to purge the PPA:


```
sudo ppa-purge -p gimp otto-kesselgulasch
```


all went well with the purge,  it did not remove the long list of packages that your log is showing.

---

### Post by Tanker Bob on 2012-05-04
I did the same thing as fooman. Gimp 2.8 had a number of broken dependencies so failed to install with Synaptic in Precise. So, I used ppa-purge and it automatically reverted me to Gimp 2.6.12 with no problems. I wonder why Gimp 2.8 installed in your system with no unmet dependencies. Synaptic usually does a good job in catching those.

---


---
title: "thunderbird"
date: 2007-05-25
forum: Installation &amp; Upgrades
---

### Post by pepitosir on 2007-05-25
I download the .gz file, I extract it and now?????? I cant install it
I try to install from SPM , it apears in my menu, but I cant open thunderbird.
How I will do it?

---

### Post by Big Ed on 2007-05-25
> **pepitosir said:**
> I download the .gz file, I extract it and now?????? I cant install it
I try to install from SPM , it apears in my menu, but I cant open thunderbird.
How I will do it?

Your trying to do this the hard way.  Ubuntu has a very nice gui application for installing software.  In the menu at the top, go to "System - Administration - Synaptic Package Manager".  You will be prompted for your password to ensure that you are the admin user on the machine.  In the bottom right corner, click on "Status".  In the top left corner, click on "Reload".  In the main window, scroll down to "Mozilla-Thunderbird", right click and select "Mark for installation".  At the top left, click on "Apply".  Accept any dependencies that come up and you should be good.

If this is your first time using Ubuntu, read up on how to enable the Multiverse, Universe and restricted repositories.  You don't need them to get Thunderbird, but there is a lot of good software in them.

Ed

---

### Post by ivesjd on 2007-05-31
what if you want thunderbird 2? since they still only have 1.5 in the repos?

---

### Post by srt4play on 2007-05-31
I think having a newer version is a separate issue from the one the OP is having.  It seems like thunderbird isn't starting at all and he thought downloading it from the mozilla website could fix it.

OP - try running thunderbird from a terminal and see if there are any error messages.

---

### Post by Big Ed on 2007-05-31
I believe that the OP was trying to install Thunderbird since it is not installed by default.  And he was trying to do it the hard way.  But it is true that if you want the latest version, then you have to either get the .gz file and install it yourself, or find a .deb file from some other debian derived distribution and give that a try.

The other solution is that Thunderbird v2.x _will_ show up in the backports once they become active.  However, I don't know when backports will start being populated.  If I want v2.x of Thunderbird, I'll wait for backports.

HTH,
Ed

---

### Post by srt4play on 2007-05-31
Actually he did do it the easy way, in Synaptic:

> I try to install from SPM , it apears in my menu, but I cant open thunderbird

Downloading the source and extracting it won't put an entry in the menus.

---

### Post by Big Ed on 2007-05-31
> **pepitosir said:**
> I download the .gz file, I extract it and now?????? I cant install it
I try to install from SPM , it apears in my menu, but I cant open thunderbird.
How I will do it?

Yes, but he tried the .gz first. That may have put in something that is causing the Synaptic installed version to fail to run.  Maybe some screwed up dependancy. 

Isn't there a 'clear' or 'clean' command in the .gz type installs that will take him back to the beginning so the Synaptic might work?

'man apt-get' mentions the source and build-dep commands.  They look like they might be useful in the case, but I've never played with them so I can't give any advice in this area.  But that looks like a good place to explore.

Ed

---


---
title: "Upgrading Ubuntu eee"
date: 2008-11-09
forum: Installation &amp; Upgrades
---

### Post by Max Ernst on 2008-11-09
I've installed Ubuntu eee 8.04.1, which is pretty much Ubuntu the most significant difference being the custom kernel complied by Adam McDaniel, (see [http://www.array.org/ubuntu/index.html]("http://www.array.org/ubuntu/index.html")).

Since the release of Ubuntu 8.10 the update manager has been notifying me that a new version is available, if I select update now, it informs me that it can only do a partial upgrade and asks if I want to proceed.

I assume it can only do a partial upgrade because I have removed myself from Ubuntu's kernel updates as per Adam's instruction (although not recommendation). I suspect reverting to the original kernel will kill all my drivers, severing me from the net and crippling the update process...

...so what is the best way to update?

If I switched repositories and installed Adam's intrepid kernel at the same time updating everything else I have installed through the Ubuntu intrepid repository, what would happen?

---

### Post by betes on 2008-11-09
From the ubuntu eee documentation:

[http://www.ubuntu-eee.com/wiki/index.php5?title=User_Guides](http://www.ubuntu-eee.com/wiki/index.php5?title=User_Guides)

See the article on your problem:

[http://www.ubuntu-eee.com/wiki/index.php5?title=Fix_the_problem_with_upgrading_and_installing_software_in_Ubuntu_Eee_8.04.1](http://www.ubuntu-eee.com/wiki/index.php5?title=Fix_the_problem_with_upgrading_and_installing_software_in_Ubuntu_Eee_8.04.1)


You have to enter these two commands in the teminal:

sudo rm /var/lib/apt/lists/*
sudo rm -R /var/lib/apt/lists/partial/*


It might give you and error message after one or both, but it should fix the problem.

---

### Post by Max Ernst on 2008-11-11
The wiki article *Fix the problem with upgrading and installing software in Ubuntu Eee 8.04.1* redirects to Jon Ramvi's blog for a description of that problem where he says,

> there was a problem with the first thousand downloaded versions, where you couldn’t upgrade nor install software. Here’s the fix. 

but I can install and update through the hardy repositories just fine, so I don't think I have this problem. 

I might be a noob, but I'm not dumb enough to rm something without knowing what it is, could you tell me exactly what those two commands are supposed to do?

---

### Post by betes on 2008-11-12
ME-

Sorry for the wrong advice.  I was having the updating problem recently so I just quickly read your post and assumed it was about the same problem.  The rm commands are not malicious, they just delete temporary information that the apt-get program stores about your packages, but you are right to ask before rm-ing something.

So now to answer your real question, ubuntu eee is not ready to be upgraded to intrepid (8.10) yet.  Check the ubuntu eee twitter page for confirmation:

[http://twitter.com/ubuntueee](http://twitter.com/ubuntueee)  (see the nov 10th entry).

I think the developer(s?) is preparing a new version but it will be released under a different name because they aren't allowed to use the ubuntu name anymore.  

Again, sorry for the mis-diagnosis.

---

### Post by Max Ernst on 2008-11-12
Betes,

It's all good. I am aware that Ubuntu eee is not ready for upgrade, I was more positing a move from Ubuntu eee 8.04.1 to vanilla Ubuntu 8.10 without re-installation. it seems the option is available, or at least the update manager is announcing ubuntu 8.10 with a little upgrade button next to it. But if I choose the button, it says it can only do a partial upgrade. My guess was this was caused by the differences in kernel. I could put the vanilla ubuntu 8.04 kernel back in place, but that would kill the driver modules and I'd loose network connectivity, and then not be able to upgrade to 8.10 using update manager. 

in the end I was wondering what would happen if I did something different - going into synaptic and installing my current kernel, replacing it with adam's intrepid kernel and updating all my installed software to the intrepid versions. Since I'm new to linux I really have no idea at this stage how updating etc really works, so I was just wondering what would happen if I tried this, it might be a really dumb idea. 

From the launchpad answer it is uncertain that ubuntu eee 8.04.1 users will be able to upgrade to ubuntu eee 8.10 when it is out without re-installation.

---


---
title: "Problems updating UE Ubuntu - Partial Update only?"
date: 2012-10-04
forum: Installation &amp; Upgrades
---

### Post by patriot56 on 2012-10-04
Hello forum
I recently had an issue with my automatic updates.  The update manager was unable to do a full "security update" and as such, only a partial update was attempted.  However, it appears that this has caused the UM to get stuck in an endless loop.
Obviously, re-booting the machine would break the loop but, I wanted to run this issue by the Ubuntu Forum before I re-booted the computer and tried the update again.

[HTML]I ran sudo apt-get update from the Terminal and the following is the result:

E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?[/HTML]I suspect that the reason for these errors are because Update Manager is currently stuck in some kind of a loop and therefore using the process necessary for the attempt.

This is a screenshot of the current progress; this has been going on now for more than 24 hours.
[ATTACH]225068[/ATTACH]
Any help is greatly appreciated.
Thank you.

---

### Post by patriot56 on 2012-10-08
Perhaps this post belongs in another thread?:???:  Maybe that's why it is being ignored?
At the time of this writing (3 days after the OP) there are 38 moderators online and ***still*** I am not getting a response....c'mon guys, give me something, _please_!!!
I need an answer to this problem.
I posted this question 3 days ago and as yet, have not gotten a single response.
That has never happened to me before on this Forum!
I have to admit I am a little disenchanted. :sad:

If my question/problem is trivial please just say so.

Kindest Regards

---

### Post by jerrrys on 2012-10-08
In your first post:

"another process using it?"

Do you have more than one package manager open?  Maybe the software center
open twice.  Or trying to do a terminal update with the SC open ?  
You can have just one open at a time.

---

### Post by Bucky Ball on 2012-10-08
> **patriot56 said:**
> Perhaps this post belongs in another thread?:???:  Maybe that's why it is being ignored?

Nope. And it's not being ignored. People are looking but obviously don't have the answers or they'd be posting.

> **patriot56 said:**
> At the time of this writing (3 days after the OP) there are 38 moderators online and ***still*** I am not getting a response....c'mon guys, give me something, _please_!!!

Repeat: If someone had something to add, moderator or otherwise (and we look at lots of posts), they would add it.

> **patriot56 said:**
> I need an answer to this problem.
I posted this question 3 days ago and as yet, have not gotten a single response.
That has never happened to me before on this Forum!
I have to admit I am a little disenchanted. :sad:

Everybody that posts in the support section needs an answer. I have posted a thread and dribbled on to myself for a week seemingly unnoticed. In the process of talking to myself here I generally fix it. Don't let it get to you. It happens.

> If my question/problem is trivial please just say so.
*NO* question posted on these forums is considered trivial by staff or users, even the spam! 

This forum is staffed by volunteers and populated by users who are here by choice. Consequently, sometimes the plan works out, other times, like this at the moment, not. But at least jerrys and I have bumped the thread to the top of the queue so who knows. If you haven't had any attention for twenty four hours (any sooner is discouraged) give your post a simple bump by posting:

> bumpThat's all you need do.

One vital piece of info ... what release are you using? I'm wondering if it might be unsupported therefore the error.

---

### Post by Elfy on 2012-10-08
> **patriot56 said:**
> Perhaps this post belongs in another thread?:???:  Maybe that's why it is being ignored?
At the time of this writing (3 days after the OP) there are 38 moderators online and ***still*** I am not getting a response....c'mon guys, give me something, _please_!!!
I need an answer to this problem.
I posted this question 3 days ago and as yet, have not gotten a single response.
That has never happened to me before on this Forum!
I have to admit I am a little disenchanted. :sad:

If my question/problem is trivial please just say so.

Kindest RegardsI seriously doubt - and am in fact positive - that you have not seen 38 staff members online. You might see a list with 38 staff members at the bottom of forums - they aren't all online :)

First I have no idea what UE is? 

It also appears that you're running a distribution upgrade - from and to what?

Lastly - you also appear to be in the midst of a partial upgrade - this is rarely a good idea.

What's the state of play with it now - the screenshot is from 3 days ago?

---

### Post by Old_Grey_Wolf on 2012-10-08
If no updates are currently running, enter this command to remove the lock.```
sudo rm /var/lib/apt/lists/lock
```Then update and upgrade again. ```
sudo apt-get update
sudo apt-get upgrade
``` Post any errors. If you have a partial upgrade you will need to remove some more files.

---

### Post by patriot56 on 2012-10-09
:oops: First, let me do a little groveling...I owe the Forum at least that, along with a *sincere apology*.
At the time of my last post, I was extremely frustrated with this problem.  I am under some pressure to present a Linux distribution that has all the "bells-and-whistles" (Ultimate Edition 3,2) and up until just recently I thought I had found it. 
You (the Forum volunteers) did not deserve that last post.  You guys are the best there are, and I mean that sincerely.  So PLEASE accept my sincerest apology. :oops:  
Now, to address each comment as best I can. 
In an effort to keep this post short I will attempt to answer each response in this post. 


The partial update state has not changed as yet, in fact I just received another "partial update notice" just about an hour ago.  I cancelled it.
There are no other processes running (that I'm aware of anyhow) that would prevent the update from continuing.

I ran 
sudo rm /var/lib/apt/lists/lock
sudo apt-get update sudo apt-get upgrade
as instructed and this is the results:
*(of course I only included the warnings) should you need the entire output, please let me know.  I withheld it because it is so lengthy. *
[CENTER]**_sudo apt-get update gave these warnings_**

[/CENTER]
W: Duplicate sources.list entry [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) oneiric-security/restricted i386 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_oneiric-security_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) oneiric-security/main i386 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_oneiric-security_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) oneiric-security/multiverse i386 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_oneiric-security_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) oneiric-security/universe i386 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_oneiric-security_universe_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

[CENTER]**_sudo apt-get upgrade gave the following:_**

[LEFT]Fetched 20.8 MB in 33s (629 kB/s)                                              
Failed to fetch [http://archive.canonical.com/ubuntu/pool/partner/a/adobe-flashplugin/adobe-flash-properties-gtk_11.2.202.243-0oneiric1_i386.deb](http://archive.canonical.com/ubuntu/pool/partner/a/adobe-flashplugin/adobe-flash-properties-gtk_11.2.202.243-0oneiric1_i386.deb)  404  Not Found [IP: 91.189.92.191 80]
Failed to fetch [http://archive.canonical.com/ubuntu/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.243-0oneiric1_i386.deb](http://archive.canonical.com/ubuntu/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.243-0oneiric1_i386.deb)  404  Not Found [IP: 91.189.92.191 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

[/LEFT]
[/CENTER]
  As I mentioned above, this is Ultimate Edition 3.2.  It has performed flawlessly until about 2-2 1/2 weeks ago.  That's when I first noticed this issue.
Before posting to the Forum I searched through about 12-15 pages of posts here and found nothing that looked like what I'm experiencing now.

Thank you all again, and again please accept a humble apology for allowing my frustration to spill over into my last post.

Sincerely, 
patriot56

---

### Post by patriot56 on 2012-10-09
> **Elfy said:**
> I seriously doubt - and am in fact positive - that you have not seen 38 staff members online. You might see a list with 38 staff members at the bottom of forums - they aren't all online :)

First I have no idea what UE is? 

It also appears that you're running a distribution upgrade - from and to what?

Lastly - you also appear to be in the midst of a partial upgrade - this is rarely a good idea.

What's the state of play with it now - the screenshot is from 3 days ago?
Elfy, I felt obligated to respond to your post regarding the inappropriate statement that I made about "seeing 38 moderators online".  You are rite of course.
If I would have just stopped and taken a breath, I probably would have never made that comment, or, for that matter, not even made the post.
My apologies.
You and the rest of the volunteers here are exceptional.
Ever say something that you wish you could take back?:(
Guess what?  I'm there!

By the way, the situation hasn't changed except that I'm not accepting the partial upgrades anymore.
And UE stands for Ultimate Edition....as I understand it, it is built on (or is) Oneiric, only with a lot of stuff added to it.  Hence, the Bells-and-Whistles I mentioned in my previous post.
In fact when I do a uname -a that's exactly what I see.
I hope this helps

---

### Post by jerrrys on 2012-10-09
Ultimate Edition; didn't know that either or I would not of responded.  Just because I tend to support ubuntu and its official spins.  Anyhow im here so in terminal:

sudo rm /var/lib/apt/lists/* -vf

sudo apt-get update

If it still gives you duplicate sources.list errors, please post the output of:

cat /etc/apt/sources.list

---

### Post by Old_Grey_Wolf on 2012-10-09
I'm glad lock is gone. Now we have something to work with to solve your problem.

> **jerrrys said:**
> ...
If it still gives you duplicate sources.list errors, please post the output of:

cat /etc/apt/sources.list

I have a feeling we are going to eventually be telling the OP how to edit the sources.list file. :)

---

### Post by patriot56 on 2012-10-09
> **jerrrys said:**
> Ultimate Edition; didn't know that either or I would not of responded.  Just because I tend to support ubuntu and its official spins.  Anyhow im here so in terminal:

sudo rm /var/lib/apt/lists/* -vf

sudo apt-get update

If it still gives you duplicate sources.list errors, please post the output of:

cat /etc/apt/sources.list
As per your instructions this is the output of the cat /etc/apt/sources.list:

# deb cdrom:[Ultimate Edition 3.2 _Oneiric_ - Release i386 (20111012)]/ oneiric main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main
# deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) oneiric-security restricted main multiverse universe

---

### Post by Old_Grey_Wolf on 2012-10-09
Edit the sources.list file by entering this command in a terminal ```
gksudo gedit /etc/apt/sources.list
```

Then put a # in front in the line at the end of the file.
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) oneiric-security restricted main multiverse universe
It should look like # deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) oneiric-security restricted main multiverse universe when you are done. Then save the file.

Then update and upgrade again. Post any errors.

---

### Post by patriot56 on 2012-10-09
> **Old_Gray_Wolf said:**
> Edit the sources.list file by entering this command in a terminal ```
gksudo gedit /etc/apt/sources.list
```Then put a # in front in the line at the end of the file.
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) oneiric-security restricted main multiverse universe
It should look like # deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) oneiric-security restricted main multiverse universe when you are done. Then save the file.

Then update and upgrade again. Post any errors.
Well Old_Gray_Wolf, it looks like that did the trick.
It appears that the update and upgrade ran as expected with no errors.
*I want you to know that I am very grateful for your help and the help of everyone that responded to this post and, again, please accept my sincerest apology for the previous rant.* [I] And I meant no disrespect.

[/I]I learned a valuable lesson here about being patient.:(
Thank you again.
Respectfully,
patriot56

---

### Post by Bucky Ball on 2012-10-09
Glad you have it sorted. And hey, we all have one of those days so I think we all understand your frustration ... difference is a lot of people don't have the guts to face it and go back and build some burnt bridges, so good work.

Good luck with presenting the Ubuntu UE *bomb*! ;)

---

### Post by patriot56 on 2012-10-09
> **Bucky Ball said:**
> Glad you have it sorted. And hey, we all have one of those days so I think we all understand your frustration ... difference is a lot of people don't have the guts to face it and go back and build some burnt bridges, so good work.

Good luck with presenting the Ubuntu UE *bomb*! ;)
Thank you Bucky Ball for your understanding.  That means a lot.
I expect the presentation to go well especially now that I have a little more insight into the potential issues.
Every time I come into this Forum with a problem, I learn something new.
I look forward to the day when I can come into the Forum and volunteer my support to those needing help instead of coming in always looking for answers.

Kindest Regards,
Patriot56 ):P

---

### Post by Elfy on 2012-10-10
Glad to see you sorted. 

> I look forward to the day when I can come into the Forum and volunteer my support to those needing help instead of coming in always looking for answers.I'd suspect that you'd be able to do that now anyway - there will be people looking for help with things you've learnt to fix - just because you've not been about long does not mean you have nothing to offer others.

Have fun.

---


---
title: "(synaptic:2423): GLib-CRITICAL **: g_child_watch_add_full: assertion 'pid &gt; 0' failed"
date: 2016-12-02
forum: Installation &amp; Upgrades
---

### Post by Shobuz99 on 2016-12-02
I have searched for this error and cannot find any posts on it.
I'm running 14.04 LTS  on a Dell Inspiron 1525 laptop with a 250GB HDD. 

I get this error message when dpkg is run to update or remove packages in Synaptic Pkg:

```
 (synaptic:2510) : Glib - CRITICAL **: g_child_watch_add_full: assertion 'pid > 0' failed 
```


I also get it on my other Dell Inspiron 1300 with 14.04 LTS:
```
 (synaptic:2423): GLib-CRITICAL **: g_child_watch_add_full: assertion 'pid > 0' failed 
```

Any updates that I run seem to install without issues of any kind. 

I don't understand what is failing. Anyone?

Thank you

Shobuz99

---

### Post by DuckHook on 2016-12-02
Do you have another update app or process running at the same time or just prior? This message shows up when the update process is locked. Updating can only be done by one app at a time. There is also a cool down period after one updating app is run before it will release the locks to another app. I vaguely recall some issues specific to an error like this and synaptic a few years ago, but thought that bug was fixed. Remember also, that on a default install, updating runs in the background. You do not have to actively invoke the update process for it to be locked to other apps.

---

### Post by Shobuz99 on 2016-12-02
> **DuckHook said:**
> Do you have another update app or process running at the same time or just prior? This message shows up when the update process is locked. Updating can only be done by one app at a time. There is also a cool down period after one updating app is run before it will release the locks to another app. I vaguely recall some issues specific to an error like this and synaptic a few years ago, but thought that bug was fixed. Remember also, that on a default install, updating runs in the background. You do not have to actively invoke the update process for it to be locked to other apps.

Thank you for your response. No I don't have another update app running at the same time or prior.
This happens on two different machines, every time I run the "Software Updater" when it loads itself 
and tells me an update is ready to be made. Both machines are 14.04 LTS.

I looked at the Bug Report for this at [https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/1282542](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/1282542)
It seems as though this has been fixed; but I also saw a comment that said to update Synaptic Pkg Mgr to a newer version.
Not sure about doing that. How do I uninstall Synaptic Pkg Mgr without using it? I assume it would be done from Terminal
but I don't recall the correct command. Is that even necessary?

Thank you DuckHook, for your continued help.

Shobuz99

---

### Post by DuckHook on 2016-12-03
Good work finding that bug report. The way I read it, the problem has not really been solved for Trusty. In the trailing posts, this was not fixed for at least some users in 15.04 or 15.10 and one user reporting the same bug in a recent version of Mint. I am assuming that you are experiencing exactly this bug.

I always have lots of trouble following the ebb and flow of bug reports, especially when they run to 60+ postings. My reading of it is as follows:

[LIST=1]
[*]The problem has been fixed in Xenial
[*]Because the bug affects only synaptic and moreover can be worked around, it has been relegated to "nuisance" status
[*]Because it is not a security issue, the fix has not been backported (meaning that Trusty will never get it)
[*]You can get rid of the bug by forcing an upgrade of synaptic to its Xenial version (as advised in post #60 by someone I assume is a synaptic developer/maintainer)
[/LIST]
The problem with the proposed solution (at least from my perspective) is that, as a matter of principle, I hate to shoehorn a later version of an app into a functioning system that is ticking along smoothly with the apps that are approved for it. I've had too many bad experiences with broken dependencies and breaking the whole upgrade subsystem trying to do that. And since we are dealing with the upgrade system itself in synaptic, it's a critical subsystem that I just don't want to monkey with in any way. If you also agree with this sentiment, then I only see two choices in front of you:

[LIST=1]
[*]Upgrade to Xenial
[*]Use another app selection tool other than synaptic
[/LIST]
Speaking only for myself, I've dropped synaptic by personal choice as my *apt* skills have grown. I now look for and manage my packages using only the command line. If bare-bones *apt* feels too intimidating for now, you may wish to look at *aptitude*, which is a CLI app that wraps many of the most important package functions into a friendly ncurses pseudo-graphical environment.

---

### Post by Shobuz99 on 2016-12-03
> **DuckHook said:**
> Good work finding that bug report. The way I read it, the problem has not really been solved for Trusty. In the trailing posts, this was not fixed for at least some users in 15.04 or 15.10 and one user reporting the same bug in a recent version of Mint. I am assuming that you are experiencing exactly this bug.

I always have lots of trouble following the ebb and flow of bug reports, especially when they run to 60+ postings. My reading of it is as follows:

[LIST=1]
[*]The problem has been fixed in Xenial
[*]Because the bug affects only synaptic and moreover can be worked around, it has been relegated to "nuisance" status
[*]Because it is not a security issue, the fix has not been backported (meaning that Trusty will never get it)
[*]You can get rid of the bug by forcing an upgrade of synaptic to its Xenial version (as advised in post #60 by someone I assume is a synaptic developer/maintainer)
[/LIST]
The problem with the proposed solution (at least from my perspective) is that, as a matter of principle, I hate to shoehorn a later version of an app into a functioning system that is ticking along smoothly with the apps that are approved for it. I've had too many bad experiences with broken dependencies and breaking the whole upgrade subsystem trying to do that. And since we are dealing with the upgrade system itself in synaptic, it's a critical subsystem that I just don't want to monkey with in any way. If you also agree with this sentiment, then I only see two choices in front of you:

[LIST=1]
[*]Upgrade to Xenial
[*]Use another app selection tool other than synaptic
[/LIST]
Speaking only for myself, I've dropped synaptic by personal choice as my *apt* skills have grown. I now look for and manage my packages using only the command line. If bare-bones *apt* feels too intimidating for now, you may wish to look at *aptitude*, which is a CLI app that wraps many of the most important package functions into a friendly ncurses pseudo-graphical environment.

Thank you for putting together an intelligent perspective of the Bug Report. 
I admit I was a bit lost because I don't read them very often. They are confusing to me, because of the comments and the "fixes" that are posted.
My sense of it tells me that you have the best approach re: the "Xenial fix" being applied to Trusty: Don't fool around with it.
Besides, I saw a comment there from someone that suggested that the word "CRITICAL" could be misinterpreted by novices as
being a serious bug; when in fact, the majority of comments allude to the bug as just an "annoyance"...which it is.
I think the commenter called for a 'reassessment' naming the error message to something less of a concern than "critical". I agree.

As far as 14.04 LTS is concerned, I'll probably stick with it until it goes to "unsupported".
I really am not anxious to go to 16.04 LTS at this point. 
Besides the "bad raps" some Ubuntu "reviewers" (re: Joe Collins) are giving 16.04 LTS, 
I'm hoping that Ubuntu's development strategy becomes a bit less 'commercial' oriented and doesn't forget about their loyal "old timer" users like me. 
I'm 67 yrs old and frankly, I don't see myself getting any more adept at "upgrades" and all that goes with them.
By the time 14.04 LTS runs out of support, I'll be pushing 70 yrs old. Life gets harder as you grow older. Trust me on this, DuckHook! :-|
Even for an old geek like me, I tend to struggle with newer versions that are designed and developed for people anxious for something "new";
including the whole Mobile spectrum. 
Even though I've developed web sites for mobile access; I have lost touch with what is being done now in that regard.
For me the irony is that I was on the ground floor of personal computers and software in 1980, while working at IBM. 
So much has changed since, that I now feel like I'm a "legacy" protector of some junk that is forgotten and laughable.
It's hard to explain the lost feelings I have. 
The only time I feel better is when someone calls me to fix their computer and I have to tell them, "Get OFF WINDOWS XP!!!" :-) :-D
You may laugh too; but there are millions of people my age and younger that STILL use that OS!! They're "afraid" of Linux too. It's insane. 
It's sad and hilarious simultaneously because I won't be laughing in a few years when it happens to me with whatever Linux distro
I end up with before I end up in a nursing home. :-( 

Anyway, enough of my babble. Thank you for your wisdom here. I do appreciate you taking the time to help me.
I know that Ubuntu is becoming a very popular OS and the forum response team is very very busy trying to help newcomers to Ubuntu Linux.
You are a very important, valuable technical member of that team, as far as I can see. And I'm very glad! :-)

Rick (Shobuz99)

---

### Post by DuckHook on 2016-12-03
Glad to be of service, Shobuzz99.

Though not strictly "solved", I believe that you've arrived at the only set of options available for this matter. If you are okay with those options, *please mark thread **solved** using *Thread Tools* in the top toolbar for the benefit of others searching for solutions*.

---

### Post by mbritovaladares on 2017-08-25
@Shobuz99, I feel like you about how Ubuntu's development forget legate users.
I have 34 years old and I miss how Ubuntu 10.04 worked with Gnome 2 and Compiz. :rolleyes:

---


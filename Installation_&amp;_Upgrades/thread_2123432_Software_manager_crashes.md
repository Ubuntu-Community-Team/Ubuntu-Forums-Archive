---
title: "Software manager crashes"
date: 2013-03-08
forum: Installation &amp; Upgrades
---

### Post by Maxfield Solar on 2013-03-08
Hello,

I have been having a problem with my Software Manager, I received some notifications that it crashed but I did not really worry about it. Then I wanted to install something and that's when I realized that there was a definite problem. The Software center would pop up, but then it would act like it was frozen, then I got more notifications that it crashed. I tried it a couple of times with the same results. I was not to concerned as I thought it would work just fine after a reboot so I did not pay much attention to the details the notifications contained. I rebooted my laptop and tried to open the software center. Now when I try to open it, it pops up, waits a minute, and disappears. I have a notification in the bar on the upper right hand side that when I click on it it gives a pop up showing the following
 "An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:
E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_quantal-updates_universe_i18n_Translation-en, E:The package lists or status file could not be parsed or opened."
 

(I don't know why my computer keeps putting an smiley face in there but it's supposed to be a : then a P)

What do I do now?

I am quit new to Linux but I like it so far. I am sorry if my lack of knowledge is apparent in my question.

Thank-you,
Kienan

---

### Post by carl4926 on 2013-03-08
I suggest you install synaptic

```
sudo apt-get install synaptic
```

Use that if you need a UI to manage software

---

### Post by p-dh on 2013-03-08
Hi Kiinan,

You could try to run the following two commands from the command line:
sudo apt-get clean
sudo apt-get update

If you continue to have difficulties, check out this [thread]("http://askubuntu.com/questions/30072/how-do-i-fix-a-problem-with-mergelist-or-status-file-could-not-be-parsed-err") on AskUbuntu.

Peace,
Paul :cool:

---

### Post by Maxfield Solar on 2013-03-09
Paul,

Thank-you for your response! The commands you gave me did not work but I went to the thread you gave me a link to and that fixed my problem.

Thanks again,
Kienan

---

### Post by Maxfield Solar on 2013-03-09
How do I mark this thread as solved?

---

### Post by ibjsb4 on 2013-03-09
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by p-dh on 2013-03-13
Hey Kienan,

What in the instructions worked for you? Just would like to know...

Thanks.

Paul :cool:

---

### Post by Maxfield Solar on 2013-03-20
Sorry I wasn't able to respond sooner. Here is the part that was most useful to me

> These terminal commands should solve your problem:
  First remove the Merge List by opening a terminal (Hit Ctrl-Alt-T to launch) and running this command
  
[INDENT]sudo rm /var/lib/apt/lists/* -vf[/INDENT]

Next generate a new one by running a simple update 
  
[INDENT]sudo apt-get update[/INDENT]

  Here is the [bug report]("https://bugs.launchpad.net/ubuntu/+source/apt/+bug/346386") (and [another]("https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/886273"))  for this problem, which is now fixed so it shouldn't create new  malformed files, however if you already have the malformed files you  need to remove them as explained in this post.

Thank-you all for your help!!

---

### Post by Maxfield Solar on 2013-03-20
I have one more question, if you look at my first post on this forum, it automatically replaced my typing with an emoticon. Is there a way to make it say what I want?

---

### Post by carl4926 on 2013-03-21
> **Maxfield Solar said:**
> I have one more question, if you look at my first post on this forum, it automatically replaced my typing with an emoticon. Is there a way to make it say what I want?

Open a reply to this message and scroll down to additional options
'Disable smilies in text' check it

Or place the text in code tags

:D
```
:D
```

---

### Post by Maxfield Solar on 2013-03-21
Thanks so much! :D

---


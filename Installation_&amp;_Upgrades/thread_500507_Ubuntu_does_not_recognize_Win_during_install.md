---
title: "Ubuntu does not recognize Win during install"
date: 2007-07-14
forum: Installation &amp; Upgrades
---

### Post by durkhrod chogori on 2007-07-14
Hi there,

I am trying to install Ubuntu in my Win box (dual boot) but it does not recognize XP. It tries to do a clean partition and I don't want that. Is there a fix for this?

Thx in advance.

---

### Post by merlinus on 2007-07-14
What are your choices when you reach the partitioning menu?

-merlin

---

### Post by bdtgp on 2007-07-14
Go to Computer Management in XP first.  Click on disk management and then right click on your drives space.  Shrink the volume the amount you want to use for Ubuntu.  Restart and try installing again-this time choose Manual when you get to partitioning and select the "free space" and create a partition for Ubuntu.

---

### Post by durkhrod chogori on 2007-07-14
OK. I did a defrag of both drives and now it's working. But I have a query:

1. When I do the manual install I need to know the input required to install Ubuntu. There is a drop down menu which I can't remember now that I need to fill in,something with ext3 and other stuff.

Can anyone help me in here?

2. When importing the Win files, I also realised that Ubuntu brings three accounts in:

2.1 Administrator
2.2 AAAA (my full rights account)
2.3 BBBB (my limited account)

It also asks me for user name and account for each.

Well, I have no idea what the "Administrator" account is as I never use it, only when booting in safe mode and even tough I always access with AAAA (full rights account or administrative account), because if I access with "Administrator" I won't have full rights anyway once logged in in safe mode.

Any ideas in here? Do I ignore the Administrator account?


Thx again.

---

### Post by durkhrod chogori on 2007-07-14
Any help.

Gee, threads move fast in here.


Ta.

---

### Post by merlinus on 2007-07-14
Is there any reason you need to import your windows accounts?  I chose to not do that, and have not had any problems.

-merlin

---

### Post by durkhrod chogori on 2007-07-14
> Is there any reason you need to import your windows accounts? I chose to not do that, and have not had any problems.

Didn't know that. Ubuntu just asked for it. So how will I use Win files in Ubuntu?

BTW, could you tell me how to do the manual install in detail? It's because after choosing "free memory" I actually need to input all the values and all that jazz.

Cheers.

---

### Post by merlinus on 2007-07-14
You can install drivers (ntfs-3g) that will allow writing to your windows partition.

As for a partitioning scheme, can you post some of your hardware specs, especially how much space you have allocated for ubuntu?

-merlin

---

### Post by durkhrod chogori on 2007-07-14
I got 37.1 GB in my D: drive in which I am planning to install Ubuntu.

When you said: 

> You can install drivers (ntfs-3g) that will allow writing to your windows partition.

Does this mean that they will write Ubuntu into D: ?

You haven't answered my previous question:

**How do I import all the Win files into Ubuntu if I don't import all my accounts?**

Cheers.

---

### Post by merlinus on 2007-07-14
ntfs-3g will let you write to your windows drives.

Are you wanting to move all your windows files into ubuntu?

-merlin

---

### Post by durkhrod chogori on 2007-07-15
Yes I will. So do I need to import my Win acc.?

---

### Post by merlinus on 2007-07-15
Once ubuntu is installed, you will be able to copy all of your data files from windows to that partition. That is what I have done.

No need to deal with windows accounts.

-merlin

---

### Post by durkhrod chogori on 2007-07-15
As I have difficulties dealing with the manual install, it's okay if I just got through the first option: guided-resize IDE1 master, partition #5 and used free space?

BTW, how do you copy those files into Ubuntu? Is it obvious? Or one must play around a bit?

Thx again, Merlin.

---

### Post by merlinus on 2007-07-15
Once installed, in the manner you already understand judging by your last post, your windows partition with show up in Nautilus, the ubuntu file manager.

In fact, there will probably be an icon on the desktop.

You can then copy whatever you like.

Post again if you have problems.  Or questions.

-merlin

---

### Post by durkhrod chogori on 2007-07-15
Hi Merlin,

Using Ubuntu now. Install went good. However I am still trying to figure how the following:

1. Can't find Nautilus.
2. What option at bootup allows you log in as non-root? It would be like limited account in Windows to avoid getting the machine infected.
3. Cannot see anywhere how to change the preferences in Firefox. Weird, in Windows it's under "tools"but here it's missing.
4. Is Evolution Mail a mail server? Kind of Thunderbird. Is it any good?

Thx again,

:)

---

### Post by durkhrod chogori on 2007-07-16
Hi Merlin,

Could you please reply to my last message?

Thx.

---

### Post by merlinus on 2007-07-16
Using Ubuntu now. Install went good. However I am still trying to figure how the following:

1. Can't find Nautilus.

** Places/Computer**

2. What option at bootup allows you log in as non-root? It would be like limited account in Windows to avoid getting the machine infected.

[B] When you login with your username and password, you are not logged in as root.

To get root access, type:

sudo <command> in a terminal

You will be asked for your password.
[/B] 
3. Cannot see anywhere how to change the preferences in Firefox. Weird, in Windows it's under "tools"but here it's missing.

** Edit/Preferences**

4. Is Evolution Mail a mail server? Kind of Thunderbird. Is it any good?

** Evolution is similar to Outlook in windows, combination email client, calendar, contact manager, etc.  I prefer Thunderbird -- simpler and better.**

Welcome to the world of ubuntu!

-merlin

---

### Post by durkhrod chogori on 2007-07-16
Hi Merlin,

Thanks for your help. I love Ubuntu it's so much more intuitive than Windows and the best thing is free of spyware and viruses. Awesome!!

OK, so basically root is disabled by default as opposed to Win where one automatically runs as such. Very nice!

Cheers,

DC. :)

---

### Post by merlinus on 2007-07-16
Very glad to hear that you are enjoying ubuntu.  Tell all your firends!

And be sure to post back if you need further assistance.

All the best....

-merlin

---

### Post by durkhrod chogori on 2007-07-17
Thx Merlinus. Spreading the word about Ubuntu's could also mean that the more popular it becomes the more it will attract malware writers.

Thx for all your tips.

Cheers,

DC,

:)

---


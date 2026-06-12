---
title: "Is anyone aware that Broadcom wireless is broken in Lucid?"
date: 2010-02-28
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Woolio1 on 2010-02-28
A few days ago, I tried out Lucid Alpha 3. I noticed, however, that whatever I tried, I couldn't get my Wireless card on my Dell Mini to work. I tried the BCMWL-kernel-source, and a few other techniques, but I couldn't get it to recognize the wi-fi card. Now, I'm not sure what to do. I've submitted a bug report, but that won't solve anything for me. I'm at a stand still.

Oh well, time to downgrade. 

Unless anyone knows how to fix this...

Henry Ericson

---

### Post by johngreth on 2010-02-28
According to the [bug report]("https://bugs.launchpad.net/ubuntu/+bug/528838"):

> Bug is easily remedied by installing the BCMWL-Kernel-Source. However, if possible, it would be convenient to add the drivers on the download ISO.

---

### Post by Woolio1 on 2010-02-28
> **johngreth said:**
> According to the [bug report]("https://bugs.launchpad.net/ubuntu/+bug/528838"):

Yes, it is easily remedied, on a certain type of Broadcom chip. However, I've tested it with different laptops, and most of them don't even recognize the Broadcom chip. Including my Dell Mini 10.

I do hope they get this fixed before Lucid's release...

---

### Post by Twitch6000 on 2010-02-28
> **Woolio1 said:**
> A few days ago, I tried out Lucid Alpha 3. I noticed, however, that whatever I tried, I couldn't get my Wireless card on my Dell Mini to work. I tried the BCMWL-kernel-source, and a few other techniques, but I couldn't get it to recognize the wi-fi card. Now, I'm not sure what to do. I've submitted a bug report, but that won't solve anything for me. I'm at a stand still.

Oh well, time to downgrade. 

Unless anyone knows how to fix this...

Henry Ericson

This does not surprise me tbh... Just look at what the last releases have broke :/.

---

### Post by katie-xx on 2010-02-28
[COLOR=Blue]Hi Guys
Broadcom wireless is not broken in Lucid, it just needs a bit of TLC :),  but if it was, do you think the Community Cafe would be the best place to say so? :)
Try posting in this forum and Im sure you will get yourselves sorted :)

[http://ubuntuforums.org/forumdisplay.php?f=377](http://ubuntuforums.org/forumdisplay.php?f=377)

Kate[/COLOR]

---

### Post by Woolio1 on 2010-02-28
It's really not worth it. Honestly, I'm going to go crying back on this one. 

It's been fun, but I'm only going to let this thing crap itself one more time before I go back to Windows 7. 

Henry Ericson

---

### Post by johngreth on 2010-02-28
have you seen this? [http://ubuntuforums.org/showthread.php?t=1323674](http://ubuntuforums.org/showthread.php?t=1323674)
4 different solutions. I'd be surprised if none of them worked.

---

### Post by katie-xx on 2010-02-28
> **Woolio1 said:**
> It's really not worth it. Honestly, I'm going to go crying back on this one. 
It's been fun, but I'm only going to let this thing crap itself one more time before I go back to Windows 7. 
Henry Ericson

[COLOR=Blue]Ive actually found Win 7 to be a major disappointment.
its absolutely rubbish at not crashing ...although it does produce lovely mini dumps files.
Worst of all it just doesnt like the networking stuff I do for a living. Official!!! Win 7 is crap at modbus and OPC :)
ive no doubt it will improve.
In the same way, why do you assume Broadcom wireless should work in Linux without any problem?
Take a look , take advice and then learn something about your pc.

Kate[/COLOR]

---

### Post by Woolio1 on 2010-02-28
> **katie-xx said:**
> [COLOR=Blue]Ive actually found Win 7 to be a major disappointment.
its absolutely rubbish at not crashing ...although it does produce lovely mini dumps files.
Worst of all it just doesnt like the networking stuff I do for a living. Official!!! Win 7 is crap at modbus and OPC :)
ive no doubt it will improve.
In the same way, why do you assume Broadcom wireless should work in Linux without any problem?
Take a look , take advice and then learn something about your pc.

Kate[/COLOR]

Windows 7 has never crashed on me. Never gotten the Blue Screen of Death, never had any problems at all. However, Ubuntu's fudged it's bootloaders, killed it's filesystems, and had major memory leaks, without me doing anything at all.

And it doesn't even support the most widely used Wireless chip in the world. That is a monumental detriment to the usefulness of the Operating System, my friend.

Henry Ericson

---

### Post by MasterNetra on 2010-02-28
> **katie-xx said:**
> [color=blue]hi guys
broadcom wireless is not broken in lucid, it just needs a bit of tlc :),  but if it was, do you think the community cafe would be the best place to say so? :)
try posting in this forum and im sure you will get yourselves sorted :)

[http://ubuntuforums.org/forumdisplay.php?f=377](http://ubuntuforums.org/forumdisplay.php?f=377)

kate[/color]

+1

---

### Post by Jesus_Valdez on 2010-02-28
Are You aware that You are complaining about an alpha release?

But well, have fun in Windows 7.

---

### Post by fatcrab on 2010-02-28
> **Woolio1 said:**
> Windows 7 has never crashed on me. Never gotten the Blue Screen of Death, never had any problems at all. However, Ubuntu's fudged it's bootloaders, killed it's filesystems, and had major memory leaks, without me doing anything at all.

And it doesn't even support the most widely used Wireless chip in the world. That is a monumental detriment to the usefulness of the Operating System, my friend.

Henry Ericson

Same here.This is why linux will never be anything  more than a hobby for me.

---

### Post by katie-xx on 2010-02-28
> **Woolio1 said:**
> Windows 7 has never crashed on me. Never gotten the Blue Screen of Death, never had any problems at all. However, Ubuntu's fudged it's bootloaders, killed it's filesystems, and had major memory leaks, without me doing anything at all.
And it doesn't even support the most widely used Wireless chip in the world. That is a monumental detriment to the usefulness of the Operating System, my friend.
Henry Ericson
[SIZE=2][COLOR=Blue]
Well Im not sure if your name is Henry Ericson or Woolio but I think you do deserve an answer.
First of all you really do need to understand who supports who re hardware and operating systems :) Dont worry, its a common mistake. It isnt the case that Microsoft, for example, support Broadcom wireless kit. Its the opposite way around. now: if, as you say, there is a problem with some Broadcom chips and Linux; then its for Broadcom to come up with the goods in the exact same way they have done with Windows.

Secondly: I would suggest if you have not experienced a Win 7 crash then you havent given it anything useful to do!
It does not like running a great deal of the network tunnelling that is in place specifically to avoid DCOM (btw ..Win7 also doesnt like DCOM)  DCOM , btw, is a very important network protocol which Microsoft introduced as a means of implementing remote procedure calls and then abandoned because they could get it to work reliably. :)

Finally: I wouldnt dream of visiting a Windows Forum and complaining something isnt working properly and also saying it works ok on Linux. 
Why do it here? Its stupid and makes no difference to your problem if something works or doesnt work on Windows.

Kate
[/COLOR][/SIZE]

---

### Post by johngreth on 2010-02-28
> well im not sure if your name is henry ericson or woolio but i think you do deserve an answer.
First of all you really do need to understand who supports who re hardware and operating systems dont worry, its a common mistake. It isnt the case that microsoft, for example, support broadcom wireless kit. Its the opposite way around. Now: If, as you say, there is a problem with some broadcom chips and linux; then its for broadcom to come up with the goods in the exact same way they have done with windows.

Secondly: I would suggest if you have not experienced a win 7 crash then you havent given it anything useful to do!
It does not like running a great deal of the network tunnelling that is in place specifically to avoid dcom (btw ..win7 also doesnt like dcom) dcom , btw, is a very important network protocol which microsoft introduced as a means of implementing remote procedure calls and then abandoned because they could get it to work reliably.

Finally: I wouldnt dream of visiting a windows forum and complaining something isnt working properly and also saying it works ok on linux.
Why do it here? Its stupid and makes no difference to your problem if something works or doesnt work on windows.

Kate

+1

---

### Post by katie-xx on 2010-02-28
[SIZE=2][COLOR=Blue]I have just completed a check and have to tell you, Henry Ericson , that no current version of Linux has major memory leak issues.

I also have to tell you that when professional network people schedule server reboots
there is a difference between the reboot time for Windows Servers and Linux Servers.
I will leave it to you to find out which of the two systems has the longest period between reboots. (for info: this blows away your memory leak rubbish)

Why have you told lies??

Kate
[/COLOR][/SIZE]

---

### Post by k3lt01 on 2010-02-28
Henry my boy my pride and joy :popcorn:.

Katie has told you what reality is in no less than 2 separate threads. You are trying to run an ALPHA release and expecting it to be a commercially ready OS. Sorry to tell you but it doesn't work that way.

In Linux the way it works is we test the Alphas and Betas, let the devs know if there is a problem, we describe it for them so they may be able to repeat it and if it is repeatable they develop a fix. Your just dumping your attitude on this one.

---

### Post by Frak on 2010-02-28
Knowing how releases have been working lately, it still won't be fixed in the final release. If, by some chance, it is, it will probably take something else down with it. Not trying to act pessimistic, but it happens every release.

Therefore, if you need to get work done without worrying whether or not your wireless will work from one minute to the next, stick with Windows.

---

### Post by Woolio1 on 2010-02-28
> **k3lt01 said:**
> Henry my boy my pride and joy :popcorn:.

Katie has told you what reality is in no less than 2 separate threads. You are trying to run an ALPHA release and expecting it to be a commercially ready OS. Sorry to tell you but it doesn't work that way.

In Linux the way it works is we test the Alphas and Betas, let the devs know if there is a problem, we describe it for them so they may be able to repeat it and if it is repeatable they develop a fix. Your just dumping your attitude on this one.

This... Is true. Perhaps I'll just throw UNR on it, and don't mess with it unless absolutely necessary. Just use it to take notes and ship them through Dropbox.

Henry Ericson

---

### Post by katie-xx on 2010-02-28
[SIZE=2][COLOR=Blue]I need to respect the number of posts you have made here .and its a lot.
But ....................................................................................................
Lets imagine that you wanted to use your wireless connection to connect to a remote server and execute a remote proceedure. Also, lets imagine the connection had to be made via a network tunnelling protocol. (Because DCOM is too unreliable)
At the moment Win 7 cannot handle it. Win XP can and Vista  can .provided you have the right version and Linux can.

Kate[/COLOR][/SIZE]

---

### Post by Woolio1 on 2010-02-28
> **Frak said:**
> Knowing how releases have been working lately, it still won't be fixed in the final release. If, by some chance, it is, it will probably take something else down with it. Not trying to act pessimistic, but it happens every release.

Therefore, if you need to get work done without worrying whether or not your wireless will work from one minute to the next, stick with Windows.

This is also true. Windows has always been my "workhorse" OS, simply because the devs don't go around breaking every release. In fact, it has worked flawlessly for me since Windows 95. 

I'll see how much longer I can tough it out.

Of course, now I'm beginning to doubt why I came here originally, when Windows has more programs, isn't broken, etc.

I hate to say it, but Microsoft has one thing above Linux: money. And if Linux doesn't get more of it, then it's doomed to remain in the realm of server hosts and hobbyists.

H.E.

---

### Post by cariboo on 2010-02-28
I moved this thread to Lucid testing and discussion so that the op could get some help with his problem. Please keep your opinions in the Cafe where they belong, this is a technical support forum.

---

### Post by katie-xx on 2010-02-28
> **Woolio1 said:**
> . And if Linux doesn't get more of it, then it's doomed to remain in the realm of server hosts and hobbyists.
H.E.
[SIZE=2][COLOR=Blue]
OmG !! you are trolling yes ? :)
That would be server hosts as in nothing at all you do today on a  computer works unless a server is there ???????
Give it up. Linux is good at some things Windows is good at others. 


Kate
[/COLOR][/SIZE]

---

### Post by Woolio1 on 2010-02-28
> **katie-xx said:**
> [SIZE=2][COLOR=Blue]I need to respect the number of posts you have made here .and its a lot.
But ....................................................................................................
Lets imagine that you wanted to use your wireless connection to connect to a remote server and execute a remote proceedure. Also, lets imagine the connection had to be made via a network tunnelling protocol. (Because DCOM is too unreliable)
At the moment Win 7 cannot handle it. Win XP can and Vista  can .provided you have the right version and Linux can.

Kate[/COLOR][/SIZE]

In case you haven't noticed, I am an average user, and a bit of a programmer. I am not a server host, nor do I ever need to use Dcom. I appreciate you trying to help, but this is getting really tiresome. I'm not always on Lucid. In fact, I've used Karmic for three months, reinstalling weekly.

There should be NO REASON I should have to reinstall weekly. That shows laziness in the dev team.

---

### Post by Woolio1 on 2010-02-28
> **katie-xx said:**
> [SIZE=2][COLOR=Blue]
OmG !! you are trolling yes ? :)
That would be server hosts as in nothing at all you do today on a  computer works unless a server is there ???????
Give it up. Linux is good at some things Windows is good at others. 


Kate
[/COLOR][/SIZE]

Erm, forgive me if I come across as trolling. I am very frustrated. Weekly reinstalls are not good for my mental health.

H.E.

---

### Post by katie-xx on 2010-02-28
> **cariboo907 said:**
> I moved this thread to Lucid testing and discussion so that the op could get some help with his problem. Please keep your opinions in the Cafe where they belong, this is a technical support forum.
[SIZE=2][COLOR=Blue]With all due respect I do believe I recommended to the OP to post here ..before you moved it :)
Unfortunately I dont believe he wants a solution.
Sorry you have been inconvenienced ..this belongs in the dustbin.


Kate[/COLOR][/SIZE]

---

### Post by Frak on 2010-02-28
> **katie-xx said:**
> [SIZE=2][COLOR=Blue]
OmG !! you are trolling yes ? :)
That would be server hosts as in nothing at all you do today on a  computer works unless a server is there ???????
Give it up. Linux is good at some things Windows is good at others. 


Kate
[/COLOR][/SIZE]
You provided him with a very specialty scenario that truthfully doesn't hold much water in the first place. Instead, it sounds like you are trying to defend Linux, which doesn't need defense.

---

### Post by cariboo on 2010-02-28
@katie-xx

I have to agree with you, so this thread is closed.

---

### Post by KiwiNZ on 2010-02-28
I will add as a foot note to the closure. This is an extract from the release notes for the Lucid Alpha....

Welcome to Lucid Lynx Alpha 3, which will in time become Ubuntu 10.04 LTS.

Pre-releases of Lucid are *not* encouraged for anyone needing a stable
system or anyone who is not comfortable running into occasional, even
frequent breakage.  They are, however, recommended for Ubuntu developers and
those who want to help in testing, reporting, and fixing bugs.

---


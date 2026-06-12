---
title: "Utter Confusion - Dual Boot"
date: 2010-12-05
forum: Installation &amp; Upgrades
---

### Post by syntax89 on 2010-12-05
Okay I'm a completely new to this and I've been reading guides, forums, and even watching youtube videos. I've been hearing about partitions and blah blah blah. I think I've seen too much because now I'm just utterly confused.

Let me get on with my list of questions...

1. [COLOR=Red]Does "Ubuntu Desktop Edition Windows Installer" require you to burn the OS to a CD or USB?[/COLOR] It gives off the impression that it in fact **does not need to be**. However everything else I see or read tell me I do. This is where I'm coming from... [http://www.ubuntu.com/desktop/get-ubuntu/windows-installer](http://www.ubuntu.com/desktop/get-ubuntu/windows-installer)

2. [COLOR=Red][COLOR=Black]Upon installation it asks me for an installation size ranging from 3-30GB.[/COLOR] Does this include the size available to anything that is added and installed thereafter or just the ubuntu OS itself? [/COLOR]

3. My computer came with a partition. So I believe it to be. It has the C: drive which is 149GB and the D: drive which has 137GB of space. Vista is installed onto the C: drive while the D: drive remains blank. [COLOR=Red]Does this count as a partition and if so is it safe to install abuntu to the D: drive? [/COLOR]

More questions will probably follow once these are answered. Thanks in advance.

---

### Post by wilee-nilee on 2010-12-05
Are you trying to install from a live windows enviroment=wubi not a true dual boot by the way.

Or are you wanting to boot a live cd or thumb and install alongside=true dual boot.

---

### Post by TBABill on 2010-12-05
Ok, it looks like you  may be confusing two different things. Ubuntu WINDOWS installer allows you to do what is referred to as a "Wubi Install" of Ubuntu. This means it is installed inside of Windows on a "virtual partition" created when you install it.

On the contrary, normal Ubuntu install requires a different download (the normal 32 bit or 64 bit Ubuntu). You then create a bootable CD or DVD from the iso you download in order to follow the prompts displayed once you boot your computer from the LiveCD (the LiveCD is the result of you burning that iso to disk). This install requires a separate partition, but it can make that partition itself. Or you can make it before installing. 

Just remember, C: and D: do not exist in Ubuntu. Those are windows partitions. THe system will recognize them as Windows partitions and allow you to boot into your Windows install or your Ubuntu install, but not at the same time. Only the Wubi install can do that.

I would suggest starting at [https://help.ubuntu.com](https://help.ubuntu.com) and read up some more on Ubuntu before deciding which way to go.

---

### Post by coffeecat on 2010-12-05
Some guides out there on the big wide internet can be a bit sub-standard so its best to start with good reading material. You can't do better than starting here:

[http://ubuntu-manual.org/](http://ubuntu-manual.org/)

Even thought it's for version 10.04, the essentials are the same in 10.10.

---

### Post by syntax89 on 2010-12-05
Thanks for the replies. That takes care of those questions but it also bring up more questions as I thought it would. This is no longer related to installation so it might need to be transferred to another forum. Sorry to any mods if they choose to take on that task.

@TBAABill - I've already scanned through those documents but I find it easier to get information from live people. Clears up most confusions. What are the main differences between a "Wubi installation" and your typical ubuntu installation?

---

### Post by wilee-nilee on 2010-12-05
Here is the wubi guide.
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

Basically wubi is a pseudo virtual that is just a folder in the windows system. To be honest a great idea, but problematic, and there are only a few on the forum that can really help you. Really even though wubi is for a beginner to try it out; with the problems it has reached a geek level help needed to fix it when broken, especially if a new user tries a install schema that puts it outside of the main C partition in windows.

A dual boot install with a booted cd or thumb is in its own partition and much easier to maintain and fix and much more help available.

Really it would be nice to have a tutorial, but the web can help you here you just have to separate the wheat from the chaff.

---


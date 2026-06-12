---
title: "usability proposition"
date: 2006-04-11
forum: Installation &amp; Upgrades
---

### Post by Boris Batkin on 2006-04-11
Several weeks ago I installed Ubuntu. I was impressed by the ease of installation as well as the ease of use. I thought: “Wow, this seems like a system which can completely replace Windows on many desktops. It's so easy that my grandmother can use it. It works out of the box.” That was up until I faced my first problem.

The problem is simple. I have a second hard drive with NTFS partition left from the Windows installation. I wanted to access my files, so I googled “ubuntu ntfs”. My first link contained all the necessary information.

[http://ubuntuguide.org/#mountunmountntfs](http://ubuntuguide.org/#mountunmountntfs)

The solution is simple and obvious. By copying and pasting several lines of text into the terminal window, I got everything working. The only problem is that there is no way my grandmother would use it. I personally find it somewhat tedious too.

My next problem was getting my printer up and running. Good old Google comes to rescue.

[http://www.ubuntuforums.org/showthread.php?t=10540&highlight=canon+i860](http://www.ubuntuforums.org/showthread.php?t=10540&highlight=canon+i860)

This time it involved copying and pasting a bit more lines in the terminal window. I got one of them wrong by copying one symbol less then necessary. I am professional software engineer, so I could figure it out right away. I'm not even mentioning my grandmother: they lost her on the first try.

I guess frequent Linux users have to go through this pattern often enough to know any better. Granted that sometimes there is a shell script to address the problem of any significant complexity, it does not seem like a common rule.

What I'd like to propose is a “one-click” solution. Let's call it “The Prescription.” User googles a problem, finds the answer, and clicks on a special icon. If the prescription is properly signed (PGP?) and the user has the key then it runs automatically. Otherwise it asks something like: “Are you sure you want to execute unsigned prescription?”

Sining the prescription is a key factor. It allows prescriptions to be targeted at the specific versions of packages. It also makes them secure because the user only gets a set of keys matching the installation.

Since addressing known problems will no longer require going to the terminal window, having prescriptions will make Ubuntu a lot more user friendly. It will also make it less tedious for advanced users.

Thanks,
	Boris Batkin

P.S. Is this a good forum for this thread?

---

### Post by aysiu on 2006-04-12
Does your grandmother install Windows from scratch?

The NTFS thing is a weird Ubuntu thing. Knoppix and Mepis (at least before it was Ubuntu-based) do this out-of-the-box--your drive is on the desktop, you click on it, it mounts, and it opens.

Printers... well, you have to get one that's compatible. Even my wife with her grandmother-friendly Mac Powerbook had to do research to find a Mac-compatible printer. Unfortunately, few Linux-compatible printers actually come with a little penguin logo on the side indicating they're Linux-friendly, so your grandmother would have to go here:

[https://wiki.ubuntu.com/HardwareSupportComponentsPrinters](https://wiki.ubuntu.com/HardwareSupportComponentsPrinters)

Frankly, I see these as non-issues for two reasons:

1. Oh, Ubuntu doesn't autodetect your NTFS partition? Well, does Windows autodetect your Ext3 partition? Nope. It's a double standard.

2. People who find copying and pasting a few terminal commands generally don't install operating systems. They buy computers with operating systems (usually Windows) preinstalled.

---

### Post by Boris Batkin on 2006-04-12
I'm currenlty reading "Ubuntu FAQ Guide". It's full of recepies. Each of them involves the same pattern described above. For example "How do I install a P2P Gnutella Client (LimeWire)?" involves a 10 step process. My examples are just... examples. They are to illustrate the usability problem.

---

### Post by aysiu on 2006-04-12
One-click fixes... sounds like CNR for Ubuntu, which has been proposed and actually could be in the works...

---

### Post by Boris Batkin on 2006-04-12
As far as I understand ( [http://www.desktoplinux.com/news/NS7474779842.html](http://www.desktoplinux.com/news/NS7474779842.html) ,
[http://www.xyzcomputing.com/index.php?option=content&task=view&id=577](http://www.xyzcomputing.com/index.php?option=content&task=view&id=577) ) CNR looks like a similar idea. However it seems focused on installation of software packages.

What I was thinking of is a combination of signed shell scripts, a Web browser plugin, and perhaps a local key manager. 

It can use some additional infrastructure: most importantly, centralized key management and prescription signing. Centralized searching is a nice bonus, if anything.

---

### Post by aysiu on 2006-04-12
You're talking about a major overhaul in Ubuntu-land.

You may want to take a look at [this link](http://www.ubuntuforums.org/showpost.php?p=406504&postcount=1). Otherwise, I'm not sure where else to point you.

---

### Post by Boris Batkin on 2006-04-12
Thank you.
I'll email Mark and we'll see what happens.

---


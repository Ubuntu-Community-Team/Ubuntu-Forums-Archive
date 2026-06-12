---
title: "Anti-Virus for Linux Mint"
date: 2016-10-19
forum: MINT
---

### Post by rosaleen on 2016-10-19
Hello

I'm relatively new to Linux Mint and I'm affraid I'm relatively easily ovewhelmed with any tasks that are exclusively performed using the command line terminal. A couple of days ago, Facebook informed me that my PC is infected with malware and I have restricted acess. While I doubt Facebook's ability to analyze threats on my PC, it has made me wary of using my computer for sensitive tasks.

I installed Sophos Anti-Virus. I think. I can't run it and I can't uninstall it. The fact that it's all performed with the terminal doesn't help. I guess I need help to 

a) uninstall sophos Anti-Virus and
b) find an Anti-Virus program for Linux that has some sort of interface.

I thank you all for any help you can give me!

---

### Post by howefield on 2016-10-19
Try the terminal command

```
sudo bash /opt/sophos-av/uninstall.sh
```

to uninstall it, although it is pretty good anti virus product in the event that you really need such a thing. Given that you have it installed it most likely wouldn't be too hard to learn how to use it. :)

ClamAV is in the repositories so you can install with the Software Centre or whatever the Mint equivalent to the Software Centre is.

Here are a couple of links for you to browse..

[https://help.ubuntu.com/community/ClamAV](https://help.ubuntu.com/community/ClamAV)
[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)

---

### Post by wyliecoyoteuk on 2016-10-19
Probably a scam.
Very unlikely that you are infected, and if you are Facebook wouldn't know anything about a mint install.

---

### Post by bearlake on 2016-10-19
Sophos Anti-Virus works very well.

--------------------------------------------------------------------
From the Terminal

At first you have to update the virus definitions with:

sudo /opt/sophos-av/bin/savupdate

Then you can scan for viruses.

# scan all file in /home #

    sudo savscan /home -all

# scan all file in /home #

or

# scan all files on sda #

    sudo savscan / -all

# scan all files on sda #



# scan from sda to mounted /Home on sdb. #

    sudo savscan /media/sam/Home/ -all 

# scan from sda to mounted /Home on sdb. #




If necessary start with root permissions: sudo savscan.

Examples:

    To check all files on the computer, displaying the name of each file:

    sudo savscan /
--------------------------------------------------------------------

Hope this helps a little.

---

### Post by rosaleen on 2016-10-19
First off, thanks for moving the topic in the right section. I was very unsure as to where to place it (that is, I couldn't find the appropriate section).

From what I gather, I would need to configure the AV Software using command lines. But I'm so fresh using Linux, I don't even understand why the command line you gave me works even though there is no uninstall.sh in the folder :shock: I better learn more about linux before I start using the anti virus.

I'm weirded out because of the Facebook notice, but how big are the chances of my having malware on my PC if I'm only using Linux?

I'll give those links a hard look, thanks!

ADDED: Also thanks to bearlake and wylecoyoteuk! Everything helps.

I do suspect a Facebook scam because 1. it only wouldn't let me log in from Firefox, with Chrome there was no problem and 2. they hand out links for software I can download, obviously only Mac and Windows. Sooooo.... it can't figure out I'm on Linux, but I knows if I have a virus? Also, it claimed there had been spamming action coming from my username and that's why I had a partial block, but no one in my (short) friend list saw anything of the sort. I'd sooner leave Facebook than I'd download something they recommend...

---

### Post by howefield on 2016-10-19
Might be worth looking at your browser extensions and checking for any that you didn't install, or at least knowingly install.

---

### Post by rosaleen on 2016-10-20
"kowingly" is key here! I really installed no extensions and my Firefox has already "warned" me that it needs an update.

The more I read about Anti Virus in Linux and the more I think about it, the more I'm unsure. Basically, as I gather, I CAN get a virus or malware. Except it won't be able to do anything because it's the same as downloading a file for windows or Mac and try tu run it under linux: it won't go, even if its presence may be recognized by third parties like Facebook. It's making me 1. wonder if I need an Anti Virus and 2. wonder if the malware can harm others just for being in my PC (i.e. me being an infected carrier and suffering none from it)

---

### Post by howefield on 2016-10-20
> **rosaleen said:**
> "kowingly" is key here! I really installed no extensions and my Firefox has already "warned" me that it needs an update.

So, there are no extensions that ring any alarms bells in your Firefox preferences ?

Shouldn't be any surprise that Firefox is due for updating, happens regularly. How are you being notified of the update, through your normal update routine ?

> The more I read about Anti Virus in Linux and the more I think about it, the more I'm unsure. Basically, as I gather, I CAN get a virus or malware. Except it won't be able to do anything because it's the same as downloading a file for windows or Mac and try tu run it under linux: it won't go, even if its presence may be recognized by third parties like Facebook. It's making me 1. wonder if I need an Anti Virus and 2. wonder if the malware can harm others just for being in my PC (i.e. me being an infected carrier and suffering none from it)

That's a reasonable enough summary and pretty much what the[ link above]("https://help.ubuntu.com/community/Antivirus") has to say.

Perhaps you could take a screenshot of this mysterious "Facebook" intrusion.

---


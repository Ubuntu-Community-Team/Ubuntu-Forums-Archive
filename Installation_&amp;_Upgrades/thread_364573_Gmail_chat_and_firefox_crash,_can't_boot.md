---
title: "Gmail chat and firefox crash, can't boot"
date: 2007-02-18
forum: Installation &amp; Upgrades
---

### Post by Phlegethon13 on 2007-02-18
Hello,

I recently posted in this topic, but it seems it has fallen on the way side.

[http://ubuntuforums.org/showthread.php?t=285123](http://ubuntuforums.org/showthread.php?t=285123)

Basically, that one was about gmail and firefox crashing.  From the sounds of it the crash was minimal for those mentioned in that thread.

I have a different issue.  I can view gmail, send messages, read messages, search messages, everything BUT chat.  As soon as I hover over someone's name and click on "Chat" firefox crashes, then the gnome panels disappear and my mouse/keyboard stop responding.   Complete system freeze.

I proceed to restart my system and I get a boot error.  Specifically grub error 24.  That error, if my memory serves me, is when the boot record or boot partition is fubar'd.  I have no idea how gmail and firefox can do this.

I wish I could give you more information but I did a reinstall of ubuntu 6.10 to get back to a working state (luckily I have system and data partitions, so I am ok, just need to reconfigure gnome and reinstall some packages).

It should be just a default intallation of 6.10 with java, possibly flash (shouldn't make a difference, but I think I installed the plugin for firefox), and that is probably it.

Any ideas?  I am using Opera now, but still wary of going to gmail.

Thanks

Greg

[edit]
Oh, and in the thread I linked, there is talk of changing your color depth to 24.  I did not do that because everyone in there has a nvidia card, I have an ATI.  System: ubuntu 6.10 w/ updates, ATI 9250.    Thanks...
[/edit]

---

### Post by Phlegethon13 on 2007-02-18
Oh, it almost happened again.

I am using Opera now (version 9.10 build 521) and this time, after using gmail for a while, chatting successfully, but leaving gmail open (with the chat window open inside gmail) for probably 20 minutes when I came back Opera was frozen, but I was able to kill it.  I have the problem report from Opera.  So if anyone wants it, or parts of it I can supply.

It seems to me now, with the problem manifesting itself in both Firefox and Opera that is it a java issue.

Anyone have any insight?


Thanks,

Greg

---

### Post by Phlegethon13 on 2007-02-18
So, now that I am using Opera (9.10 build 521) it happened again, only not the same this time.

This time I used gmail, chatted successfully, but left gmail open for probably 20 minutes while I was away from the computer.  When I returned Opera was not responding.  Luckily I was able to kill Opera without having any other adverse effects on ubuntu.  In fact, now I am back in Opera and everything seems fine.

I have the crash/problem report for Opera if anyone wants it or a part of it.

And, now that the same type of issue has happened with both Firefox and Opera I am wondering if it is a java or flash issue.

I am going to revisit the post I linked to in my orignal comment, see if they have any ideas.

Thanks,

Greg

[edit]
Sorry for the double post, I thought I lost the first one, it wasn't showing up at first.  This one is probably better worded anyways.
[/edit]

---

### Post by mdecler2 on 2007-02-24
I have an identical problem with FF. However, when I chat, FF usually crashes when I have recieved several gmail chat responses within a minute. My roommate is purposefully sending me hanous amounts of chat messages when my gmail is open to criticize my Ubuntu OS. :)
I know I could block him, but I'd rather fix the problem first.

When FF crashes from the gmail chats, it just hangs, and I have to kill it with a -9. I think gmail chat is a Java feature...but I am not sure. I have been having other problems with Java as well, including very slow performance on the VNES site, and random crashes when I try to start some of the Java games there.

Perhaps anyone has any insight? I tried installing the new Java plugin for FF, but I have no idea if it is using that plugin or some old automatix garbage I installed several months ago.

---

### Post by Danny Boy on 2007-02-25
I've never experinced the a problem with Google Gmail/Talk in FF or Opera on Ubuntu. 

If it's causing that much of a problem, connect with Gaim, here is Google step by step:

[http://www.google.com/support/talk/bin/answer.py?answer=24073](http://www.google.com/support/talk/bin/answer.py?answer=24073)

---

### Post by mdecler2 on 2007-03-02
I see this as a cool alternative...unfortunately I don't use Google Talk enough to put in extra effort into signing in everytime I am logged on. I just get chat messages once and a while while I am writing some emails. 
Am I correct in saying that Google will not forward chat messages sent to me through gaim? That seems like something Google cannot do without a FIrefox plugin.
I am going to figure out how I can re/install a new version of the java_vm. I can think of no other alternative.

---

### Post by Danny Boy on 2007-03-02
> **mdecler2 said:**
> I see this as a cool alternative...unfortunately I don't use Google Talk enough to put in extra effort into signing in everytime I am logged on. I just get chat messages once and a while while I am writing some emails. 
Am I correct in saying that Google will not forward chat messages sent to me through gaim? That seems like something Google cannot do without a FIrefox plugin.
I am going to figure out how I can re/install a new version of the java_vm. I can think of no other alternative.

Since I connect most of the time with Gaim, I use gMail without chat. In gMail at the bottom of your inbox is the options to use gMail with or without chat. Just select the without chat option, your messages would automatically come to Gaim.

---


---
title: "Lubuntu runs quite slowly."
date: 2010-04-05
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by themusicalduck on 2010-04-05
I'm trying to resurrect a friends computer by installing Lubuntu 10.04 onto it. I hoped that it would be lightweight enough to provide a fairly responsive working laptop for him, but haven't been much impressed by it.

I'm wondering if I'm the only one who has experienced this, or if anyone knows any reasons why it wouldn't perform too well?

The laptop is an Inspiron 1300. It has 256mb of ram and a 1.7 celeron. The specs are pretty underwhelming, but I figured it would handle Lubuntu alright.

Everything will run in Lubuntu, and it boots fairly quick. But in general use it's quite sluggish. The mouse will move choppily about half the time (basically whenever Lubuntu is doing something).

Browsing the internet is pretty tiresome as it takes a good while to open a new window or load a page with epiphany (chromium is worse). Trying to type a document can be slow. Doing something as simple as copy and pasting text can take a good few second while the laptop locks up and switching windows can take up to ten seconds or more.

Browsing the internet and using open office is pretty difficult.

The taskbar has a CPU indicator which is full whenever it does something (save a document, paste text). The weird thing is, if I run top in a terminal, nothing shows up as using CPU when it is like this. The top CPU users just sit at 5% or so, which means I can't find out what is the biggest cause of the slowdowns.

Last I checked, nearly all the ram was being used while running some applications, which is probably to be expected.

I guess my question is, am I expecting too much for it to run well on this machine? Should I try something lighter than Lubuntu?

---

### Post by kerry_s on 2010-04-06
> I guess my question is, am I expecting too much for it to run well on this machine? Should I try something lighter than Lubuntu?

yes! linux software is constantly updated & it's done on newer machines, no one really cares how there stuff runs on the old crap. 
you can still get by using some of the older lighter programs.

for you it would be great if you could add more ram.
if not, try lenny lxde, i'm using it on 450mhz 256mb ram.
[http://cdimage.debian.org/debian-cd/5.0.4/i386/iso-cd/debian-504-i386-businesscard.iso](http://cdimage.debian.org/debian-cd/5.0.4/i386/iso-cd/debian-504-i386-businesscard.iso)

select the advanced-> other desktops-> lxde

---

### Post by Longinus00 on 2010-04-06
> **themusicalduck said:**
> I'm trying to resurrect a friends computer by installing Lubuntu 10.04 onto it. I hoped that it would be lightweight enough to provide a fairly responsive working laptop for him, but haven't been much impressed by it.

I'm wondering if I'm the only one who has experienced this, or if anyone knows any reasons why it wouldn't perform too well?

The laptop is an Inspiron 1300. It has 256mb of ram and a 1.7 celeron. The specs are pretty underwhelming, but I figured it would handle Lubuntu alright.

Everything will run in Lubuntu, and it boots fairly quick. But in general use it's quite sluggish. The mouse will move choppily about half the time (basically whenever Lubuntu is doing something).

Browsing the internet is pretty tiresome as it takes a good while to open a new window or load a page with epiphany (chromium is worse). Trying to type a document can be slow. Doing something as simple as copy and pasting text can take a good few second while the laptop locks up and switching windows can take up to ten seconds or more.

Browsing the internet and using open office is pretty difficult.

The taskbar has a CPU indicator which is full whenever it does something (save a document, paste text). The weird thing is, if I run top in a terminal, nothing shows up as using CPU when it is like this. The top CPU users just sit at 5% or so, which means I can't find out what is the biggest cause of the slowdowns.

Last I checked, nearly all the ram was being used while running some applications, which is probably to be expected.

I guess my question is, am I expecting too much for it to run well on this machine? Should I try something lighter than Lubuntu?

I find xubuntu to be very usable (for light web browsing, nothing flash heavy) on a p3 800mhz with 256mb or ram. It's got karmic but still should be heavier weight than lucid lubuntu. You should not have to use a year old distro(leny) to get decent computing.

If you pay attention in top you'll probably find that your iowait (wa in the cpu line) is maxed out every time it feels slugish. What is likely causing this is the computer running out of ram and having to swap like crazy. On first boot my computer has around 100MB+ of free ram so your friends computer should have more.

There's a bug in ureadahead that murders ram everytime it does a reprofile so I have to reboot twice when that happens or else the computer is virtually unusable.

---

### Post by themusicalduck on 2010-04-06
I tried rebooting the PC about 4 times times and checked ram usage on bootup. So far every time around 200mb has been in use. After a little while this seems to increase to all the ram except for about 10 mb.

Anothing strange thing. This is shown in top. I installed htop to be able to see things a bit more clearly, and htop shows as only 80mb being in use!

However, system profiler and benchmark shows there being about the same amount of ram being used as what top shows.

This suggests there is something wrong with ram usage, it makes sense that its relying too much on swap, because the hdd light goes crazy when it starts to run slowly.

Is there any known workaround for this bug? Or should I perhaps try Karmic instead? Though it would be nice to install Lucid now so it doesn't need upgrading later.

EDIT: Actually, if my memory is right, top shows how much ram is reserved and how much in use as together doesn't it? So perhaps htop is accurate and this is just the best performance I'll get out of it.

---

### Post by Longinus00 on 2010-04-06
Top shows all memory consumed, including memory used by the disk cache and buffers. An easier way to check free memory is to run free.
```
$ free -m
             total       used       free     shared    buffers     cached
Mem:          3962       1585       2376          0        207        484
-/+ buffers/cache:        893       3068
Swap:         5122          0       5122

```

The line you are looking for is the one that goes "-/+ buffers/cache:". The following two numbers are the amounts of memory that your computer has used and is free after taking into account buffers and cache.

---

### Post by themusicalduck on 2010-04-06
Ah, thanks. In that case there is about 100mb free with a few apps open, which is reasonable.

It actually seems to be running a bit better after updating today. There was a new kernel which might have fixed something. I'll continue testing it and hope that it stays this way.

---

### Post by phillw on 2010-04-06
> **themusicalduck said:**
> Ah, thanks. In that case there is about 100mb free with a few apps open, which is reasonable.

It actually seems to be running a bit better after updating today. There was a new kernel which might have fixed something. I'll continue testing it and hope that it stays this way.

Hi, which version of Lubuntu are you using? If you are using 10.04, then I'd advise you add the lubuntu ppa for the latest versions of the desktop system.

I have added the instructions to the wiki page [https://wiki.ubuntu.com/Lubuntu#Download](https://wiki.ubuntu.com/Lubuntu#Download) Lubuntu

I'm not very familiar with editing wiki pages, so it may be easier to read the original instructions over at [http://forum.phillw.net/viewtopic.php?f=4&t=54&p=73#p73](http://forum.phillw.net/viewtopic.php?f=4&t=54&p=73#p73)

Regards,

Phill.

---

### Post by Longinus00 on 2010-04-06
> **themusicalduck said:**
> Ah, thanks. In that case there is about 100mb free with a few apps open, which is reasonable.

It actually seems to be running a bit better after updating today. There was a new kernel which might have fixed something. I'll continue testing it and hope that it stays this way.

The system may also become pretty bogged down while it's doing a check for new updates as that causes a lot of disk access. It's doubly bad in my case because my hard drive has seen its fair share of abuse (laptop hd) and has many bad sectors and seek errors. If you feel confident you can change how often the auto update happens or you can disable it entirely.

---

### Post by themusicalduck on 2010-04-06
Thanks phillw, I installed the updates.

It seems like all the updates together have improved things greatly, since it's running pretty much as I'd expect now. Hopefully it stays like this after future updates.

Thanks for the helpful replies.

---

### Post by phillw on 2010-04-07
> **Longinus00 said:**
> 
you can change how often the auto update happens or you can disable it entirely.

Hi, there is no auto-update in Lubuntu 10.04; it's on the list of 'things to do' :)

A full decision on the least processor / resource hungry method has not been reached yet, possibly using cron and the update script in post #7 was / is one option that was under discussion.

Regards,

Phill.

---

### Post by phillw on 2010-04-07
> **themusicalduck said:**
> Thanks phillw, I installed the updates.

It seems like all the updates together have improved things greatly, since it's running pretty much as I'd expect now. Hopefully it stays like this after future updates.

There does seem to be couple a things that were being 'pulled in' from Ubuntu 'main' that can cause a performance loss (i.e. using more resources). I'm without my emails at the moment, but I do know it is being looked at; a fix may be out for it, there was certainly one committed. 

To keep track of the development you can join the mailing list over here --> [https://wiki.ubuntu.com/Lubuntu#Joining](https://wiki.ubuntu.com/Lubuntu#Joining) the Team & Participating  You will get information on Lubuntu far faster than relying on me relaying information :)

Regards,
Phill.

---


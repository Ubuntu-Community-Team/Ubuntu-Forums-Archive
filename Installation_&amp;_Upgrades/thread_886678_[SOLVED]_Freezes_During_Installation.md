---
title: "[SOLVED] Freezes During Installation"
date: 2008-08-11
forum: Installation &amp; Upgrades
---

### Post by zdunham on 2008-08-11
Alright here is what has been going on:

I'm making an internet kiosk at work using Ubuntu so people can go on sites that are blocked by the rest of the network, emails, etc. This computer is a VERY OLD IBM. First I tried to install Ubuntu and I got to the screen where you select partitioning and such. I told it to just use the whole drive and it failed and wanted to resize the drive. So I used a Windows CD to format the drive and then went back to the Ubuntu disk and now it freezes every time right before it loads up the screen after I choose Install. It also freezes if I try to run from disk right after I choose run from disk. I was thinking this could be due to lack of memory since the machine is so old. I wasn't told how much it has but it's pretty bad, really bad. Any other opinions? Thanks in advance.

---

### Post by snowpine on 2008-08-11
> **zdunham said:**
> Alright here is what has been going on:

I'm making an internet kiosk at work using Ubuntu so people can go on sites that are blocked by the rest of the network, emails, etc. This computer is a VERY OLD IBM. First I tried to install Ubuntu and I got to the screen where you select partitioning and such. I told it to just use the whole drive and it failed and wanted to resize the drive. So I used a Windows CD to format the drive and then went back to the Ubuntu disk and now it freezes every time right before it loads up the screen after I choose Install. It also freezes if I try to run from disk right after I choose run from disk. I was thinking this could be due to lack of memory since the machine is so old. I wasn't told how much it has but it's pretty bad, really bad. Any other opinions? Thanks in advance.

Ubuntu is not always the best choice for "very old" computers; it is a modern, full-featured OS that is optimized for today's computers. The minimum ram to install Ubuntu from the Live CD is 384mb, and that is no guarantee of "snappy" performance. Without more info, the best recommendation I can give is to try installing Xubuntu using the Alternate CD, which only requires 128mb of ram.

Why don't you find out the specs for this computer (one way to tell if it has no OS installed is by running Setup at the initial bios screen) so we can make a recommendation.

---

### Post by zdunham on 2008-08-11
Well then if memory is the case, (I'll find out the specs in a few), is there a different linux distribution that requires WAY less RAM? I have the feeling this computer doesn't even have 128 MB but I could be wrong.

---

### Post by snowpine on 2008-08-11
> **zdunham said:**
> Well then if memory is the case, (I'll find out the specs in a few), is there a different linux distribution that requires WAY less RAM? I have the feeling this computer doesn't even have 128 MB but I could be wrong.

DSL (Dam* Small Linux) and Puppy are two of the most popular distros for old computers. They both run from Live CDs so you can test them out. Good luck!

---

### Post by zdunham on 2008-08-11
> **snowpine said:**
> DSL (Dam* Small Linux) and Puppy are two of the most popular distros for old computers. They both run from Live CDs so you can test them out. Good luck!

Any that you know of that install? I need to make the machine as secure as possible, meaning that the users on it cannot install anything and cannot do anything except browse the internet basically. Except me of course I'll be admin :).

---

### Post by snowpine on 2008-08-11
> **zdunham said:**
> Any that you know of that install? I need to make the machine as secure as possible, meaning that the users on it cannot install anything and cannot do anything except browse the internet basically. Except me of course I'll be admin :).

DSL and Puppy can both install to a hard drive. I just meant that, because they run from Live CD, you can test to make sure you like them and they run on your hardware, before you go through the trouble of a hard disk install. 

I will point out however that running an OS from a Live CD is incredibly secure, since the medium is read-only!  :)

ps Try a google search for "kiosk linux" for example: [http://www.ehartwell.com/InfoDabble/HowTo:_Create_a_boot-from-CD_browser_kiosk_with_Firefox_and_Linux](http://www.ehartwell.com/InfoDabble/HowTo:_Create_a_boot-from-CD_browser_kiosk_with_Firefox_and_Linux)

---

### Post by zdunham on 2008-08-11
Thanks alot I'll try it out.

---

### Post by zdunham on 2008-08-11
Do you happen to know if I can install KDE on any of those distros?

---

### Post by snowpine on 2008-08-11
> **zdunham said:**
> Do you happen to know if I can install KDE on any of those distros?

KDE is not light-weight. I imagine you can add KDE to just about any distro, but the question is, will its performance be satisfactory on your system specs? I've only used it once, but I would say IceWM is the lightweight alternative that's most similar to KDE.

---

### Post by zdunham on 2008-08-11
> **snowpine said:**
> KDE is not light-weight. I imagine you can add KDE to just about any distro, but the question is, will its performance be satisfactory on your system specs? I've only used it once, but I would say IceWM is the lightweight alternative that's most similar to KDE.

Nice I'll try that with DSL. I might be able to limit user permissions enough with whatever DSL comes with I'll have to see. Thanks alot.

---

### Post by zdunham on 2008-08-12
DSL is so annoying to use I just cannot do it. I'm going to try Xubuntu on there, previously Mandriva was successfully installed, although it says it requires more than this computer has. This comp has 128 MB RAM and a 650 MHz processor....don't laugh. Mandriva says it requires more than that but it still worked. It has roughly the same requirements as Xubuntu from what I've seen so I'll try that because the interface is so much nicer.

---

### Post by snowpine on 2008-08-12
> **zdunham said:**
> DSL is so annoying to use I just cannot do it. I'm going to try Xubuntu on there, previously Mandriva was successfully installed, although it says it requires more than this computer has. This comp has 128 MB RAM and a 650 MHz processor....don't laugh. Mandriva says it requires more than that but it still worked. It has roughly the same requirements as Xubuntu from what I've seen so I'll try that because the interface is so much nicer.

Xubuntu should work, just be sure to use the Alternate Install CD rather than the Live CD. And if you can get an extra stick of ram... :)

---

### Post by snowpine on 2008-08-12
ps You may find some helpful information in this thread: [http://ubuntuforums.org/showthread.php?t=873112](http://ubuntuforums.org/showthread.php?t=873112)

---

### Post by zdunham on 2008-08-12
Thanks alot, I'll post how it all goes after it's installed.

---

### Post by zdunham on 2008-08-12
Thanks Snowpine, it boots up with no problems now I just have to update and install some printing software and limit the guest user :)

---


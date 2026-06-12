---
title: "Thunderbird 3 on Karmic Koala a.k.a. Ubuntu 9.10"
date: 2009-07-16
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by motang on 2009-07-16
I been using Thunderbird 3 beta 2 to pre beta 3 on all my computers on various platforms and it is much faster than Thunderbird 2 and a huge improvement as well in my opinion.  I just downloaded the soon to be out beta 3 and loving it. It integrates very well into OS (the look part) like FF 3.x does, so it doesn't matter if you are on Ubunut or Win (I don't have access of OS X) it looks part of the OS. I was wondering if it will be part of Ubuntu Karmic Koala (or available in the repos) instead of Thunderbird 2? Thanks.

---

### Post by scouser73 on 2009-07-16
Sounds good, I think Thunderbird is excellent, I used it on XP, and when I switched to Ubuntu I downloaded it. It's simply the best email client, so I can't wait for Thunderbird 3 to come along.

---

### Post by edam on 2009-09-06
Unfortunately, a [search for "thunderbird"]("http://packages.ubuntu.com/search?suite=karmic&section=all&arch=any&searchon=names&keywords=thunderbird") in karmic's packages turns up a lot of packages relating to thunderbird 2...  :(

I really want TB3 as well. They've added support for message filters on a per-folder bases for IMAP accounts, which I need. I hope it makes it in karmic.

Anyone else got any info on this?

---

### Post by | MM | on 2009-09-06
You can check out the Mozilla Daily PPA if you want Thunderbird 3.

[https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa](https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa)

---

### Post by motang on 2009-09-06
Yep, I am using the Mozillas PPA and currently using Thunderbird 3 Beta4pre and loving it. :D

---

### Post by nanog on 2009-09-06
Yes...in my experience beta4pre is faster and more stable than thunderbird 2 (especially for imap). I wish evolution was a functional alternative but for imap and exchange (required for my job) it just does not work well. Its one of the first things I uninstall.

---

### Post by wfp on 2009-09-06
Will have to give it a try. Been using Thunderbird for years now. Looking back it is the only application that I have Never had a problem with rock solid.

---

### Post by motang on 2009-09-06
Yes, it is very much rock solid, and I have been using the mail app since it was bundled with Netscape back in the late 90s. :D

---

### Post by VMC on 2009-09-07
I forgot about this topic. I reminded myself to check out version 3. I'm using version 2 right now. I like Thunderbird much better than Evolution anyway.

---

### Post by sports fan Matt on 2009-09-07
When I add the [https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa](https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa) and add the key from my desktop..and reload and check for updates..still shows I have Thunderbird version 2.0.0.23 (20090812)..Any Ideas?

---

### Post by zekopeko on 2009-09-07
> **sox fan Matt said:**
> When I add the [https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa](https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa)

You added this line in the software sources, right: ```
deb http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu karmic main
```

---

### Post by sports fan Matt on 2009-09-07
I did and even removed and re entered it and it doesnt pop up in the update manager.

---

### Post by MythAaron on 2009-09-07
What are the group's opinions about the tab feature?  It seems completely useless to me and I deactivated the feature.

---

### Post by DougieFresh4U on 2009-09-07
I found it in Synaptic after installing the ppa
Been using 3 version for a long time on other installs and love it.
'Shredder' is what they were calling the pre.

---

### Post by phenest on 2009-09-07
I think Thunderbird should be default instead of Evolution, and as such, get improved integration with Gnome, like email notifications.

---

### Post by sports fan Matt on 2009-09-07
Thanks Dougie..that worked

---

### Post by sports fan Matt on 2009-09-07
The same Thing I also see. When it does become Thunderbird will it drop the shredder name or be like Shiretoko?

---

### Post by DougieFresh4U on 2009-09-07
> **sox fan Matt said:**
> Thanks Dougie..that worked

Your welcome
Nice to see ya back.

---

### Post by sports fan Matt on 2009-09-07
Glad to be back...Would it be horrible if I went into the menu properties and renamed it to thunderbird?

---

### Post by motang on 2009-09-07
> **sox fan Matt said:**
> When I add the [https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa](https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa) and add the key from my desktop..and reload and check for updates..still shows I have Thunderbird version 2.0.0.23 (20090812)..Any Ideas?
So in Synaptic it shows Thunderbird 2.x? If so try TB3's code name Shredder.

---

### Post by Marat89 on 2009-09-08
HI
Is there any way to get other language pack? I need German, But I can not find the package for TB 3

---

### Post by sports fan Matt on 2009-09-08
Hi Marat,

There is this page: [http://www.mozillamessaging.com/en-US/thunderbird/early_releases/downloads/..with](http://www.mozillamessaging.com/en-US/thunderbird/early_releases/downloads/..with) a release in german.  

Can the mozilla build ppa be used as well? Im not sure if it would be translated into german. ( only way I think if German was the default lamguage at setup of Ubuntu, am i wrong?

---

### Post by Dgurion on 2009-09-27
Any chance of Thunderbird 3 making it into official repos? Its at Beta 4 now.. Pretty close to an RC release.

---

### Post by hblaw on 2009-09-28
> **phenest said:**
> I think Thunderbird should be default instead of Evolution, and as such, get improved integration with Gnome, like email notifications.

Not sure of this - whether Thunderbird 3 provides a wide-screen vertical view like evolution and Outlook? I think this layout best utilizes the screen.

---

### Post by froggyswamp on 2009-09-28
I'd also like Thunderbird 3 beta to be packed into Karmic, cause it's plain better then v 2.
Considering how slowly v 3 is being developed - hoping for a final release any time soon is useless.

---

### Post by rogerdean on 2009-09-28
Hi Matt
Once you've got the PPA repo set up you need to install the package 'thunderbird-3.0' rather than 'thunderbird'. It should use a new profile /home/.thunderbird-3.0 so you'll need to migrate your data too
Cheers
Roger

---

### Post by motang on 2009-09-28
> **hblaw said:**
> Not sure of this - whether Thunderbird 3 provides a wide-screen vertical view like evolution and Outlook? I think this layout best utilizes the screen.
Thunderbird 3.0 does have the wide view. That has been in since 2.0

---

### Post by sports fan Matt on 2009-09-28
I cant run any version of thunderbird since last week..it wont start...Ive had a few topics started and no one seems to understand why, but the package needed is libstdc++5.  Doing a sudo apt-get install libstdc 5 refers to no installation candiate, and trying to pull the package from the jaunty repos is a no go, I get a bad file descriptor.  So until this gets fixed Im having to use evolution, which is hard to get around :)

---

### Post by Guruji on 2009-09-28
Does Thunderbird 3 have Backup/Restore option like evolution? or gnome panel calendar integration (with lightning)?

---

### Post by MadMan2k on 2009-09-28
> **Guruji said:**
> or gnome panel calendar integration (with lightning)?
there is an extension for that - even works with thunderbird2. (Evolution Mirror)

---


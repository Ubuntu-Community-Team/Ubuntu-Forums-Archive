---
title: "[SOLVED] Disable updates FOR GOOD - pretty please?"
date: 2008-06-02
forum: Installation &amp; Upgrades
---

### Post by Thanh-BKK on 2008-06-02
Hello :)

I thought i had it done. You know, a 101% perfectly running system, only waiting to be messed up by some update.

So i did what i thought disabled updating - by setting it all to "manual".

But Ubuntu beat me - now, instead of "there are 49 updates, 3 of which may make your next reboot an adventure" i get ANOTHER nagging thing - "Your update information is outdated. Please check for potential disaster right now or i won't give you peace!"

Please please please - how can i make my Hardy to just forget that there are repositories and continue to just work as perfectly as it does?

I am sure there is a way to do just that.... please, someone, tell me how to..... many many thanks in advance.

Best regards......

Thanh

---

### Post by sports fan Matt on 2008-06-02
I guess im a tad lost..You just want to do the updates yourself cause youre worried the updates are doing something to your system?

---

### Post by Thanh-BKK on 2008-06-02
Hi :)

Kind of :) The thing is, my computer and Ubuntu are a total dream-team. No glitches, no bugs, no hiccups. And i very much want to keep it exactly that way.

Many many people have problems or discover bugs AFTER an update. And THAT i want to prevent - by simply not updating at all. 

So i set it to "manual", thinking "now the updater leaves me alone because i told him i'll do it myself". If i really do or not isn't the updater's business, thank you, i decide when or if i want to update.

Unfortunately Ubuntu won't let me make my own decision and forces me "thru the backdoor" to at least check for updates. I may still ignore them, yes. but i don't want to see ANY "update" nagging. 

Really, if i WANT to update, i'll check myself, i don't need a nanny telling me about it.

So, is it possible?

Best regards.....

Thanh

---

### Post by tk03759 on 2008-06-02
Did you try going to 'System' > 'Administration' > 'Software Sources' and then unchecking "Check for updates.." in the "Updates" tab. You may still recieve notifications about the updates you have right now, but you shouldn't be bothered about anymore.

You can do an "sudo apt-get upgrade" in terminal to just install the ones its bothering you about without making update manager check for more.

---

### Post by peterbrewer on 2008-06-02
One of the main reasons for updates is to maintain the security of your system.  Unless you are manually looking for security updates then I do not think it is sensible to disable the automatic updating service.  One on the main strengths of Linux is that it is open source so when bugs are found several people can work to patch them quickly and then distribute updates, however in the same way an open source system advertises the vulnerability so if you don't run the update you take a risk.

---

### Post by sports fan Matt on 2008-06-02
I see both points:

1.  A healthy, stable system is a great working system.  I TOTALLY get the fact you dont want things to break, we all dont.  

2.  But I also see Peter's point. If updates are there through "update manager", much like in windows and mac, its telling you "hey, we found a few glitches, here are the improvements".  Are they 100 percent foolproof?  Probably not depending on the update..But let me ask, What would happen if an update came through and you didnt update and then subsequently had wierd things going on with your computer?  I see both points, just something to think about.

---

### Post by jwmislan on 2008-06-02
> **peterbrewer said:**
> One of the main reasons for updates is to maintain the security of your system.  Unless you are manually looking for security updates then I do not think it is sensible to disable the automatic updating service.  One on the main strengths of Linux is that it is open source so when bugs are found several people can work to patch them quickly and then distribute updates, however in the same way an open source system advertises the vulnerability so if you don't run the update you take a risk.

 All true in theory, but hardy kernel 2.6.24-17 update recently caused thousands ~ of machines to reboot into busybox - by cause of not recognizing any root drive - and with new /dev/sdx designation for hardrives sata,ide - new kernel standard.
This by a kernel security update, - and for those currently installing hardy 8.04?
Are we  end users just lab rats?, or do canonical try any tests before they release major system updates like this?.

That's why some of us are weary about ubuntu updates.

Making matters worse is -
Bug reports state that canonical will not support a fix for this in the LTS 8.04 release. 

What's up with this??? what benefit does long term service give if not immediate fixes:arrow: for major problem conditions existing, discovered, or caused by rash updates. 

Here is a reference link to start with -
[http://ubuntuforums.org/showthread.php?t=809926](http://ubuntuforums.org/showthread.php?t=809926)

For more info on this subject, you can search the  ubuntu forums for  'hardy busybox' 

May be this will help some to decide if they want to do updates, or upgrades to hardy at this time.

---

### Post by rockface on 2008-06-02
You can turn off automatic-updates for good by going from 'system' then to the 'preferences' menu and selecting 'sessions'. All auto-started desktop settings are here.

This is how I set my machines up. I either check through console or synaptic
manually each day. 

I set up my machines this way for myself. This is not how I would set it up for other people and I would heed others words when they say leave it be. 

Ubuntu Linux is not Microsoft, they are far more trustworthy updates wise.
But alas even Ubuntu is not immune so I do see where you are coming from.

---

### Post by wolfen69 on 2008-06-02
if you see an update icon on your taskbar, just right click it and uncheck "show notifications".

---

### Post by Thanh-BKK on 2008-06-02
Hello :)

Thank you all very much for replying. I believe i can now mark this thread as "solved" - i found what caused that notification to pop up. My router "hung up on me", it does that when i had a successful day, torrent-wise, and pumped a LOT of data thru - like yesterday, i moved over 10 GB in one session. So while torrents were still going, http failed me (it also wouldn't open web sites). 

Apparently, what Ubuntu was complaining about was NOT that i didn't update but that it couldn't connect to the update server/repository. Once i had my router rebooted, it checked on the repos and came back with "Your system is up to date". I like to see that, even knowing it's NOT up to date (i did NOT install that new kernel - for i have read far too many horror stories about it, altough on my second, "test" computer, it installed and works without a glitch.

I understand fully about the "security" related issues, however as i mentioned before, i have no stuff on my computer that would be of any interest to any hacker out there, plus my router itself has a firewall built-in, too, so i feel safe with Ubuntu.

I am right now in the process of installing Hardy on my third (and last) computer ("last" because i have "only" three), thanks to the great people on this forum this is possible as they have given me instructions how to get it done (that machine won't boot from CD and i can't get into the BIOS - Compaq!) and after that's done i am officially and completely 100% Windows-free. And as soon as my boyfriend becomes familiar with Ubuntu i will sneak it onto his laptop too, and that day i'll have a sticker made to put on the outside of my apartment door:

Attention - you are entering a Windows-free area!

With best regards.......

Thanh

---


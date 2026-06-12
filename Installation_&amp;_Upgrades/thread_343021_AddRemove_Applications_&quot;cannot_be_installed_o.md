---
title: "Add/Remove Applications &quot;cannot be installed on your computer type&quot;"
date: 2007-01-20
forum: Installation &amp; Upgrades
---

### Post by EmilyRose on 2007-01-20
Hi there, I just installed Ubuntu today, and am having problems with the Add/Remove applications. I started installing gmail notifier but then realized I needed to make a phone call so I canceled and logged off (I'm on dialup), and when went to retry I got a "cannot be installed on your computer type (i386). Either the application requires special hardware features or the vendor decided to not support your computer type." - this is now true not just of gmail notifier but of nearly all of the applications. What happened when I clicked cancel? And what do I have to do to fix it?? 

Lots of thanks in advance!!

Emily

---

### Post by taurus on 2007-01-20
Paste the output of this command from a terminal here.

Applications -> Accessories -> Terminal
```
sudo apt-get update
```

---

### Post by EmilyRose on 2007-01-20
Hey there, it went through and downloaded/installed a whole bunch of packages... and so then I went and checked and Add/Remove apps works again!! Thank you SOO much!!

Emily

---

### Post by taurus on 2007-01-20
You're welcome.  Sometimes, it just needs to update the repos list.  ;)

---

### Post by wislon on 2007-02-09
I've tried this method, as well as doing the System > Administration > Software sources thing. Doesn't matter what I do, it keeps coming back and telling me that my list is out of date and that it needs to redownload it. I let it do that, and I still get this same error message.

Any more thoughts?

---

### Post by taurus on 2007-02-09
Try

```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by wislon on 2007-02-09
Thanks taurus,  am giving it a whirl now. The apt-get update keeps timing out now (murphy's law!), with the occasional bad sig GPG key error. We'll get there in the end, I am sure :)

---

### Post by wislon on 2007-02-10
Back again, still no joy. 

Tried the apt-get clean/update/upgrade, it found a few kernel upgrades and everything (which I believe has been a bit of a debacle in itself). Pulled everything down once it had all stabilised, but still can't use the add/remove (tho apt-get install seems to work just fine).

It was working in Dapper, but seems to have broken once I upgraded to Edgy (note that I **upgraded** and didn't do a clean, fresh install). Because my internet connectivity is limited, I added the Edgy CD to the repos list to reduce the amount of stuff I downloaded.

Could this have affected it? Another option I have considered is to uninstall the 'add/remove' app, and then reinstall, if someone could tell me what this app's name is to actually uninstall? :)

Please have a little patience with me, I am still relatively new to using ubuntu (and linux as a whole), and some stuff is not immediately obvious! :)

Thanks!

wislon

---

### Post by wislon on 2007-02-10
Aha! I think I have the solution!

After poking around a bit more on the forum, I came across a thread 

[https://help.ubuntu.com/community/Repositories/Ubuntu#head-5bbef89639d9a7d93fe38f6356dc17847d373096](https://help.ubuntu.com/community/Repositories/Ubuntu#head-5bbef89639d9a7d93fe38f6356dc17847d373096)

that explained about adding and setting up repositories. I went and had a look at the 'System > Administration > Synaptic Package Manager' (since this appears to be the be-all and end-all for all software installations) and had a look under its settings menu item. 

I noticed that ALL the repos on the 'Ubuntu 6.10' tab were **not** ticked (tho there's repositories links in my sources.list). They used to be, before I upgraded from Dapper, so this must have turned them off somewhere...

Anyway, I ticked them all.  Also, the only thing in 'Internet Updates'  that was ticked was 'Important Security Updates', and so I put a tick in 'Recommended Updates' too. I left everything else alone. When I hit 'Close', it told me my sources list needed to be updated, so I let it do its thing, and lo and behold (!), over 100MB of updates suddenly became available.

The very top one is 'app-install-data-commercial', which looks extremely promising. I've temporarily told it NOT to get OpenOffice, and have left it downloading the other 30-odd MB of stuff. If this fixes the problem (or not) I'll post back here, so it can hopefully help someone else one way or another.

---

### Post by wislon on 2007-02-10
Ha! It worked! taurus, you were right (of course). Had I had the right sources selected, your sequence of commands would have fixed it. Thanks for your input tho! :)

---

### Post by mrodent on 2008-03-29
Hi, 

pretty much a newbie/struggler with Linux

thanks to both I overcame this tricky first prob with 7.10.

I have a question tho: I don't like to rely on the Net always being there when I need it so like to keep relatively up to date versions of my vital software installation files on local media should my system crash or be nicked or be smashed or whatever, in circumstances where I have to reinstall everything fast and without the Net.

I did download the tar.gz of the latest Linux version of Thunderbird but, extracting the files, was completely unable to get it running.  I eventually found my way here.

Does anyone know anything about how to install TBird from the downloaded tar.gz???

Thanks,
Mike

---


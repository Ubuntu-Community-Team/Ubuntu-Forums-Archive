---
title: "Firefox 3.0 final"
date: 2008-06-18
forum: Installation &amp; Upgrades
---

### Post by Samfisher on 2008-06-18
Hey guys,
I was just wondering if Firefox 3.0 final is in the ubuntu repositories (well, i'm using the gamearena.com.au and internode mirrors - I'm in Australia :D)?

I also have the 'http://ppa.launchpad.net/fta/ubuntu' repository enabled.

However, I have not seen a firefox 3.0 update appearing in the update manager since 10am PDT, so I'm not entirely sure.
Is there a way to check if it's final or RC1/2?

And if I am using a release candidate and firefox 3.0 final is not yet in the ubuntu repositories, can someone show me how to install using the firefox-3.0.tar.bz2 from the mozilla website?

Thanks, much appreciated,
SamFisher

---

### Post by nsramkishen on 2008-06-18
Hi Samfisher,

Last week I installed some updates, and one of the updates was Firefox 3. I was wondering how it got installed before the official release. I did check the "About" dialog, and there was no mention of RC or anything. This morning (18 June 07:00 (GMT+05:30, Indian Standard Time)), there were a couple of updates for Firefox 3. Try the Update Manager now. It should list FF3.

Cheers...

---

### Post by wolfen69 on 2008-06-18
you're good to go.

hardy is gonna wind up being the best version ever, no doubt.

---

### Post by Samfisher on 2008-06-18
Nope, I still don't have anything in update manager unfortunately. I might try switching to the au.ubuntu.com mirror.

---

### Post by Firetech on 2008-06-18
When i upgraded just now, i got version 3.0+nobinonly-0ubuntu0.8.04.1 (I.E. no RC, no beta). This package is available in the hardy-updates ("Recommended updates") repository, make sure you enable it using synaptic or the "Software sources" utility.

---

### Post by SkonesMickLoud on 2008-06-18
In Firefox go to "Help >> About Mozilla Firefox"  If it says "Version 3.0", you're good.  If not, try updating again.  If that doesn't do it just wait a bit, your repo's will have it soon.

---

### Post by firsttry on 2008-06-18
Does anyone know if the final be available in the gutsy (7.10) repos as well? Anyone know when?

I have all gutsy and gutsy-updates in restricted, universe, multiverse and backports included in my sources.list, so it should be spotted when (if?) it is released.

I'm hoping it'll happen before the 24hr world record on spreadfirefox.com are up, otherwise might have to install it without the package manager (I'd prefer not to)!

---

### Post by Magnes on 2008-06-18
Downloading from repository won't count in the establishing of world record. You have to download it from the official site.

---

### Post by firsttry on 2008-06-18
I was wondering about that!

Still, will ff3 enter one of the official gutsy repositories?

---

### Post by tom56 on 2008-06-18
No, it won't.

---

### Post by TheAJKMan on 2008-06-18
Okay, I'm hoping this topic is still being watched, cos I'm just wondering if it has been released as version 3.0a8. I installed via the terminal window using 'sudo apt-get install firefox-3.0' otherwise, what is the best way to d/l and install the latest version of FF so that I do my bit towards the record :) Please keep in mind that I'm still a relative newb of linux :) THanks in advance.

---

### Post by firsttry on 2008-06-18
That sounds like alpha-8 to me, not the final release... I'm surprised it's not being backported, isn't that what gutsy-backports is for? FF is the default Ubuntu browser and a 2->3 update is quite an important one.
I can't upgrade to hardy yet as I use Ubuntu at work, but even though gutsy is not LTS shouldn't this update be included in the backports repo?

---

### Post by TheAJKMan on 2008-06-18
firsttry, I figured that, was hoping someone would take note of my own plea for help and help me install the final version. The Firefox site doesn't have any help there that I have been able to find. I have it downloaded to my desktop, but absolutely no idea how to install it from there. And in my efforst, I think I messed some things up, cos I now no longer have a help button in my launch panel either :( *sigh* The joys of being a newb ;)

---

### Post by firsttry on 2008-06-18
To install it without a package manager I would create a directory called /opt, if you don't have it already:
```
mkdir /opt
```
copy your downloaded firefox into that directory, change to it and then run:
```
tar xvjf firefox-3.0.tar.bz2
```
Then you can run firefox by typing
```
/opt/firefox/firefox
```
in the shell. You then have to add icons and all to the menus manually.

---

### Post by TheAJKMan on 2008-06-18
Err, there may be a minor problem doing it that way. When I initially d/l the tarball, I said to open it automatically in the archive manager. I then extracted it to my desktop in a folder called firefox. I don't have the .tar.bz2 file anymore. Should I just d/l that file again and save it to my desktop and then run your suggestion?

---

### Post by firsttry on 2008-06-18
Yep, or simply move that directory into /opt. All the tar command does is extract it. You should be able to run the firefox from that directory to load ff3 wherever it's located, but in general I try to stick to installing programs without a package manager into the /opt directory though.

---

### Post by TheAJKMan on 2008-06-18
firsttry, I've got it running, but was a battle to get it going. Fisrt tried as you suggested and in a polite way it told me I couldn't copy into the /opt directory(which existed already), so I started muttering. Then I remembered something someone had told me about nautilus, so I copied the tar file using nautilus, after a bit of battling finally managed to get the archive manager to extract it. Now am running it. Now, I just have to work out how to get icons onto the start menu and onto my panel. But, that is a lesson for another day :) Thanks for your help, it is appreciated :)

---

### Post by z0mbie on 2008-06-18
I don't think it adds to the Firefox counter when you download from the repositiories. You can download the tar package from Firefox's website so your download is recorded. Essentically RC3 is the final product if you're worried about an up to date version.

Here's a thorough guide from Ubuntu's documentation:

[https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)

---

### Post by lsutiger on 2008-06-18
On 7.10

I d/l and unpacked to /usr/lib/mozilla/firefox. It ran fine, but it would not  install the flash plugin. When I d/l, unpacked and ran the install for flash,  it seemed to have worked. BUT, when I try to view a flash video, it crashes.

---


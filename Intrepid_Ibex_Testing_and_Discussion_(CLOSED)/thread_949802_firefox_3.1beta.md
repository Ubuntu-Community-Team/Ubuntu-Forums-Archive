---
title: "firefox 3.1beta"
date: 2008-10-16
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by naubusan on 2008-10-16
How is it working in Intrepid??

---

### Post by aysiu on 2008-10-16
> **naubusan said:**
> How is it working in Intrepid??
I just tried it yesterday, It works fine. I can't say I'm a big fan of the new Control-Tab behavior. If that keeps up and there's no easy way to fix it in about:config or through an extension, I may have to ditch Firefox.

Why would ever want to keep switching back and forth between the two most recently used tabs?

---

### Post by zoomy942 on 2008-10-16
3.1?  howd you get that?  i have 3.0.3

---

### Post by aysiu on 2008-10-16
> **zoomy942 said:**
> 3.1?  howd you get that?  i have 3.0.3
Oh, I just downloaded it from the Mozilla website to test it out. I reverted back to 3.0.3 within minutes. I can't stand the new Control-Tab behavior.

---

### Post by OrangeCrate on 2008-10-16
> **aysiu said:**
> Oh, I just downloaded it from the Mozilla website to test it out. I reverted back to 3.0.3 within minutes. I can't stand the new Control-Tab behavior.

I'd like to try it, but I'm reluctant to add non-repo stuff to development software. I guess I'll just wait until Intrepid goes final. It's not long now...

---

### Post by aysiu on 2008-10-16
Well, it doesn't really interfere with the repositories version. It's a .tar.bz2 you can just download and "install" next to the current Firefox.

To try it out, paste these commands into the terminal: ```
wget -c http://jp-nii02.mozilla.org/pub/mozilla.org/firefox/releases/3.1b1/linux-i686/en-US/firefox-3.1b1.tar.bz2
cp -R ~/.mozilla ~/.mozilla.backup
sudo tar -jxvf firefox-3*.tar.bz2 -C /opt
rm firefox-3*.tar.bz2
sudo mv /opt/firefox/plugins /opt/firefox/plugins.backup
sudo ln -s /usr/lib/xulrunner-addons/plugins /opt/firefox/plugins
sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
sudo ln -s /opt/firefox/firefox /usr/bin/firefox
``` if you want to revert back to the repositories version of Firefox, paste these commands in: ```
sudo rm /usr/bin/firefox
sudo dpkg-divert --rename --remove /usr/bin/firefox
sudo rm -r /opt/firefox
```

---

### Post by talkingwires on 2008-10-16
I was secretly hoping the 3.1 beta would pop up on getdeb.net, but no luck. Does anyone know if the official tarball uses a different folder than ~./mozilla/firefox so that you can try it out without messing up 3.03?

---

### Post by aysiu on 2008-10-16
If you use the instructions I just gave, the second command backs up your settings folder, so you'd just restore the backup if it somehow got screwed up.

---

### Post by go7Ul1ai on 2008-10-16
> **talkingwires said:**
> I was secretly hoping the 3.1 beta would pop up on getdeb.net, but no luck. Does anyone know if the official tarball uses a different folder than ~./mozilla/firefox so that you can try it out without messing up 3.03?

You can download Ubuntu Tweak- [http://ubuntu-tweak.com](http://ubuntu-tweak.com) . When it's installed (.deb available), click onto third-party software, select the "Firefox Development version", update then enter in a terminal:

```
sudo apt-get install firefox-3.1
```

This will install the latest version of 3.1 as "minefield", the codename of firefox, this way it keeps your current version of Firefox. 

I hope this helps,

Lee

---

### Post by gjoellee on 2008-10-16
I think Firefox 3.1 is quit good, but the Ctrl+Tab pictures you get are not really good. They should be improved!

---

### Post by explemonk on 2008-10-16
> **aysiu said:**
> Oh, I just downloaded it from the Mozilla website to test it out. I reverted back to 3.0.3 within minutes. I can't stand the new Control-Tab behavior.

I hate it too.  It can be disabled in about:config by setting

browser.ctrlTab.mostRecentlyUsed
browser.ctrlTab.smoothScroll

to false.

---

### Post by aysiu on 2008-10-16
> **explemonk said:**
> I hate it too.  It can be disabled in about:config by setting

browser.ctrlTab.mostRecentlyUsed
browser.ctrlTab.smoothScroll

to false.
Thanks. I'll have to try that.

---

### Post by swj on 2008-10-16
3.1B seems to be a little faster (gmail)...and ablock plus 0.7.5.5 works!  Whats not to like?

Oh, I never used the Ctrl+Tab anyway. ;)

---

### Post by ubulette on 2008-10-17
I maintain a package since day 1.
See [https://launchpad.net/~fta/+archive](https://launchpad.net/~fta/+archive)
It didn't make it into Intrepid, so I will upload it in Jaunty in a few weeks.

---

### Post by plun on 2008-10-17
> **ubulette said:**
> I maintain a package since day 1.
See [https://launchpad.net/~fta/+archive](https://launchpad.net/~fta/+archive)
It didn't make it into Intrepid, so I will upload it in Jaunty in a few weeks.

Thanks for that...:)

I still don't know who to file bugs running your repo :confused:

Mark them in a special way ?

Thunderbird 3 is just great.. including Lightning..:)

---

### Post by ubulette on 2008-10-17
> **plun said:**
> Thanks for that...:)

I still don't know who to file bugs running your repo :confused:

Mark them in a special way ?

Thunderbird 3 is just great.. including Lightning..:)

you can come ask on IRC, as mentioned in the header of my PPA.

I'm a member of the Ubuntu Mozilla team so i'm always in. Just lurk there until i show up, or PM me. Or better, ask publicly, someone will answer immediately, or I will when I come back.

---

### Post by Sand Lee on 2008-10-17
> **explemonk said:**
> I hate it too.  It can be disabled in about:config by setting

browser.ctrlTab.mostRecentlyUsed
browser.ctrlTab.smoothScroll

to false.

I agree, the new ctrl+tab is a real turnoff.

---

### Post by ubulette on 2008-10-17
> **explemonk said:**
> I hate it too.  It can be disabled in about:config by setting

browser.ctrlTab.mostRecentlyUsed
browser.ctrlTab.smoothScroll

to false.

I don't hate it as I'm not really using it. I prefer the new [_Ctrl-Tab_ extension]("http://en.design-noir.de/mozilla/ctrl-tab/") (from where this feature initially came from) changing the list at the far right of the tab bar into something fancy.

---

### Post by plun on 2008-10-17
> **ubulette said:**
> you can come ask on IRC, as mentioned in the header of my PPA.

I'm a member of the Ubuntu Mozilla team so i'm always in. Just lurk there until i show up, or PM me. Or better, ask publicly, someone will answer immediately, or I will when I come back.

Ok...

Maybe better to mark bugs with [fta ppa]  :confused:

But.. there are nearly no bugs...  copy/paste was a trouble a week ago. 


Also a late congrats for being a Motu....:lolflag:   Just great !  


(I also don't like IRC for different reasons...)

---


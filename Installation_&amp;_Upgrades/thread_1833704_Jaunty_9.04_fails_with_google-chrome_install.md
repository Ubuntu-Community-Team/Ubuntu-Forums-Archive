---
title: "Jaunty 9.04 fails with google-chrome install"
date: 2011-08-26
forum: Installation &amp; Upgrades
---

### Post by cfgauss on 2011-08-26
I have 9.04 and can't upgrade at this time. I have the correct old-releases 9.04 repositories. When I try to install google-chrome-beta google-chrome-stable or google-chrome-unstable I get these errors:
```

The following packages are BROKEN:
  google-chrome-beta 
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 24.3MB of archives. After unpacking 98.4MB will be used.
The following packages have unmet dependencies:
  google-chrome-beta: Depends: libasound2 (> 1.0.22) but 1.0.18-1ubuntu9 is installed.
                      Depends: libc6 (>= 2.11) but 2.9-4ubuntu6.3 is installed.
                      Depends: libcups2 (>= 1.4.0) but 1.3.9-17ubuntu3.9 is installed.
                      Depends: libfontconfig1 (>= 2.8.0) but 2.6.0-1ubuntu12 is installed.
                      Depends: libgconf2-4 (>= 2.27.0) but 2.26.0-0ubuntu1 is installed.
                      Depends: libgcrypt11 (>= 1.4.2) but 1.4.1-2ubuntu1 is installed.
                      Depends: libgtk2.0-0 (>= 2.18.0) but 2.16.1-0ubuntu2 is installed.
                      Depends: libstdc++6 (>= 4.4.0) but 4.3.3-5ubuntu4 is installed.
                      Depends: libatk1.0-0 (>= 1.30.0) but 1.26.0-0ubuntu2 is installed.
Unable to resolve dependencies!  Giving up...

``` 
Any pointers would be gratefully received.

---

### Post by mörgæs on 2011-08-26
9.04 is unsupported. Better to go for a clean install of a supported release:

[http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Version_timeline](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Version_timeline)

---

### Post by cfgauss on 2011-08-26
> **mörgæs said:**
> 9.04 is unsupported. Better to go for a clean install of a supported release

Agreed. This is better but not possible on this box for a while.

Why can't I install a clean version of google-chrome under 9.04 assuming I have an "up-to-date" 9.04?

---

### Post by recluce on 2011-08-26
> **cfgauss said:**
> Agreed. This is better but not possible on this box for a while.

Why can't I install a clean version of google-chrome under 9.04 assuming I have an "up-to-date" 9.04?

Did you even read the error messages you posted? Chrome requires more recent versions of a couple of libraries than what you have installed. This is obviously due to the fact that you are running an unsupported, old version of Ubuntu.

Try Opera instead, it should work.

---

### Post by drpjkurian on 2011-08-26
Hi 
What I feel is that Google chrome browser which is available for download siuts the latest version of Ubuntu. The Jaunty version of chrome belongs to 'history'.

---

### Post by drpjkurian on 2011-08-26
Upgrade your OS man!

---

### Post by Enigmapond on 2011-08-26
Jaunty died.RIP..so if you are trying to update anything, it probably will cause you a mess of problems. If you want to updating, you NEED to upgrade, (with a fresh install), of either 10.04 (I recommend) or 11.04. This will solve all your issues.

---

### Post by dajare on 2011-09-03
I have the same question and the same problem. Unfortunately, the latest Ubuntu release my hardware will run reliably is 9.04 (I have tried each new release since then), so there's no other option. I had Chrome 11 Beta running, but uninstalled it to update to latest version ... only to get the error messages recorded by the thread starter.

So again: does **anyone** know where to find the last version (probably 12) of Chrome that will install on Jaunty? Please??

---

### Post by dajare on 2011-09-03
It took a long, long search and quite a bit of checking "google-chrome-stable_current_i386.deb" packages, but I finally found a release of Chrome v. 11.0.696.68 which will do me fine!

Here's the page with the download:

[]("http://ishare.iask.sina.com.cn/f/15447397.html")[http://ishare.iask.sina.com.cn/f/15447397.html](http://ishare.iask.sina.com.cn/f/15447397.html)

Thank goodness a big green arrow pointing down is fairly self-explanatory! 

@cfgauss - works for me - hope it works for you.

---

### Post by mörgæs on 2011-09-04
Sorry for spoiling the joy, but now you have a versions of Chrome with security holes running on a version of Ubuntu with security holes. New versions are released for a reason.

I think it would be better to focus on getting a recent version of Ubuntu running, for example by adding boot options or trying Xubuntu.

---

### Post by dajare on 2011-09-04
> **mörgæs said:**
> Sorry for spoiling the joy, but now you have a versions of Chrome with security holes running on a version of Ubuntu with security holes. ....

My joy is much more robust than that. ;)

Of course there is something in what you say. But with every new release since 9.04 I have tried the live disk to see how things would go ... and no release since then gives me reliable (or any) wireless. Having spent *many* hours trying to get newer releases working, I have settled for 9.04 and the pleasure of actually having a usable machine!

I was blissfully unaware of Xubuntu, however. I'll certainly give it a look -- thanks.

And if anyone would like to make a donation so I can finally retire this antique Toshiba laptop ... PM me! :D

---

### Post by MARP1961 on 2011-09-04
If you post the full specifications of your old laptop I'm sure someone here could get your wireless working on Lucid 10.04. Jaunty is dead! Your laptop is not.

---

### Post by cfgauss on 2011-09-19
> **dajare said:**
> 
@cfgauss - works for me - hope it works for you.

*Many* thanks! It works for me on Jaunty 9.04 AMD64.

---

### Post by Z-Funk on 2012-12-11
If people choose to run old versions of Ubuntu, instead of badgering them to update even when they tell the reasons why they can't, maybe you should actually try to provide the information they're looking for.

Here is a page with old stable releases which work on older versions of ubuntu:

[http://linuxfreedom.com/hacktolive/repo/archive/pool/main/g/google-chrome-stable/](http://linuxfreedom.com/hacktolive/repo/archive/pool/main/g/google-chrome-stable/)

and here

[http://www.ubuntuupdates.org/pm/gooagle-chrome-stable](http://www.ubuntuupdates.org/pm/gooagle-chrome-stable)

Give people the information they are looking for rather than question their reasoning why.

---

### Post by mörgæs on 2012-12-11
Often people don't know what they are looking for until questioned. 

Closing the thread, as it concerns an obsolete version of Ubuntu.

---


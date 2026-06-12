---
title: "hmm GDebi Package Installer doesnt like Google Chrome"
date: 2009-08-18
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by meeples on 2009-08-18
evry single time i try to open the google chrome deb Gdebi "closes unexpectedly" 

very frustrating.

i went to GetDeb.net and downloaded the first one i saw and no problems. anyone else want to please try and see if its just me?:confused:

---

### Post by taavikko on 2009-08-18
If gdebi is failing use "sudo dpkg -i package.deb" to install, if it fails on any other debs, search/file for existing bugs.

---

### Post by jpeddicord on 2009-08-18
Consider using the daily PPA:

[https://launchpad.net/~chromium-daily/+archive/ppa](https://launchpad.net/~chromium-daily/+archive/ppa)

Haven't had problems there.

---

### Post by Katalog on 2009-08-18
> **jacobmp92 said:**
> Consider using the daily PPA:

[https://launchpad.net/~chromium-daily/+archive/ppa]("https://launchpad.net/%7Echromium-daily/+archive/ppa")

Haven't had problems there.

+1. Definitely the way to go. I run the Chromium builds from that repo and they work like a charm, as well as getting updated on pretty regular basis.

---

### Post by meeples on 2009-08-18
> **Katalog said:**
> +1. Definitely the way to go. I run the Chromium builds from that repo and they work like a charm, as well as getting updated on pretty regular basis.

thanks, is it better than official google release?

---

### Post by VMC on 2009-08-18
> **taavikko said:**
> If gdebi is failing use "sudo dpkg -i package.deb" to install, if it fails on any other debs, search/file for existing bugs.

Mine also failed and this method using dpkg worked.

---

### Post by Katalog on 2009-08-18
> **meeples said:**
> thanks, is it better than official google release?

There is no official Google Chrome release for Linux right now. The packages you download from GetDeb are just packaged by some anonymous person who knew how to turn it into a deb, so you never really know what you're getting. But the Chrominum Dailys run like a champ and are probably more up to date than the package you were trying to install.

---

### Post by Regenweald on 2009-08-18
to add the ppa via the terminal:
```

sudo add-apt-repository ppa:chromium-daily

```

---

### Post by jpeddicord on 2009-08-18
> **Katalog said:**
> There is no official Google Chrome release for Linux right now. The packages you download from GetDeb are just packaged by some anonymous person who knew how to turn it into a deb, so you never really know what you're getting. But the Chrominum Dailys run like a champ and are probably more up to date than the package you were trying to install.

They have [dev channel]("http://dev.chromium.org/getting-involved/dev-channel") builds, but I don't think there as up-to-date as the daily PPA.

---

### Post by meeples on 2009-08-18
> **Katalog said:**
> There is no official Google Chrome release for Linux right now. The packages you download from GetDeb are just packaged by some anonymous person who knew how to turn it into a deb, so you never really know what you're getting. But the Chrominum Dailys run like a champ and are probably more up to date than the package you were trying to install.


no. there is.

theres a developers release: [http://www.google.com/chrome/intl/en/eula_dev.html?dl=unstable_i386_deb]("http://www.google.com/chrome/intl/en/eula_dev.html?dl=unstable_i386_deb")

thats what keeps crashing Gdebi. i tried it when it first came out and its def Google Chrome not Chromium. although i am aware they are pretty much the same thing.

im using the chromium daily as i type this and wow. its almost too fast:O

---

### Post by meeples on 2009-08-18
> **Regenweald said:**
> to add the ppa via the terminal:
```

sudo add-apt-repository ppa:chromium-daily

```

thanks, didnt know you could at ppa's that way, but i already got it lol

---

### Post by VMC on 2009-08-18
> **meeples said:**
> thanks, didnt know you could at ppa's that way, but i already got it lol

Yes, its the first time I've seen it use also. Thanks.

---

### Post by Regenweald on 2009-08-18
> **meeples said:**
> thanks, didnt know you could at ppa's that way, but i already got it lol

> **VMC said:**
> Yes, its the first time I've seen it use also. Thanks.

I only learned of it recently also :)
 
[http://ubuntuforums.org/showthread.php?t=1213538](http://ubuntuforums.org/showthread.php?t=1213538)

---

### Post by oztrailrider on 2009-08-18
I experienced the same thing when I tried to install Chrome. You will need to install it using dpkg for now. I found it had already been reported and confirmed on launchpad.

[Bug #407198]("https://bugs.launchpad.net/ubuntu/+source/gdebi/+bug/407198")

---

### Post by Regenweald on 2009-08-18
But is it a chrome thing or a gdebi thing? I was having some problems installing Opera 10 recently and blamed opera. Then to find out that gdebi was having problems via launchpad. I've simply been using dpkg -i to install the odd .deb

---

### Post by Katalog on 2009-08-19
> **meeples said:**
> no. there is.

theres a developers release: [http://www.google.com/chrome/intl/en/eula_dev.html?dl=unstable_i386_deb](http://www.google.com/chrome/intl/en/eula_dev.html?dl=unstable_i386_deb)

thats what keeps crashing Gdebi. i tried it when it first came out and its def Google Chrome not Chromium. although i am aware they are pretty much the same thing.

im using the chromium daily as i type this and wow. its almost too fast:O

I think you misunderstood what I meant by the term "official release". The dev builds that come from Google are still not what I would consider "official" releases, even though they still come from Google. What I was referring to is that you still can't go to the Google Chrome home page and download a final, official build released specifically for Linux (or Mac either, for that matter). If you go to that page it still only has downloads for Windows.

---

### Post by philinux on 2009-08-20
> **Regenweald said:**
> to add the ppa via the terminal:
```

sudo add-apt-repository ppa:chromium-daily

```

I like this. Neat

---

### Post by shakaran on 2009-08-20
The google's guys should work more on .debs. They announced a 4.0.x version without full support for linux yet? This is a serious thing, dont increase your version number so easy!

---

### Post by ktp on 2009-08-20
> **jacobmp92 said:**
> They have [dev channel]("http://dev.chromium.org/getting-involved/dev-channel") builds, but I don't think there as up-to-date as the daily PPA.

Dev channel builds are usually week or so behind because they want to try to keep it "safe".

Another good thing about the PPA is now there is natvie 64-bit build.  :P

---

### Post by jpeddicord on 2009-08-20
> **ktp said:**
> Dev channel builds are usually week or so behind because they want to try to keep it "safe".

Another good thing about the PPA is now there is natvie 64-bit build.  :P

The PPA builds in 64-bit mode now? That's news to me. I thought it was still installing as a 32-bit wrapper.

EDIT: So it does! The 64-bit Flash plugin is working.

---

### Post by ktp on 2009-08-20
> **jacobmp92 said:**
> The PPA builds in 64-bit mode now? That's news to me. I thought it was still installing as a 32-bit wrapper.

EDIT: So it does! The 64-bit Flash plugin is working.

Yep it is...I noticed it once I saw totem plugin.

[https://launchpad.net/~chromium-daily/+archive/ppa](https://launchpad.net/~chromium-daily/+archive/ppa)
> FAQ:
* The amd64 package is no longer using ia32-libs. It contains ***native*** 64bit debs.

V8 still need some performance tunning and still can't get Java plugin to work but overall it is pretty good.

---

### Post by VMC on 2009-08-20
> **shakaran said:**
> The google's guys should work more on .debs. They announced a 4.0.x version without full support for linux yet? This is a serious thing, dont increase your version number so easy!

I'm not sure I understand your statement. I just received an update to google-chrome to 4.0.202.2

Edit: I see. You mean they updated Chrome to v4 without support. Well, so far I haven't needed any. It works perfect for me.

---

### Post by ktp on 2009-08-20
> **VMC said:**
> I'm not sure I understand your statement. I just received an update to google-chrome to 4.0.202.2

Edit: I see. You mean they updated Linux to v4 without support. Well, so far I haven't needed any. It works perfect for me.

increasing numbers just might mean moving close to beta...this is google we are talking about where everything is beta.  :lolflag:

---

### Post by shakaran on 2009-08-21
Yeah, the version 30.0.1532 will have full support... LOL

---


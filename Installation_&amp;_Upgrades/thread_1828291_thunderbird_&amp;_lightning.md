---
title: "thunderbird &amp; lightning"
date: 2011-08-18
forum: Installation &amp; Upgrades
---

### Post by allenb.bigal on 2011-08-18
I'm using TB 3.1.11 and Linux 2.6.32.33.39 and I'm wanting to install the Lightning addon but I'm getting nowhere. Every time I try to install different versions of Lightning it fails telling me that the version is not comatible with Thunderbird. Anybody got a solution to this or do I just have to wait?
Thanks
Allen from Oz

---

### Post by YesWeCan on 2011-08-18
Hey Allen from Oz,
Are you running 64-bit? I had that exact symptom and I had to Google for a 64-bit version of Lightening which I found here:
[http://releases.mozilla.org/pub/mozilla.org/calendar/lightning/releases/1.0b2/contrib/linux-x86_64/](http://releases.mozilla.org/pub/mozilla.org/calendar/lightning/releases/1.0b2/contrib/linux-x86_64/)
I don't know whether that is the latest version or not.

---

### Post by SoFl W on 2011-08-18
I was able to install 1.0b5 with Ubuntu 10.4 64 bit.  I don't remember what I followed to get it to install, but I did do it recently.  I will see if I can find the thread.[URL="http://releases.mozilla.org/pub/mozilla.org/calendar/lightning/releases/1.0b1/contrib/linux-x86_64/"]
[/URL]
I was using TB 3.x at the time, I am now using TB 6.

---

### Post by allenb.bigal on 2011-08-18
Thanks guys.

Would you believe that I'm not all that sure whether I'm running 64 or 32 bit. I think I'm running 32 bit though. I do know that my  processor is a Intel(R) Atom(TM) CPU 230 @ 1.60GHz .

How can I check whether I'm running 64 bit or not?

Thanks
Allen from Oz

---

### Post by YesWeCan on 2011-08-18
uname -m

---

### Post by allenb.bigal on 2011-08-18
uname -m came back with x86_64, so I guess that means I am on 64 bit. I clicked on the link provided by YesWeCan and it downloaded Lightning and then protested that it was not compatible with Firefox 3.6.18! I thought that lightning was an addon to Thunderbird. Am I all up the creek or what?

Allen
Oz

---

### Post by YesWeCan on 2011-08-18
I'm using Ubuntu 10.10 64 bit and these are my TB and FF versions.

---

### Post by SoFl W on 2011-08-18
See if this helps
[https://help.ubuntu.com/community/ThunderbirdLightning](https://help.ubuntu.com/community/ThunderbirdLightning)

---

### Post by dniMretsaM on 2011-08-18
You might try updating Thunderbird.

```
sudo add-apt-repository ppa:mozillateam/thunderbird-stable
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by allenb.bigal on 2011-08-18
It seems that no matter what I do, the bloody thing is trying to add lightning to Firefox, whereas I want to add it to Thunderbird.

Am I on the wrong tram?

Thanks

Allen 
Oz

---

### Post by Hakunka-Matata on 2011-08-19
This system:

[LIST]
[*]2.6.38-10-generic x86_64
[*]Firefox 5.0 **Mozilla Firefox for Ubuntu canonical - 1.0**
[*]**Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.2.18) Gecko/20110617 Lightning/1.0b2 Thunderbird/3.1.11**
[/LIST]
I just now got lightning installed, I had tried downloading Lightning 1.0b2 separately from some link I saw on this thread, and it refused to download, pop-up came on and said the version was not compatible with Firefox 5.0.

Firefox - Thunderbird & lightning all interact with each other to a certain degree, google it.

So how did I get Lightning to download and work, by simply using synaptic: it's listed as "**xul-ext-lightning**"
see attached graphic/screenshot.

You system is not identical to mine, but maybe synaptic will get you the correct version of Lightning.

Hope this might help you.

---

### Post by allenb.bigal on 2011-08-19
Mission accomplished. Finished up upgrading Thunderbird to v 6.0 and even though there was an error in the process it seems to be working OK. Something about a file that was trying to be overwritten yet was needed in the new version. Resulted in one package not upgraded which was 
thunderbird-gnome-support-dbg.

Many thanks to all and specially dniMretsaM, whose suggestion solvd the problem. Good on yer MasterMind.

Allen
Oz

---

### Post by dniMretsaM on 2011-08-19
Glad you got it fixed!

---


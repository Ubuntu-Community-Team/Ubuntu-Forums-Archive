---
title: "Install USB Lubuntu on PowerPC Mac"
date: 2010-05-10
forum: Installation &amp; Upgrades
---

### Post by wbar2 on 2010-05-10
I'm wanting to install a version of Ubuntu on a Mac G3 iBook. It has a 600 MHz PowerPC processor and about 512 MB RAM. The CD-ROM does not work properly. 

I was thinking of trying to install Lubuntu 10.04 on it, but I cannot find a PowerPC version anywhere. So, I'm thinking maybe I can install a minimum version of Ubuntu and add lubuntu-desktop later?

I also don't know much about installing from USB drive, especially on a PowerPC Mac. I really think this is the key issue, since the CD-ROM isn't working properly. Does anyone know how to do this on a PPC Mac or know where to find some more information on how to do it?

I have Googled this issue, and I have not found anything related to the specifics of these questions.

---

### Post by narendraD on 2010-05-10
Lubuntu or LXDE is not available for powerPC. So Ubuntu (If it has a PowePC version) may be the only option. installing Ubuntu and then adding LXDE will not work.

As for USB install, Unetbootin or Startup Disk will do.

---

### Post by eltonw on 2010-05-10
With a flaky CD/DVD drive, you might be better to consider a network install. If you can burn the ISO to USB and you can see it mounted via the Disk Utility, you might be able to go to System Preferences and see if is listed in the choices for Startup Disk.

It is important that you choose an architecture-specifid distro, even a Live CD (Intel 386 or AMD 64 bit) will run on the PPC.

GOOGLE is your friend, as (e.g.) this SEARCH for "linux on PPC" 
:[http://www.google.com/custom?hl=en&client=pub-9300639326172081&cof=FORID%3A13%3BAH%3Aleft%3BCX%3AUbuntu%252010%252E04%3BL%3Ahttp%3A%2F%2Fwww.google.com%2Fintl%2Fen%2Fimages%2Flogos%2Fcustom_search_logo_sm.gif%3BLH%3A30%3BLP%3A1%3BLC%3A%230000ff%3BVLC%3A%23663399%3BDIV%3A%23336699%3B&adkw=AELymgVhr3Em__JZQFsAuNYA4s0LKuyeUECdCwler9WFrfDUxxfFUvlhDEP8n0MQq_U0oRIbzBir0UgWkDssmdTL14kQLyWZhV0Cf1hepin3YDMrWh4vVFU&channel=6911402799&q=linux+on+ppc&btnG=Search&cx=!partner-pub-9300639326172081%3Ad9bbzbtli15]("http://www.google.com/custom?hl=en&client=pub-9300639326172081&cof=FORID%3A13%3BAH%3Aleft%3BCX%3AUbuntu%252010%252E04%3BL%3Ahttp%3A%2F%2Fwww.google.com%2Fintl%2Fen%2Fimages%2Flogos%2Fcustom_search_logo_sm.gif%3BLH%3A30%3BLP%3A1%3BLC%3A%230000ff%3BVLC%3A%23663399%3BDIV%3A%23336699%3B&adkw=AELymgVhr3Em__JZQFsAuNYA4s0LKuyeUECdCwler9WFrfDUxxfFUvlhDEP8n0MQq_U0oRIbzBir0UgWkDssmdTL14kQLyWZhV0Cf1hepin3YDMrWh4vVFU&channel=6911402799&q=linux+on+ppc&btnG=Search&cx=%21partner-pub-9300639326172081%3Ad9bbzbtli15")

HTH...

---

### Post by wbar2 on 2010-05-11
> **eltonw said:**
> With a flaky CD/DVD drive, you might be better to consider a network install. If you can burn the ISO to USB and you can see it mounted via the Disk Utility, you might be able to go to System Preferences and see if is listed in the choices for Startup Disk.

It is important that you choose an architecture-specifid distro, even a Live CD (Intel 386 or AMD 64 bit) will run on the PPC.

GOOGLE is your friend, as (e.g.) this SEARCH for "linux on PPC" 
:[http://www.google.com/custom?hl=en&client=pub-9300639326172081&cof=FORID%3A13%3BAH%3Aleft%3BCX%3AUbuntu%252010%252E04%3BL%3Ahttp%3A%2F%2Fwww.google.com%2Fintl%2Fen%2Fimages%2Flogos%2Fcustom_search_logo_sm.gif%3BLH%3A30%3BLP%3A1%3BLC%3A%230000ff%3BVLC%3A%23663399%3BDIV%3A%23336699%3B&adkw=AELymgVhr3Em__JZQFsAuNYA4s0LKuyeUECdCwler9WFrfDUxxfFUvlhDEP8n0MQq_U0oRIbzBir0UgWkDssmdTL14kQLyWZhV0Cf1hepin3YDMrWh4vVFU&channel=6911402799&q=linux+on+ppc&btnG=Search&cx=!partner-pub-9300639326172081%3Ad9bbzbtli15]("http://www.google.com/custom?hl=en&client=pub-9300639326172081&cof=FORID%3A13%3BAH%3Aleft%3BCX%3AUbuntu%252010%252E04%3BL%3Ahttp%3A%2F%2Fwww.google.com%2Fintl%2Fen%2Fimages%2Flogos%2Fcustom_search_logo_sm.gif%3BLH%3A30%3BLP%3A1%3BLC%3A%230000ff%3BVLC%3A%23663399%3BDIV%3A%23336699%3B&adkw=AELymgVhr3Em__JZQFsAuNYA4s0LKuyeUECdCwler9WFrfDUxxfFUvlhDEP8n0MQq_U0oRIbzBir0UgWkDssmdTL14kQLyWZhV0Cf1hepin3YDMrWh4vVFU&channel=6911402799&q=linux+on+ppc&btnG=Search&cx=%21partner-pub-9300639326172081%3Ad9bbzbtli15")

HTH...

Sorry for not clarifying, but I've Googled the issue. I've edited by first post to reflect this.

---

### Post by wbar2 on 2010-05-12
I now have Lubuntu running on my iBook, basically following this thread:
[http://ubuntuforums.org/showthread.php?t=1454430](http://ubuntuforums.org/showthread.php?t=1454430)

---


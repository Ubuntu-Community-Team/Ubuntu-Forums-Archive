---
title: "gmail in indicator-applet"
date: 2009-09-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by zorkerz on 2009-09-25
Has anybody found a way to get notified of new gmail messages in indicator-applet under karmic?

Previously I used gm-notify but recently it has stopped working (see [bug #433412]("https://bugs.launchpad.net/gm-notify/+bug/433412")).

---

### Post by hikaricore on 2009-09-25
gmail-notify works fine for me in the "system tray" if that's an alternative.

---

### Post by ernstblaauw on 2009-09-25
Well, there are a lot of options if you don't need the new messaging menu. For example checkgmail for a copy of the Windows Gmail Notifier (by Google), or gnome-gmail-notifier if you want to use the osd notify.

However, I just searched and I could only find gm-notify to take advantage of the new indicator applet, and that program is only available for Jaunty. 

However, I think this is one of the most wanted (and useful) applications for the indicator applet. Has anyone else a suggestion or solution? It can also work with a generic imap plugin for the indicator applet, but I did not see one.

---

### Post by hanzomon4 on 2009-09-25
gmail imap + evolution

---

### Post by alexmurray on 2009-09-26
> **hanzomon4 said:**
> gmail imap + evolution

+1 on this for me - I also use gmail via imap with evolution and find it works quite nicely

---

### Post by ernstblaauw on 2009-09-26
> **alexmurray said:**
> +1 on this for me - I also use gmail via imap with evolution and find it works quite nicely

Well, you have to keep Evolution open - and I use the web interface of gmail so for me, there is no need to keep the program opened (besides the indicator). So, I would love to see another solution for the indicator-applet.

---

### Post by mal on 2009-09-26
cGmail works for me.  It's in the repositories.

Mal

---

### Post by ernstblaauw on 2009-09-26
> **mal said:**
> cGmail works for me.  It's in the repositories.

Mal

Well, here it does not interact with the indicator-applet. So for me, it's not the ultimate mail checker.

---

### Post by macstevejb on 2009-09-26
I use checkgmail...it's also in the repos

regards,

:)

---

### Post by nanomad on 2009-09-26
> **zorkerz said:**
> 
Previously I used gm-notify but recently it has stopped working (see [bug #433412]("https://bugs.launchpad.net/gm-notify/+bug/433412")).

I've attached a patch to the bug report.

---

### Post by Arquis on 2009-09-26
The indicator applet works with Thunderbird? Just curious...

---

### Post by ernstblaauw on 2009-09-26
> **nanomad said:**
> I've attached a patch to the bug report.

Where can I download gm-notify for Karmic? I only found a [version for Jaunty]("https://launchpad.net/~gm-notify-maintainers/+archive/ppa").

---

### Post by rburkartjo on 2009-09-26
i use checkgmail also works fine

---

### Post by nanomad on 2009-09-26
> **ernstblaauw said:**
> Where can I download gm-notify for Karmic? I only found a [version for Jaunty]("https://launchpad.net/~gm-notify-maintainers/+archive/ppa").

[https://launchpad.net/~gm-notify-maintainers/+archive/ppa](https://launchpad.net/~gm-notify-maintainers/+archive/ppa)

---

### Post by zorkerz on 2009-09-26
Alot of people have posted good solutions but most are missing the point.

I am looking for indicator-applet integration for the gmail web interface. I would also like it to use notify-osd. gm-notify is the only option that meets these requirements to my knowledge. Unfortunately it has stopped working in karmic and the developer of it has been silent for a good while.

In the past I have been most satisfied with check-gmail but that has not been integrated with the indicator-applet.

---

### Post by Joe_Bishop on 2009-09-26
> **zorkerz said:**
> Alot of people have posted good solutions but most are missing the point.

I am looking for indicator-applet integration for the gmail web interface. I would also like it to use notify-osd. gm-notify is the only option that meets these requirements to my knowledge. Unfortunately it has stopped working in karmic and the developer of it has been silent for a good while.

In the past I have been most satisfied with check-gmail but that has not been integrated with the indicator-applet.
Man, it's so easy to build your own package:
[LIST=1]
[*]Use the link above to download gm-notify tarboll
[*]Unpack tarball
[*]Change IndicatorMessage to Indicator in line 209 of file gm-notify.py
[*]Execute: sudo aptitude install debhelper; dpkg-buildpackage -rfakeroot
[/LIST]
It's all, you will get you *deb package

---

### Post by zorkerz on 2009-09-26
Oh wow. Giovanni Condello just released a patch fixing the bug in gm-notify I mentioned above. So for now gm-notify is my preferred choice though it has some kinks to work out.

---

### Post by ernstblaauw on 2009-09-26
> **zorkerz said:**
> Oh wow. Giovanni Condello just released a patch fixing the bug in gm-notify I mentioned above. So for now gm-notify is my preferred choice though it has some kinks to work out.
How can I install that version on Karmic? Can you help me?

> **nanomad said:**
> [https://launchpad.net/~gm-notify-maintainers/+archive/ppa](https://launchpad.net/~gm-notify-maintainers/+archive/ppa)
I only see a Jaunty version over there.

---

### Post by zorkerz on 2009-09-26
It looks like they are using a new method to add a ppa in karmic.

Go to the "Other Software" tab in system->administration->software sources

Then click the add button and past the following line```
ppa:gm-notify-maintainers/ppa
```You will need to add the authentication file. The one provided for jaunty at [https://launchpad.net/~gm-notify-mai...s/+archive/ppa]("https://launchpad.net/%7Egm-notify-maintainers/+archive/ppa") should work fine i believe. Update your sources and install gm-notify.


To get the newest patch I had to go edit the gm-notify.py file itself.

```
sudo nano /usr/bin/gm-notify.py
```Press ctrl+w and search for ```
new_indicator = indicate.IndicatorMessage()
```Replace this line with ```
new_indicator = indicate.Indicator()
``` Finally press ctrl+o to save the file.

gm-notify can be started by selecting system->preferences->GMail Notifier Configuration (you can immediately close the configuration window)

---

### Post by puccaso on 2009-09-26
yea i did that too
but there are still problems with it
and it kills the indicator applet.

needs alot of work

---

### Post by zorkerz on 2009-09-26
What problems are you having?

Its been working fine for me today. Definitely needs work but no show stoppers.

---

### Post by ernstblaauw on 2009-09-27
> **zorkerz said:**
> What problems are you having?

Its been working fine for me today. Definitely needs work but no show stoppers.

Well, it seems sometimes it shows a already read message. And I actually don't know the rationale behind the indicator-applet, but if I get a new e-mail, the icon of the indicator-applet does not change (so I do not see there is a new message if I've missed the OSD notify). Is that a bug or expected behavior?

---

### Post by glroig on 2009-09-27
can't select sounds...

---

### Post by zorkerz on 2009-09-27
Those all sound like valid bugs to me. A few have been reported on launchpad already but some have not.

---

### Post by andresmh on 2009-09-27
How do you configure this gmail notifier to work with a custom doimain hosted on Gmail's Google Apps?

---

### Post by zorkerz on 2009-09-27
hmm im not sure you might want to ask it as a question on launchpad as well. Im not sure anyone who knows the package well is following this thread.

---

### Post by ernstblaauw on 2009-09-28
> **zorkerz said:**
> hmm im not sure you might want to ask it as a question on launchpad as well. Im not sure anyone who knows the package well is following this thread.
I added some comments and opened a new bug report. I think this gm-notify has a lot of potential with the upcoming Karmic release. If the author gets it right, gm-notify will be used a lot. Hopefully, the author can address some small bugs and feature requests :-).

---

### Post by zorkerz on 2009-09-28
I agree this app has a lot of potential because many people use gmail and it appears to be the only option for integrating the gmail web interface with the indicator-applet.

For those interested ernstblaauw's bug can be found here [bug#438149]("https://bugs.launchpad.net/gm-notify/+bug/438149").

---


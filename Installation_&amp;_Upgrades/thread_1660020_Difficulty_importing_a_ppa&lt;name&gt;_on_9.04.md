---
title: "Difficulty importing a ppa:&lt;name&gt; on 9.04"
date: 2011-01-04
forum: Installation &amp; Upgrades
---

### Post by dayosh on 2011-01-04
Greetings!  As the title suggests, I've been trying to add (via terminal) a ppa:<name> from [**_this site_**]("http://gtk-apps.org/content/show.php?content=104309&forumpage=6") (finally got around to getting a Wacom Bamboo), but every time I try to do as it suggests, I get the following error:
```

$ sudo add-apt-repository ppa:hughescih/ppa
sudo: add-apt-repository: command not found

```
I read another person having this problem, to which it was suggested to download and install the *python-software-properties* package.  I found I already had this installed, but to double-check, I've uninstalled and re-installed it to make sure, and still to no avail.  I wasn't sure if I'm still missing something or what the deal may be.  If any readouts are needed, just let me know with the commands, and I'll be happy to post.  Thank you very much in advance.  :)

---

### Post by wojox on 2011-01-04
You can't add ppa's like that in Jaunty. You need to upgrade to Karmic or higher since Jaunty is no longer supported.

---

### Post by kostkon on 2011-01-04
Yes, you can't use this command in 9.04.

You'll have to manually add the PPA to your software sources list. I believe you'll find [this video]("http://blog.launchpad.net/ppa/adding-a-ppas-key-to-ubuntu") useful.

---

### Post by dayosh on 2011-01-05
Thank you both, very greatly!  Unfortunately, I caved in and just upgraded to 9.10 (bugger) so I could add the ppa.  Heh.  The kicker now is, the ppa is apparently either down temporarily or no longer working (ain't that just how it goes?  :p  ).  To add insult to injury, I've still been unsuccessful in getting my Bamboo to work with Linux even after the upgrade, which rather confuses me, as I've read numerous times that this particular model (the Pen & Touch CTH460) is supposed to (practically) "plug-in and go".  Ah, well..I suppose I'll have to keep researching.  I appreciate the quick responses from you both, however!  This community has always overwhelmed me with its outright helpfulness and its knack for making newbies like myself feel welcome, and it's people like you both who are to blame.  Thank you both very much once again!  :)

---

### Post by psusi on 2011-01-05
You should upgrade again ( preferably to 10.04 ) since 9.04 is only supported for 3 more months.

---

### Post by dayosh on 2011-01-05
You mean 9.10 is only supported for 3 more months?

---

### Post by psusi on 2011-01-06
> **dayosh said:**
> You mean 9.10 is only supported for 3 more months?

Err, yea ;)

---

### Post by dayosh on 2011-01-06
Hrm.  I'll have to look into that, then.  Thanks for the heads-up!  You know...I of all people certainly do not mean to sound ungrateful with all of the hard work and effort that coders around the world are putting in to make the Ubuntu project even better...but, is it so much to ask for a release that's just...well...permanent?  lol  It's just so confusing and rather frustrating at times, when one gets used to a particular distro, only to have the support yanked out from under the distro's proverbial feet.  :p

---

### Post by oldos2er on 2011-01-06
Maybe an LTS (Long Term Support) release would suit you better. [http://en.wikipedia.org/wiki/List_of_Ubuntu_releases](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases)

---

### Post by psusi on 2011-01-07
> **dayosh said:**
> Hrm.  I'll have to look into that, then.  Thanks for the heads-up!  You know...I of all people certainly do not mean to sound ungrateful with all of the hard work and effort that coders around the world are putting in to make the Ubuntu project even better...but, is it so much to ask for a release that's just...well...permanent?

Yes, it is too much to ask.  It takes a lot of effort to keep back porting security fixes to old versions of software, and a lot of storage space on the mirrors to keep many different releases around.  If they were all kept forever, then right now the mirrors would have to hold 11 releases instead of just 5, and every time a security bug was found, the devs would have to review and possibly patch 11 versions instead of 5, and this would only grow worse as time marches on.

The compromise is that every other year's spring release is long term support, and kept around for 5 years, but the rest are only 18 months.  So if you would rather run outdated software than upgrade every 6-12 months, then you should stick with an LTS release.

---

### Post by mörgæs on 2011-01-07
I think 'outdated' is a strong word. Sticking to the LTS releases is a good idea, and my guess is that it is the norm on server side. What matters is that there are security releases. 

The development of Ubuntu seems to be focused on Software Centre, Unity, 'social web' applications and the like, all of which I can happily live without. As for the important stuff like Open Office and Gimp, an old release is as good as a new one.

---

### Post by psusi on 2011-01-07
> **mörgæs said:**
> As for the important stuff like Open Office and Gimp, an old release is as good as a new one.

Most people disagree with that, often quite strongly.  Not being able to get the latest openoffice, firefox, and a few others on an older LTS release is a big complaint by a lot of people.

---


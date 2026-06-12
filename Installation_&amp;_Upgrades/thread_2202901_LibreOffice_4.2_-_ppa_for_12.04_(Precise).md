---
title: "LibreOffice 4.2 - ppa for 12.04 (Precise) ?"
date: 2014-01-31
forum: Installation &amp; Upgrades
---

### Post by NTL2009 on 2014-01-31
A while back, I installed the ppa so I could install LO 4.1 through Synaptic. I understand this allows for auto updates (I installed earlier versions through the deb, so I uninstalled those first).

I don't see any updates available for 4.1 to 4.2. Will there be a different ppa to add? How long might this take to get published? If it does get published, should my Update manager just pick it up?

I haven't even been able to find if LO 4.2 will run under 12.04 (Precise). Will it even run OK? Where would I find that info?

TIA - NTL2009

---

### Post by ajgreeny on 2014-01-31
There is a ppa at [https://launchpad.net/~libreoffice/+archive/libreoffice-prereleases](https://launchpad.net/~libreoffice/+archive/libreoffice-prereleases)

I have no idea how many problems it might cause you, so proceed with some caution and read all the info on the ppa site.

---

### Post by NTL2009 on 2014-01-31
Thanks, maybe I'll try it on a separate partition where I have another 12.04 install, so as not to risk my main system.

I suppose I can install from the deb, and see if any dependency problems show up.

I guess I'm surprised this isn't just covered on the site - which LO versions will run on which Ubuntu versions? I mean 12.04 is still _the_ LTS.

-NTL2009

---

### Post by The Spectre on 2014-02-01
LibreOffice 4.2 just showed up for 13.10 (Saucy) a couple of hours ago in the main LibreOffice PPA...

[https://launchpad.net/~libreoffice/+archive/ppa](https://launchpad.net/~libreoffice/+archive/ppa)

I would imagine that it won't be much longer for the 12.04 (Precise) version to show up.

---

### Post by claracc on 2014-02-01
The libreoffice in a fully updated precise ubuntu is 3.5.7.2, see attached image. 

Once a release is out, the versions of the software packages remain to give stability to the release, and they used to receive security updates but no advanced or new releases (except firefox case and others). 

This is the case of libreoffice in precise 12.04, I think they'll remain in release 3.5 and will deliver updates to  solve bugs (perhaps) and manage security holes, but it is not expected a 4.0 or more libreoffice in precise.

To have the last thing or the newer one, you can use ppas (if there is one) for the required software or the last ubuntu release 13.10.

---

### Post by ajgreeny on 2014-02-01
I'm using LO 4.1.4.2 from the [http://ppa.launchpad.net/libreoffice/libreoffice-4-1/ubuntu](http://ppa.launchpad.net/libreoffice/libreoffice-4-1/ubuntu) ppa and it is working faultlessly as far as I can tell.

It is a lot faster than the 3.5.7.2 version default for precise, and I would recommend it highly, though your situation may vary from mine, of course.

---

### Post by Bashing-om on 2014-02-01
NTL2009; Hi !

Though NOT directed at precise, the latest and greatest here, and as well other links:
[http://discourse.ubuntu.com/t/libreoffice-4-2-0-rc2-with-full-l10n-in-the-ppa-for-trusty-and-saucy-and-some-numbers-on-4-2/1423](http://discourse.ubuntu.com/t/libreoffice-4-2-0-rc2-with-full-l10n-in-the-ppa-for-trusty-and-saucy-and-some-numbers-on-4-2/1423)

As another bonus, perhaps talk direct with one of those involved in the development of LO.

[INDENT][INDENT]ununtu, free flow of information
[/INDENT][/INDENT]

---

### Post by The Spectre on 2014-02-01
LibreOffice 4.2 is now available for Ubuntu 12.04 (Precise) at the main LibreOffice PPA...

[https://launchpad.net/~libreoffice/+archive/ppa](https://launchpad.net/~libreoffice/+archive/ppa)

---

### Post by NTL2009 on 2014-02-03
> **The Spectre said:**
> LibreOffice 4.2 is now available for Ubuntu 12.04 (Precise) at the main LibreOffice PPA...

[https://launchpad.net/~libreoffice/+archive/ppa](https://launchpad.net/~libreoffice/+archive/ppa)

Thanks, just saw this post, I wasn't getting anymore updates to the thread.

OK, I've got it loaded now and it looks good.

All's well that ends well, but I'm still rather confused about this ppa process. When I went to the linked site, I just didn't see anything obvious to tell me that this ppa would now allow me to load 4.2.0 through Synaptic. Scrolling down the packages, I saw this (one of 47 packages in the list):

>  libreoffice	 1:4.2.0~rc4-0ubuntu1~precise4	Rico Tzschichholz (2014-02-01)

I guess that's obvious to people familiar with this process, but it didn't mean anything to me. But when I added the ppa to Synaptic (same as I did before), and reloaded, it showed the updates available. Since they include precise in the drop down menu, it led me to assume it was ready for download. I guess it would be nice to have something in plain language for those of us not so familiar with the process.

At any rate, thanks for the help, and thanks to the LibreOffice developers - this is really useful for me.

-NTL2009

---

### Post by The Spectre on 2014-02-04
> **NTL2009 said:**
> I guess that's obvious to people familiar with this process, but it didn't mean anything to me. But when I added the ppa to Synaptic (same as I did before), and reloaded, it showed the updates available. Since they include precise in the drop down menu, it led me to assume it was ready for download. I guess it would be nice to have something in plain language for those of us not so familiar with the process.
I found this online that might help explain...

[http://www.makeuseof.com/tag/ubuntu-ppa-technology-explained/](http://www.makeuseof.com/tag/ubuntu-ppa-technology-explained/)

[http://digitalstudio7.blogspot.com/2013/10/ubuntu-abc-lesson-301265-what-is-ppa.html](http://digitalstudio7.blogspot.com/2013/10/ubuntu-abc-lesson-301265-what-is-ppa.html)

[http://www.techerator.com/2011/07/an-introduction-to-ubuntus-personal-package-archives/](http://www.techerator.com/2011/07/an-introduction-to-ubuntus-personal-package-archives/)

Some of the info may be dated do to some of them referencing older versions of Ubuntu but the info should still be useful.

---

### Post by NTL2009 on 2014-02-04
> **The Spectre said:**
> I found this online that might help explain...

[http://www.makeuseof.com/tag/ubuntu-ppa-technology-explained/](http://www.makeuseof.com/tag/ubuntu-ppa-technology-explained/)

[http://digitalstudio7.blogspot.com/2013/10/ubuntu-abc-lesson-301265-what-is-ppa.html](http://digitalstudio7.blogspot.com/2013/10/ubuntu-abc-lesson-301265-what-is-ppa.html)

[http://www.techerator.com/2011/07/an-introduction-to-ubuntus-personal-package-archives/](http://www.techerator.com/2011/07/an-introduction-to-ubuntus-personal-package-archives/)

Some of the info may be dated do to some of them referencing older versions of Ubuntu but the info should still be useful.

Thanks, I probably wasn't clear - I pretty much 'get' the process of adding a ppa and what it is. 

My confusion was specific to this LibreOffice release for 12.04 (Precise). Before 01FEB2014, I went to [https://launchpad.net/~libreoffice/+archive/ppa](https://launchpad.net/~libreoffice/+archive/ppa) , there was a pull-down for 12.04 (Precise) and the lines to add to software sources in Synaptic were shown. But they did nothing when I added them. After the fact, I think I understand now that the supporting packages were not yet built and released to that site. But that is confusing - why have the drop-down and the links if the packages are not yet available?

And how does one know that they are released? With clues form people here, I could guess that that package > [COLOR=#000000]*libreoffice     1:4.2.0~rc4-0ubuntu1~precise4    Rico Tzschichholz (2014-02-01) *[/COLOR] was the one that was key, since the date matched the info posted here, and the title seemed to refer to the build I was looking for (I read elsewhere that RC4 was the same as final release). But how would I know that -  there are 47 packages there, and I have no idea what all those different names mean?

It just seems to me the pull-down should give a "Not Available Yet - WIP" response. Wouldn't that make it clear for more people? I'll see if there is a feedback link on that site.

But since the ppa is up now and active, and I have it working, I'll mark this thread SOLVED. Thanks to all for the feedback and help. LO 4.2 is looking good! I've noticed a few nice UI improvements (right click for a list of tabs in a spreadsheet, CNTRL-G/F for next FIND back/forth), I'm sure I'll see more as I dig around.

-NTL2009

---

### Post by ajgreeny on 2014-02-04
I have just updated my Xubuntu 12.04 64bit system from LO 4.1 to 4.2 using that ppa and so far, with the playing around I have done, it seems to be very good and quite a bit quicker.

If it should start playing up, and causing me problems, I can easly downgrade again to 4.1, but it all looks good at the moment.

---

### Post by SuperFreak on 2014-02-08
> **The Spectre said:**
> LibreOffice 4.2 is now available for Ubuntu 12.04 (Precise) at the main LibreOffice PPA...

[https://launchpad.net/~libreoffice/+archive/ppa](https://launchpad.net/~libreoffice/+archive/ppa)

Upgraded with the PPA but Update offered on the system was a partial one which I usually avoid. I updated anyway, hopefully there is no breakage

---

### Post by rewyllys on 2014-02-09
Three days ago I went through the ppa installation process for Libre Office 4.2 from the LO Website, and installed v. 4.2 in Linux Mint Maya (LM 13).  The installation process requires only copying 3 command-line commands from the LO Website into the Terminal; it took me perhaps as much as 2 whole minutes.

So far, LO 4.2 is working just fine in LM 13.  BTW, LM 13 is based on Ubuntu 12.04 (Precise).

---


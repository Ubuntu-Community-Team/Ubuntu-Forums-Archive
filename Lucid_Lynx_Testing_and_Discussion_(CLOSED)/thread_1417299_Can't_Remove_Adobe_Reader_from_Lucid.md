---
title: "Can't Remove Adobe Reader from Lucid"
date: 2010-02-27
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Lunx on 2010-02-27
Today I came across an article about security vulnerabilities with Adobe  Reader 9.3

[http://www.adobe.com/support/security/bulletins/apsb10-07.html](http://www.adobe.com/support/security/bulletins/apsb10-07.html)

Since I have no real need for this app, I figured I would remove it  altogether, but trying to do so has been a nightmare so far, with no joy.

first thing I tried was through a terminal

```
sudo apt-get remove acroread
```No go, error message instead

[I]Reading package lists... Done
Building dependency tree       
Reading  state information... Done
Package acroread is not installed, so not  removed
0 upgraded, 0 newly installed, 0 to remove and 0 not  upgraded.[/I]

If I go to Ubuntu Software Centre, it doesn't show up in list of  installed packages, despite it showing up in my menu **Applications  > Office > Adobe Reader 9**, and there doesn't seem to be a way  of removing it via Software Centre either. I installed the package originally from the Adobe  site, and followed their installation instructions (yeah, I know,  probably wasn't the best way to go about installing in first place :redface:). 

I've asked a couple of other people on another forum if they could help,  but they've run out of ideas as well, so I figured I beg for help here.

Thanks in advance
Pete

---

### Post by Lunx on 2010-02-27
I went looking through my files to see where this app was installed to, found it in /opt/Adobe

Would simply deleting this file be enough, and would it remove the FF plugin as well, or is that going to be found in mozilla somewhere?

Sorry, I'm three-parts asleep and brain isn't working as it should.

---

### Post by cong06 on 2010-02-27
I mean, I'm sure you already thought about "finding" it.

Maybe try following the icon it made to where it's actual install folder is? (though I'm sure you already found it: /opt/Adobe)

I'm pretty sure that deleting it would cause everything to stop working, but you'd probably want to clean things up (Firefox settings, dead links pointing to /opt/Adobe, Nautilus settings etc.)

But I'm just guessing...

---

### Post by OrangeCrate on 2010-02-27
We already have the fix in the repositories (check the package version in Synaptic).

> Adobe recommends users of Adobe Reader 9.3 and earlier versions for Windows, Macintosh and UNIX update to Adobe Reader **9.3.1**.

---

### Post by cong06 on 2010-02-27
Well, in that case if it's a problem with a busted package, maybe just over-install with 9.3.1?

---

### Post by Lunx on 2010-02-27
> **cong06 said:**
> Well, in that case if it's a problem with a busted package, maybe just over-install with 9.3.1?


Yeah, I was thinking perhaps I'd try updating, then see what happens regarding removing it.

I didn't really explain myself very well in my OP. When I say it doesn't show up in Ubuntu Software Centre, it actually does under "Office", but not when I then select "Installed Software". If I click the More Info link for Adobe Reader, I get the following

*This software is available from the 'lucid-partner' source, which you are not currently using.*

I had a look at my software sources in Synaptic, but nothing there about 'lucid-partner', everything still mentions Karmic ATM, apart from *Medibunti - Ubuntu 10.04 "lucid lynx" free nonfree*, and similar Medibuntu entry for source.

---

### Post by Lunx on 2010-02-27
> **cong06 said:**
> I mean, I'm sure you already thought about "finding" it.

Maybe try following the icon it made to where it's actual install folder is? (though I'm sure you already found it: /opt/Adobe)

Yep, that directory seems to be where it all lives, the only other file I founder is in usr/bin, but it's got a symbolic link pointing to /opt/Adobe

I'll have a go at upgrading and see what that does, whether it will then let me remove it.

Not that much of a problem, but it was using a trial version of some Adobe software a bit over a year ago, and the amount of crap it left behind after uninstalling was one reason I finally got up the courage to give Linux a try (not to mention MS deciding my 'puter needed a restart after installing updates, and shut down without even having the courtesy to warn me and suggest I save my work first. A half-hour's work on a very important document shot to pieces).

---

### Post by Lunx on 2010-02-28
No longer a problem, solved in a rough and ready manner by a fresh install (I reverted from Lucid back to Karmic as it isn't quite stable enough for me to risk using as my only OS). That's not a criticism of Lucid either BTW, I know the risks of running alpha releases LOL

---


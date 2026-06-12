---
title: "Install Open Office 3.0"
date: 2008-07-27
forum: Installation &amp; Upgrades
---

### Post by rvasandani on 2008-07-27
Sir,
I have downloaded Openoffice 3.0 (Beta) from Openoffice.org but I am unable to install it on Ubuntu 8.04. May I request you to help me out.
Vasandani

---

### Post by miesnerd on 2008-07-27
I think this linked thread will answer all your questions.
Open office is awesome!

[http://ubuntuforums.org/showthread.php?t=747722](http://ubuntuforums.org/showthread.php?t=747722)

---

### Post by Ashejoe on 2008-07-27
Believe me... I feel your pain when it comes to trying to make sense out of the procedural chaos of installing a Linux program that is not part of the official Ubuntu repository... like OpenOffice 3.  I imagine it's probably the single biggest reason many people quickly become totally frustrated with Linux and head back on bended knee to Microsoft ?

But like yourself, I wanted to experience OpenOffice 3.  And, after struggling with trying to load the Debian version for well over an hour, I finally gave up and settled on a different strategy......

I downloaded the MICROSOFT WINDOWS version of OpenOffice 3 and loaded it onto my Ubuntu 8.04 system using WINE.  (are you familiar with WINE ?    [www.winehq.org/site/download](www.winehq.org/site/download)  then pick the Ubuntu link.  It installs real easy... even for me.)

It works.... even if it is a back door approach !

---

### Post by Sef on 2008-07-28
> I have downloaded Openoffice 3.0 (Beta) from Openoffice.org but I am unable to install it on Ubuntu 8.04. May I request you to help me out.
Vasandani

Download the Linux [deb package]("http://download.openoffice.org/3.0beta/") for your system (32-bit or 64-bit.)  If you are not sure, then you most likely need the 32-bit version.

> Sir

Not everyone here is a sir.  Best just to start typing the problem.

---

### Post by Ashejoe on 2008-07-28
I tend to disagree with you Sef.

True, you can download the DEB package from the OpenOffice.org website.  **The problem is trying to install it !!!**  That's what rvasandani and I are trying to figure out.

When you unpack that DEB package there are dozens of "separate" DEB packages, none of which make much sense to a Linux novice, like myself.  There is no clear, clean, logical way to install the Beta 3 package unless one is very knowledgeable about working in Konsole mode.

---

### Post by Elfy on 2008-07-28
Change to the directory in a terminal and run

```
sudo dpkg -i *.deb
```

You'll need to make launchers as they are in't the install package yet - or weren't when I did it, my menu launcher is to

/opt/openoffice.org3/program/soffice

---

### Post by miesnerd on 2008-07-28
> **forestpixie said:**
> Change to the directory in a terminal and run

```
sudo dpkg -i *.deb
```

You'll need to make launchers as they are in't the install package yet - or weren't when I did it, my menu launcher is to

/opt/openoffice.org3/program/soffice

forestpixie is right on. But, like i said in my above post, all of that is linked in the URL I provided to a thread. It has the shortcuts to both installing and where the launchers are.
If you're using 32 bit linux you'll have to take out the <force architecture> tag, but  sudo dpkg -i *.deb works. I know. I did it yesterday with the 2nd beta release of OpenOffice.org!

---

### Post by Vinas on 2008-07-29
I would like to kindly point out that the location may vary. For me it's:
**/opt/ooo-dev3/program**

Then from there I just open writer by doing **[COLOR="SeaGreen"]./swriter[/COLOR]** for instance. I can verify the dkpg -i *.deb installs just fine on amd64 builds. :guitar:

Cheers!

---

### Post by miesnerd on 2008-07-29
> **Vinas said:**
> I would like to kindly point out that the location may vary. For me it's:
**/opt/ooo-dev3/program**

Then from there I just open writer by doing **[COLOR="SeaGreen"]./swriter[/COLOR]** for instance. :guitar:

Cheers!

Excellent point. On different systems, it is dependent on what else is installed, and thus, what else is in /opt/

Good call.

---

### Post by lametike on 2008-10-18
i also have this problem! after getting the stable version of the ooo3.0,
some of the files showed:"depenecy is not satisfiable"

---

### Post by Enigmacat on 2008-11-04
I ran in to a problem when installing. One deb. just seemed not to be in the package: ooobasis3-en-US could not be found. Without this my install was worthless. Any way around this?

---


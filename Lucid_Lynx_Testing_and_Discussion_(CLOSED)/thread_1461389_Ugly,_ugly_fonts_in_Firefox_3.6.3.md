---
title: "Ugly, ugly fonts in Firefox 3.6.3"
date: 2010-04-24
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Robert Koehler on 2010-04-24
Love the new look with Lucid, but the font rendering in Firefox on my system is, well, not the best --- see attachment.

The font in Chrome and elsewhere, however, is just fine.

If there a fix I'm missing?

---

### Post by gradinaruvasile on 2010-04-24
Is the Firefox that came with the system or the one downloaded from their site?

Firefox has this font smoothing issues because it uses general font smoothing (that lacks full hinting) - compiling it with customized options however will make it use the Ubuntu style smoothed fonts. By default, Ubuntu-provided Firefox is compiled this way.This ubuntu-style smoothing is made with patching certain libraries and it is not a general Gnome or Linux thing (Debian has ugly system fonts for example).

The generic Linux version from the mozilla site however has general compiling options, that doesnt include the Ubuntu-style smoothing.

And it might be that, even if you use the Lucid version, that xulrunner or Firefox is not compiled with customized options. Probably later this will be corrected.

---

### Post by &#1057;&#1090;&#1088;&#1072;&#1085;&#1085;&#1080;&#1082; on 2010-04-24
Looks bad.

---

### Post by Miguel on 2010-04-24
My take at this is that some code wrote some hinting rules at ~/.fonts.conf or something similar. It happened the same to me while I was running kubuntu and ubuntu with google chrome. For some reason, chrome refused to directly use the KDE preferences and wrote a .fonts.conf file with all hinting deactivated. In KDE, that was only noticeable in chrome and perhaps arora. Once I booted into Ubuntu, firefox read the same rules and looked identical.

---

### Post by Killigrew on 2010-04-24
hmm, can't you just change the standard font of Firefox in the Settings? 
i am using free sans and never experienced any problem with ugly fonts..

greetings

---

### Post by randomizer101 on 2010-04-24
I have always found Firefox takes me an hour to get the fonts right from a fresh installation (thank goodness I don't lose my preferences with every installation of a distro) on Linux. It seems to ignore GNOME settings so you need a custom ~/.fonts.conf to get it right, and there's a ton of different combinations of hinting and smoothing to mess with. However I've noticed with the version that comes in the Lucid repos it seems to be ok out of the box, at least to my eyes.

---

### Post by mikewhatever on 2010-04-24
By default, Firefox uses the fonts suggested by the site creator. It won't, if you open Edit->Preferences->Content->Advanced, and untick the 'Allow pages to choose their own fonts ...' box. If that's still bad, you can play with font selection (second from top), until satisfied.

---

### Post by dcstar on 2010-04-24
> **Robert Koehler said:**
> Love the new look with Lucid, but the font rendering in Firefox on my system is, well, not the best --- see attachment.

The font in Chrome and elsewhere, however, is just fine.

If there a fix I'm missing?

The latest Ubuntu repository Firefox 3.6.3 is now complied with font smoothing - this change only occurred a few weeks ago.

Prior to that I was using PPA versions that were compiled with this option because of this exact issue, but the "official" version now does the job for me.

If you installed 10.04 from a CD I am not sure if the version you may be running is one with this option.

You may also need the firefox-gnome-support package.

---

### Post by Robert Koehler on 2010-04-25
> By default, Firefox uses the fonts suggested by the site creator. It  won't, if you open Edit->Preferences->Content->Advanced, and  untick the 'Allow pages to choose their own fonts ...' box.

That did the trick! Thanks!

---

### Post by RickyCodes on 2010-04-25
It also looks to be a video driver. 

Mine looked like this right after I installed the RC on both of my PC's one with an ati card and one with the nvidia card. Enabled the drivers and then it looked normal.

---

### Post by fab.head on 2010-04-25
> **Miguel said:**
> My take at this is that some code wrote some hinting rules at ~/.fonts.conf or something similar. It happened the same to me while I was running kubuntu and ubuntu with google chrome. For some reason, chrome refused to directly use the KDE preferences and wrote a .fonts.conf file with all hinting deactivated. In KDE, that was only noticeable in chrome and perhaps arora. Once I booted into Ubuntu, firefox read the same rules and looked identical.

Thanks Miguel! Your solution worked for me :)

---

### Post by bburg on 2010-04-27
This helped me:

[Re: Firefox 3.5 not following gnome font settings]("http://ubuntuforums.org/showpost.php?p=7634222&postcount=12")

---

### Post by andrewabc on 2010-04-27
I know with ubuntu 9.10 installing WINE can screw up firefox fonts.
So check and see if you installed WINE.

---


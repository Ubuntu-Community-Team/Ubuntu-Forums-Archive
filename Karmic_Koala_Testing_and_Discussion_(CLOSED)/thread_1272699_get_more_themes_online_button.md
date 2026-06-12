---
title: "get more themes online button"
date: 2009-09-22
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by meeples on 2009-09-22
i have only just noticed it. :D
[IMG]http://i37.tinypic.com/dzj77o.png[/IMG]

the only problem is,
it points to [art.gnome.org/themes]("http://art.gnome.org/themes/") instead of [gnome-look.org]("http://www.gnome-look.org/")

---

### Post by olskar on 2009-09-22
IMO the KDE approach is MUCH better. In there you can see a small screenshot of the theme (inside the themechooser) and just press download. The same goes for wallpapers. Everything is collected from kdelook.

Edit: But better than nothing, don't want to sound all pessimistic :)

---

### Post by meeples on 2009-09-22
> **olskar said:**
> IMO the KDE approach is MUCH better. In there you can see a small screenshot of the theme (inside the themechooser) and just press download. The same goes for wallpapers. Everything is collected from kdelook.

Edit: But better than nothing, don't want to sound all pessimistic :)

yea i agree, theres an app you can get but again it just downloads from art.gnome.org.

at least a link is a start :lolflag:

---

### Post by Tibuda on 2009-09-22
That's nice.

I agree about the URL, gnome-look got much better stuff available.

---

### Post by puccaso on 2009-09-22
sudo apt-get install gnome-art

---

### Post by MadsRH on 2009-09-22
> **meeples said:**
> ...the only problem is,
it points to [art.gnome.org/themes]("http://art.gnome.org/themes/") instead of [gnome-look.org]("http://www.gnome-look.org/")

File a bug ;-)

---

### Post by meeples on 2009-09-22
> **MadsRH said:**
> File a bug ;-)

wish i could.

launchpad keep *BLEEP*ing up everytime i try o.O

---

### Post by Starks on 2009-09-22
Bug filed.

[https://bugs.edge.launchpad.net/ubuntu/+source/gnome-control-center/+bug/434944](https://bugs.edge.launchpad.net/ubuntu/+source/gnome-control-center/+bug/434944)

---

### Post by Seventh Reign on 2009-09-22
Hey,  its a move in the right direction.

---

### Post by meeples on 2009-09-22
> **Starks said:**
> Bug filed.

[https://bugs.edge.launchpad.net/ubuntu/+source/gnome-control-center/+bug/434944](https://bugs.edge.launchpad.net/ubuntu/+source/gnome-control-center/+bug/434944)

thanks!:popcorn:

---

### Post by meeples on 2009-09-22
> 

Thanks, but this is an upstream design decision, and not a bug:

"The gnome-look.org website is not an official GNOME website, so we cannot
guarantee that it will always be a suitable destination."


very poor decision.

art.gnome.org/themes/ doesnt even contain full themes, just window borders and icons and other elements of themes.

i thought gnome were trying to up there game on usability?

---

### Post by Merk42 on 2009-09-22
Oh I can see it now...

"We found the average user didn't download more themes, so clearly the default is good enough"

---

### Post by blakamin on 2009-09-22
Shame about the bug report. 
:(

---

### Post by orlox on 2009-09-22
Besides, the "splash screens" and "login window" in art.gnome will become irrelevant in karmic...

Been wanting to see something like this, but I don't think it's worth to add something so unpolished in the release...In any case, I don't think the direct link to gnome-look would help a noob, the large amount of categories would probably confuse them.

I think the kde approach is the right one, with full themes readily available for download with screenshots.

---

### Post by mejy on 2009-09-22
I've already commented on the bug, but I feel this is a problem with art.gnome.org, not gnome-appearance properties - 

I think perhaps the answer to this is to invest some time in art.gnome.org prior to Gnome 3, rather than to endorse an unoffiial, commercially managed website, and as such should be a separate bug. Specifically, a group of site maintainers selecting the best of the community's artwork would result in a high quality and consistent pool of artwork, instead of the current set of outdated art of varying quality.

---

### Post by blakamin on 2009-09-22
Basically art.gnome.org needs to be updated along the lines of gnome-look, or all the artists have to upload their themes to both (if art.gnome.org had a "real" spot for complete themes)

---

### Post by meeples on 2009-09-23
> **blakamin said:**
> Basically art.gnome.org needs to be updated along the lines of gnome-look, or all the artists have to upload their themes to both (if art.gnome.org had a "real" spot for complete themes)

yeah and then maybe they could integrate an updated Gnome Art app into appearance preferences, quality themes with the bother of tarballs :)

---

### Post by Starks on 2009-09-23
Both Art Gnome and Gnome Look are quite terrible at making "themes" easy to install.

---

### Post by meeples on 2009-09-23
> **Starks said:**
> Both Art Gnome and Gnome Look are quite terrible at making "themes" easy to install.

what if the tarballs that the themes come in were renamed to .theme or something simple, and gnome updated the file-roller to recognise .themes and open appearance preferences and install them when the file was opened?

e.g. simply renaming NewWave.tar.gz to NewWave.theme or even NewWave.thm

that way the compression and file structure isnt changed...but file-roller recognises it as a system theme and we have an easy way to install themes..

---

### Post by orlox on 2009-09-23
Perhaps they could work out something like the "apt://" links. Just a simple "theme://" that points to the url of the tar.gz file that could be handled by a firefox extension.

Perhaps adoption of "apt://" links is not so good, but I think the same idea could be applied very well to gnome or kde themes...

Even though, I think that canonical could do a very good job by creating a community driven site for kde and gnome themes, that focuses on basic system theming. Only system wide themes (no "controls", "metacity", and gtk sections separetely), gdm themes (for the new gdm of course) and xsplash themes (though there's no frontend for managing xsplash themes yet).

I find gnome-look awesome, and it will always be a good place to store themes for particular applications (i.e. gnomenu, cairo clock, dockbarx), but a more centered and coherent solution for system theming is required.

---

### Post by Tibuda on 2009-09-23
> **meeples said:**
> what if the tarballs that the themes come in were renamed to .theme or something simple, and gnome updated the file-roller to recognise .themes and open appearance preferences and install them when the file was opened?

e.g. simply renaming NewWave.tar.gz to NewWave.theme or even NewWave.thm

that way the compression and file structure isnt changed...but file-roller recognises it as a system theme and we have an easy way to install themes..

Nice idea. .theme for GTK/Metacity themes (as they both are installed at ~/.themes or /usr/share/themes) and .icon for icons/cursor themes (as they both are installed at ~/.icons or /usr/share/icons).

---

### Post by orlox on 2009-09-23
> **danielrmt said:**
> Nice idea. .theme for GTK/Metacity themes (as they both are installed at ~/.themes or /usr/share/themes) and .icon for icons/cursor themes (as they both are installed at ~/.icons or /usr/share/icons).

Adding extensions would be great also, and could also be used to standardize theme packs. It's quite common in gnome-look that people upload themes in tar.gz files that contain emerald, metacity, and icons inside. I don't know if adding many different extensions for all types of themes is not so reasonable, perhaps it would be better to establish a simple .theme format that could hold any type of theming, described perhaps by a simple text file in the archive.

Even more, a centralized tool to manage theme installation/removal could be created, not just icons/metacity/gtk-controls/cursors but application specific things. Perhaps this thing is pointing a bit too high right now, but it would be awesome to create a standard way for applications to handle theme management.

---

### Post by chrisccoulson on 2009-09-23
Upstream already rejected the idea of having a link to gnome-look, because it is not an official GNOME website, and they have absolutely zero control over content, availability and licensing. art.gnome.org is an official GNOME website, and I don't really see why an official GNOME tool shouldn't link to the official GNOME website.

---

### Post by cyberkilla on 2009-09-23
> **chrisccoulson said:**
> Upstream already rejected the idea of having a link to gnome-look, because it is not an official GNOME website, and they have absolutely zero control over content, availability and licensing. art.gnome.org is an official GNOME website, and I don't really see why an official GNOME tool shouldn't link to the official GNOME website.

Not meaning to be critical of everything, but neither of the websites are particularly easy to browse. The screenshots open up on a laggy pop-up windows, or there isn't enough info to determine whether the theme is what you're searching for. 

Is there some sort of application to browse through community themes and see screenshots? That would definitely be something unique and interesting for new users.

---

### Post by Merk42 on 2009-09-23
> **orlox said:**
> Adding extensions would be great also, and could also be used to standardize theme packs. It's quite common in gnome-look that people upload themes in tar.gz files that contain emerald, metacity, and icons inside. I don't know if adding many different extensions for all types of themes is not so reasonable, perhaps it would be better to establish a simple .theme format that could hold any type of theming, described perhaps by a simple text file in the archive.

Even more, a centralized tool to manage theme installation/removal could be created, not just icons/metacity/gtk-controls/cursors but application specific things. Perhaps this thing is pointing a bit too high right now, but it would be awesome to create a standard way for applications to handle theme management.

Standardize? In Linux? hahaha but but you're taking away my FREEDOM man!!

For those of you running Windows 7, even they made sharing themes a breeze.  You can export is as .themepack (as simple as going to "share theme", this .themepack can contain wallpaper(s), icons (for a few),  cursors, sounds and a screensaver.

I'd be great if GNOME had the same, but, well, see above.


If the problem with linking to art.gnome.org is bad because of layout/choices, where does one file a bug to improve it?

---

### Post by orlox on 2009-09-23
> **Merk42 said:**
> Standardize? In Linux? hahaha but but you're taking away my FREEDOM man!!

For those of you running Windows 7, even they made sharing themes a breeze.  You can export is as .themepack (as simple as going to "share theme", this .themepack can contain wallpaper(s), icons (for a few),  cursors, sounds and a screensaver.

I'd be great if GNOME had the same, but, well, see above.


If the problem with linking to art.gnome.org is bad because of layout/choices, where does one file a bug to improve it?

Probably you can post a bug in gnome-appearance-properties in bugzilla. All gnome core projects are handled there. Just don't go posting this in launchpad cause they rarely check there.

---

### Post by meeples on 2009-09-23
> **Merk42 said:**
> Standardize? In Linux? hahaha but but you're taking away my FREEDOM man!!

:lolflag:

---

### Post by MadsRH on 2009-09-23
> **chrisccoulson said:**
> Upstream already rejected the idea of having a link to gnome-look, because it is not an official GNOME website, and they have absolutely zero control over content, availability and licensing. art.gnome.org is an official GNOME website, and I don't really see why an official GNOME tool shouldn't link to the official GNOME website.

Well, if the official site you link to has nothing to offer, why link to it? The button was suppose to improve the user-experience, but I don't think that's the case.
I say, remove the button until there's a better theme-website to link to.

---

### Post by meeples on 2009-09-23
> **madsrh said:**
> well, if the official site you link to has nothing to offer, why link to it? The button was suppose to improve the user-experience, but i don't think that's the case.
I say, remove the button until there's a better theme-website to link to.

+1

---

### Post by hotstovejer on 2009-09-24
You can change where the links point. Go into gconf-editor and go to Apps -> Control Center -> Appearance. Change it up to whatever you want.

Thanks!

---


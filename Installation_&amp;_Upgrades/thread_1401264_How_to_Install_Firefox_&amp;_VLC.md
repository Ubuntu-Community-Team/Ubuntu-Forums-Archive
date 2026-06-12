---
title: "How to Install Firefox &amp; VLC?"
date: 2010-02-07
forum: Installation &amp; Upgrades
---

### Post by karumudi7 on 2010-02-07
Today I downloaded Firefox 3.6 for Ubuntu; But how to install that.
Already I have previovs version.

Also how to download latest version of VLC,
Today I installed 1.0.3 but NO sound.

I am NEWBIE to UBUNTU,
Using Karmic.

---

### Post by presence1960 on 2010-02-07
If you are new and are not familiar with linux it is best to not download software from third party web sites, but rather use Synaptic Package Manager (System > Administration > Synaptic Package Manager). You can install ubuntizilla to manage FF & Thunderbird versions and install VLC from there also.

[http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page) - for info on ubuntuzilla script / software sources

You can also install vlc by opening a terminal and running ```
sudo apt-get install vlc
``` Or is it sudo aptitude in kubuntu, I forget I haven't used Kubuntu for over a year!

You can also install ubuntizilla by substituting "ubuntuzilla" for vlc in the above command

---

### Post by nanotube on 2010-02-07
first, the ubuntuzilla script package is not in the default repositories. second, the ubuntuzilla script has been superseded by the ubuntuzilla repository. 

but all that's beside the point. 

the main idea put forth by presence1960 is quite valid: if you're new, stick to software that's in the official repositories.  you can grab firefox and vlc out of the repos using synaptic package manager. no need to go around downloading stuff willy nilly off the web.

---


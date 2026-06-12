---
title: "How To Install Plugin Architecture on Ubuntu 9.10 Server ?!"
date: 2010-03-12
forum: Installation &amp; Upgrades
---

### Post by banyezdemah on 2010-03-12
Hi 
 
I have an Ubuntu 9.10 Server (cacti is installed) and I do not know how to install Cacti Plugin Architecture on it. 
Does anyone can help me on this? 
 
----------------------------------------------- 
DISTRIB_ID=Ubuntu 
DISTRIB_RELEASE=9.10 
DISTRIB_CODENAME=karmic 
DISTRIB_DESCRIPTION="Ubuntu 9.10" 
----------------------------------------------- 
 
 
Thx[[IMG]http://twitter.com/favicon.ico[/IMG]]("http://search.twitter.com/search?q=Hi%0D%0A%0D%0AI%20have%20an%20Ubuntu%209.10%20Server%20%28cacti%20is%20installed%29%20and%20I%20do%20not%20know%20how%20to%20install%20Cacti%20Plugin%20Architecture%20on%20it.%0D%0ADoes%20anyone%20can%20help%20me%20on%20this%3F%0D%0A%0D%0A-----------------------------------------------%0D%0ADISTRIB_ID%3DUbuntu%0D%0ADISTRIB_RELEASE%3D9.10%0D%0ADISTRIB_CODENAME%3Dkarmic%0D%0ADISTRIB_DESCRIPTION%3D%22Ubuntu%209.10%22%0D%0A-----------------------------------------------%0D%0A%0D%0A%0D%0AThx")[[IMG]http://www.google.com/favicon.ico[/IMG]]("http://www.google.com/search?q=Hi%0D%0A%0D%0AI%20have%20an%20Ubuntu%209.10%20Server%20%28cacti%20is%20installed%29%20and%20I%20do%20not%20know%20how%20to%20install%20Cacti%20Plugin%20Architecture%20on%20it.%0D%0ADoes%20anyone%20can%20help%20me%20on%20this%3F%0D%0A%0D%0A-----------------------------------------------%0D%0ADISTRIB_ID%3DUbuntu%0D%0ADISTRIB_RELEASE%3D9.10%0D%0ADISTRIB_CODENAME%3Dkarmic%0D%0ADISTRIB_DESCRIPTION%3D%22Ubuntu%209.10%22%0D%0A-----------------------------------------------%0D%0A%0D%0A%0D%0AThx")[[IMG]http://static.smarterfox.com/media/wiki-favicon-sharpened.png[/IMG]]("http://smarterfox.com/wikisearch/search?q=Hi%0D%0A%0D%0AI%20have%20an%20Ubuntu%209.10%20Server%20%28cacti%20is%20installed%29%20and%20I%20do%20not%20know%20how%20to%20install%20Cacti%20Plugin%20Architecture%20on%20it.%0D%0ADoes%20anyone%20can%20help%20me%20on%20this%3F%0D%0A%0D%0A-----------------------------------------------%0D%0ADISTRIB_ID%3DUbuntu%0D%0ADISTRIB_RELEASE%3D9.10%0D%0ADISTRIB_CODENAME%3Dkarmic%0D%0ADISTRIB_DESCRIPTION%3D%22Ubuntu%209.10%22%0D%0A-----------------------------------------------%0D%0A%0D%0A%0D%0AThx&locale=en-US")[[IMG]http://static.smarterfox.com/media/popup_bubble/oneriot-favicon.ico[/IMG]]("http://www.oneriot.com/search?p=smarterfox&ssrc=smarterfox_popup_bubble&spid=8493c8f1-0b5b-4116-99fd-f0bcb0a3b602&q=Hi%0D%0A%0D%0AI%20have%20an%20Ubuntu%209.10%20Server%20%28cacti%20is%20installed%29%20and%20I%20do%20not%20know%20how%20to%20install%20Cacti%20Plugin%20Architecture%20on%20it.%0D%0ADoes%20anyone%20can%20help%20me%20on%20this%3F%0D%0A%0D%0A-----------------------------------------------%0D%0ADISTRIB_ID%3DUbuntu%0D%0ADISTRIB_RELEASE%3D9.10%0D%0ADISTRIB_CODENAME%3Dkarmic%0D%0ADISTRIB_DESCRIPTION%3D%22Ubuntu%209.10%22%0D%0A-----------------------------------------------%0D%0A%0D%0A%0D%0AThx")

---

### Post by JohnYYC on 2010-04-22
I am having the same issue. I have found a few guides and I have followed them but I end up getting a error when I run the command:

```

# mysql cacti < cacti-plugin-arch/pa.sql

```

---

### Post by JohnYYC on 2010-05-05
Bump!

Anyone?

---

### Post by davidmerrick on 2010-06-28
I thought I'd had it figured out but I screwed up somewhere because one of my devices isn't updating.

I wrote up a guide on how to get to where I'm at now: [http://bit.ly/cacti-pa-ubuntu-910](http://bit.ly/cacti-pa-ubuntu-910). Hope it helps, and I'll add more when I get the install locked down!

---

### Post by J-C90 on 2010-07-12
I've got it to the point where it looked to be all installed and working but the poller fails to run with an invalid path error. I have not been able to track down where that problem is after a day of searching, so I am now downloading CactiEZ to give that a try instead.

My guide is here if anyone wants to try and work it out. I'm installing it as a VM:

[http://58.96.99.76/joomla/index.php/tech-a-it-stuff/networking-other/66-cacti-plugin-architecture-install-on-ubuntu](http://58.96.99.76/joomla/index.php/tech-a-it-stuff/networking-other/66-cacti-plugin-architecture-install-on-ubuntu)

A friend of mine apparently has it running on 10.04 but I am not sure how he did it, just that it took him a few days of stuffing around. Such a shame the PIA is not included in the base package.

---


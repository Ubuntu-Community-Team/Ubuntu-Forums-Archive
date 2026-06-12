---
title: "Make SeaMonkey the default browser"
date: 2014-07-10
forum: Installation &amp; Upgrades
---

### Post by RogerDavis on 2014-07-10
How do I set SeaMonkey as the default browser?  I don't even see a choice to add anything other than Firefox and Browser.

---

### Post by slooksterpsv on 2014-07-10
You can choose other and locate it yourself, if you installed it via a PPA (as I can't find it in repos) or via a DEB it should be in /usr/bin.

I didn't know seamonkey was still around... seems kind of old.

---

### Post by deadflowr on 2014-07-10
Not sure, might be because of what category seamonkey falls under.
For me, my browser's fall into WebBrowsers.

Possibly look at the desktop file for seamonkey in 
/usr/share/applications
(Best to open gedit and then open it from there.)

Look at what the Category listing says.

my thoughts on the matter anyway.

---

### Post by deadflowr on 2014-07-10
> **slooksterpsv said:**
> You can choose other and locate it yourself, if you installed it via a PPA (as I can't find it in repos) or via a DEB it should be in /usr/bin.

I didn't know seamonkey was still around... seems kind of old.

I'm guessing that this is unity. Inside system settings > details > default applications.
If so, there is no other option.
Total guess though...

---

### Post by pololo on 2014-07-10
I am using Seamonkey with Xubuntu, in Ubuntu may be in a similar manner.

Setting -> Preferred Applications -> Web Browser and select Other, you must specify the path where is the seamonkey-bin, for me is located at my home: ~/seamonkey2x/seamonkey/seamonkey-bin

---

### Post by RogerDavis on 2014-07-11
I'm using Ubuntu 14.04 and Gnome, and there is NO option for Other at System Settings > Details > Default Applications.

So my biggest problem is how to specify "Other".

Secondly, I still haven't found the SeaMonkey folder.

---

### Post by RogerDavis on 2014-07-11
Found the folder location >  /opt/seamonkey

---

### Post by RogerDavis on 2014-07-21
I tried selecting "make SeaMonkey the default browser" but that doesn't work, I still get bumped to FireFox sometimes.

---

### Post by RogerDavis on 2014-07-24
For how to actually accomplish this, see  [http://ubuntuforums.org/showthread.php?t=2234277&p=13081343#post13081343](http://ubuntuforums.org/showthread.php?t=2234277&p=13081343#post13081343)

---


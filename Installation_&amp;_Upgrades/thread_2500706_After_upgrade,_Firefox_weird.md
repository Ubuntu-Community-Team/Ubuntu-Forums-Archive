---
title: "After upgrade, Firefox weird"
date: 2024-09-09
forum: Installation &amp; Upgrades
---

### Post by john163 on 2024-09-09
I updated my 20.04 to 22.04.4  Now, Firefox acts like it's always in incognito mode... it doesn't have any of my bookmarks or passwords, and when I close and reopen it, it forgets everything I've done.

---

### Post by deadflowr on 2024-09-09
Not sure when it happened, but Firefox on 22.04 is a snap package.
You can replace it with another Firefox, either ppa, tar package directly from Firefox, or flatpak.
And see if that helps.

Personally, I follow this guide to add mozilla's repository:
[https://support.mozilla.org/en-US/kb/install-firefox-linux#w_install-firefox-deb-package-for-debian-based-distributions](https://support.mozilla.org/en-US/kb/install-firefox-linux#w_install-firefox-deb-package-for-debian-based-distributions)
That way it updates along with the normal updates.

---

### Post by john163 on 2024-09-09
> **deadflowr said:**
> Not sure when it happened, but Firefox on 22.04 is a snap package.

Sooo... Ubuntu changed how Firefox is deployed, knowing that would wipe out all history and bookmarks and saved passwords, and didn't tell anyone???

I had no notice that "Hey, if you do this, everything in Firefox is gonna get wiped out, you had better manually back up now".

How happy am I? :-|

---

### Post by ajgreeny on 2024-09-09
I have never used the snap Firefox but use the FF archive extracted and run it from the executable file contained in that.
This uses the same profile, ie, all the history and bookmarks from the .deb versions installed previously, though it can be necessary to start FF the first time with command **firefox -p** and choose the profile you want from that.

The snap uses a new profile I think, which I believe is in the folder **~/snap/firefox** so it should be possible if you wish to move your old profile folder into that new snap one.
I can't give more detail as I've never used the snap version and have no personal experience of this.

---


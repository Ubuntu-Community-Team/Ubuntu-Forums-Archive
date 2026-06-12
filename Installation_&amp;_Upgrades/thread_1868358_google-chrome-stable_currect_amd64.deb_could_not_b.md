---
title: "google-chrome-stable_currect_amd64.deb could not be opened"
date: 2011-10-24
forum: Installation &amp; Upgrades
---

### Post by Ifaistos on 2011-10-24
Hello :-)
This is the error I get when I d/l and try to install the chrome instead of the chromium that we have in Ubuntu Software Center.

"google-chrome-stable_currect_amd64.deb could not be opened"

Should I install synaptic?

I never had a problem with previous versions.
I just upgraded to 11.10, and I am facing various issues.
This is one of them.

Any ideas?
Thank you all in advance.

---

### Post by tors on 2011-10-24
> **Ifaistos said:**
> Hello :-)
This is the error I get when I d/l and try to install the chrome instead of the chromium that we have in Ubuntu Software Center.

"google-chrome-stable_currect_amd64.deb could not be opened"

Should I install synaptic?

I never had a problem with previous versions.
I just upgraded to 11.10, and I am facing various issues.
This is one of them.

Any ideas?
Thank you all in advance.


It looks like you have a spelling mistake in that sentence, "currect" should perhaps be "current"?

---

### Post by Ifaistos on 2011-10-24
yes you are right there is a mistake.
But the mistake is mine in copying the name of the error message.

The file is downloaded and double clicked.
Then the Software center produces that error message.

Still having the problem.  Anyone?

---

### Post by tors on 2011-10-24
You could try to install it from a terminal with "dpkg"

#> sudo dpkg -i $HOME/Desktop/google-chrome-stable_current_amd64.deb

---

### Post by Ifaistos on 2011-10-24
This is the result...

Selecting previously deselected package google-chrome-stable.
(Reading database ... 132325 files and directories currently installed.)
Unpacking google-chrome-stable (from .../google-chrome-stable_current_amd64.deb) ...
dpkg: dependency problems prevent configuration of google-chrome-stable:
 google-chrome-stable depends on libnspr4-0d (>= 4.7.3-0ubuntu1~); however:
  Package libnspr4-0d is not installed.
 google-chrome-stable depends on libcurl3; however:
  Package libcurl3 is not installed.
dpkg: error processing google-chrome-stable (--install):
 dependency problems - leaving unconfigured
Processing triggers for gnome-menus ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for man-db ...
Errors were encountered while processing:
 google-chrome-stable


What could be wrong?!

---

### Post by tors on 2011-10-24
It looks like "libnspr4-0d" and "libcurl3" are not installed.
Maybe they are available in the repository.
You could try:

#> sudo apt-get install libnspr4-0d libcurl3


, to see if they are available and if so install them.

---

### Post by Ifaistos on 2011-10-24
It worked !!!

I wonder why the dependencies where missing.
I just did a clean install.

Thanks a million for the help :-)

---


---
title: "Unable to install Google Chrome with Software Installer after 14.04 -&gt; 16.04 Upgrade"
date: 2016-09-19
forum: Installation &amp; Upgrades
---

### Post by netsurfau on 2016-09-19
I just upgraded from 14.04 to 16.04 (which ran smoothly and only had a message about having to manually re-install some apps), and started re-installing
my regularly used apps.  I downloaded google-chrome-stable_current_amd64.deb from Google and when I tried running the installer. it opened up the 
"Ubuntu Software" app and appeared with an "Install" button.  I click on the button, install starts, then stops about three seconds later.
I now have an icon in the Launcher bar with a question mark and says "waiting to install", but clicking on it does nothing.
If I check the "Installed" tab in Ubuntu Software, under "Installed Add-ons" "google-chrome-stable" appears twice, with an Install button next to it.  But, if I
click on the Install button, I'm asked if I want to remove the app, and when I click Remove, I get an error message saying "Sorry, this did not work" "Removal
of google-chrome-stable failed."

What am I missing?

---

### Post by netsurfau on 2016-09-20
I managed to get the GDebi Package Installer, installed (Not all installs working).
With this I was able to sort out this issue.  

Now to work out why other system apps are crashing.

---


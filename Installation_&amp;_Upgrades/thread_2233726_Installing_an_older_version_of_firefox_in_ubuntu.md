---
title: "Installing an older version of firefox in ubuntu"
date: 2014-07-10
forum: Installation &amp; Upgrades
---

### Post by Vishnu27 on 2014-07-10
I need to install firefox 3.6.15 in ubuntu 12.04.The OS already comes with a much newer firefox(Firefox 30).Please provide the steps to uninstall Firefox 30 and install Firefox 3.6.15.

---

### Post by Dennis N on 2014-07-10
You realize that 3.6.15 is quite old (released in 2011) and definitely not recommended for use.  There is a general comment on custom Firefox installation of a second version in this thread: [http://ubuntuforums.org/showthread.php?t=2233150](http://ubuntuforums.org/showthread.php?t=2233150) post #2. 

Doing such a manual installation requires some user background on profiles:

[https://support.mozilla.org/en-US/kb/profiles-where-firefox-stores-user-data](https://support.mozilla.org/en-US/kb/profiles-where-firefox-stores-user-data)
[https://support.mozilla.org/en-US/kb/profile-manager-create-and-remove-firefox-profiles](https://support.mozilla.org/en-US/kb/profile-manager-create-and-remove-firefox-profiles)

---

### Post by Vishnu27 on 2014-07-11
Please provide step by step installation procedure.I do not wish to have both versions of firefox together.

Please provide a clean uninstallation and installation procedure.

---

### Post by ian-weisser on 2014-07-11
1) Use the package manager to remove the (newer) version of Firefox.
2) Obtain the older version of Firefox from your own source.
3) Install the older version Firefox. The installation method depends upon if your source is a .deb, tarball, or something else.

Since the older version of Firefox will lack many security fixes, I recommend against storing any sensitive/personal data or running any important services on that machine. I wouldn't consider it secure.

---

### Post by Rob Sayer on 2014-07-11
I don't think you need to run the latest version of all software but with a browser, yes.  As mentioned, if you use an old firefox version you're making your system vulnerable to hacks.

However, I sympathize.  I hate the new firefox releases.  It's been going downhill for some time.

Basically Mozilla has turned me into a Chrome user.  If firefox is going to use a bad imitation of the Chrome UI why not?  Chrome uses significantly less RAM and is much faster.  And it has up to date Flash support in linux.

---

### Post by Dennis N on 2014-07-11
Firefox will run from where you put it's program folder. /opt is a good place, so that other users can access it as well. You could even put it in your home folder. If the folder is at /opt/firefox, make a launcher with command /opt/firefox/firefox to start it, but I would first test it by running from the terminal in case it doesn't work 100% correctly since it is so old. Plugin or extension versions that work with it could no longer be available. You should run it a new profile just to avoid problems with current plugins or extensions.

After confirming that it works, you could remove the other installation with the software center, or a package manager (but why bother? you may want it later.)

Good luck and cross your fingers that you don't have any security issues.

---


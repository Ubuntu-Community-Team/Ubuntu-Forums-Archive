---
title: "Yep - I've managed to destroy my Firefox"
date: 2005-06-07
forum: Installation &amp; Upgrades
---

### Post by twoseids on 2005-06-07
Hi all,

New to Linux and Ubuntu, though I have been having some success the past week thanks to the great documentation and great folks out there.

I was running the upgraded Firefox 1.0.4, and everything was going just fine.  [COLOR=Red]NOTE TO READERS:  IF EVERYTHING IS GOING JUST FINE, DON'T MESS WITH IT.[/COLOR]  I read up on how to migrate my Windows Thunderbird profile to Ubuntu Thunderbird, and it went great - I'm up and running with all my folders and e-mails.

I tried the same thing with Firefox (basically copying my Windows profile folder info directly over the Ubuntu profile information but keeping the same folder name), and when I tried to open up Firefox, I got a mostly blank screen.  The menu bar options (File, Edit, View, etc.) were all textually crammed into the upper left of the screen.  There was the hint of an address bar, but you can't click in it.  Nothing was clickable, actually.

I tried a complete removal and reinstallation through Synaptic Package Manager, and even found a different entry to install "mozilla-firefox" (which uninstalled "firefox") but nothing has restored my Firefox browser.

Help!  I'm back in Windows for the time being and I don't like it!

---

### Post by tread on 2005-06-07
remove the mozilla settings in your home directory: the directory will be 

/home/username/.mozilla

the problem is probably a permissions issue, i suggest doing

chown username.username -R .mozilla

before you delete the directory.

---

### Post by ow50 on 2005-06-07
You really shouldn't copy the entire profile directory. Here's an untested list of what to copy:
bookmarks.html
cookies.txt
formhistory.dat
hostperm.1
key3.db
signons.txt
user.js

And perhaps prefs.js, but you might want to edit it and remove some lines first.

---

### Post by twoseids on 2005-06-07
And ten minutes later, I'm happy to be writing this reply from my Firefox browser in Ubuntu.  Thanks a million, tread!

ow50 - I just may try that!  Good words.

---


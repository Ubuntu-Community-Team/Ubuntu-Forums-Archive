---
title: "How list unuseable, unsupported packages after upgrade"
date: 2009-12-10
forum: Installation &amp; Upgrades
---

### Post by Ordes on 2009-12-10
i upgrade jaunty to karmic.. everything fine

Some packages are not supported anymore e.g pulse audio devise chooser, remastersys (old version).

When i checked synaptic and searching for them, they still had been installed, and i had to remove them through synaptic...

Now, these two, i still remember, as i use them often, and recognized it at once, that they were missing...

Question:
How can i filter packages like that (e.g in synaptic), so i can get rid of them, i tried broken packages, but nothing shows up in there.

any suggestions

thank you

---

### Post by oldfred on 2009-12-10
I periodically run these to houseclean, I assume they still work in Karmic as I just did a clean install. Some have suggested caution as deborphan will delete anything you manually installed.

HouseKeeping:
sudo apt-get update 
sudo apt-get upgrade 
sudo apt-get autoremove
# removes .deb
sudo apt-get autoclean

HOWTO: Cleaning up all those unnecessary junk files...
but see caution above.
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

---

### Post by Ordes on 2009-12-12
thanks...

the guide was pretty helpful....

---


---
title: "Update Manager won't install my updates, it gives an error message"
date: 2007-12-07
forum: Installation &amp; Upgrades
---

### Post by jerseyboy91 on 2007-12-07
When I tried to update using Update Manager today, I got this error after I entered my password in it:

Failed to run /usr/sbin/synaptic '--hide-main-window' '--non-interactive' '--parent-window-id' '50331651' '--progress-str' 'Please wait, this can take some time.' '--finish-str' 'Update is complete' '--set-selections-file' '/tmp/tmphkGDx4' as user root.

And I guess I can't do any sudo commands afterwards. It's weird, because it's been working for a while, and now this happens. Anyone have any ideas?

---

### Post by taurus on 2007-12-07
What happens if you open a terminal and run these two commands?

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by jerseyboy91 on 2007-12-07
Nothing shows up on the terminal showing an update. It just goes to a new blank line for me to type a new command. I think something's wrong with the sudo command on my pc.

---

### Post by taurus on 2007-12-07
It would be nice if you can post the commands and the complete outputs.

---

### Post by DouglasAWh on 2008-05-27
Any problems with this is 8.04?  I'm having some problems.

---


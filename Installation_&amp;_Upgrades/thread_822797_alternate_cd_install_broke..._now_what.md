---
title: "alternate cd install broke... now what?"
date: 2008-06-08
forum: Installation &amp; Upgrades
---

### Post by mlwalla on 2008-06-08
So I was doing a clean install of 8.04 on my desktop but got an error during the "select and install software" step.  I went ahead and finished the install after skipping the other steps.  When it rebooted I got to the command line ok.  I tried installing 'ubuntu-desktop' from the cd, but no dice- guess the image was corrupt or something...

Is there a way to finish the install from the network by configuring the apt sources from the command line?  Or is there more involved with the 'select and install software' step of the alternate cd install process than the desktop stuff?

I'm out of blank cds, and the burner on the old laptop I'm posting from now is a little dodgy anyway.  I'm hoping there is a way to get around this...

---

### Post by arinlares on 2008-06-08
you would probably want to order a live cd, or go to a friend's house and borrow a disc and his burner.

---

### Post by Sef on 2008-06-08
Are you connected to the net? If so, then try this code:

```
sudo apt-get update && sudo apt-get dist-upgrade
```

Did you try startx and see if you get a desktop?

If not, then try this command,  ```
sudo apt-get update && sudo apt-get install ubuntu-desktop
```

---


---
title: "Update problem"
date: 2008-06-28
forum: Installation &amp; Upgrades
---

### Post by RamR on 2008-06-28
The other day I started update manager to install the newest updates.  The Update Manager window came up but not all the way... just a blank gray window.  Then I couldn't even close the window.  I had to restart the computer and then I had problems starting Ubuntu again.  Finally, today I was able to start Ubuntu but I am still having the same update issue and now I can't even access any of the file system.  When I try a small window opens that looks like an error message window but again it is a blank gray window.

Any ideas about what might be the problem?

---

### Post by iaculallad on 2008-06-28
Try using your terminal instead to do your update:

```
sudo apt-get update && sudo apt-get upgrade
```

And try to post the displayed Error.

---

### Post by RamR on 2008-06-28
When I open the terminal window it is blank.  I can't enter anything in it.  Also, I don't get any error message that I can read.  Just blank windows when I use Update Manager or try to access any files.

---

### Post by iaculallad on 2008-06-28
What video card are you currently using?

---

### Post by RamR on 2008-06-28
> **iaculallad said:**
> What video card are you currently using?

Intel 82852/855GM

---

### Post by iaculallad on 2008-06-28
> **RamR said:**
> Intel 82852/855GM

Try to reset your xorg.conf file: Press the Ctrl+Alt+F1 to enter your virtual terminal. Input your authenticated username and password.

On the terminal, issue the command below and try to answer the questions it ask. (Try using default answers/values)

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Then press Ctrl+Alt+F7 to get back to your GUI.

---

### Post by RamR on 2008-06-28
> **iaculallad said:**
> Try to reset your xorg.conf file: Press the Ctrl+Alt+F1 to enter your virtual terminal. Input your authenticated username and password.

On the terminal, issue the command below and try to answer the questions it ask. (Try using default answers/values)

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Then press Ctrl+Alt+F7 to get back to your GUI.


Followed these instructions but got the message that the xorg file could not be created because the system seems to be set to "read only".

Don't know how that happened or how to rectify it.

---

### Post by RamR on 2008-06-28
> **iaculallad said:**
> Try to reset your xorg.conf file: Press the Ctrl+Alt+F1 to enter your virtual terminal. Input your authenticated username and password.

On the terminal, issue the command below and try to answer the questions it ask. (Try using default answers/values)

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Then press Ctrl+Alt+F7 to get back to your GUI.


Followed these instructions but got the message that the xorg file could not be created because the system seems to be set to "read only".

Don't know how that happened or how to rectify it.

---


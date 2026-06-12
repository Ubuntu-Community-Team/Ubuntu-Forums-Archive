---
title: "can't install upgrades on an 800 * 576 screen"
date: 2012-01-02
forum: Installation &amp; Upgrades
---

### Post by bjbraams on 2012-01-02
My Dell Inspiron Nettop Mini is set to an 800 * 576 screen resolution. (I have given up trying to set it to anything larger than that.) I am running Ubuntu 11.10 and wish to install upgrades. After the initial phase a pop-up box appears informing me that some number of upgrades will be downloaded, it involves so many MB and will take so many minutes; do I want to proceed?

I want to proceed, but the YES button to say so is outside the lower end of my small screen. I cannot move the window and I cannot change the font settings; I don't know how to confirm to the system that I want to proceed with the upgrade.

Is there a work-around?

---

### Post by Frogs Hair on 2012-01-02
One way would be to right click the title bar of the update manger , select resize , compress the window to a workable size . Another option is to install update from the terminal . ```
sudo apt-get update
``` ```
sudo apt-get upgrade
```

---

### Post by bjbraams on 2012-01-02
Thank you @Frogs Hair for the reply. I succeeded with use of the pair of recommended apt-get commands.

For the record and perhaps for other users that read this: I was not able to resize the pop-up window. The option seems to be there under right-click on the title bar, but I can't find a way to use it and grab hold of an edge to drag around for the resize action.

---


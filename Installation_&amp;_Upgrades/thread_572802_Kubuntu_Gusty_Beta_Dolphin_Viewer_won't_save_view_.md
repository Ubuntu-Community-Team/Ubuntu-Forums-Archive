---
title: "Kubuntu Gusty Beta Dolphin Viewer won't save view mode"
date: 2007-10-10
forum: Installation &amp; Upgrades
---

### Post by Slim Backwater on 2007-10-10
Just trying out the Gusty Beta of Kubuntu.

When I insert my USB drive, Dolphin will open and start in "Preview" mode which is a large icon view.  I prefer details so I can press CTRL+2 or View-> View Mode -> Details.

However when I go into a sub directory, the view reverts back the the large icon "preview" mode.

The view properties looks like it *should* set the defaults, but it's not working.

I change the view to details, click View -> Adjust View Properties -> View Mode = Details, Apply view properties to = All Folders and Click Ok.  I confirm, go into a subdirectory and it's BACK to preview mode.

My machine is technically a Ubuntu 7.04, switched to Kubuntu Desktop (sudo apt-get install kubuntu-desktop) and then recently a update-manager -d to get to the beta.

Can anyone confirm this behaviour in Dolphin in the Gusty Beta?  

Thanks.

---

### Post by 1m.dm on 2007-10-22
Confirmed! I updated to 7.10 from 7.04 and experienced the same problem.

---

### Post by Slim Backwater on 2007-10-30
It bugged me so much I switched back to Konqueror:

1. Open Dolphin, right click on any folder folder and select Properties

2. On the "Type: Folder" line, click the little wrench.

3. In Application Preference Order I moved Konqueror higher than Dolphin.

4. Ok, Ok, and now Konqueror is the default.

Apparently it's fixed in KDE4 which wasn't ready for 7.10.

._.

---

### Post by FooAtari on 2008-01-13
Is there no fix for this?  It's damn annoying

---

### Post by fatbuttlarry on 2008-02-11
Agreed!  I'll keep searching!

---

### Post by HitoraTaiko on 2008-02-19
I've found that if you go into Settings->Configure Dolphin you can change the default view mode under General...and that sticks. Also, below that, is an option to "Save View properties for each folder" ...and that also seems to make things stick ^_^

---


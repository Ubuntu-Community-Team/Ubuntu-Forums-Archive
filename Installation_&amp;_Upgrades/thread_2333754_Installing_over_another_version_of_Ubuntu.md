---
title: "Installing over another version of Ubuntu"
date: 2016-08-12
forum: Installation &amp; Upgrades
---

### Post by brdmartin on 2016-08-12
Hi friends,
I've currently got the Gnome desktop installed, but I would like to switch to KDE. I have my HD partitioned, there are some windows programs I still would like to use. When I try to install Kubuntu, it doesn't give an automatic option to install in a particular partition. I then went into the manual/custom option. There appears to be checkboxes to select a particular partition, they don't do anything. If I highlight the partition I want, and click okay, it gives me an error message - I should have written down what it said though.

So how can I erase, or otherwise install over the disk partition that currently houses Gnome Ubuntu?

B

---

### Post by wildmanne39 on 2016-08-12
What version of Gnome Ubuntu are you using? and you could just install KDE desktop and then you can switch between the two if you like by just logging out of one and into the other.

---

### Post by brdmartin on 2016-08-12
I tried that, but some kind of error came up, and I was hoping that just installing KDE over Gnome would be much easier. I'm using the most recent stable version of Gnome.

---

### Post by yancek on 2016-08-12
> If I highlight the partition I want, and click okay, it gives me an  error message - I should have written down what it said though.

Yes, you should have.  Would it have been "no mount point selected"?  Using the Manual or Custom option and highlighting a partition will require you to click the change tab below the main window.  This should open an Edit partition window where you select the mount point, filesystem type and will have a check box to select to format it.  Formatting the selected partition will, of course, overwrite any data on that partition so if you have data you want to save, do that first and make sure you get the correct partition.

You mention  some windows programs you would like to use but don't indicate a windows installation or which release?

It would probably be easier to just install the KDE Desktop Environment as suggested.

---


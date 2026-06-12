---
title: "Please help me get Aptana Studio working"
date: 2009-10-12
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by bowarwick on 2009-10-12
Yesterday I upgraded my computer from 9.04 to  9.10.

I installed Aptana Studio for the first time today and I'm having a problem.

When I try to "install new features", I click the "install" button and nothing happens. This is an essential part of Aptana and I would really like to get this working.

I tried following other install guides for older versions of Ubuntu but with no success, like

[http://maketecheasier.com/install-aptana-studio-in-ubuntu-intrepid/2009/03/23](http://maketecheasier.com/install-aptana-studio-in-ubuntu-intrepid/2009/03/23)

Has anyone else got it working?  I appreciate any help.

---

### Post by loadbrain on 2009-10-16
I got exactly the same problem...
Any hint to solve tis would be great...

---

### Post by UnSandpiper on 2009-10-16
Me and others had the same issue. 

Someone in the forum suggested to create a startup script or start Aptana/Eclipse from the terminal and do a: 
```
export GDK_NATIVE_WINDOWS=true
```
before launching the application. 
Everything works fine for me this way.

---

### Post by loadbrain on 2009-10-16
Alright, I will give it a try later today!
ThanksQ:guitar:

---

### Post by knarf on 2009-10-16
The workaround (as it is not really a solution) seems to be very simple actually: press the Enter key after highlighting the button (with mouse or keyboard). For some reason the mouse clicks do not trigger the correct callback even though they are registered - the button visually responds but the related action is not performed. When you use the keyboard instead of the mouse it works as it should. This is probably a problem with SWT, not with Aptana or Eclipse...

---

### Post by loadbrain on 2009-10-17
Ok, great, this works, but now I get an error:
> Cannot complete the install because one or more required items could not be found.
  Software being installed: PDT Runtime Feature 2.0.0.v20090315-1850 (org.eclipse.php.feature.group 2.0.0.v20090315-1850)
  Missing requirement: PDT Runtime Feature 2.0.0.v20090315-1850 (org.eclipse.php.feature.group 2.0.0.v20090315-1850) requires 'org.eclipse.dltk.core.feature.group [1.0.0,2.0.0)' but it could not be found

Any ideas?

---

### Post by loadbrain on 2009-10-17
Ok, found it out:

Your error suggests that you haven't enabled the Galileo (Eclipse) update site.

---

### Post by tosi on 2009-10-17
Enabling Galileo update site downloads official PDT, not the Aptana plugin.

Here's how I fixed it to download the Aptana plugin:
1. Reinstall Aptana Studio (remove the Aptana folder and re-extract Aptana archive).
2. Make a launcher for Aptana Studio. Here's what I've used, following UnSandpiper advice:
```

#!/bin/bash
export GDK_NATIVE_WINDOWS=true
"/path/to/aptana/installation/AptanaStudio"

```
3. Make this file executable, start Aptana Studio using the launcher and install the PHP plugin.

---


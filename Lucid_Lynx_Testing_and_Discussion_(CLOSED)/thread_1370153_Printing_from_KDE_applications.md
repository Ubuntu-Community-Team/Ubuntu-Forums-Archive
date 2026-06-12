---
title: "Printing from KDE applications"
date: 2010-01-01
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by brm on 2010-01-01
I am experiencing a return of old problems (some of them previously solved) with printing from KDE applications in the alpha versions of Kubuntu Lucid Lynx (10.04). At present, printing of text --- at least from Kate --- appears to be working fine; printing from Konqueror is once again a problem. 

I live in Canada. Although we have largely adopted the metric system, we use US paper sizes. Our standard page size, is therefore not A4, but rather 8.5x11 inches. On my ancient HP LaserJet 4l, the imageable area of a US letter page is 8x10 inches. Output from Konqueror does not respect these parameters: the text runs off the bottom of the page. Between 3.5 and 4 lines are lost at the bottom of each page.

I tested with a longish web page from the kde.org web site believing that, of any webpage, it would be designed to render well in Konqueror. The page I chose is: [http:///www.kde.org/whatiskde/project.php](http:///www.kde.org/whatiskde/project.php).

The amateur analyst in me is wondering if the A4 page size is perhaps not hard-coded into Konqueror (but not necessarily into Kate). Since A4 is slightly longer (and narrower) than US letter, that could explain the spillover at the bottom the page. It is not possible to determine the default setup because the system-config-printer-kde applet is broken in SystemSettings (Launchpad Bug 331192 and KDE Bug 209379), but the print dialog did specify that it was using US paper sizes.

Before I file bugs at Launchpad (the Kubuntu bug tracker) and on the KDE Bugzilla, I would be interested to know if others have noted a similar problem.

I will be posting this message on ubuntuforums.org, kubuntuforums.net and to the kde-linux mailing list. The mailing list version will have two attachments: (1) a PDF of the exact state of the web page that I used for the test; (2) the text file, a dump of line numbers, that I used for testing Kate.

---


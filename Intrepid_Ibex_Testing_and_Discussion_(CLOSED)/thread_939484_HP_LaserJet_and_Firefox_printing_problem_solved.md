---
title: "HP LaserJet and Firefox printing problem solved"
date: 2008-10-06
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by brm on 2008-10-06
This is an account of a problem solved. I am reporting it because I am sure there are other users out there who are as picky as I am :-) .

I recently installed the beta of Kubuntu Intrepid Ibex. I was annoyed that the print preview of pages in Firefox showed the header but the actually hard copy output was consistently missing the header. It made me even more annoyed to realize that the ability to set printable area, margins sizes, header and footer sizes has been removed from Firefox 3 --- at least in its most recent iterations. BTW, the last time that I had tried printing from Konqueror, it was even more seriously broken and I feared that I was facing being unable to print Web pages at all from an Intrepid Ibex session.

The print parameters that have been removed from Firefox are nominally available in the GNOME print manager, although that offers little joy to us KDE users. Moreover, there is some question whether the functionality is fully implemented yet in GNOME.

After hunting and some gnashing of teeth, I have found a 90% solution. The missing 10% is the subject of a bug report on the Mozilla bug database. The 90% solution is a special paper type in the page setup dialog in Firefox. The option is under |File |Page Setup |Paper Size. Like 99.99% of users in North America, mine was set by default to US Letter. It hadn't occurred to me to look at different sizes until I got advice that LaserJet users needed to define a custom paper size to deal with the unprintable area on all four sides of a page printed by all LaserJet models. I checked the dialog and there was the well-kept secret: a pre-defined type of US Letter HP LJ.

The missing 10% is this: (1) The header and footer are actually printed outside the area which both HP hardware specs and the CUPS driver define as the "imageable area", and; (2) the header and footer were offset to the right 1/8".

The bug report which I filed on the Mozilla Bugzilla is below (# 458641):

> User-Agent:       Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.0.3)
Gecko/2008092515 Ubuntu/8.10 (intrepid) Firefox/3.0.1
Build Identifier: Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.0.3)
Gecko/2008092515 Ubuntu/8.10 (intrepid) Firefox/3.0.1

HP LaserJets (to the best of my knowledge, all models going back to
introduction c:a 1986 of the technology) have an imageable area of 8.0 x 10.0
in. (203.2 x 254.0mm).

CUPS defines the imageable area of HP LaserJet using these figures, with
lower-left corner of area at 0.x25 x 0.5 in. (6.4 x 12.7mm) from lower-left
edge of paper and upper-right corner at 8.25 x 100.5 in. (209.6x266.7mm).

The printed output of a Firefox page is shifted 1/8 in. (~3mm) to the right of
the imageable area as outlined on the CUPS Printer Test Page. As a result, the
right-most 1 1/2 letters of the header and footer are lost.

Also, the headers and footers both print outside the imageable area as printed
on the CUPS Test Page. Nominally, these lines should therefore not print. On my
particular HP (an ancient LJ 4L), they did show, but as this is out-of-spec,
positive results cannot be guaranteed.

Reproducible: Always

Steps to Reproduce:
1. From CUPS admin page ([http://localhost:631](http://localhost:631)), print a test page
2. in |File |Page Setup, select the predefined paper type US Letter HP LJ and
click "Apply". Print a page from Firefox.
3. Hold the two pages together and up to a light and note the placement of the
Firefox header and footer with respect to the border of the CUPS Test Page
which defines the nominal outer limits of the imageable area of the printer.

Actual Results:  
1. Header and footer are both outside the border of the CUPS Test Page.
2. Entire header and footer lines are offset 1/8 in. to the right of the border
of the CUPS Test Page.

Expected Results:  
1. Header and footer both within the border of the CUPS Test Page.
2, First character of the header and footer aligned with the left border of the
CUPS Test Page.

Other details:
Kubuntu Intrepid Ibex beta, dist-upgraded at least 2x daily while the distro
remains in development.
Firefox 3.0.3 (pace the build identifier)
CUPS 1.3.8-11ubuntu2


---


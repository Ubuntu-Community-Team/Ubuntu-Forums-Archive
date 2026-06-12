---
title: "CUPS 1.4.1 - Printing shifted about 0.25 off lower page"
date: 2009-10-15
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by emarkay on 2009-10-15
This is with a HP PSC1300, and the "hpcups 3.9.8"  Printer driver: The bottom 1/4 inch or so of pages printed in OO, the Ubuntu test print and the CUPS test print is missing, as if the entire print image is skewed down.

Using the CUPS test page, the top horizontal printed line is 0.55" from page top, and only the top 0.1" of the words "Printer Test Page" at the bottom have printed. The test page's stated "Media Dimensions" are correct (8.50 x 11.00)
However, "Media Limits" (as printed on the page) are "0.25 x 0.50 x 8.25 x 10.88" inches. This is not correct, as I measure 10.60" in the printed page, from the top of page to where the printed text is truncated.

 HP Specifications are: Top=0.06 inch (1.5 mm) | Bottom= 0.50 inch (12.7 mm) | Left and Right=0.25 inch (6.4 mm), which should give me a print area of only 10.44 inches. (11.00 - 0.5 - 0.06)
 The actual printed CUPS test page has a measured print area of 10.05.  (11.00 - 0.55 - 0.40).

I am also getting a status on this page of "Processing page 2..." which cannot be as this is a one page print - unless that is where the missing text is "floating"...

Confirmed that the HP 1310 and 1358 hpcups 3.8.9 driver also have this problem.  However, I have resolved this issue by selecting the "HP PSC 1300 Series hpijs, 3.9.8" driver, but  there is still, obviously, the issue with the "hpcups" driver.

See Bug: [https://bugs.launchpad.net/ubuntu/+source/system-config-printer/+bug/452307](https://bugs.launchpad.net/ubuntu/+source/system-config-printer/+bug/452307)
The Print Troubleshooter output is also listed in that bug report.

---


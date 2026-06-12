---
title: "&quot;ignore data&quot; - Brother HL-6050dn and firefox"
date: 2011-07-12
forum: Installation &amp; Upgrades
---

### Post by xigen on 2011-07-12
My Brother HL-6050dn has been fantastic. Up until a recent upgrade of Firefox (5.0) it just worked.

When I attempt to print a page via firefox my printer says "ignore data".

I reinstalled FF via synaptic.  Unfortunately the issue remains.

The issue is restricted to Firefox.  I can print from Chrome and Libre Office.

Suggestions?

---

### Post by xigen on 2011-07-14
Bump.

---

### Post by doctor_overbyte on 2011-07-21
I have the same problem with my Brother HL-5250DN and Firefox 5.0 for Ubuntu on Ubuntu 11.04.   When I print, as used to work on prior Ubuntu release with Firefox 3.x.x, it worked fine.  On 11.04, with other programs as you mentioned, printing works fine.  But with Firefox 5.0, the printer only outputs an error page.  Looking at the Firefox Page Setup dialog, I see the "Format For" says "Any Printer for portable documents".   When I change that by pulling down and selecting my Brother printer and then "Apply", the change does not hold.  That is, when I bring up the Page Setup again, the entry still says "Any Printer".  I think that's why Firefox is throwing errors at the printer.  It is apparently sending some sort of portable document format file instead of the Brother script format output file.   The Brother just gets garbage.  However, Chromium, Google Chrome, and LibreOffice all print just fine.   The problem must be with Firefox not setting itself for the selected printer.  I can't believe that we're the only two folks having this problem, unless it only happens when the system default printer is a network printer, which most people probably don't have.

I have no such trouble with Firefox 5.0 on Windows using same network and printer.

I reported this as a bug on Ubuntu's Launchpad, but it probably won't get much attention there because (1) there's no package name for Firefox-5.0, just for earlier packages of Firefox, even though 5.0 is the version being distributed on Ubuntu 11.04 as the standard browser; and (2) there's no "heat" for this bug, that is, I'm the only one so far to submit or comment.

Here's the bug report:  [https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/812554]("https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/812554").  Go there and add a comment saying that you have the same problem and giving your details.  Maybe it will bubble up to someone's attention.

---


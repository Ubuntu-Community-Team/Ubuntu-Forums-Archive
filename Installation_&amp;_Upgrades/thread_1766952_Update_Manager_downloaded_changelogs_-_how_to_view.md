---
title: "Update Manager downloaded changelogs - how to view from command line"
date: 2011-05-25
forum: Installation &amp; Upgrades
---

### Post by snorbert on 2011-05-25
Hi folks,
Is it possible to download from the command line the same changelogs that Update Manager downloads for pending updates?

I have already tried apt-listchanges, but it doesn't give quite the same output as Update Manager does for the same package - Update Manager has something useful for ordinary people at the beginning of the changelog.  For example, Update Manager has this to say at the beginning of the chromium-browser changelog:
```
Version 10.0.648.205~r81283-0ubuntu0.10.10.1: 
  With this version (like with 10.0.648.204), you may notice that the saved
  passwords are no longer accessible in Chromium. (LP: #743494) This is due to
  an incompatibility between Chromium's GNOME keyring integration and the password
  sync feature that was introduced in Chromium 10.
[...more explanation, then standard apt-listchanges style changelog starting with 11.0.696.68~r84545-0ubuntu0.10.10.1 follows]
```

but apt-listchanges and indeed Synaptic just display the developer-oriented part of the changelog for chromium-browser:
```
chromium-browser (11.0.696.68~r84545-0ubuntu0.10.10.1) maverick-security; urgency=low
  [ Fabien Tassin <fta@ubuntu.com> ]
  * New Minor upstream release from the Stable Channel (LP: #781822)
    This release fixes the following security issues:
    + WebKit issues:
      - [64046] High, CVE-2011-1799: Bad casts in Chromium WebKit glue. Credit
        to Google Chrome Security Team (SkyLined).
      - [80608] High, CVE-2011-1800: Integer overflows in SVG filters. Credit
        to Google Chrome Security Team (Cris Neckar).
[...]
```

I'd really like to read the "for ordinary people" preface to the changelogs that Update Manager displays, but for me, the drawbacks of viewing a hundred of these in the Update Manager are:
[LIST]
[*] I have a pretty poor Net connection and the download latency for changelogs is high (even from a very close mirror), so I'd like to download them and view them offline
[*] I'd much prefer to use the whole screen to read a few of these quickly rather than fiddle with the little viewing pane in U.M.
[*] I can not search across the changelogs in the way I could with **grep** or **less**.
[/LIST]

Is there a way to download the same changelogs that Update Manager displays using a command line tool, or even a simple way to do it in Python?  I can do the whole custom tool thing when I find time to spend on acquiring the needed skills, I was just wondering if non-programmers (or programmers with enough other stuff on their plate) have a way to achieve the same end.

---


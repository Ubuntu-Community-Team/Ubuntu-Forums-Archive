---
title: "Repairing firefox install"
date: 2007-06-13
forum: Installation &amp; Upgrades
---

### Post by shearn89 on 2007-06-13
Hey all - bit of a problem.
Downloaded firefox 2 from mozilla. Then foolishly extracted to /usr/lib/  : didn't work very well, so tried to follow an update howto on the ubuntu wiki.
Now, when i run "firefox" from a terminal (or anywhere), the process "firefox-bin" starts, but no window pops up.... I tried reinstalling using synaptic, but that didn't seem to make a difference...

Help!

update: now i get this:
```

XML Parsing error: undefined entity
Location: chrome://browser/content/browser.xul
Line Number 100, Column 5:

<command id="browser:ReadMail" oncommand="MailIntegration.readmail();" label="&mailbutton.readmail.label;" />

```


UPDATE: just fixed it. no worries.

---


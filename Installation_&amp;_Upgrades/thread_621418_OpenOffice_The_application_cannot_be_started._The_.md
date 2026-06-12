---
title: "OpenOffice: The application cannot be started. The user interface language..."
date: 2007-11-23
forum: Installation &amp; Upgrades
---

### Post by Sporkmaster on 2007-11-23
I just installed openoffice MANUALLY :mad: because of the computer's total lack of internet card.

When starting Open Office, I get the error message

> The application cannot be started.
The user interface language cannot be determined.

And when running the command ```
openoffice.org2.3 -writer %U
``` in the terminal, I recieve the error
```
[Java framework] Invalid value for bootstrap variable UNO_JAVA_JFW_VENDOR_SETTINGSjavaldx failed!
```

shortly followed by a dialog box containing the previous error.

Any help? Because I have to give this computer back by tomorrow

---

### Post by Sporkmaster on 2007-11-23
bump

---

### Post by Ehtetur on 2007-11-23
You need these installed for the user language
openoffice.org-java-common
openoffice.org-l10n-common
openoffice.org-l10n-en-gb

I'm pretty sure that java error is also related to the user language but for openoffice to work, you'll also need this package:
openoffice.org-java-common

---

### Post by Sporkmaster on 2007-11-23
Any way to get those without a direct internet link?

---

### Post by Sporkmaster on 2007-11-23
*crickets a-chirping

---

### Post by Ehtetur on 2007-11-23
I think openoffice is included on the LiveCD, So just make sure that the CD is set as installable in synaptic: Synaptic --> Settings --> Repositories..

---

### Post by Sporkmaster on 2007-11-23
[RESOLVED] - Connected to internet and sudo apt-get openoffice.org

---


---
title: "gedit: Unable to save to SFTP/FTP"
date: 2009-07-29
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Stereotypical Rage on 2009-07-29
Hello All,

Since upgrading to Karmic (from Jaunty via update manager) this past weekend, I haven't be able to save to FTP or SFTP via gedit. gedit just says there's an error. However if I run gedit I get this message:

```
** (gedit:8384): CRITICAL **: document_saved: assertion `error->domain == G_CONVERT_ERROR' failed
```

I have tried using the gedit that came with Jaunty and it still didn't work and gave the same exact error (outside of the PID changing) I have tried to save via SCREEM and it works as it should, but I don't want to switch. Is anyone having similar issues with gedit?  How can I file a proper bug on LaunchPad (never done so before)?

gedit version: gedit 2.27.3

---

### Post by Naddiseo on 2009-07-30
I reported a similar one a few weeks ago. I don't get the same error though.

[https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/399995](https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/399995)

---

### Post by Stereotypical Rage on 2009-07-30
> **Naddiseo said:**
> I reported a similar one a few weeks ago. I don't get the same error though.

[https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/399995](https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/399995)

But you report it crashes, the error I get does not crash gedit. It leaves it intact, but I can't edit or close out of the doc. I can open a new one though.

---


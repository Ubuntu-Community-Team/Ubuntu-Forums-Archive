---
title: "Roundcube, connecting w. SMTP + IMAP"
date: 2021-11-10
forum: Installation &amp; Upgrades
---

### Post by civilpolisen on 2021-11-10
We've had Roundcube for webmail for a long time and now we're upgrading to meet the demand from colleagues and clients about a working smart-phone compatible alternative.

I've installed it all successfully and all software runs... But the software will not connect to SMPT and IMAP to the current services at our company.

I've been battling this issue for a week... and I'm running out of ideas! It's from the last page at the installer, there is a feature to verify IMAP and SMPT but no connection is made...

My setup is Ubuntu 20.04 and I'm running the latest vrsion of RoundCube.

---

### Post by MAFoElffen on 2021-11-13
Latest version of RoundCube from "where"? PPA or from RoundCube?

A few things... Make sure the information your have for connecting to your company's email server, for both IMAP and STMP is complete. In this repsect, it has the same challenges of connection issues as other mail service providers...

Meaning for IMAP, that it includes the prefix to the address, port, method, any username/password, etc. for example for connection to their IMAP:
```

address='ssl://imap.hostedservername.com'
port='993'
username='UserName@hostedservername.com'
password='5Swn87#sAbQ'

```
And to their SMTP:
```

address='ssl://smtp.hostedservername.com'
port='465'
username='UserName@hostedservername.com'
password='5Swn87#sAbQ'

```
RoundCube has a chackBox that you can select for the SMTP credentials. that you can select, if the credentials are the same as the IMAP credentials, so you don't have to type in the same...

****
Here is where I suspect you may have had your connection problem...

In the IMAP configuration section of RoundCube, there is a checkbox option that say "auto_create_user"... When selected, it adds a user record to it's database... If it is not selected, *it doesn't create that user record and that user will not be able to login, nor connect to the host server to both IMAP and SMTP services*... Because that user record does not exist.

This sounds suspiciously like what you are describing. 

I know... In my head and reasoning, it is to me, like, in what circumstance would you not want to create that record? So why is that even an option not to? And if there was some reason, why is that not a selected as default? IDK.

---


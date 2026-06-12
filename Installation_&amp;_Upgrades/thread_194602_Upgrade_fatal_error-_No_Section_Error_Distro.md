---
title: "Upgrade fatal error- No Section Error: Distro"
date: 2006-06-11
forum: Installation &amp; Upgrades
---

### Post by jpbennett on 2006-06-11
I used the Synaptic Package Manager to upgrade my DELL Inspiron B130 laptop from Breezy to Dapper. It went for quite a while, then broke with this error:

A fatal error occured.
Please report this as a bug and include the files /var/log/dist-upgrade.log and / var/log/dist-upgrade-apt.log in your report. The upgrade aborts now.
Your original sources.list was saved in /etc/apt/sources.list.distUpgrade.

Traceback (most recent call last):
   ...
   File "/usr/lib/python2.4/ConfigParser.py", line 511, in get
   raise NoSectionError(section)
   NoSectionError: no section: 'Distro'

What do I do now? The laptop boots, but clearly something went wrong. The biggest problem so far is that it cannot make a network connection (ethernet or wireless). I now have an upgrade CD to use. Does my next step use the sources.list backup the error message mentions? I don't know what to do with that.

Eventually, it sounds like I need to report this as a bug. But to do that I need to register. The registration process sends the password via email. I cannot get email because the upgrade error broke my network connection (I'm borrowing a machine for this posting). So, hopefully someone here can help. Thanks.

---

### Post by jpbennett on 2006-06-26
I've now gotten internet access again, and reported the bug to the proper authorities. In fact, the upgrade seems to be working. But I still don't know what to do about the aborted upgrade. Does anyone know what's the right next step?
- repeat the upgrade?
- do something with the sources.list backup?
- get the automatic updates the synaptic package manager tells me about?

Thanks for any help.

---


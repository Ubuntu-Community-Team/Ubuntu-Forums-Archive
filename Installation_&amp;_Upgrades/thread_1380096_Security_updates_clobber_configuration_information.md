---
title: "Security updates clobber configuration information"
date: 2010-01-13
forum: Installation &amp; Upgrades
---

### Post by bkline on 2010-01-13
Why can't Ubuntu store configuration information in a way that it wouldn't need to be clobbered in order to apply security updates?  For example, this mornings updates told me I had to choose between using a new version of smb.conf that's part of the security patches, stick with the old version, or let the update installer merge them.  Of course, the first two choices have obvious drawbacks: why should I have to choose between losing all my SMB settings or refusing security fixes?  So I chose the merge, which came back with "Conflicts found during three-way merge! Please edit `/etc/samba/smb.conf' and sort them out manually."  How ugly is that?  Why can't local settings be stored separately from the distro files? :(

---

### Post by mikewhatever on 2010-01-13
I was wondering, have you modified your smb.conf manually? I have, and on seeing this message left the default of keeping the existing configuration. Could it be that this message comes up if you modify the config file?

---

### Post by kostkon on 2010-01-13
> **mikewhatever said:**
> Could it be that this message comes up if you modify the config file?
I think that's the case.

---

### Post by mikewhatever on 2010-01-13
> **kostkon said:**
> I think that's the case.

That is a real revelation. It was driving me mad asking about the menu.lst in 9.04 on one computer, and I didn't know why.:)

---

### Post by bkline on 2010-01-13
> **mikewhatever said:**
> I was wondering, have you modified your smb.conf manually? I have, and on seeing this message left the default of keeping the existing configuration. Could it be that this message comes up if you modify the config file?

Possibly.  It would be nice if there were a separate file in which settings for the local machine could be put so they wouldn't be stepped on by security updates.

> I am sick of dumb non-descriptive thread titles.

Sorry, I'll try to do better next time. :-)

---

### Post by doas777 on 2010-01-13
I can confirm, it only prompts when the file's modified date is not the one expected (indicating that it has been changed by a user.)

---


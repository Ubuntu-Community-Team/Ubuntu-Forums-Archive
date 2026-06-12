---
title: "Netboot Install with Interactive Preseed script"
date: 2017-03-23
forum: Installation &amp; Upgrades
---

### Post by Omnihaand on 2017-03-23
I'm looking to add a Kerberos hostkey to a fresh install during the netboot install process. But, it's looking like this might be more work than it's worth.  Is there a better way than a custom UDEB or mucking about with debconf? :confused:

Specifically, I'm looking at this section here:

[INDENT]Generally, a script run from the seed file via late_command, cannot interact with the user. If you need to interact, there are generally three options:

    Create a custom UDEB that interacts with debconf, and include it with the CD.
    Create a 'firstrun' script that executes the first time the system boots, and disables itself on completion.

    Access debconf directly within your script. [/INDENT]

From this page:
[https://help.ubuntu.com/community/InstallCDCustomization](https://help.ubuntu.com/community/InstallCDCustomization)

The goal is to not leave a password or active Kerberos credentials laying around while the installer does it's thing.  I could go back later to add the krb5.keytab, but that wouldn't be a very interesting solution, now would it?  :popcorn:

---


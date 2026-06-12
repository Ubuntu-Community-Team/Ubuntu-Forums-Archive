---
title: "Autoinstall Ubuntu 20 not working with RSYSLOG"
date: 2020-12-28
forum: Installation &amp; Upgrades
---

### Post by scahartner on 2020-12-28
Following the guide : [https://ubuntu.com/server/docs/install/autoinstall-reference](https://ubuntu.com/server/docs/install/autoinstall-reference)

```
reporting:
 central:
  type: rsyslog
  destination: @192.168.0.172
```

I tried to configure rsyslog to help me diagnose a problem where a the automated installation consistently fails. Adding the section from the documenation fails with a YAML error advising that the @ character is not valid in YAML as shown in the example.

Error reported was : "found character that cannot start any token while scanning for the next token at line"

---

### Post by scahartner on 2020-12-28
Using the following:
```
  reporting:
    central:
      type: rsyslog
      destination: "192.168.0.172"

```

Results in another error: KeyError: 'rsyslog'

---

### Post by scahartner on 2020-12-28
Found the solution for this:

**The rsyslog reporter does not yet exist**

---


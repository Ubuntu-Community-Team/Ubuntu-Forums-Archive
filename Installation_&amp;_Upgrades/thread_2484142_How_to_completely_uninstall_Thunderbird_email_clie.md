---
title: "How to completely uninstall Thunderbird email client?"
date: 2023-02-18
forum: Installation &amp; Upgrades
---

### Post by skylinestar on 2023-02-18
I have no use for that email client. I was told that Firefox and Thunderbird are closely related. I want to uninstall Thunderbird safely without affecting Firefox. How do I do that safely?

---

### Post by TheFu on 2023-02-18
```
sudo apt remove  thunderbird*
```
Was this a trick question?

Firefox and thunderbird are from the same company and use the same toolkit, but they aren't tightly coupled.
If Thunderbird is installed as a snap, use the normal **snap remove** command.

pine and elm are fine email clients.

---

### Post by SeijiSensei on 2023-02-19
These days pine is called alpine.

To be thorough, delete the .thunderbird directory in your $HOME:

```
cd ~
rm -rf .thunderbird

```

It's where any mail and configuration data are stored.

---


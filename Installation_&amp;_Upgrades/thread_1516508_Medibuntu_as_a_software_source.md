---
title: "Medibuntu as a software source?"
date: 2010-06-23
forum: Installation &amp; Upgrades
---

### Post by ibates on 2010-06-23
How do I insert Medibuntu as a software source?

Are there any other reliable general software sources worth inserting?

---

### Post by spcwingo on 2010-06-23
This command should be run in the Terminal  (Applications &#8594; Accessories &#8594; Terminal):

```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```

---

### Post by oldos2er on 2010-06-23
> **ibates said:**
> How do I insert Medibuntu as a software source?

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---


---
title: "The package indexes are currently changed by apt-get."
date: 2011-06-04
forum: Installation &amp; Upgrades
---

### Post by 9000cse on 2011-06-04
Hi all and a good morning or afternoon to you all.
I'm try to install auto updates and keep getting

'The package indexes are currently changed by apt-get.'

How do I get around this problem?

Thanks
Andt

---

### Post by mörgæs on 2011-06-04
You could try to boot the computer and run

```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```

Please post the error messages, if any.

---

### Post by 9000cse on 2011-06-04
Well that seemed to work, apart from the update bit, I got errors. upgrade fine.
Thanks.

---


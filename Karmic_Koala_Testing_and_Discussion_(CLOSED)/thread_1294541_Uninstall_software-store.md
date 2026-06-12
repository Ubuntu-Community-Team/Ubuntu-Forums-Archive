---
title: "Uninstall software-store"
date: 2009-10-18
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by linusr on 2009-10-18
I have Ubuntu Karmic installed from Alpha 4. software-store package is removed during one of the update but not completely. Complete uninstall of software-store always returns error.

But, this hasn't caused any issues yet..

Should I do an full install?

---

### Post by tekstr1der on 2009-10-18
Create the missing directory and this will be resolved. I needed to do that here too.

```
sudo mkdir /var/cache/software-store/xapian
```

I will now uninstall cleanly.

---

### Post by linusr on 2009-10-18
> **tekstr1der said:**
> Create the missing directory and this will be resolved. I needed to do that here too.

```
sudo mkdir /var/cache/software-store/xapian
```

I will now uninstall cleanly.

worked! Thnx.

---


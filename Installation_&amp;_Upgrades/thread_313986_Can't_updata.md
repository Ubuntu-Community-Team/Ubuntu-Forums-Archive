---
title: "Can't updata??"
date: 2006-12-06
forum: Installation &amp; Upgrades
---

### Post by Jennal on 2006-12-06
there is a message that prompt me to upgrade, 3 libs, but when i click the install button, it dosen't work, and told me that can't download...and show me the web address, but i check the address, it dose can't be downloaded, how   could it be? what's wrong with it??:confused: :confused:

---

### Post by taurus on 2006-12-06
Can you run it from a terminal and paste the error message here?

Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude upgrade
```

You probably need to include your /etc/apt/sources.list here as well...

```
cat /etc/apt/sources.list
```

---

### Post by Jennal on 2006-12-06
it works, thanks

---

### Post by taurus on 2006-12-06
So everything is fine now!

---


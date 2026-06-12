---
title: "Upgrade to edgy - repeating the fetch"
date: 2006-12-21
forum: Installation &amp; Upgrades
---

### Post by izmeh on 2006-12-21
I am new to linux of any distro and had installed Dapper recently.

Tonight i installed a compatible network device so that i could upgrade via update manager.

I went through the steps to accept the download/install/remove/upgrade the files. So far i've gotten to a point where it keeps repeating the "fetching" of 968 files.

Im not sure whats going on and was hoping someone had a solution.

---

### Post by taurus on 2006-12-21
Is your network working?  Open a terminal, Applications -> Accessories -> Terminal, and paste the output of this command here!

```
ping -c 3 www.yahoo.com
```

---

### Post by izmeh on 2006-12-21
it is indeed working. im posting from with in linux

---

### Post by taurus on 2006-12-21
What does your /etc/apt/sources.list look like then?

```
cat /etc/apt/sources.list
```

---

### Post by izmeh on 2006-12-21
Never mind this error, i did a check on the install disc and was given an error.

I decided to burn the iso again and perform a clean install of edgy.

Thanks for the help though

---

### Post by taurus on 2006-12-21
Make sure you burn it at a slow speed like 4x...

---


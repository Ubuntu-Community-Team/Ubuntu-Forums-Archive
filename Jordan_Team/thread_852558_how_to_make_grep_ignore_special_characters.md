---
title: "how to make grep ignore special characters"
date: 2008-07-07
forum: Jordan Team
---

### Post by mkrahmeh on 2008-07-07
usually i use grep to search long *man* pages for certain options rather than going through the whole manual..however when i need to view the part related to certain option, grep interprets that option as its own which causes unexpected behaviour or displaying available options for grep..for instance i need to check what -r exactly does in *userdel* as in
```
man userdel | grep -r
```
now grep modifies its behaviour accordingly, but i need it to search for -r in the man page instead..

```
man grep | grep exact
```
ddnt really help :)
any suggestions ??

---

### Post by sisco311 on 2008-07-07
```
man userdel | grep -- -r
```-- = end options
or
```
man userdel | grep -A 10 -- -r
```

> 
-A NUM, --after-context=NUM
              Print NUM  lines  of  trailing  context  after  matching  lines.
              Places   a  line  containing  a  group  separator  (--)  between
              contiguous groups of matches.  With the  -o  or  --only-matching
              option, this has no effect and a warning is given.


---

### Post by mkrahmeh on 2008-07-08
thx, this solves the problem. 
now how can i search for a sequence of words, like 
```
man grep | grep "end options"
```
preferably case insensitive search

---

### Post by sisco311 on 2008-07-08
```
 man grep | grep -i -A 3 -- "--IgnorE-CasE"
```

---

### Post by AboSamoor on 2008-07-08
I hope this will work:

man userdel | grep '\-r'

---

### Post by mkrahmeh on 2008-07-10
thx guys..u rock
:guitar:

---


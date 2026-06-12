---
title: "finding installed programs"
date: 2010-06-05
forum: Installation &amp; Upgrades
---

### Post by has63 on 2010-06-05
installed fcrackzip, but now i can't find it in apps  to open it. do all programs open in apps?

---

### Post by sanderd17 on 2010-06-05
try the commandline. type "fcra" and autocomplete with a tab, what does it do?

If it autocompletes, add the "--help" option to see how you can use it.

---

### Post by radddi on 2010-06-05
Hello, has63, welcome to the Ubuntu Forums.

As I see it, this program is command line only. To run it you should first open the command line and then check out its manual page for further information. First Applications >> Accessories >> Terminal, then type:

```
man fcrackzip
```

EXAMPLES:
       fcrackzip -c a -p aaaaaa sample.zip
              checks the encrypted files in sample.zip for all lowercase 6 character passwords (aaaaaa ... abaaba ... ghfgrg ... zzzzzz).

       fcrackzip --method cpmask --charset A --init AAAA test.ppm
              checks the obscured image test.ppm for all four character passwords.

       fcrackzip -D -p passwords.txt sample.zip
              check for every password listed in the file passwords.txt.

---

### Post by wojox on 2010-06-05
```
whereis fcrackzip
```

---


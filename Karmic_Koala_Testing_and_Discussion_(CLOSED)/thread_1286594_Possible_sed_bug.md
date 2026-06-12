---
title: "Possible sed bug"
date: 2009-10-09
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by lovinglinux on 2009-10-09
I think it is possible that sed has a bug in Karmic.

I'm trying to filter a file using sed using a regular expression that would remove any character that is not a number. It works most of the time, but not when sed encounters a special character, like ä, â, á, à. 

The expression is this:

```
sed -e 's/[^0123456789]//g'
```

So would be nice if someone could test it to see if the problem is real or if I'm doing something wrong, before I send a bug report.

---

### Post by Hallavej on 2009-10-09
It works here.

---

### Post by MacUntu on 2009-10-09
Works here too.```
test@box:~$ echo "a1äÖü3ößß3&#8364;&#8364;á7à¶µ" | sed -e 's/[^0123456789]//g'
1337

```

---

### Post by lovinglinux on 2009-10-09
> **MacUntu said:**
> Works here too.```
test@box:~$ echo "a1äÖü3ößß3€€á7à¶µ" | sed -e 's/[^0123456789]//g'
1337

```

Thanks.

Using that command it works for me too. It doesn't work when piping the cat results of some really large text files (~600.000 lines in total). Could it be the file encoding, messing with sed?

---

### Post by lovinglinux on 2009-10-10
I guess it is a sed bug, because I ran the same regular expression with the same big files using perl and the output was perfect.

EDIT: bug reported at [https://bugs.launchpad.net/ubuntu/+source/sed/+bug/447866](https://bugs.launchpad.net/ubuntu/+source/sed/+bug/447866)

---


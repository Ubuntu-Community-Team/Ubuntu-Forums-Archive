---
title: "Tmp directory filling up on boot"
date: 2009-06-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by cariboo on 2009-06-24
I have a 5Gb partition for /. I get notices that the hard drive is almost full when doing updates. After searching the partition a bit I found that there were 2057 files totaling 1.5Gb in /tmp. I can delete the files and get the space back. This happens on every reboot, has anyone else run into this?

Edit: I should add that this happened with both 2.6.30-9 and 2.6.30-10

---

### Post by MacUntu on 2009-06-24
Nope.```
user1@test:~$ du /tmp -h -s
64K	/tmp
```

---

### Post by Martje_001 on 2009-06-24
Oh Jeez, mine is big compared with MacUntu's:
```
martijn@mekkie:~$ du /tmp -h -s
80K	/tmp

```
:O

---

### Post by cariboo on 2009-06-24
I just did a cold boot and running du on /tmp results in this:

```
du /tmp -h -s
501M	/tmp
```

and it seems to be growing. the only thing I have running if Firefox with 2 tabs open. is the result after typing this line:

```
du /tmp -h -s
910M	/tmp
```

I tried just a restart, and it doesn't happen.

---

### Post by Martje_001 on 2009-06-24
Which folders grow? And how is your memory usage?

---

### Post by moomex on 2009-06-24
Same problem here. I thought this bug was due to ubuntuone-client trying to sync my folder to the web. I could be wrong!!

---

### Post by moomex on 2009-06-24
my /tmp folder was 1GB. I deleted those files (which start with tmp****** ). then I did a cold reboot. The files were generated again and it's

```
du /tmp -h -s
910M	/tmp
```

---

### Post by cariboo on 2009-06-24
I don't think it has anything to do with UbuntuOne, as during a warm boot, the problem doesn't happen.

As an aside, UbuntuOne seems to be broken after this mornings update.

---

### Post by cariboo on 2009-06-24
I was wrong, it does happen after a warm boot.

---

### Post by moomex on 2009-06-24
> As an aside, UbuntuOne seems to be broken after this mornings update.

In my case, ubuntuOne was broken but today's update fixed everything. :P

---

### Post by cariboo on 2009-06-25
It turns out it was a problem with UbuntuOne, it was trying to sync folders, and because it was broken, it couldn't sync. I will be posting an UbuntuOne bug, once I get back to my main computer.

---


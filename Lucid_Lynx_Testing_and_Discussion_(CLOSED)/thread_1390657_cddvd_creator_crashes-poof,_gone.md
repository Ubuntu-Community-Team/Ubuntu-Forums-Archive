---
title: "cd/dvd creator crashes-poof, gone"
date: 2010-01-25
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by dannyboy79 on 2010-01-25
when I insert a blank dvd-r, then drag and drop a dvd .iso file , then I hit write to disc, then that window just disappears into thin air. don't know what info I can post to help someone help me troubleshoot this issue. wouldn't want this to an issue for lucid final release. trying to burn that same dvd .iso using brasero results in a successful burn so not sure what cd/dvd creator is doing???

---

### Post by VMC on 2010-01-25
> **dannyboy79 said:**
> when I insert a blank dvd-r, then drag and drop a dvd .iso file , then I hit write to disc, then that window just disappears into thin air. don't know what info I can post to help someone help me troubleshoot this issue. wouldn't want this to an issue for lucid final release. trying to burn that same dvd .iso using brasero results in a successful burn so not sure what cd/dvd creator is doing???
Can you please try opening Brasero thru a terminal and see if you can burn it that way. If not at least we get some info from the terminal output.

Also have you checked /var/logs for any messages that may help?

---

### Post by dannyboy79 on 2010-01-26
as I said, brasero burns dvd iso's just fine so i am not sure how to open the cd/dvd creator window through the terminal so that I can paste output. i am not sure about any /var/log/ files but i will look tonight.

---

### Post by phenest on 2010-01-26
dannyboy, are you doing this from nautilus, because I just tried and got the same result.

---

### Post by phenest on 2010-01-26
```
nautilus --no-default-window --no-desktop burn:///
```
...will bring up that same nautilus window, however, there is no output.

---


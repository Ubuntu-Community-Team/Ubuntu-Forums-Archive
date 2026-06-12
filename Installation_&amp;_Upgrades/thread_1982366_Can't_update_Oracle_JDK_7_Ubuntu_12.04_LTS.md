---
title: "Can't update Oracle JDK 7 Ubuntu 12.04 LTS"
date: 2012-05-18
forum: Installation &amp; Upgrades
---

### Post by Kreaninw on 2012-05-18
I can't update Oracle JDK 7 on Ubuntu 12.04 LTS.

[[IMG]http://img705.imageshack.us/img705/530/screenshotfrom201205182.png[/IMG]]("http://imageshack.us/photo/my-images/705/screenshotfrom201205182.png/")

Uploaded with [ImageShack.us]("http://imageshack.us")

[[IMG]http://img406.imageshack.us/img406/530/screenshotfrom201205182.png[/IMG]]("http://imageshack.us/photo/my-images/406/screenshotfrom201205182.png/")

Uploaded with [ImageShack.us]("http://imageshack.us")

Hey, thanks to [QIII]("http://ubuntuforums.org/member.php?u=628170") and [darkod]("http://ubuntuforums.org/member.php?u=946366"). The problem solved.

---

### Post by QIII on 2012-05-18
What happens if you choose to update?

Those messages are informational.  Mine updates normally via the command line.

If choosing to update does or does not work, please let me know.  It looks like I may want to make some more updates to the Community Java Wiki.

---

### Post by Kreaninw on 2012-05-18
> **QIII said:**
> What happens if you choose to update?

Those messages are informational.  Mine updates normally via the command line.

If choosing to update does or does not work, please let me know.  It looks like I may want to make some more updates to the Community Java Wiki.

When I clicked install update button, it's always show the pop-up window like the image I showed in the first post. ](*,)

And how can I update it via command-line and why software updater just doesn't work? Thanks

---

### Post by darkod on 2012-05-18
Run in terminal:
sudo apt-get update
sudo apt-get upgrade

---

### Post by QIII on 2012-05-18
I will look in to the graphical update method and contact webupd8.

You can do command line updates as follows:

```
sudo apt-get update
```

```
sudo apt-get dist-upgrade
```

---

### Post by darkod on 2012-05-18
> **QIII said:**
> ```
sudo apt-get dist-upgrade
```

Isn't dist-upgrade to upgrade the ubuntu version? Aren't we talking only about JDK here?

---

### Post by QIII on 2012-05-18
> **darkod said:**
> Isn't dist-upgrade to upgrade the ubuntu version? Aren't we talking only about JDK here?

I use dist-upgrade exclusively, primarily to catch dependency resolutions.

I saw this update go by.  

However, I'll check to be sure.

In any case, upgrade should work so it wouldn't be a problem.

---

### Post by Psidawg on 2012-05-24
Here is how I did it

```
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-jdk7-installer
```

EDIT: I seen this was solved but the solutions provided above did not work for me. So I added the one that worked for me for others who may come across this thread.

---


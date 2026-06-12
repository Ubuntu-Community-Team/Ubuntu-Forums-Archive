---
title: "Ubuntu 21.10 to 22.04"
date: 2022-04-27
forum: Installation &amp; Upgrades
---

### Post by richramik on 2022-04-27
Hey Gang:

I want to upgrade Ubuntu 21.10 to 22.04.

I changed "Notify me of a new Ubuntu version" to "For any new version" in the Software & Updates tool.  Gave it a try.

I then shut my desktop down and brought it back up.  I then ran the Software & Updates tool.  It didn't find anything.

I suppose there is a command line I could enter in Terminal Mode which will accomplish the upgrade to 22.04.

HELP!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

Thanks In Advance,
Rich Ramik

---

### Post by ActionParsnip on 2022-04-27
```

sudo do-release-upgrade -d

```

Should do it

---

### Post by richramik on 2022-04-27
Thank you very much.  I'll give it a try when I get home from work.

Rich Ramik

---

### Post by richramik on 2022-04-27
I just received a private message from a friend showing the following command line:

sudo do-release-upgrade -c -d

It seems he found it on the web.  What would be the difference between what you provided versus what my friend provided????

Thanks,
Rich Ramik

---

### Post by deadflowr on 2022-04-27
The -c option is only suppose to check if a new release is available.
Not sure if you can upgrade with it.

Another option which is simple and allows upgrading using the graphical upgrader is to run update-manager with the -d option.
Easy to do just open the run dialog with alt+F2 and enter the command
```
update-manager -d
```
As long as the system is up-to-date it should give an option to upgrade to the new release.

---

### Post by grahammechanical on 2022-04-27
This thread has relevant information on this issue.

[https://ubuntuforums.org/showthread.php?t=2474227](https://ubuntuforums.org/showthread.php?t=2474227)

To put it simply, the upgrade path to 22.04 is not yet available.

Regards

---

### Post by richramik on 2022-04-27
Well now, I shall not tempt fate!!!!!  

Knowing my luck, I would attempt the upgrade via the command line and I would see a Mushroom Cloud were my desktop machine used to be.  LOLOLOL

Thanks for the assistance, but I shall wait until resolved.  Like I said, BOOMMMMMMMM!!!!!!!!
Thanks,
Rich Ramik

---

### Post by richramik on 2022-04-27
Hey Gang:

NO BOOOOOOMMMMMMMMM!!!!!!!!!!

When I got home this evening the upgrade path to 22.04 was available.  And it worked!!!!!!!!

Thanks Again,
Rich Ramik

---

### Post by jmichaels29 on 2022-04-27
> **richramik said:**
> Well now, I shall not tempt fate!!!!!  

Knowing my luck, I would attempt the upgrade via the command line and I would see a Mushroom Cloud were my desktop machine used to be.  LOLOLOL

Thanks for the assistance, but I shall wait until resolved.  Like I said, BOOMMMMMMMM!!!!!!!!
Thanks,
Rich Ramik


I tempted fate with an attempted upgrade using terminal - I tempted fate and was burnt.

---


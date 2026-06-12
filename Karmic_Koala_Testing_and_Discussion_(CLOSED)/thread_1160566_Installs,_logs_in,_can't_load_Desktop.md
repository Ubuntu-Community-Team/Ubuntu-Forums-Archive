---
title: "Installs, logs in, can't load Desktop"
date: 2009-05-15
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by keithpeter on 2009-05-15
Hello All

Karmic Koala Alpha 1 installed on an ASUS Pundit P1 (AMD dual core, nvidia integrated graphics, 870+ Mb available)

Installed on a 28Gb partition set as root, manual partitioning keeping a 22Gb home partition (not reformatted).

Installed OK, got passed graphical log in, desktop background visible, the spinning wheel jumping a little, brief flash of the 'restricted driver' alert picking up the nvidia. 

Error messages below received. CTRL-ALT-F1 got me back to prompt. Shut down from there.

Is any of this remotely worth filing as a bug?

---

### Post by Sub101 on 2009-05-15
The .dmrc error should not stop a boot. So I would suggest it is the second error.

This thread here fixed the problem for another, pre koala, user. 

As for filing a bug report, it may be worth it.

[http://ubuntuforums.org/showthread.php?t=917306](http://ubuntuforums.org/showthread.php?t=917306)

---

### Post by keithpeter on 2009-05-16
> **Sub101 said:**
> The .dmrc error should not stop a boot. So I would suggest it is the second error.

This thread here fixed the problem for another, pre koala, user. 

As for filing a bug report, it may be worth it.

[http://ubuntuforums.org/showthread.php?t=917306](http://ubuntuforums.org/showthread.php?t=917306)

Tried the chmod commands mentioned in that thread, still getting the error messages. The error messages persist when I reinstall 9.04 as well. My home partition is recognised ok.

---

### Post by taavikko on 2009-05-16
did you check that files on your $HOME is owned by you not root.
```
ls -la
```
should print all the relevant.

---

### Post by keithpeter on 2009-05-16
> **taavikko said:**
> did you check that files on your $HOME is owned by you not root.
```
ls -la
```
should print all the relevant.

Yup, home files are showing 500 500 mostly, a few belong to keith keith and one or two belong to root root.

I'm assuming the permission change was caused by 9.10 alpha 1 installer as I have re-installed os and preserved the /home before now OK.

---

### Post by taavikko on 2009-05-16
> **keithpeter said:**
> Yup, home files are showing 500 500 mostly, a few belong to keith keith and one or two belong to root root.

I'm assuming the permission change was caused by 9.10 alpha 1 installer as I have re-installed os and preserved the /home before now OK.

Please paste the output, it's far more helpful than commenting what belongs to whom ;)

---

### Post by keithpeter on 2009-05-16
> **taavikko said:**
> Please paste the output, it's far more helpful than commenting what belongs to whom ;)

I take your point ;) but I had no network on the pc in question as wifi wasn't happening until Gnome working properly.

[http://ubuntuforums.org/showthread.php?t=1136357](http://ubuntuforums.org/showthread.php?t=1136357)

[http://ubuntuforums.org/showthread.php?t=1005794](http://ubuntuforums.org/showthread.php?t=1005794)

Looks like the user order has changed between 9.04 and 9.10 alpha 1. Some people saw that going from 8.04 to 8.10

I used the command

```
sudo chown -R keith:keith /home/keith
```

to change home drive permissions for my user. I guess this will only affect those who use a separate home partition and who upgrade by reinstalling in another partition.

Thanks.

---


---
title: "Warning: &quot;Failure to download extra data files&quot; error"
date: 2015-06-13
forum: Installation &amp; Upgrades
---

### Post by Jonners59 on 2015-06-13
I keep getting a message pop up warning of failure to down load data.  The app it refers to is already installed and works.  I have also tried to "Run this action now" and makes no difference.

Any help to get rid of it, please.

Please see attached
[ATTACH=CONFIG]262568[/ATTACH]

---

### Post by dino99 on 2015-06-13
As i remember, wine-silverlight aka compholio was used at the biginning of the project; now wine-staging from the pipelight/stable ppa is what you need to use

---

### Post by Jonners59 on 2015-06-14
> **dino99 said:**
> As i remember, wine-silverlight aka compholio was used at the biginning of the project; now wine-staging from the pipelight/stable ppa is what you need to use

Cheers Dino99
The app is working fine, it's just this beeping warning.  Do you know how to get rid of it???????

---

### Post by Jonners59 on 2015-06-17
bit of a nudge...  Any help please!?!?!?!?!?

---

### Post by Jonners59 on 2015-08-06
bump

---

### Post by howefield on 2015-08-06
Do you have anything in this folder ?

/var/lib/update-notifier/user.d/

---

### Post by Jonners59 on 2015-08-06
> **howefield said:**
> Do you have anything in this folder ?

/var/lib/update-notifier/user.d/

Like the Steptoe n Son pic !!!

No, nothing.  I have just run a purge and install of these apps to see what happens.

---

### Post by Jonners59 on 2015-08-06
OK, so purging and reinstalling the various apps worked.

```
sudo apt-get purge "app name"
```
```
sudo apt-get install "app name"
```

I have other issues to do with app install, updates for which I shall start a new thread.

---

### Post by Jonners59 on 2015-08-07
no....  it's back again

---

### Post by Jonners59 on 2015-10-05
Any help with this please!?!?!?!?!  Getting VERY annoying!

---

### Post by Jonners59 on 2015-10-09
Help Plaease

---

### Post by muppet317 on 2016-01-07
dino999 had the answer. i've been having the same problem with wine-browser-installer.

go into synaptic package manager, mark whichever wine version is causing the "failure to download extra data files" for complete removal, mark wine-staging for upgrade - run those changes. then install all available upgrades - seems to have fixed the problem for me.

---

### Post by Jonners59 on 2016-01-10
> **muppet317 said:**
> dino999 had the answer. i've been having the same problem with wine-browser-installer.

go into synaptic package manager, mark whichever wine version is causing the "failure to download extra data files" for complete removal, mark wine-staging for upgrade - run those changes. then install all available upgrades - seems to have fixed the problem for me.
Thanks Muppet317
Dinno999 is good.
Yup followed all that, but now have no Netfix.

---


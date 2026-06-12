---
title: "Can't able to install .DEB packages"
date: 2008-10-16
forum: Installation &amp; Upgrades
---

### Post by rams123 on 2008-10-16
**I have internet connection only in xp **.

So I downloaded wine(.deb) in **xp** from [http://wine.budgetdedicated.com/archive/index.html]("http://wine.budgetdedicated.com/archive/index.html") and opened in **Kubuntu**. But when i am trying to install that ,error is coming !( Not only wine even some other .deb packages also.)

**Error **: Dependency is not satifiable : binfmt-support

**Screen Shot** - [http://img80.imageshack.us/my.php?image=snapshot2cj4.png]("http://img80.imageshack.us/my.php?image=snapshot2cj4.png")

What to do ?

---

### Post by tangibleorange on 2008-10-16
why not just install it from the repos?

```
sudo apt-get install wine
```

---

### Post by rams123 on 2008-10-16
I don't have internet connection in **Kubuntu** !

---

### Post by iaculallad on 2008-10-16
> **tangibleorange said:**
> why not just install it from the repos?

```
sudo apt-get install wine
```

The OP posted that he/she can connect to the net using windoze only. So the OP preferred downloading the DEB package using windoze and manually installing it on (k)Ubuntu.

@rams123:

You do need to connect to the internet to satisfy Wine's dependency. Otherwise, you have to download and manually install all the dependency before you could successfully install Wine.

---

### Post by Partyboi2 on 2008-10-16
[[COLOR=Blue]Here[/COLOR]]("http://packages.ubuntu.com/hardy/wine") is a list of the dependencies if you decide to do it the manual way. You could also look at Using the [[COLOR=Blue]generate download script[/COLOR]]("https://help.ubuntu.com/community/Synaptic/PackageDownloadScript") in synaptic as a possibility.

---

### Post by rams123 on 2008-10-16
So I have to download **All** dependencies OR only** binfmt-support ** ?

---

### Post by Partyboi2 on 2008-10-16
You will need all the dependencies to successfully install it. 
You may already have some installed, you can check by searching through synaptic package manager for each dependency before you download it.

---

### Post by tangibleorange on 2008-10-16
sorry i guess i have trouble reading bold text interspersed with normal text...

---


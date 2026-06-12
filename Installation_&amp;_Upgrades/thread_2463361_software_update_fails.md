---
title: "software update fails"
date: 2021-06-09
forum: Installation &amp; Upgrades
---

### Post by OldSmoky2 on 2021-06-09
The software updater is failing with the following message: 
" The following packages have unmet dependencies:
grub-efi-amd64-signed: Depends: grub2-common (>= 2.02~beta2-36ubuntu3.31) but 2.04-1ubuntu35.6 is to be installed"

---

### Post by drjdmartin on 2021-06-09
Have you tried any of these suggestions:

[https://askubuntu.com/questions/140246/how-do-i-resolve-unmet-dependencies-after-adding-a-ppa](https://askubuntu.com/questions/140246/how-do-i-resolve-unmet-dependencies-after-adding-a-ppa)

I'd try 

[FONT=var(--ff-mono)]> sudo apt-get -f install[/FONT]

---

### Post by MAFoElffen on 2021-06-09
Open a terminal:
```

sudo apt-get install -f
sudo apt-get clean

```
Then list out the Installed Grub 2 package
```

sudo apt-cache policy grub2

```
Post the results, which will show the current installed and any installation candidate...

---

### Post by OldSmoky2 on 2021-06-14
I just tried apt update and it worked flawlessly. Problem solved. Thank you.

---


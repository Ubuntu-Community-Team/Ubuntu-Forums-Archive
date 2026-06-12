---
title: "Awkward GPG error with Ubuntu Server running “sudo apt-get update”"
date: 2013-07-17
forum: Installation &amp; Upgrades
---

### Post by GabMus on 2013-07-17
[COLOR=#333333][FONT=UbuntuRegular]I just installed raring 32 bit server on an old machine, it seemed to work fine, but when I try to run "sudo apt-get update" I get this error (I'm translating from italian):
```
[/FONT][/COLOR][FONT=Ubuntu Mono]E: GPG Error: http://security.ubuntu.com raring-security Release: The following signatures were not valid: NODATA 1 NODATA 2[/FONT][COLOR=#333333][FONT=UbuntuRegular]
```
[/FONT][/COLOR][COLOR=#333333][FONT=UbuntuRegular]This is just awkward, I never experienced something like this, what should I do?
PS: I can't install any package because they are not recognised (i.e. if i try to install openjdk-6-jdk it tells me that the package cannot be found)[/FONT][/COLOR]

---

### Post by dino99 on 2013-07-17
try:

sudo apt-get clean
cd /var/lib/apt
sudo mv lists lists.old
sudo mkdir -p lists/partial
sudo apt-get clean
sudo apt-get update

---

### Post by GabMus on 2013-07-17
> **dino99 said:**
> try:

sudo apt-get clean
cd /var/lib/apt
sudo mv lists lists.old
sudo mkdir -p lists/partial
sudo apt-get clean
sudo apt-get update
I already tried, but it doesn't work :\

---

### Post by oldos2er on 2013-07-17
Try ```
sudo apt-key update
```

---

### Post by GabMus on 2013-07-17
> **oldos2er said:**
> Try ```
sudo apt-key update
```
I receive this output:
```
gpg: key 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changedgpg: key FBB75451: "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>" not changed
gpg: key C0B21F32: "Ubuntu Archive Automatic Signing Key (2012) <ftpmaster@ubuntu.com>" not changed
gpg: key EFE21092: "Ubuntu CD Image Automatic Signing Key (2012) <cdimage@ubuntu.com>" not changed
gpg: Total number processed: 4
gpg:              unchanged: 4



```

And sudo apt-get update still returns the same error :(

---

### Post by oldos2er on 2013-07-17
Can you install and remove packages ok? If so I wouldn't worry about the error.

---

### Post by GabMus on 2013-07-18
> **oldos2er said:**
> Can you install and remove packages ok? If so I wouldn't worry about the error.
I can't, it is like the repos are empty. If I try to install something it says that the package doesn't exist.

---

### Post by oldos2er on 2013-07-18
Can you post your sources.list? ```
cat /etc/apt/sources.list
```

---


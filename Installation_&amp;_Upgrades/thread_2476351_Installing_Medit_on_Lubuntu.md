---
title: "Installing Medit on Lubuntu"
date: 2022-06-23
forum: Installation &amp; Upgrades
---

### Post by Donnie Love on 2022-06-23
I need to learn how to install Medit text editor on Lubuntu 18.04.

---

### Post by #&amp;thj^% on 2022-06-23
Doesn't this just work:?
```
sudo apt install medit
```
or am i missing something?
[https://packages.ubuntu.com/bionic/medit](https://packages.ubuntu.com/bionic/medit)

---

### Post by Donnie Love on 2022-06-23
No.
E: Unable to locate package medit

---

### Post by howefield on 2022-06-23
Looks like it was removed from the repositories after the Bionic release (18.04)

---

### Post by #&amp;thj^% on 2022-06-23
It looks like it is in the proposed repo.
Do you know how to enable that?

---

### Post by #&amp;thj^% on 2022-06-23
> **howefield said:**
> Looks like it was removed from the repositories after the Bionic release (18.04)

Thanks howefield, I thought something was off.

It looks like it is in the proposed repo.
Do you know how to enable that?

---

### Post by deadflowr on 2022-06-23
Check it really is 18.04.
Check that universe is enabled.
Run an apt update first.

I see this on an 18.04 install:
```
me@me:~$apt policy medit
medit:
  Installed: (none)
  Candidate: 1.2.0-3
  Version table:
     1.2.0-3 500
        500 http://us.archive.ubuntu.com/ubuntu bionic/universe amd64 Packages
```
So definitely available on 18.04.
To check *buntu release 
```
lsb_release -a
```
to enable universe
```
sudo add-apt-repository universe
```
And apt update to refresh everything and check to see if it has problems
```
sudo apt update
```
apt update is very good at showing when issues are happening with package management and usually why.

---

### Post by #&amp;thj^% on 2022-06-23
> **deadflowr said:**
> Check it really is 18.04.
Check that universe is enabled.
Run an apt update first.

I see this on an 18.04 install:
```
me@me:~$apt policy medit
medit:
  Installed: (none)
  Candidate: 1.2.0-3
  Version table:
     1.2.0-3 500
        500 http://us.archive.ubuntu.com/ubuntu bionic/universe amd64 Packages
```
So definitely available on 18.04.
To check *buntu release 
```
lsb_release -a
```
to enable universe
```
sudo add-apt-repository universe
```
And apt update to refresh everything and check to see if it has problems
```
sudo apt update
```
apt update is very good at showing when issues are happening with package management and usually why.
Good Work  deadflowr i knew it was there>>>some where...:lolflag:

---

### Post by Impavidus on 2022-06-23
Now keep in mind that Lubuntu 18.04 has already reached end of life. The repositories are still there as Ubuntu 18.04 is still supported, but packages in the universe repository may no longer be maintained.

---

### Post by #&amp;thj^% on 2022-06-23
> **Impavidus said:**
> Now keep in mind that Lubuntu 18.04 has already reached end of life. The repositories are still there as Ubuntu 18.04 is still supported, but packages in the universe repository may no longer be maintained.

+1 on the EOL, but to be fair, Universe

This repository also consists free and open source software but [B][U]Ubuntu doesn’t guarantee of regular security updates to software in this category.
[/U][/B]
Software in this category are packaged and maintained by the community. The Universe repository has a vast amount of open source software and thus it enables you to have access to a huge number of software via apt package manager.

---

### Post by Donnie Love on 2022-06-24
"Check it really is 18.04."

I'm sorry, I was mistaken. I currently have 21.10 installed. I didn't know it had been updated.
But I still need to install Medit.

"It looks like it is in the proposed repo.
Do you know how to enable that?"

No, I'm sorry. I do not.

---

### Post by ajgreeny on 2022-06-24
Lubuntu 21.10 and all the other 21.10 DE versions are very soon to be completely out of support and from then you will be unable to update or install any more packages.

It is very insecure to continue using that version so I very strongly recommend that you reinstall a new, fully supported version of your chosen OS, Lubuntu 22.04 being my suggestion if you are to remain with Lubuntu.
Upgrading is possible 21.10 to 22.04 but a clean install is your best course of action in my opinion, though you can certainly try it if you wish.

Make sure 21.10 is fully updated then run the version upgrade.  If that is not successful, backup al your personal files and folders, including all the hidden ones, in your /home/***username*** folder, reinstall the OS then restore all those backed up files and folders.

Good luck!

---

### Post by #&amp;thj^% on 2022-06-24
> **Donnie Love said:**
> 

"It looks like it is in the proposed repo.
Do you know how to enable that?"

No, I'm sorry. I do not.
No matter now ubuntu 18.04 was the last version to have medit/mooedit in the repos

---

### Post by deadflowr on 2022-06-24
For what it's worth when something disappears in Ubuntu you can usually look to upstream Debian for the why:
[https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=939531]("https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=939531")


Too bad no one wants to work on it and create either an appimage, snap or flatpak for it.
Seems like the perfect candidate for one of those.

---


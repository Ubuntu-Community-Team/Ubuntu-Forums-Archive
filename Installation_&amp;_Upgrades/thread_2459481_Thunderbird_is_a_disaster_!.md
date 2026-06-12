---
title: "Thunderbird is a disaster !"
date: 2021-03-19
forum: Installation &amp; Upgrades
---

### Post by janvi2 on 2021-03-19
6th time, I am loosing all my Emails this year after snap updates of Thunderbird. New versions offer menues to import other mail clients but cannot read their own data nor the own account data of its previous versions. Account data always needs new setup und local emails folders needs to be retrieved from cryptical directories. Not enough - each updates opens a new cryptical directory and the old one remains (luckily to move the old mails by hand). How can I  disable the snap updates for thunderbird only ?

As we can see in the screendump, the developers now improved the hints for crashing the installed version before starting the new update

---

### Post by TheFu on 2021-03-19
Don't use snaps. There is a normal package for it.
```
$ dpkg -l thunderbird
...
ii  thunderbird    1:78.7.1+build1-0ubuntu0.20.04.1 amd64        Email, RSS and
```
Remove the thunderbird snap.  ```
sudo snap remove thunderbird
```
Install the thunderbird apt package.  ```
sudo apt install thunderbird
```
Be happy.

---

### Post by T6&amp;sfpER35% on 2021-03-19
or if you get really fed up with thunderbird , try [mailspring](https://linuxhint.com/install_mailspring_ubuntu/)
;)

---

### Post by janvi2 on 2021-03-20
What does that mean ?
```
Save data of snap "thunderbird" in automatic snapshot set #10 
```
This took a long time but everything seems well now. All mail copies seems to be also in old snap/thunderbird/common folders. 
Can I remove this or are they shared with the Firefox Browser ?

---

### Post by TheFu on 2021-03-20
Thunderbird is separate from Firefox.  I wouldn't delete anything, just mv the directory somewhere else until you are 100% positive it isn't needed.

```
mv ~/.thunderbird  ~/.thunderbird-old
```
If you want to be really kewl - you can schedule ~/.thunderbird-old to be deleted in a week now.
```
echo "rm -rf ~/.thunderbird-old" | at now + 7 days
```
This way it is around enough time that you'll know the new setup is working.

BTW, I've never used thunderbird as a snap.  The data for it and hence the directory for that could be somewhere else.  Perhaps under ~/snap/..... something. Please check that to be certain.  [https://askubuntu.com/questions/762354/where-can-ubuntu-snaps-write-data](https://askubuntu.com/questions/762354/where-can-ubuntu-snaps-write-data) explains more.

---

### Post by janvi2 on 2021-03-20
To make sure, nothing is lost, I put mail data into ~/mail directory month ago with nightly backup script beside changing from pop to imap. Everything seems ok now. As you suggest, I am going to be careful before erasing old ~/snap dirs.

---


---
title: "Upgrading Dapper to Edgy"
date: 2008-02-28
forum: Installation &amp; Upgrades
---

### Post by crapple on 2008-02-28
So here is my problem when I type in this code in the terminal
```
gksu &#8220;update-manager -c -d&#8221;

```
the update manager tells me 8.4 is available but I need 6.10 because I am running 6.6 .

If I try this code

```
gksu &#8220;update-manager -c &#8221;
```

It doesn't tell me there are any updates.

I know you are not supposed to skip versions.

Any Ideas?

---

### Post by overdrank on 2008-02-28
HI and you can try, ```
gksu update-manager -c -d
``` Or you can try and edit your /etc/apt/sources.list and change from dapper to edgy. But why not just install Feisty or Gutsy?

---

### Post by crapple on 2008-02-28
That gets me 8.4 again.

I am going to update to a higher version but you are not supposed to skip any versions.

---

### Post by overdrank on 2008-02-28
> **crapple said:**
> That gets me 8.4 again.

I am going to update to a higher version but you are not supposed to skip any versions.

This is suggested ( not to skip version) . But I was thinking of the new install. you can try and edit your /etc/apt/sources.list and change from dapper to edgy

---

### Post by crapple on 2008-02-28
I have tried doing a new install but the disk I used burnt wrong and I ran out of disks.

How do I get update manger to show 6.10 instead of 8.4?

---

### Post by overdrank on 2008-02-28
> **crapple said:**
> I have tried doing a new install but the disk I used burnt wrong and I ran out of disks.

How do I get update manger to show 6.10 instead of 8.4?

Hi and I believe edgy was released In October 26, 2006
[http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)
I believe the support has ended
So you may try to edit your /etc/apt/sources.list and hope that works.

---

### Post by crapple on 2008-02-28
Can someone just tell how to tell update manger to update to 6.10 instead of 8.4?

---

### Post by zvacet on 2008-02-29
Upgrade lead you to Hardy because it is next LTS release and in this case you can skip versions.I think only way to upgrade to Edgy is to change source list.Don´t get me wrong I want to add little remark.Edgy will be supported until april and in april Hardy will be released.If you in april have Edgy you will have to upgrade to Hardy and that will look like this Edgy<Feisty>Gutsy>Hardy.If you don´t have any special reason to do upgrade my advice is to wait Hardy.But that is just suggestion.If you still want to upgrade change source list with this command

```
  sudo sed -e 's/\sdapper/ edgy/g' -i /etc/apt/sources.list 
```

after that do upgrade with 

```
 sudo apt-get update && sudo apt-get dist-upgrade && sudo apt-get dist-upgrade
```

to be sure everything is O.K.

```
sudo apt-get update && sudo apt-get dist-upgrade
  sudo apt-get -f install
  sudo dpkg --configure -a 
```

[B]EDIT:Before you do any of this be sure that your system is up-to-date with
```
sudo apt-get update && sudo apt-get upgrade
```[/B]

---


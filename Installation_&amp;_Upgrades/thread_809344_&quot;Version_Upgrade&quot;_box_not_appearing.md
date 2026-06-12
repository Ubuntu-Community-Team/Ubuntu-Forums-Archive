---
title: "&quot;Version Upgrade&quot; box not appearing"
date: 2008-05-27
forum: Installation &amp; Upgrades
---

### Post by cesy on 2008-05-27
I've been trying to upgrade from Gutsy to Hardy, and installed the latest updates, but the "Version Upgrade" button does not appear in Adept Manager when the instructions claim it should, and I can't see what's wrong.
I also have a backup install on another partition that was left from when I upgraded to Edgy, and I want to upgrade that, too, but when I tried to upgrade that from Edgy to Feisty, following the instructions, that also didn't have the "Version Upgrade" button appearing.
Does anyone have any suggestions?

---

### Post by zvacet on 2008-05-27
Edgy is not supported anymore.It can be done but it is long way to go,so I don´t think that is what are you looking for.You can try 

```
sudo apt-get update && sudo apt-get upgrade
```

and then see in Adept if you get message for new version.If that doesn´t help you can edit your source list and replace every gutsy with hardy and save and close file.

```
sudo aptitude update
sudo aptitude full-upgrade
```

---

### Post by cesy on 2008-05-27
When I looked on the Help, it said that to upgrade from Edgy, they recommend going through all the other versions. Is there another way to upgrade from Edgy? I know it's not supported any more, but I still have a partition with it on.

I tried the code you suggested but it still didn't work.

I read somewhere else that editing the sources.list as you said is a bad idea, though they didn't explain why. Can you tell me what the disadvantages are, please?

---

### Post by zvacet on 2008-05-27
I thought that you want to upgrade Gutsy to Hardy.If you want to upgrade Edgy edir youur source list and in every line you will replace  **archive.ubuntu.com** with **old-releases.ubuntu.com** Your suouce list will look like this

> ## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) edgy main restricted universe multiverse
deb-src [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) edgy main restricted universe multiverse

deb [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) edgy-proposed main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse
deb-src [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb-src [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse
deb-src [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

Save and close file.

```
sudo apt-get update && sudo apt-get upgrade
```

After that upgrade to Feisty.Once in Feisty you will have to edit your source list again and replace **old-releases.ubuntu.com** with **archive.ubuntu.com** After that yo uwill have to update Feisty and then upgrade to Gutsy.

---

### Post by cesy on 2008-05-27
As I tried to say in my first post, I have one partition with Gutsy which I want to upgrade to Hardy, and another partition with Edgy which I also want to upgrade. I was having the same problem with both, so asked about both in the same post.

Thank you for the suggestion. I'll try that now.

---

### Post by cesy on 2008-05-27
I still don't have the "Version Upgrade" button.

---

### Post by zvacet on 2008-05-27
Upgrade Gutsy with alternate CD.[Here]("http://releases.ubuntu.com/kubuntu/hardy/")** In system>admin software sources uncheck all third party repos before upgrade.**

---


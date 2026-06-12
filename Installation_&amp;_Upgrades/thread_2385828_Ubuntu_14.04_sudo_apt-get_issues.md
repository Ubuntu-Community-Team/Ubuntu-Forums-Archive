---
title: "Ubuntu 14.04 sudo apt-get issues"
date: 2018-02-25
forum: Installation &amp; Upgrades
---

### Post by tesszach on 2018-02-25
I am struggling with 'sudo apt-get update'  command. Plz find my attachments for error and system settings. Plz guide me to resolve this issue. Thanks in advance.

---

### Post by Bashing-om on 2018-02-25
tesszach; Hello - Welcome to the forum.

Your release is utopic .. that is 14.10. That 14.10 is long time dead and the software repository no longer exists . You must upgrade to a current release . A long hard road to do an on-line End_Od_Life upgrade from 14.10; highly recommend that you back up your personal data and do a clean fresh install of 16.04 .

[INDENT][INDENT]all good things some to an end
[/INDENT][/INDENT]

---

### Post by Impavidus on 2018-02-25
Your "Other Software" refers to trusty on the old-releases server. Trusty is not old yet (well, it's quite old, but still supported), so that doesn't really make sense. You should be able to disable those.

The problem is that, although the "Updates" tab says you use the trusty repositories (from the server for India), your sources.list refers to utopic (from the US server), which is what apt-get update uses. Utopic, which is Ubuntu 14.10, reached end of life a long time ago. If this was changed recently, so that the software packages currently installed are actually all belonging to Ubuntu 14.04, you can simply fix your sources.list:```
# First make a backup
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bck

# Then change the sources to trusty
sudo sed -i s/utopic/trusty/ /etc/atp/sources.list
```
If there's more damage, take this as an opportunity to get a more recent release, using a fresh install.

---

### Post by tesszach on 2018-02-26
thanks :)

---

### Post by tesszach on 2018-02-26
Hi Impavidus,  I just tried ur suggestions and again executed 'sudo apt-get update' .Still I m getting error :( .  Error :::: -  "[COLOR=#ff0000][I]W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty/Release](http://us.archive.ubuntu.com/ubuntu/dists/trusty/Release)  Unable to find expected entry 'restricted/source/Sources' in Release file (Wrong sources.list entry or malformed file)
E: Some index files failed to download. They have been ignored, or old ones used instead[/I][/COLOR]." Any easy solution for this other than a fresh install. Thanks in advance

---

### Post by Impavidus on 2018-02-26
From a pm by OP:[QUOTE=tesszach]Hi.. thanks for your reply on my query.
  
  My ubuntu version is 14.04. Because of 'sudo apt-get update' issues I  tried so many solution from google without any understanding.I changed  my sources.list, updates tab,authentication tab ...etc. Now I totally  became blank. Can you please guide me to resolve these issues. Thanks in  advance.

Thanks[/QUOTE]
(Please keep this in the forum. There are others who may help too.)

So you're deeper into trouble already. The easiest solution is undoubtedly a fresh install, but it may be possible to fix this. You may learn more that way. But I don't know how.

---

### Post by deadflowr on 2018-02-26
Well, outside of a clean install what does the actual sources.list file show
```
cat /etc/apt/sources.list
```
please copy it and paste it into the thread, rather then a screenshot.
(Use code tags)

---

### Post by tesszach on 2018-02-26
Hii.. deadflowr,
cat /etc/apt/sources.list
```
###### Ubuntu Main Repos
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty main restricted universe multiverse 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty main restricted universe multiverse 

###### Ubuntu Update Repos
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-security main restricted universe multiverse 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates main restricted universe multiverse 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-security main restricted universe multiverse 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates main restricted universe multiverse 

###### Ubuntu Partner Repo
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner

###### Ubuntu Extras Repo
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
```

---

### Post by tesszach on 2018-02-27
Hi.. deadflowr, thanks. Any suggestion on my issue from your side???

---

### Post by deadflowr on 2018-02-27
Try a lists purge
```
sudo rm -rf /var/lib/apt/lists/*
sudo apt-get clean
sudo apt-get update
```

Somehow someone a few weeks (or months, time flies) back had the same error, with the same non-default generated sources.list, but I think that one was for xenial.
Unfortunately, I cannot find that thread. So maybe I'm delusional about it.

---


---
title: "Unable to upgrade from 11.10 to 12.04LTS"
date: 2013-03-10
forum: Installation &amp; Upgrades
---

### Post by f.arthur on 2013-03-10
Hello,
I have been trying to upgrade from 11.10 to 12.04 but i keep getting these error messages

W:Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/karmic-backports/main/source/Sources](http://gb.archive.ubuntu.com/ubuntu/dists/karmic-backports/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/karmic-backports/restricted/source/Sources](http://gb.archive.ubuntu.com/ubuntu/dists/karmic-backports/restricted/source/Sources)  404  Not Found
, W:Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/karmic-backports/universe/source/Sources](http://gb.archive.ubuntu.com/ubuntu/dists/karmic-backports/universe/source/Sources)  404  Not Found
, W:Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/karmic-backports/multiverse/source/Sources](http://gb.archive.ubuntu.com/ubuntu/dists/karmic-backports/multiverse/source/Sources)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.


My first Ubuntu installation was 9.10(Karmic Koala) and I have always done upgrades till my current version 11.10(Oneiric Ocelot)
I think there is no more support for some Karmic packages and this is affecting my upgrade. 
Can anyone help ?

---

### Post by darkod on 2013-03-10
If you are currently on oneiric your sources should point to it, not karmic. Yes, the karmic repos are closed. But you shouldn't have any sources for karmic anyway.

Try disabling these repos, or if you need them than change them to oneiric from karmic.

---

### Post by f.arthur on 2013-03-12
How do i disable repos.
I am quite new at this and will be grateful if you could walk me through the process.

---

### Post by darkod on 2013-03-12
If I'm not mistaken, in 11.10 you need to open Update Manager and it will show all the default repos. Third-party repos might be in the second or third tab, not sure right now.

Another alternative, which will show them better, is opening in the gedit text editor the file /etc/apt/sources.list. It contains all repos. Open terminal and execute:
```
gksu gedit /etc/apt/sources.list
```

That will open the text file and in there are all of them. Compare them with the error message and you can disable the ones you want to disable by putting the # symbol at the start of the line. Everything after the # is ignored. That way you can easily disable things, and later enable them if you want to by removing the #. Save and close the file. Then in terminal run:
```
sudo apt-get update
```

It should run with no errors. And you should be able to upgrade to 12.04 LTS or install any software without problems.

---

### Post by f.arthur on 2013-03-14
Thanks i did it and the updates started but i got another error

Failed to fetch [http://ubuntu.datahop.net/ubuntu/pool/main/g/gwibber/gwibber-service-twitter_3.4.2-0ubuntu2.2_all.deb](http://ubuntu.datahop.net/ubuntu/pool/main/g/gwibber/gwibber-service-twitter_3.4.2-0ubuntu2.2_all.deb) Size mismatch

Can you help?

---

### Post by darkod on 2013-03-14
The file might be wrong or corrupted there. Try another server. Simply change the update server, reload the sources and try again.

---

### Post by f.arthur on 2013-03-14
still the same.

---

### Post by darkod on 2013-03-14
Have no clue. Try googling this type of error, maybe it would help if you remove/purge the program (package) and try to install it later.

---


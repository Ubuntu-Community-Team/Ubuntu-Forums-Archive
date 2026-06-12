---
title: "How to install DigiKam 1.0.0 stable from Lucid?"
date: 2009-12-28
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by koosfoto.hu on 2009-12-28
Greetings,

While running DigiKam under Ubuntu KK... I contacted the support of DigiKam. 
I learnt, that with Ubuntu an unstable version of the program is delivered and that I (everyone) should change to the 1.0.0 stable version.

The topic is here:
[https://bugs.kde.org/show_bug.cgi?id=220043](https://bugs.kde.org/show_bug.cgi?id=220043)

I tried to install it from Lucid, however, I keep on getting error messages... 

How could the new DigiKam version (1.0.0) be installed easily under KK Ubuntu?

Thanks a lot,

Tamas

---

### Post by philip5 on 2010-01-01
> **koosfoto.hu said:**
> Greetings,

While running DigiKam under Ubuntu KK... I contacted the support of DigiKam. 
I learnt, that with Ubuntu an unstable version of the program is delivered and that I (everyone) should change to the 1.0.0 stable version.

The topic is here:
[https://bugs.kde.org/show_bug.cgi?id=220043](https://bugs.kde.org/show_bug.cgi?id=220043)

I tried to install it from Lucid, however, I keep on getting error messages... 

How could the new DigiKam version (1.0.0) be installed easily under KK Ubuntu?

Thanks a lot,

Tamas
If you still use 9.10/Karmic and want to use the latest Digikam 1.0.0 (and kipi-plugins 1.0) then you could grab the packages from my repo:

[https://launchpad.net/~philip5/+archive/extra](https://launchpad.net/~philip5/+archive/extra)

Hope that solves it for you.

Regards,

Philip

---

### Post by koosfoto.hu on 2010-01-02
Thanks a lot, Philip!

Before installing it... a question:
Do you see ayn "danger" to install the 1.0.0 of Digikam under Ubuntu KK??
(I mean... dependencies, what might be different in the two versions of Ubuntu, or anything alike...)

Thanks a lot!

Happy New Year.

Tamas

---

### Post by philip5 on 2010-01-02
No danger and the difference is that the 1.0.0 final (that you find on my repo) have a lot of bugfixes, new features etc so there is no draw back what I know of.

Don't forget to update the kipi-plugins that you also find on my repo. They give enhancements to the Digikam experience. Same with them, bugfixes, new features etc.

Happy Digikaming...

---

### Post by koosfoto.hu on 2010-01-03
Thanks, Philip!

I am just doin it... 

The terminal answered:

```
light@mind:~$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 43C56F3F
[sudo] password for light: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys 43C56F3F
gpg: requesting key 43C56F3F from hkp server keyserver.ubuntu.com
gpg: key 43C56F3F: "Launchpad extra" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
```

It is oké, I think... meaning that this was already the good key... Is it so?

DigiKam is installed and kipi-plugins are being installed now... 

And, yes... YES! I have the 1.0.0 installed!!!!

Super! THANKS, Philip!

Would you post a note at 
[https://bugs.kde.org/show_bug.cgi?id=220043](https://bugs.kde.org/show_bug.cgi?id=220043)
as well... Or, may I post your solution? 
May be it is useful for people from KDE, as well.
What do you think???

THANKS A LOT!!!!!!!!!!!

So, I go DigiKaming... a la Philip! :-)

Friendly greetings,

Tamas

---

### Post by dbd on 2010-01-05
Thanks Philip, that's really handy :)

---

### Post by philip5 on 2010-01-05
> **dbd said:**
> Thanks Philip, that's really handy :)

You're welcome. 

Hope the packages works for you and that you enjoy the extra they give. :)

---

### Post by koosfoto.hu on 2010-01-06
Thanks again!
It works nice... 

I posted your answer at KDE, as well. 

Friendly greetings,

Tamas

---

### Post by philip5 on 2010-03-30
Just bumping this thread with that I now have Digikam 1.2.0 and kipi-plugins 1.2.0 for Karmic on my PPA on Launchpad. More info about the PPA is to be found by following the link in my signature...

Have fun with this awesome piece of software that Digikam is! :D

---

### Post by Arla on 2010-03-30
> **philip5 said:**
> Just bumping this thread with that I now have Digikam 1.2.0 and kipi-plugins 1.2.0 for Karmic on my PPA on Launchpad. More info about the PPA is to be found by following the link in my signature...

Have fun with this awesome piece of software that Digikam is! :D

Great to hear you've added it, I was wondering when I might be able to get the 1.2 version when I saw it come out yesterday.

Unfortunately after adding your extras PPA (I assume that's the right one since it had DigiKam in it) I get the following when trying to update

W: Failed to fetch [http://ppa.launchpad.net/philip5/extra/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/philip5/extra/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found

Is this because it's built for Karmic? I do notice if I change the lucid to karmic it seems to at least get a Packages.gz file (which makes me wonder if this is a bug/unintended feature of using the command 
```
 sudo add-apt-repository ppa:user/ppa-name 
```
since that was how I added your repository).

---

### Post by philip5 on 2010-03-30
> **Arla said:**
> Great to hear you've added it, I was wondering when I might be able to get the 1.2 version when I saw it come out yesterday.

Unfortunately after adding your extras PPA (I assume that's the right one since it had DigiKam in it) I get the following when trying to update

W: Failed to fetch [http://ppa.launchpad.net/philip5/extra/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/philip5/extra/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found

Is this because it's built for Karmic? I do notice if I change the lucid to karmic it seems to at least get a Packages.gz file (which makes me wonder if this is a bug/unintended feature of using the command 
```
 sudo add-apt-repository ppa:user/ppa-name 
```
since that was how I added your repository).
You have done the adding of the repository correct but as you see in my post I have only built it for Karmic and from the reading of your posting you use Lucid that my PPA won't support untill Lucid is final.

---

### Post by Arla on 2010-03-30
> **philip5 said:**
> You have done the adding of the repository correct but as you see in my post I have only built it for Karmic and from the reading of your posting you use Lucid that my PPA won't support untill Lucid is final.

Yeah, didn't work when I changed to Karmic, missing dependencies. Hadn't read carefully that it was just Karmic (since the post was in the Lucid forums, I made an assumption).

Will happily wait for final date when I can update, of course a little later I'll be updated to Mini Mouse :)

---

### Post by Nobby on 2010-03-31
Hey Philip, thanks for providing that repository.  Used it to update digikam to 1.2 on my Lucid install and seems to work fine :D

---

### Post by philip5 on 2010-04-01
> **Nobby said:**
> Hey Philip, thanks for providing that repository.  Used it to update digikam to 1.2 on my Lucid install and seems to work fine :D
Good to hear! The packages in my repository should work just fine but you never now... :)

Have fun!

---


---
title: "Update manager not finding gutsy"
date: 2007-10-17
forum: Installation &amp; Upgrades
---

### Post by redzion28 on 2007-10-17
The front page says gutsy is available for download. I tried to upgrade using the update manager but it doesn't find anything. Am I doing something wrong?

---

### Post by redzion28 on 2007-10-17
Hmm it has changed back .Sorry.

---

### Post by superyounan1 on 2007-10-18
what changed back? I'm trying to upgrade now too "00 days left", but it just says I'm up to date

---

### Post by superyounan1 on 2007-10-18
ugh, i feel so bad for being impatient, can't help it.

anyone else having trouble? or is it upgrading for you?

---

### Post by ebs16 on 2007-10-18
this should help if you're trying to upgrade from fiesty:

[https://help.ubuntu.com/community/GutsyUpgrades#head-6e4364746e366128df274be82e17b4173bdf6d2f](https://help.ubuntu.com/community/GutsyUpgrades#head-6e4364746e366128df274be82e17b4173bdf6d2f)

---

### Post by John Bennett on 2007-10-18
Same here.

I followed these instructions:

[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

I do not get this message:

[img]http://www.ubuntu.com/files/u1/710_update-manager-upgrade.png[/img]

Instead, the manager says my system is up-to-date, with no option for Gutsy.

---

### Post by timo_01 on 2007-10-18
> **John Bennett said:**
> Same here.

I followed these instructions:

[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

I do not get this message:

[img]http://www.ubuntu.com/files/u1/710_update-manager-upgrade.png[/img]

Instead, the manager says my system is up-to-date, with no option for Gutsy.


try this: ```
 gksu  update-manager -d 
```

---

### Post by margori on 2007-10-18
The last lines you suggested are for update Feisty to Gutsy Release Candidate. It seems that we have to wait a for the official release of Gutsy.

---

### Post by erginemr on 2007-10-18
The ubuntu site is constantly changing their content. They had suggested downloading the Beta version of Gutsy one hour ago, now they are saying Gutsy is coming soon. I guess, they have discovered an impotant but at the last minute.

So, I suggest waiting for a while (say, one day) before the actual upgrade.

---

### Post by capitocapito on 2007-10-18
It's release day, and my update manager cannot find gutsy either.

I would like to know why this is.  If other people can find it, why can't I?

---

### Post by jetthe on 2007-10-18
> **capitocapito said:**
> It's release day, and my update manager cannot find gutsy either.

I would like to know why this is.  If other people can find it, why can't I?


Probably because you're using diffrent mirrors. Be patient and your time will come.

---

### Post by Beggar on 2007-10-18
Be careful update-manager -d will upgrade to the latest development release, I know your trying to help, but you could damage peoples systems by posting information like that.

the command you are looking for is 

```
sudo update-manager --dist-ugprade
```

(no thats not a typo, you can spell it properly as well, but this way is funnier).

---

### Post by arusarka on 2007-10-18
I'm having similar problems upgrading form ubuntu 7.04 to 7.10 (64 bit)

when I do sudo update-manger --dist-upgrade a pop up comes up showing 

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=46753&stc=1&d=1192751294[/IMG]

And i have reloaded synaptic several times and also applied all the updates but it is of no help

thanks in advance

---

### Post by arusarka on 2007-10-18
it just started working

i think the mirror was updated just a little while ago

---

### Post by punkrokk on 2007-10-18
I just opened hen closed the Synaptic Package Manager, then reran the  System Update tool and it appeared for me ... HTH

---

### Post by gganitis on 2007-10-19
I had the same problem, but solved when I wrote:

[B]sudo update-manager --dist-ugprade
[/B] as Beggar said!

---

### Post by piotr.rusol on 2007-10-19
I had the same problem.
In my case solution was:

**sudo update-manager -c**

OR if you want

**sudo update-manager --check-dist-upgrades**

Only with this parameter update-manager correctly find new release.
Why? I don't but it works.

Good luck! :guitar:

---


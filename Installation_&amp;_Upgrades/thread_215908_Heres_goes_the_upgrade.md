---
title: "Heres goes the upgrade"
date: 2006-07-14
forum: Installation &amp; Upgrades
---

### Post by reegz on 2006-07-14
Hi guys,

I'm currently upgrading my distro to 6.06 as we speak.. no no not  on this pc.. another one. I've opted to do the whole 
```
apt-get update && sudo apt-get dist-upgrade
``` 

Looking good so far. altho i question my wisdom.. i'v dialed into the network at work and am performing this upgrade remotely.. dunno if its a smart thing to do. :-k 

hey if something goes wrong.. i might get monday off to re-install :-D 

anyway my 2 cents.. been using ubuntu since 4.something (i cant remember) and im very proud to sing the praises of this distro to anyone who will listen. installed 6.06 for a collegue this week. this was the cleanest, most simplest ubuntu install i have ever performed. im very impressed.

thats my 2 cents.. lemme monitor my upgrade.. 

ciao

---

### Post by Engnome on 2006-07-14
Hmm yeah alot of people have had problems with dist upgrading. (including me) Don't you have to change all breezy to dapper in sources.list?

Oh and welcome to the forum, newbie:p  This is the forum discussion part, were you discuss the *forums.*

---

### Post by NewWaves on 2006-07-14
Ubuntu is so simple to upgrade!  I've heard a lot of mocking of ubuntu but it's so nice to just type a few keys and have ubuntu do its thing, come back to the desk and your up to a new version!

---

### Post by reegz on 2006-07-14
lol... yeah my mistake. wrong section of the forum..

anyhoo.. upgrade is complete... i'l go in tomorrow to view the carnage... wish me luck

---

### Post by reegz on 2006-07-14
> **Engnome said:**
> Hmm yeah alot of people have had problems with dist upgrading. (including me) Don't you have to change all breezy to dapper in sources.list?

Oh and welcome to the forum, newbie:p  This is the forum discussion part, were you discuss the *forums.*

Yeah, had to update the sources.list. Changed all references to breezy to be dapper.

---

### Post by reegz on 2006-07-17
lol... think i did something wrong. Upgrade went fine, no problems.. 

except this.. i now have xubuntu as opposed to ye good ol ubuntu. i dont mind this, but why did apt install xubuntu??

another thing, when i change users (in a shell), i get this output

```

configuration error - unknown item 'QUOTAS_ENAB' (notify administrator)
configuration error - unknown item 'NOLOGIN_STR' (notify administrator)
configuration error - unknown item 'ENV_HZ' (notify administrator)
configuration error - unknown item 'CHFN_AUTH' (notify administrator)
configuration error - unknown item 'CLOSE_SESSIONS' (notify administrator)

```

another thing thats puzzling me... i now have the following added mounts

```

varrun                498M   84K  498M   1% /var/run
varlock               498M  4.0K  498M   1% /var/lock
udev                  498M  108K  498M   1% /dev
devshm                498M     0  498M   0% /dev/shm
lrm                   498M   19M  480M   4% /lib/modules/2.6.15-26-386/volatile

```

Perhaps someone could shed some light on these issues.

nonetheless, i still dig ubuntu.

---

### Post by reegz on 2006-07-17
Never mind.. A bit of searching on this very forum and the answer to the environment variables was solved. However, if anyone has anything to say about the other problems, i'm listening :D :D

---


---
title: "Repository problems"
date: 2006-06-01
forum: Installation &amp; Upgrades
---

### Post by Micro$oftWinblows on 2006-06-01
I've recently installed Ubuntu 6.06 from the cd with no problems, I've enabled all the repositories but certain things such as nonfree-flashplayer, and java, even mplayer aren't in the repositories. Anyone have any idea what's going on?

Here's my sources.list:

I personally can't see anything wrong with it.

deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe


Much appreciated.

---

### Post by llamakc on 2006-06-01
Here's mine:

ken@vulva:~$ cat /etc/apt/sources.list
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe multiverse
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

#deb [http://ato.netsons.org/ubuntu/](http://ato.netsons.org/ubuntu/) binary/


deb [http://theli.free.fr/packages/dapper/](http://theli.free.fr/packages/dapper/) ./


But I installed Automatix which made my life much easier.

---

### Post by johnc4510 on 2006-06-01
After enabling the extra repositories do these in terminal:
sudo apt-get update
sudo apt-get upgrade 
Then the items you want should be available.

---

### Post by Micro$oftWinblows on 2006-06-01
Hm I'm looking into Automatix now. I'd still like to know why I can't see nonfree plugins etc, and if there's any way to fix it.

---

### Post by johnc4510 on 2006-06-01
Just follow my instructions

---

### Post by llamakc on 2006-06-01
Because they reside in multiverse and your sources.list didn't specify that. Moreso, the universe entry was for -backports, and not the regular universe repository.

---

### Post by Micro$oftWinblows on 2006-06-02
[QUOTE=johnc4510]After enabling the extra repositories do these in terminal:
sudo apt-get update
sudo apt-get upgrade 
Then the items you want should be available.[/QUOTE]

Still nothing. The plugins I wanted weren't there so I went to Add/Remove programs.

'sun-java5-bin' is not available in any software channel

The application might not support your system architecture.

This kind of thing happened. Gar.

---

### Post by Micro$oftWinblows on 2006-06-02
I think I see my problem now...

---


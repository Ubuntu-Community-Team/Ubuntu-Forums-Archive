---
title: "Deluge installation problem due to python(jaunty)"
date: 2009-03-04
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by aniketgore on 2009-03-04
I am using jaunty alpha 5 AMD64. I was able to install delug with alpha 4. But now i am unable to install it. It says python 2.6.1 is installed when 2.6 or <2.6 is required. 
             I tried to complie using sourse it doesnt compile. Please give some solution so i can install delug.(I have tried using ADD/REMOVE and Synaptic Package manager nothing helps.)

---

### Post by heathman001 on 2009-03-05
I'm having the same problem. Deluge worked in Jaunty alpha 4 (amd64), but it won't install in a clean install of alpha 5 (amd64). 

> sudo apt-get install deluge
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  deluge: Depends: deluge-common (= 1.1.3+dfsg-1) but it is not going to be installed
E: Broken packages


---

### Post by aniketgore on 2009-03-05
Yes same problem i am getting. 

If i try using apt-get install delug*          it says python version is incorrect.

---

### Post by cariboo on 2009-03-06
You will have to wait until Deluge is updated. I am using Transmission until it is fixed.

Jim

---

### Post by andrewsomething on 2009-03-06
There are bugs filed and patches submitted about this issue, just waiting on sponsors for upload. In the meantime, I have python 2.6 compatable packages of deluge and python-libtorrent (needed by deluge) in my PPA if you're interested:

[https://edge.launchpad.net/~andrewsomething/+archive/ppa](https://edge.launchpad.net/~andrewsomething/+archive/ppa)

---

### Post by Darkshade on 2009-03-06
> **andrewsomething said:**
> There are bugs filed and patches submitted about this issue, just waiting on sponsors for upload. In the meantime, I have python 2.6 compatable packages of deluge and python-libtorrent (needed by deluge) in my PPA if you're interested:

[https://edge.launchpad.net/~andrewsomething/+archive/ppa](https://edge.launchpad.net/~andrewsomething/+archive/ppa)

Thank you! I can get rid of Transmission again :D

---

### Post by BobCFC on 2009-03-06
> **andrewsomething said:**
> There are bugs filed and patches submitted about this issue, just waiting on sponsors for upload. In the meantime, I have python 2.6 compatable packages of deluge and python-libtorrent (needed by deluge) in my PPA if you're interested:

[https://edge.launchpad.net/~andrewsomething/+archive/ppa](https://edge.launchpad.net/~andrewsomething/+archive/ppa)



Thanks mate!  I would give you a medal but they seem to have gone

---

### Post by scaine on 2009-03-07
The deluge team now have their own "official" PPA for Ubuntu.
[https://launchpad.net/~deluge-team/+archive/ppa]("https://launchpad.net/%7Edeluge-team/+archive/ppa")

Word of warning though, it was working last week, but broke at some point in the last 3 days... it just hangs on start up now.  Nice to know it's going to be kept up to date automatically though.

---


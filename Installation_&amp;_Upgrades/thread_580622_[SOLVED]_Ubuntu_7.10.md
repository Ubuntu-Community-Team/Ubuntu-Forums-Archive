---
title: "[SOLVED] Ubuntu 7.10"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by Source4 on 2007-10-18
Hello, I am trying up update to 7.10 from 7.04.  And every time I try to do it I get the same message.

Error during update
A problem occured during the update. This is usually some sort of network problem, please check your network connection and retry.
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-security/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/feisty-security/Release.gpg) Connection failed [IP: 91.189.89.8 80]
Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg](http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg) Could not resolve 'wine.lowvoice.nl'
Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz](http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz) Could not resolve 'wine.lowvoice.nl'

I'm not sure if this is an port problem because I am on a campus line, or if it is something else.

Any help would be great!!

---

### Post by mrvertigo on 2007-10-18
if youve ever gotten through to update/upgrade before your probably ok, the ubuntu servers are fully loaded right now so they have been acting weird such as slow downloads and denying access, just wait till morning and you'll be fine most assuridly!

---

### Post by tonywhelan on 2007-10-18
> **Source4 said:**
> Hello, I am trying up update to 7.10 from 7.04.  And every time I try to do it I get the same message.

Error during update
A problem occured during the update. This is usually some sort of network problem, please check your network connection and retry.
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-security/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/feisty-security/Release.gpg) Connection failed [IP: 91.189.89.8 80]
Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg](http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg) Could not resolve 'wine.lowvoice.nl'
Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz](http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz) Could not resolve 'wine.lowvoice.nl'

I'm not sure if this is an port problem because I am on a campus line, or if it is something else.

Any help would be great!!

Ubuntu servers/mirrors all over the planet are probably very slow right now because everyone is upgrading and installing new software. My ISP's mirror is serving at a fraction of the normal speed, and I am also getting some errors or long delays trying to install things on my fresh new 7.10 build.

I would probably have been a better idea to wait a few days till things quieten doen, but I couldn't help myself ....

---

### Post by tonywhelan on 2007-10-18
It would probably have been a better idea to wait a few days till things quieten down, but I couldn't help myself .... :)

---

### Post by mrvertigo on 2007-10-19
lol i know the feeling thats why i update usually 2-3 days before the official launch and update a week after :P

---

### Post by ElSeeDee on 2007-10-19
Holy schniekies! I've been "Fetching the upgrades" since 10:00am (Pacific). It's 9:00om now and I'm still at 1177 of 1242. Whew! It's gonna be a long night!

---

### Post by mrvertigo on 2007-10-19
lol i know the feeling

---

### Post by mkeaneaz on 2007-10-19
at least you are downloading i am hanging all the time.

---

### Post by ElSeeDee on 2007-10-19
Are you sure you're hanging? Because I was "hung" at 1177 of 1242 for hours. I just waited it out.

---

### Post by Source4 on 2007-10-19
that's what I assumed it was, I just was so impatient! lol
I tried to download it as soon as I woke up!
I'm going to try again, RIGHT NOW!

---

### Post by jlachovsky on 2007-10-20
I keep getting this error when I try and upgrade:

Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg:](http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg:) Could not resolve 'wine.lowvoice.nl'
[http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_US.bz2:](http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_US.bz2:) Could not resolve 'wine.lowvoice.nl'
[http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz:](http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz:) Could not resolve 'wine.lowvoice.nl'


Any suggestions?

---

### Post by Source4 on 2007-10-23
I have let a couple days go by and I still get this message

Error

Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg](http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg) Could not resolve 'wine.lowvoice.nl'
Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_US.bz2](http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_US.bz2) Could not resolve 'wine.lowvoice.nl'
Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz](http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz) Could not resolve 'wine.lowvoice.nl'


What is going on?

:(

---

### Post by Source4 on 2007-10-23
Does 

 NO_PUBKEY 2EBC26B60C5A2783

mean anything?

---

### Post by Source4 on 2007-10-26
Now when I try to install the system I get the error message 

Getting upgrade prerequisites failed

The system was unable to get the prerequisites for the upgrade. The upgrade will abort now and restore the original system state.

Please report this as a bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bugreport.

this is starting to really frustrate me!!!

If ANYONE has any info on how to help me it would be AMAZING!!!!

---

### Post by louieb on 2007-10-26
Those repositories its having trouble with are 3rd party.  That is they are not official Ubuntu repositories.  Edit /etc/apt/sources.list and comment them out. (put a # at the start of their lines).

You can go to wine site after the upgrade and get the Gutsy repositories for wine.

---


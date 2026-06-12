---
title: "aMSN not working on 7.10"
date: 2007-10-26
forum: Installation &amp; Upgrades
---

### Post by Martin1 on 2007-10-26
I have just upgraded from Feisty Fawn to Gutsy Gibbon and when I tried to log onto aMSN it told me "This profile is being used by another aMSN session please use another one" I didn't have this problem last year when I upgraded from Edgy to Feisty, so does anybody have any ideas?

---

### Post by ubunter1 on 2007-10-26
ive the same problem,and then it went missing from my right notification bar,wonder how to fix this as well.

---

### Post by Martin1 on 2007-10-29
I have discoverd that it was settings for previous versions of Ubuntu still in my system after the upgrade that stopped aMSN among other things from working. 

Once I removed these old settings I have managed to get aMSM and nearly everything else working. 

I hope that helps you Ubunter1.

---

### Post by Selcal on 2007-10-29
so Pidgen is out of the question?  My msn account works fine with Pidgen.

---

### Post by Biggy on 2007-10-29
> **ubunter1 said:**
> ive the same problem,and then it went missing from my right notification bar,wonder how to fix this as well.

try this :

$ sudo mv /usr/bin/wish /usr/bin/wish-backup
$ sudo ln -s /usr/bin/wish8.4 /usr/bin/wish

$ sudo apt-get install tcl8.4-dev

work fine for me...

---

### Post by ubunter1 on 2007-10-29
thanks for the reply,when i tried to enter those commands in the terminal it came up as this- robert@robert-desktop:~$ $ sudo mv /usr/bin/wish /usr/bin/wish-backup
bash: $: command not found.

---

### Post by ubunter1 on 2007-10-29
i just tried it without the$ symbol:) it somewhat worked but gave me this--
robert@robert-desktop:~$ sudo mv /usr/bin/wish /usr/bin/wish-backup
[sudo] password for robert:
robert@robert-desktop:~$ sudo ln -s /usr/bin/wish8.4 /usr/bin/wish
robert@robert-desktop:~$ sudo apt-get install tcl8.4-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libc6-dev linux-libc-dev
Suggested packages:
  glibc-doc manpages-dev tcl8.4-doc
The following NEW packages will be installed:
  libc6-dev linux-libc-dev tcl8.4-dev
0 upgraded, 3 newly installed, 0 to remove and 2 not upgraded.
Need to get 0B/4721kB of archives.
After unpacking, 19.7MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Media change: please insert the disc labeled
 'Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)'
in the drive '/cdrom/' and press enter

---

### Post by Jored on 2007-10-30
I had pretty much the same experience as Ubunter1.

I recently upgraded to 7.10GG and Im still struggling with fonts, text sizes and various other upgrade problems.

When I click on the envelope icon to read messages in my Inbox, I get a message back that says:

Cant execute application : mozilla $url. Check preferences.

In my other PC running 7.04 FF I have the exact same preferences and never experienced this problem.

---

### Post by ubunter1 on 2007-10-30
> **Jored said:**
> I had pretty much the same experience as Ubunter1.

I recently upgraded to 7.10GG and Im still struggling with fonts, text sizes and various other upgrade problems.

When I click on the envelope icon to read messages in my Inbox, I get a message back that says:

Cant execute application : mozilla $url. Check preferences.

In my other PC running 7.04 FF I have the exact same preferences and never experienced this problem.

i know that for me to access my email from amsn i went to preferences and changed the mozilla url to firefox(which is the browser i run) and that worked.

but now none of it works no text shows up and no notification bar icon when running. i did a full install from scratch from fiesty so old versions shouldn't be a problem.hopefully we can fix this i like pidgin but it doesnt look like it has as many features as amsn,like the one  click to go to email.

im still getting the dcopserver error as well

---


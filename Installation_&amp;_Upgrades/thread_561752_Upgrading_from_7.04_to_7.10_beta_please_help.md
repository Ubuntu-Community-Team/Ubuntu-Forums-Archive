---
title: "Upgrading from 7.04 to 7.10 beta please help"
date: 2007-09-27
forum: Installation &amp; Upgrades
---

### Post by threndil on 2007-09-27
Hi there, I am new to ubuntu and linux and am a complete newbie. I am trying to upgrade from ubuntu 7.04 to 7.10 using the "update-manager -d" command but it keeps saying my system is up to date and nothing is coming up. If someone could help me on this that would be great.

---

### Post by pixels on 2007-09-27
I'm having an issue upgrading too. 

When it's in the middle of fetching after using the update-manager -d command, it stops and tells me it can't get three files from this site:

[http://wine.lowvoice.nl/](http://wine.lowvoice.nl/)

I have no idea what's going on - but I don't even have wine installed on my system - assuming that's what it means. I'm quite confused.

:confused:

---

### Post by greymarch on 2007-09-28
> **pixels said:**
> I'm having an issue upgrading too. 

When it's in the middle of fetching after using the update-manager -d command, it stops and tells me it can't get three files from this site:

[http://wine.lowvoice.nl/](http://wine.lowvoice.nl/)

I have no idea what's going on - but I don't even have wine installed on my system - assuming that's what it means. I'm quite confused.

:confused:

I am having the exact same problem when trying to upgrade to gutsy using update manager.  I will post something if I can find a solution.

---

### Post by pixels on 2007-09-28
> **greymarch said:**
> I am having the exact same problem when trying to upgrade to gutsy using update manager.  I will post something if I can find a solution.

Thanks :)

---

### Post by jbayone on 2007-10-01
I was having this problem too.  I just went to Synaptec and removed that third-party repository.

---

### Post by Linuxfriends on 2007-10-01
Hello,
I am a new Linux User... I just upgraded from 7.04 to 7.10 Beta.. Begin I got a couple
error messages.. but I followed the instruction (Download Install Instruction at same
web site) everything upgrade OS Ok.  The command during I installed:  update-manger -d , It prompted an error.. But after that I used command:  
sudo nano /var/lib/update-manager/meta-release
and then press Ctrl+ o and Ctr + x  ....
more commands by follow upgrade instruction.

Good Luck,[http://ubuntuforums.org/images/smilies/guitar.gif](http://ubuntuforums.org/images/smilies/guitar.gif)

---

### Post by pixels on 2007-10-08
> **jbayone said:**
> I was having this problem too.  I just went to Synaptec and removed that third-party repository.

I'd try that if I knew how.

---

### Post by william_nbg on 2007-10-08
try using the command:

sudo upgrade-manager -c -d

---


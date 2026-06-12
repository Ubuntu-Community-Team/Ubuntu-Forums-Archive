---
title: "update-manager not work"
date: 2006-11-28
forum: Installation &amp; Upgrades
---

### Post by carmelo on 2006-11-28
after upgrade (Dapper to Edgy Beta) update-manager not work.
The applet notify me about new upgrades availabe, click on the icon open update-manager.
I select install all upgrades, prompt for password and nothing happens.

With synaptic i have no problem.

I execute update-manager from the shell:
carmelo@Sirio:~$ update-manager
Introspect error: The name org.freedesktop.UpdateManager was not provided by any .service files
no listening object (The name org.freedesktop.UpdateManager was not provided by any .service files) 


Thanks.

---

### Post by bapoumba on 2006-11-28
Hi, are you running on an italian environment ? There is a [bug]("https://launchpad.net/products/update-manager/+bug/51419")  :/
For now, the use of synatpic or apt-get or aptitude is recommended

---

### Post by carmelo on 2006-11-28
Thank you,

I'll wait that Italian Ubuntu translators solve the problem.

---

### Post by armalite on 2006-11-30
Thank you for this thread, it's been a long ago I was wondering why this so weird problem...

---

### Post by pcivill on 2006-12-04
I am on the English version, not Italian.. I get the same error when I run /usr/bin/update-manager from a terminal. Then the gui launches sucessfully, however I have to prompt it to check. When I  try to run Update Manager from the System/Administration window nothing happens. Thank you for any help you can give!

---

### Post by bapoumba on 2006-12-04
@ pcivill : do you get the exact error message "Introspect error..." ?
Do you have an error message with **sudo apt-get update** or **sudo aptitude update** ?

---

### Post by pcivill on 2006-12-04
Thanks! Both of those work with no problems.

---

### Post by pcivill on 2006-12-04
Here is a copy/paste of the error. Thanks!

/usr/bin/update-manager
Introspect error: The name org.freedesktop.UpdateManager was not provided by any .service files
no listening object (The name org.freedesktop.UpdateManager was not provided by any .service files)

---

### Post by bapoumba on 2006-12-04
Welcome (did not do much).
Well, if you have all your Ubuntu on english locales (no italian ones) you should probably add this to the bug report.

---

### Post by OttifantSir on 2006-12-06
Well, haven't been using Linux long enough to be entirely comfortable with the Terminal, but I thought I'd give it a go as my Update Manager just hanged. So, I typed sudo apt-get update and got this:

Hent:1 [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) edgy Release.gpg [191B]
Ign [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) edgy/main Translation-no                      
Ign [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) edgy/restricted Translation-no                
Ign [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) edgy/universe Translation-no                  
Ign [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) edgy/multiverse Translation-no                
Hent:2 [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) edgy-updates Release.gpg [191B]            
Ign [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) edgy-updates/main Translation-no              
Ign [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) edgy-updates/restricted Translation-no        
Ign [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) edgy-updates/universe Translation-no          
Ign [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) edgy-updates/multiverse Translation-no        
Funnet [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) edgy Release                               
Funnet [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) edgy-updates Release
Hent:3 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-no
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-no
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-no
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Translation-no
Funnet [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release
Funnet [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) edgy/main Packages
Funnet [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) edgy/restricted Packages
Funnet [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) edgy/universe Packages
Funnet [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) edgy/multiverse Packages
Funnet [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) edgy/main Sources
Funnet [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) edgy/restricted Sources
Funnet [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) edgy/universe Sources
Funnet [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) edgy/multiverse Sources
Funnet [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) edgy-updates/main Packages
Funnet [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) edgy-updates/restricted Packages
Funnet [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) edgy-updates/universe Packages
Funnet [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) edgy-updates/multiverse Packages
Funnet [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) edgy-updates/main Sources
Funnet [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) edgy-updates/restricted Sources
Funnet [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) edgy-updates/universe Sources
Funnet [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) edgy-updates/multiverse Sources
Funnet [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages
Funnet [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages
Funnet [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages
Funnet [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Packages
Funnet [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources
Funnet [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources
Funnet [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources
Funnet [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Sources
Hentet 3B på 2s (1B/s)
Leser pakkelister ... Ferdig

I realise this is in Norwegian, so a few words to explain: Hent=Fetch, get, acquire. Hentet=past tense of hent. Funnet=past tense of Finn=Find. Leser=present tense of Lese=to read. Pakkelister=plural of pakkeliste=package list.

Now, for the question: Does this mean I actually updated anything? Update Manager said it were about to update evince for a DoS when parsing crafted PS files.

If it wasn't updated, will it be enough to add evince to the end of the the terminal command to update it?

---


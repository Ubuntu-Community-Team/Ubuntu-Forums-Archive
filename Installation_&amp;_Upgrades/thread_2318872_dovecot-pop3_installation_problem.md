---
title: "dovecot-pop3 installation problem"
date: 2016-03-30
forum: Installation &amp; Upgrades
---

### Post by Amine_TAGUI on 2016-03-30
Hello , i want to install this package but i got the following error : E: Unable to locate package dovecot-pop3I tried apt-get update and teh --fix-missing option in vein , i think i have to add resources to /etc/apt/sources.list ... ([http://www.linuxquestions.org/questions/linux-newbie-8/failed-to-start-dovecot-pop3-imap-server-880547/](http://www.linuxquestions.org/questions/linux-newbie-8/failed-to-start-dovecot-pop3-imap-server-880547/))
i added the following lines 
deb [http://xi.dovecot.fi/debian/](http://xi.dovecot.fi/debian/) stable-auto/dovecot-2.2 main

deb-src [http://xi.dovecot.fi/debian/](http://xi.dovecot.fi/debian/) stable-auto/dovecot-2.2 mainThat i found in this website [http://wiki.dovecot.org/PrebuiltBinaries](http://wiki.dovecot.org/PrebuiltBinaries)  , and when i do apt-get update i get this errors :
```
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease
  
Err [http://xi.dovecot.fi](http://xi.dovecot.fi) stable-auto/dovecot-2.2 InRelease
  
Err [http://xi.dovecot.fi](http://xi.dovecot.fi) stable-auto/dovecot-2.2 Release.gpg
  Could not resolve 'xi.dovecot.fi'
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg
  Could not resolve 'extras.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty InRelease
  
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates InRelease
  
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports InRelease
  
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security InRelease
  
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty Release.gpg
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates Release.gpg
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports Release.gpg
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security Release.gpg
  Could not resolve 'archive.ubuntu.com'
Reading package lists... Done
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/trusty/InRelease](http://archive.ubuntu.com/ubuntu/dists/trusty/InRelease)  


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/trusty-updates/InRelease](http://archive.ubuntu.com/ubuntu/dists/trusty-updates/InRelease)  


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/trusty-backports/InRelease](http://archive.ubuntu.com/ubuntu/dists/trusty-backports/InRelease)  


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/trusty-security/InRelease](http://archive.ubuntu.com/ubuntu/dists/trusty-security/InRelease)  


W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/trusty/InRelease](http://extras.ubuntu.com/ubuntu/dists/trusty/InRelease)  


W: Failed to fetch [http://xi.dovecot.fi/debian/dists/stable-auto/dovecot-2.2/InRelease](http://xi.dovecot.fi/debian/dists/stable-auto/dovecot-2.2/InRelease)  


W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/trusty/Release.gpg](http://extras.ubuntu.com/ubuntu/dists/trusty/Release.gpg)  Could not resolve 'extras.ubuntu.com'


W: Failed to fetch [http://xi.dovecot.fi/debian/dists/stable-auto/dovecot-2.2/Release.gpg](http://xi.dovecot.fi/debian/dists/stable-auto/dovecot-2.2/Release.gpg)  Could not resolve 'xi.dovecot.fi'


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/trusty/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/trusty/Release.gpg)  Could not resolve 'archive.ubuntu.com'


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/trusty-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/trusty-updates/Release.gpg)  Could not resolve 'archive.ubuntu.com'


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/trusty-backports/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/trusty-backports/Release.gpg)  Could not resolve 'archive.ubuntu.com'


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/trusty-security/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/trusty-security/Release.gpg)  Could not resolve 'archive.ubuntu.com'


W: Some index files failed to download. They have been ignored, or old ones used instead.
```


And umm ... i found this but i don't really know how it works [http://linuxappfinder.com/package/dovecot-pop3d](http://linuxappfinder.com/package/dovecot-pop3d)
-------------------------------------------------


P.S : i'm using 14.04.1 Ubuntu

---

### Post by QLee on 2016-03-30
You have followed the instructions on that page for installing to Debian, remove that source from your sources list and follow the instructions a bit further  down the page for Ubuntu. Dovecot is already in the Ubuntu repositories using the apt-get command they give should get you more success. Note: you will have to use sudo apt-get.

Did you have an Internet connection when you tried the update, it seems your system can't find the Ubuntu repositories either and your system at 14.04.1 isn't the latest version of Ubuntu 14.04 so it seems you haven't been upgrading your system either.

[edit] I won't be able to help you with dovecot itself, that's not the mail server I use. Someone else here likely will post if you have problems with dovecot once you get it installed.

---

### Post by Amine_TAGUI on 2016-03-30
Okay thanks i'll do that :),
Omg i remember disconnecting from the internet because i was following certains steps (I feel ashemed lol) ...
I had problems with the last ubuntu version that's why i use the current one that i have .
Umm just in case , what mail do you use ? And can you link me to a tutorial post or video ?! That can help me a lot :)

---

### Post by QLee on 2016-03-31
> **Amine_TAGUI said:**
> Okay thanks i'll do that :),
Omg i remember disconnecting from the internet because i was following certains steps (I feel ashemed lol) ...
I had problems with the last ubuntu version that's why i use the current one that i have .
Umm just in case , what mail do you use ? And can you link me to a tutorial post or video ?! That can help me a lot :)

No need to feel ashamed, simple mistakes happen to everyone and it is a learning opportunity, next time you see the problem you will figure it out quickly. Actually, in this case, it's a good thing your system didn't try to install that Debian stuff, it might have messed up your Ubuntu and you would have had to have managed to get it uninstalled before getting what you really want. 

By upgrade I meant the point release of 14.04 LTS not an upgrade to a different version, there may have been some security upgrades since 14.04.1, I also prefer to use LTS versions of Ubuntu. 

Here are some links to Ubuntu documentation for Dovecot, it looks fairly straightforward and lots of people looked at this thread so post any questions that you have if you run into difficulty.
 [edit] If so, it would probably be a good idea to either change the topic to something more specific to your question or post a new thread with that specific topic.

[https://help.ubuntu.com/lts/serverguide/dovecot-server.html](https://help.ubuntu.com/lts/serverguide/dovecot-server.html)
[https://help.ubuntu.com/community/Dovecot](https://help.ubuntu.com/community/Dovecot)

---


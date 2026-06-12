---
title: "likewise-open vs centrify express"
date: 2012-02-13
forum: Installation &amp; Upgrades
---

### Post by linux.girl on 2012-02-13
Hello everyone,

I am trying to figure out the best solution to add a linux desktop to a windows ad. Until today, I used likewise-open, but more and more people are telling me perhaps I should move to centrify express.

My question to this wonderful community is: does anyone here have experience with both (or heard of others with experience with both) and can tell me what are the general pros and cons of each one of them?

As always, thanks in advance!

linux.girl

---

### Post by JS207 on 2012-02-13
FWIW, there have been a few independent review that I found useful, here are some links
* [http://jeremyrnelson.tumblr.com/post/9553593398/integrating-linux-with-windows-active-directory](http://jeremyrnelson.tumblr.com/post/9553593398/integrating-linux-with-windows-active-directory)
* [http://ninjix.blogspot.com/2011/01/puppet-module-for-centrify-express.html](http://ninjix.blogspot.com/2011/01/puppet-module-for-centrify-express.html)
* [http://davidmburke.com/2010/09/16/linux-and-active-directory-round-2/](http://davidmburke.com/2010/09/16/linux-and-active-directory-round-2/)
I think the consensus has been that Centrify Express has been more stable. 
 
Also note that Likewise Software exited this business, and sold off Likewise Open to another vendor in asset sale, so it is no longer called Likewise Open, but something else. 
 
Good luck.

---

### Post by linux.girl on 2012-02-13
thanks for the tip, i didnt know likewise open was sold :-(

I am having my first try with centrify and so far, a few issues:

1 - on likewise, it is very easy to make the ad user admin on the local ubuntu machine. on centrify, still breaking my teeth to do. Following this tutorial here: [http://www.youtube.com/watch?v=JEDPHizGaF8&feature=player_embedded](http://www.youtube.com/watch?v=JEDPHizGaF8&feature=player_embedded) but it is not working because the command sudo adquery -A username is not working... :-(

2 - hostname...weird things happening...after i add the computer to the ad and logged in with the ad user, it changed the hostname (on the command prompt) from the name i gave to ubuntu...if i check /etc/hosts, it shows the name i gave...but the cmd prompt still shows otherwise...

I didnt have to do any of that with likewise, everything was intuitive...but still want to give centrify a try....does anyone have suggestions?

thanks!

---

### Post by linux.girl on 2012-02-13
ok, solved the admin problem...and the hostname solved itself. all of a  sudden i opened a new cmd prompt and the correct hostname appeared.


even though I am happy it fixed itself, i still need to understand why this happened so I can avoid it in other deployments.


any ideas why this happened?


thanks a lot!


linux.girl

---

### Post by sumana.annam on 2012-02-13
Here is another link which compares Centrify Express vs Likewise. Hope this helps.

[http://www.thevarguy.com/2010/07/23/active-directory-integration-centrify-express-vs-likewise/](http://www.thevarguy.com/2010/07/23/active-directory-integration-centrify-express-vs-likewise/)

---

### Post by sumana.annam on 2012-02-13
linux-girl:

I am not sure what exactly happened so I just tested this in my environment and do not see the behavior described. Few questions for you:

- Did a randomn name get assigned to this machine ?
- Is it a hostname of another machine in your environment ?
- Do your machines get IP Address via DHCP and register themselves in DNS ?

My only suspicion is that IPaddress of this current machine was earlier assigned to another host. I may be wrong but thats all I can guess at this point.

---

### Post by linux.girl on 2012-02-15
Hi Sumana,
 
Thank you for your reply. To answer your  questions, no random name was assigned to the machine, it is a unique  hostname and machine does get the IP via DHCP and DNS.
 
As I  explained in post, it solved itself, but because I want to deploy this  on several machines, I wanted to make sure I understand why this  happened. It is not critical to the process, but still.
 
Anyways, thanks a lot for your help!


linux.girl

---


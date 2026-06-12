---
title: "Mail problems with new releases"
date: 2011-12-20
forum: Installation &amp; Upgrades
---

### Post by ubix on 2011-12-20
Does anybody know how to install Evolution 3.2.1. on Ubuntu 10.10 (Maverick)?

Beside mutilated capabilities of the new GUI on Ubuntu, one of my other reasons and deciding factors not to upgrade to the Unity based newer releases are major problems in maintaining mail compatibility. Namely with the help of Evolution I managed to keep almost 20 years old mail boxes accessible to this day. I even fixed the problem with my address books, which had been losing my contacts in all Ubuntu releases after 10.10 Maverick Meerkat.

The culprit are not the new Unity based Ubuntu releases, but rather the upgrade of Evolution {{ version: 2.30.3-1 ubuntu7.3 (evolution) }} which was last installed on Ubuntu 10.10 (Maverick Meerkat) to Evolution {{ version: 3.2.1 }} which comes with newest Ubuntu releases.

I would like to manually upgrade Evolution  2.30.3-1 on my Ubuntu 10.10 (Maverick) to Evolution 3.2.1. Simply removing and re-installing Evolution in Ubuntu SW Centre does not work. I tried to download and install {{ evolution_3.2.1-0ubuntu1.debian.tar.gz }} and {{ evolution_3.2.1.orig.tar.bz2 }}, but both of these options proved to be useless. The first of the two has no source files in the tarball, but the second has no INSTALL* file and not uprising is lacking any reference to Ubuntu.

If I can install Evolution 3.2.1. on Ubuntu 10.10 (Maverick), I may be able to solve the email and addressbook compatibility problems between Evolution  2.30.3-1 and Evolution 3.2.1, since I was able recovered my contacts in my VirtualBox on Ubuntu 11.10 (Oneiric Ocelot).

---

### Post by ubix on 2011-12-20
I was hoping for someone to tell me what exactly should be the release/version number parameters in the command like:
   ```
sudo apt-get install evolution
```

perhaps something like:
   ```
sudo apt-get install evolution_3.2.1
```

Note the last command fails, since the release number or its format is incorrect.

---

### Post by ubix on 2011-12-21
I am disappointed long time Evolution companion is left out in dry! Are you guys all using Thunderbird mail? Let me then try another related issues. 

(1) Has anybody been able to import Evolution mail into Thunderbird. 

(2) What calendar is *»Ubuntu endorsed«* or perhaps what are you suggesting we use instead of Evolution Calendar.

---

### Post by n08rak35 on 2012-01-07
I too am trying to solve Evolution problems. I have happily used Evolution for a couple of years, but since upgrading to 11.10, I have not been able to even open Evolution.

I may try un-install/re-install, but would love to hear of others' experiences.

---

### Post by cl17g on 2012-01-09
> **n08rak35 said:**
> I too am trying to solve Evolution problems. I have happily used Evolution for a couple of years, but since upgrading to 11.10, I have not been able to even open Evolution.
 
I may try un-install/re-install, but would love to hear of others' experiences.


I had a bad experience after upgrading to Ubuntu 11.10 and Evolution 3.2.1. No way of having Evolution  working properly from behind a proxy. At home it works fine. I have no idea of what the problem can be. The old version of Evolution used to work well even from behind the proxy. ](*,)

---

### Post by ubix on 2012-01-17
> **n08rak35 said:**
> I too am trying to solve Evolution problems. I have happily used Evolution for a couple of years, but since upgrading to 11.10, I have not been able to even open Evolution.

I may try un-install/re-install, but would love to hear of others' experiences.It looks you are running *»GNOME Classic«*. Trying to start *»Evolution«* from *»Applications->Internet«* the menu there does not start the initial setup. However, you should be able start Evolution from terminal (just open the terminal and type in **evolution** /all lowercase/ and press enter).

If you manage to recover all your mail and address books, and decide you wish to continue to use Evolution rather than switching to Thunderbird, you should fix your *»Applications->Internet«* menu to include ***»Evolution & Calendar«*** and remove the current Evolution option that is useless.

If you do not know how to fix your menus, and you run *»GNOME Classic«* I can help you with this.

---

### Post by cl17g on 2012-01-17
> **ubix said:**
> It looks you are running *»GNOME Classic«*. Trying to start *»Evolution«* from *»Applications->Internet«* the menu there does not start the initial setup. However, you should be able start Evolution from terminal (just open the terminal and type in **evolution** /all lowercase/ and press enter).

If you manage to recover all your mail and address books, and decide you wish to continue to use Evolution rather than switching to Thunderbird, you should fix your *»Applications->Internet«* menu to include ***»Evolution & Calendar«*** and remove the current Evolution option that is useless.

If you do not know how to fix your menus, and you run *»GNOME Classic«* I can help you with this.

I am using Gnome classic too, and I can open Evolution 3.2.1. The problem in my case is that it hangs when I work from behind a proxy, despite the fact that (apparently) I have configured the proxy as I used to do with the previous versions of Ubuntu & Evolution. Maybe the problem is more with Ubuntu 11.10 than with Evolution 3.2.1.

Btw, does anyone know how to install extra-dictionaries in Evolution 3.2.1?

Thank you.

---

### Post by ubix on 2012-01-17
Try to configure proxy not to use the same proxy for all protocols. For instance select HTTP proxy only. I remember I had Evolution issues with proxy on my FW even in Maverick or earlier and had to disable it as I suggested to you above. BTW how did you configure proxy in Ubuntu 11.10, the configuration program which used to be *»gnome-network-properties«* is no longer available?

---

### Post by cl17g on 2012-01-18
> **ubix said:**
> Try to configure proxy not to use the same proxy for all protocols. For instance select HTTP proxy only. I remember I had Evolution issues with proxy on my FW even in Maverick or earlier and had to disable it as I suggested to you above. BTW how did you configure proxy in Ubuntu 11.10, the configuration program which used to be *»gnome-network-properties«* is no longer available?

I will try and let you know! Thank you.

To configure the proxy in Ubuntu 11.10, go in the "System Settings" and under "Network" you will find the proxy settings. However, i tried also with the old-fashioned way of editing the /etc/bash.bashrc file by adding the lines 

export http_proxy=”<address of the proxy>”
export https_proxy=”<address of the proxy>”
export ftp_proxy=”<address of the proxy>”

I hope that this method is still valid!

---

### Post by cl17g on 2012-01-18
Unfortunately, it didn't work! Evolution still hangs on "Fetching Mail"...

BTW, should someone be interested in the issue, I found how to add dictionaries to Evolution. I could not find national dictionaries in the software center, but using

sudo apt-get install aspell-XX
[FONT=monospace]
[/FONT]with XX the language abbreviation (in capital letters) I solved the problem.

---

### Post by ubix on 2012-01-18
> **cl17g said:**
> ... I hope that this method is still valid!Thanks for proxy info. With Evolution, I suggest in **"Evolution -> Preferences -> Edit -> Receiving Email -> Use secure connection"** you try to change the ***»SSL encryption«*** to ***»TLS encryption«***. Perhaps they've changed the default to SSL now. It used to work with TLS in the past.

---

### Post by cl17g on 2012-01-18
> **ubix said:**
> Thanks for proxy info. With Evolution, I suggest in **"Evolution -> Preferences -> Edit -> Receiving Email -> Use secure connection"** you try to change the ***»SSL encryption«*** to ***»TLS encryption«***. Perhaps they've changed the default to SSL now. It used to work with TLS in the past.
In fact, SSL is what I need! And trying to change this makes no difference.

---

### Post by ubix on 2012-01-18
> **cl17g said:**
> In fact, SSL is what I need! And trying to change this makes no difference.Actually, it was silly of me to suggest it would make a difference. It would make more sense to test ***»no encryption«***, however for that you'd have to arrange with your provider to allow pulling mail without encryption. Some mail servers are user configurable in this respect.
   
I do think that your proxy's SSL may be screwing up. I know, I had had this problem until I configured my proxy ***»not to use the same proxy for all protocols«***.  Unfortunately this option is not there anymore. 

I have no idea whether exporting proxy system variables from bashrc works. You should be able to tell this by testing. I think you'd be much better off asking these questions in either Network or perhaps Security threads. Nevertheless, I believe that not using encryption temporarily will solve your most pressing problem until you find a satisfactory solution.

Perhaps all you need to do is make sure your proxy is using the same SSL version (usually the latest "SSL_v3").

---

### Post by cl17g on 2012-01-19
Thank you for your advice. In fact, everything (the browser, skype, apt-get, ...) seems to work properly, except Evolution so I think the proxy should be configured correctly. I'll try to understand what changed since my previous release of Unbuntu/Evolution.

---

### Post by ubix on 2012-01-19
I feel silly responding, since I really have nothing concrete, the whole ordeal is only very familiar  to me, and I do see some differences between your scenario and mine. First let me reiterate I also believe proxy is configured correctly, however, due to the ever more evident lack of on-line support for some products, like IPCop for instance, there is a chance it may not have been properly updated with the latest "SSL_v3" (perhaps reinstalling latest release of your "router/security server" would solve all your problems). Fear that this would not solve anything, and that in future it would get only worse, forced me to kick my Open Systems FW out of the picture (to my dismay Open Systems just ain't reliable any more). 

I am almost certain that Evolution mail's SSL has a conflict with proxy's SSL. You confirmed that by running mail without any problems without proxy. In fact fetching mail with Evolution doesn't need to be proxied, since Evolution utilizes local, in your case, Ubuntu OpenSSL server. I can confirm that setting up proxy ***»not using the same proxy for all protocols«*** in Ubuntu 10.10 does not set HTTPS and FTP protocols. Though there is no mention of mail in proxy configuration, this may force Evolution to talk to proxy SSL server (which I suspect is out of date, hence causing the Evolution to hang).

Good luck

---

### Post by ChrisNZ on 2012-01-24
Hi Guys

I too have just Upgraded the Desktop Home system as I did the "old" laptop and finding some "quirky" things with my fav old email software - Evo! :(
The install told me that i needed to import/transfer all my email to the 'mbox' system before I could start it. So presuming that it was a new storage requirement I did so.

Now I have duplicate folders - (some Historic data/emails) and very slow getting emails, errors in sending them, although my Contacts seem to stay intact (whew)!

So i'm watchng this thread to see what the issues are and if I can find a fix or it resolves itself with updates and fixes in due time??

If you come across this post and can see what I'm facing or how to "complete the mail merge"? then please post.

Cheers from NZ

---


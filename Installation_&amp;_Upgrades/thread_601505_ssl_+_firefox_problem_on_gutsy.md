---
title: "ssl + firefox problem on gutsy"
date: 2007-11-03
forum: Installation &amp; Upgrades
---

### Post by damageinc on 2007-11-03
There's something wrong with Gutsy that prevents me from accessing ssl websites through Firefox. I was using Feisty and chose to upgrade to Gutsy via the update manager. After the update was finished I immediately couldn't access any ssl sites. I rebooted and updated again to no avail. 

I then managed to get hold of the ISO image and burned it to cd. After I finished installing Gutsy, it still didn't work. I then installed Feisty again, and then ssl worked. I booted off the Gutsy CD and tried to browse using it as a Live CD and it failed too.

I'm sitting on an ADSL connection that is shared by two computers, one XP and the other mine. The XP's machine's ssl has continued working. I typed about:config in firefox and enabled all unchecked ssl settings on the Gutsy Live CD to no effect.

Is there something setting somewhere that I could check that would tell me what's wrong?

My configuration:
Wired LAN -> ADSL -> Internet
Netgear Switch/Router 10/100
Using Live CD so it's using the dhcp

---

### Post by ttthebear on 2007-11-03
I am having a similar problem.  I am able to view https sites but not able to download anything from an https site.

I tried firefox, opera and text based lynx.  So I know it is not a browser issue.

I did notice that in lynx I get this error message.

SSL error:no issuer was found-Continue? (y) 

I also notice that with firefox I get the following symptoms:

Click the install now link.  Nothing happens for about 10 minutes.  then it pops up the install now box.  Then it goes to the add-ons dialog box and does nothing

I can download files from other sites using http.

In particular I am trying to download firefox extensions from 

[https://addons.mozilla.org](https://addons.mozilla.org)

---

### Post by ttthebear on 2007-11-03
Found out a little more after using wget to try and download.

ERROR: Certificate verification error for addons.mozilla.org: self signed certificate in certificate chain
To connect to addons.mozilla.org insecurely, use `--no-check-certificate'.
Unable to establish SSL connection.

I checked the cert from my Mac  it appears to be from XRamp and valid

---

### Post by viniciusandre on 2007-12-25
Same problem as me...

Please, let me us know if you find out what's happening.
It's horrible to stay without the firefox extensions... :(

Thanks!

---

### Post by niceguy123 on 2007-12-28
Worse here.

Installed Gutsy and now I can't access the internet at all. (I'm writing from my notebook).

Any help would be appreciated.

---

### Post by moux_pl on 2008-02-23
I had the same problem with Lodge stayonline.net service. I just couldn't register in their server in order to browse the Internet. You have to go to their welcome site first so server knows your MAC and after that you can browse the internet. 

I was getting similar exception in lynx: SSL no issuer found. 

After digging a bit from windows :( on a another laptop i found some tip. 

 echo 0 > /proc/sys/net/ipv4/tcp_window_scaling 

I tried few options there but this one was necessary for Gutsy to work with stayonline. 


Hope it will help anybody who will decide to use Gutsy in hotels. 


Good luck.

---


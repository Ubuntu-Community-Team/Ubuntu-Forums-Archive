---
title: "Can't Upgrade"
date: 2008-11-29
forum: Installation &amp; Upgrades
---

### Post by dude1234 on 2008-11-29
hi guys

I have ubuntu 6.10 installed on my spare PC. Hadn't used it for about 12 months. It still works fine (email, web, etc) but I can't get the updates to download. Also I can't get it to upgrade to the latest version either. The update manager seems to do the right thing at first but then it gives error messages - the server not responding, authentication, blah, blah. It's not my internet connection because I'm on the internet right now! There are 172 updates. It seems a better idea to upgrade first.

thanks for help

---

### Post by abn91c on 2008-11-29
try changing repositories servers, like to the USA servers. Then you may have to upgrade to 7.xx first then 8.xx
the ubuntu website has the instructions on how to upgrade
also do sudo apt-get check, do  whatever it tells you to do if anything, then sudo apt-get update, followed by sudo apt-get dist-upgrade

---

### Post by markbuntu on 2008-11-29
I think 6.10 is finished, as in no longer supported. Is it an LTS? If not it only has 18 month support lifespan.

Maybe you can find some mirror that has the last updates. You really need the last updates to upgrade. Anyway, most upgrades fail miserably so you might want to just save yourself the headache and do a nice clean install of something new, like 8.04.

Try the MIT mirror, I don't think they clean it out, just add stuff.

They still have the dapper drake mirror, is that 6.10?

[https://launchpad.net/ubuntu/+mirror/ubuntu.media.mit.edu-archive](https://launchpad.net/ubuntu/+mirror/ubuntu.media.mit.edu-archive)

---

### Post by dude1234 on 2008-11-30
thanks guys

I've been trolling around myself and found out about the LTS versions - and the other versions like 6.10 having a short life span. Everything still appears to work on 6.10 mind you.

I think the best thing for me is to burn a new CD to upgrade to 8.04. Pity I'll have to set up my ISP protocols again.

Out of interest though. How do I change the location where my updater goes looking for the updates?

cheers

---

### Post by abn91c on 2008-12-04
> **dude1234 said:**
> thanks guys

I've been trolling around myself and found out about the LTS versions - and the other versions like 6.10 having a short life span. Everything still appears to work on 6.10 mind you.

I think the best thing for me is to burn a new CD to upgrade to 8.04. Pity I'll have to set up my ISP protocols again.

Out of interest though. How do I change the location where my updater goes looking for the updates?

cheers

to change servers go to the adept manager then  in the menu bar look for repositories, there change to a different server like the USA servers, click ok then follow the default directions next.

---


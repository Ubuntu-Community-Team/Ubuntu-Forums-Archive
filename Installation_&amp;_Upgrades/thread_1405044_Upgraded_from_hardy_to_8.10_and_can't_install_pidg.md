---
title: "Upgraded from hardy to 8.10 and can't install pidgin"
date: 2010-02-12
forum: Installation &amp; Upgrades
---

### Post by amsterdamharu on 2010-02-12
Upgraded from Hardy to 8.10 and noticed pidgin is missing so go to synaptic and try to install it but get the follwoing message:> 
pidgin:
  Depends: pidgin-data (<1:2.5.2-z) but 1:2.6.5-0ubuntu1~pidgin3.8.04 is to be installed
 Depends: libpurple0 but it is not going to be installed

Enabled pidgin (3rd party) repository, refreshed and tried again but get this error:
> pidgin:
 Depends: libpurple0 but it is not going to be installed
 Depends: perlapi-5.8.8  but it is not installable
 Recommends: pidgin-libnotify but it is not going to be installed
Everything is checked: main universe, restricted and multiverse. 
purlapi is installed and re installed but keep getting the error:
[http://packages.ubuntu.com/hardy/perlapi-5.8.8](http://packages.ubuntu.com/hardy/perlapi-5.8.8)

I got the latest pidgin in Hardy because the one from from ubuntu didn't work half the time and could not connect to Yahoo or QQ so it was for 90% useless. Getting pidgin from pidgin worked on Hardy and I am not sure why the upgrade removed it and why I am not able to put it back.

---

### Post by tommcd on 2010-02-12
Ubuntu 8.10 will reach end of life (EOF) in April 2010.
[http://www.ubuntugeek.com/ubuntu-version-names-and-end-of-life-details.html](http://www.ubuntugeek.com/ubuntu-version-names-and-end-of-life-details.html)
 I really don't think it would be very productive to be wasting time with this for an OS that only has 2 months of support left. Your best bet to solve this quickly would be to do a clean install of Ubuntu 9.10. Pidgin is present in the 9.10 repos. It will also be a newer version of Pidgin than what would be available in 8.10.

---

### Post by amsterdamharu on 2010-02-12
Thank you for your reply.

I had to update my lts 8.04 because the anjuta package in there was ancient, will revert back to 8.04 and forget about Anjuta on this desktop and try it on the Lucid laptop.

---


---
title: "Dapper to Edgy Update Troubles"
date: 2007-02-28
forum: Installation &amp; Upgrades
---

### Post by Willorbill1 on 2007-02-28
[FONT="Arial Black"][/FONT] I am using the so called offical update (**gksu "update-manager -c"**) and then clicking on the button and all goes well and it says i completed the fetching, but at the same time an error window pops up saying: **Failed to fetch [http://theli.free.fr/packages/dists/dapper/listen/binary-i386/Packages.gz](http://theli.free.fr/packages/dists/dapper/listen/binary-i386/Packages.gz) 301 Moved Permanently**
I included a screenshot of what happens for further deatil. I dont even use Listen, just that one time, but i dint do anything, i think... 

Does anyone have this problem also, or even better, know what to do??

---

### Post by Kateikyoushi on 2007-02-28
I would comment the line so it will be ignored by adding a # to the beginning of it.
The site moved and now the repo migt be down. If you do not need it at all remove it completely.

---

### Post by Willorbill1 on 2007-02-28
ok thank im not really sure what that means, as u can tell i am a newb, but i will try it

Ok i dont think i did the right thing but heres the story, i figured the best way to get rid of the binary or whatever the heck it was, was to uninstall Listen, unfoutunetly i am still runnung into the problem _Could you help me out in a more detailed way plz????_

---

### Post by Kateikyoushi on 2007-02-28
I am sorry for the lack of information in my previous post.

You need to edit your sources.list and remove or comment that line so it will be ignored. To do so copy the next line to the terminal.

```
gksudo gedit /etc/apt/sources.list
```

Put a # infront of the line whic gives the error or delete it if you do not need it anymore.

Save and try to update then upgrade.

---

### Post by Willorbill1 on 2007-03-01
Wooow, sorry for the total brain fart. That is embarrasing, but at least i learn and Mucho Gacas for the help.:oops:

---


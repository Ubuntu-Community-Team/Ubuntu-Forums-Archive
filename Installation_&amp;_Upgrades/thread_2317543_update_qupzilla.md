---
title: "update qupzilla"
date: 2016-03-17
forum: Installation &amp; Upgrades
---

### Post by rico6 on 2016-03-17
Hello,
I just installed qupzilla. When I open Qupzilla I get a notification that tells me there is an update available but there is no place where I could downloads this update. I tried sudo apt-get update && sudo apt-get upgrade but it has no result. Could somebody tells me how I could downloads the update?

---

### Post by v3.xx on 2016-03-17
How did you install Qupzilla, from what source?

---

### Post by QDR06VV9 on 2016-03-17
There is also a PPA you can add to stay current.
[URL="https://launchpad.net/~nowrep/+archive/ubuntu/qupzilla"]https://launchpad.net/~nowrep/+archive/ubuntu/qupzilla

From the maintainer
[http://blog.qupzilla.com/2011/12/qupzilla-gets-ppa.html](http://blog.qupzilla.com/2011/12/qupzilla-gets-ppa.html)
[/URL]

---

### Post by RobGoss on 2016-03-17
[FONT=Helvetica Neue][COLOR=#333333]You can uninstall it then run the following command from your terminal[/COLOR][/FONT]

```



[COLOR=#333333][FONT=Monaco]sudo add-apt-repository -y ppa:nowrep/qupzilla
[/FONT][/COLOR]
sudo apt-get update&#8203;

[COLOR=#333333][FONT=Monaco]sudo apt-get install qupzilla[/FONT][/COLOR]
```

---

### Post by rico6 on 2016-03-18
Thank you for help. First I had installed qupzilla using the ubuntu software database. Now I have ad the PPA and I runned sudo apt-get update && sudo apt-get upgrade. Now I have the newest version.

---

### Post by RobGoss on 2016-03-18
Glad to hear you have everything working, if all is well would you mind marking this thread as solved. Thanks so much.

---


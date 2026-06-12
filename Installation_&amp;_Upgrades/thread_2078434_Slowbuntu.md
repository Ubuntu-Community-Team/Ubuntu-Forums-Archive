---
title: "Slowbuntu"
date: 2012-10-31
forum: Installation &amp; Upgrades
---

### Post by birdfoot on 2012-10-31
my computer is running 12.04. It takes a loooong time to restart and im keep getting notifications that Ubuntu couldn't download from the repositories. I want to reinstall the whole system but there are a lot of programs with setups that took a long time. Is there another option for me? Possibly to upgrade in some special way so that it fixes the problems I'm experiencing?

also, once i upgrade (or totally reinstall the system), what is the best way to speed up the boot time to as short as possible?

---

### Post by Bucky Ball on 2012-10-31
Have you installed any third-party repositories and then it became slower? I wouldn't think about reinstalling/upgrading just yet. May be a minor glitch (and you may face major ones with a 3 week old release).

You shouldn't need to speed up the boot time on a healthy install. There's not a lot you can do in Linux anyhow. You could try switching off services that boot with your machine. I'm using Xubuntu and it's Setting>Sessions & Startup. In Ubuntu should be in settings somewhere. Have a look there now and see if that is your problem. Because you are getting the repo error I'd say more likely related to that and that should be fixable.

You obviously have a problem since install if you have been experiencing this since then.

Could you also post your sources.list by opening a terminal and:

```
nano /etc/apt/sources.list
```Post the output back here, please.

---

### Post by birdfoot on 2012-10-31
> **Bucky Ball said:**
> Have you installed any third party repositories and then it became slower?

Yes, and I'm not sure.

Thanks for your reply.

---

### Post by birdfoot on 2012-10-31
> **Bucky Ball said:**
> Have you installed any third-party repositories and then it became slower? I wouldn't think about reinstalling/upgrading just yet. May be a minor glitch (and you may face major ones with a 3 week old release).

You shouldn't need to speed up the boot time on a healthy install. There's not a lot you can do in Linux anyhow. You could try switching of services that boot with your machine. I'm using Xubuntu and it's Setting>Sessions & Startup. In Ubuntu should be in settings somewhere. Have a look there now and see if that is your problem. Because you are getting the repo error I'd say more likely related to that and that should be fixable.

You obviously have a problem since install if you have been experiencing this since then.

Could you also post your sources.list by opening a terminal and:

```
nano /etc/apt/sources.list
```Post the output back here, please.

[http://static.inky.ws/image/3345/image.jpg](http://static.inky.ws/image/3345/image.jpg)

---

### Post by Bucky Ball on 2012-10-31
Open Software Sources (you can get there through Update Manager and 'Settings' button at bottom left) and untick the redshift-ppa and the torproject.org entries, all of them. Try an update and report any errors. If you're not getting any, open a terminal and:

```
sudo apt-get upgrade
```

That will get apps and software up to date for your release, not upgrade you to the next one.

PS: The link you provided is not the output of 'nano /etc/apt/sources.list' I requested but does provide some relevant info anyhow. ;)

---


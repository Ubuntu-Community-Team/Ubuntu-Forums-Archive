---
title: "Cannot install anything"
date: 2011-10-14
forum: Installation &amp; Upgrades
---

### Post by kyBorg on 2011-10-14
I just installed Kubuntu 11.10 on my laptop and after installing Firefox I cannot install anything else. I get this message in Muon if I want to install f.e. GIMP:
"It looks like an other Software manager is already running. Close other software managers to install or remove softwares." (translated from hungarian, I am not sure that this is the message in english)
What can I do? Please help!

---

### Post by matt_symes on 2011-10-14
Hi

Open a terminal and type

```
sudo lsof /var/lib/dpkg/lock
```

Enter your password. It will not be echoed to the screen.

Post the results back here.

Kind regards

---

### Post by kyBorg on 2011-10-14
I typed the code and my password, then after 1-2 seconds of waiting the username@computer:~$ came back but nothing else happened. After that I tried to install the GIMP but had the same error..:S

---

### Post by matt_symes on 2011-10-14
Hi

That's odd. Open a terminal and type

```
sudo apt-get update
```

Copy and paste the results from the terminal back into your next post.

Kind regards

---

### Post by kyBorg on 2011-10-14
Hi

I tried to update too: then it finds lots of updates but ignores them, and after that I get this:

```
W: Failed to fetch http://ppa.launchpad.net/ferramroberto/linuxfreedomlucid/ubuntu/dists/oneiric/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/ferramroberto/linuxfreedomlucid/ubuntu/dists/oneiric/main/binary-i386/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/oneiric/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/oneiric/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

Thanks for the help and the fast answers anyway. :)

---

### Post by kyBorg on 2011-10-14
This 4 message is probably because I tried to install GIMP and update Firefox from PPA with Konsole. Before that I only got the Found and Ignored messages.

---

### Post by matt_symes on 2011-10-14
Hi

> **kyBorg said:**
> Hi

I tried to update too: then it finds lots of updates but ignores them, and after that I get this:

```
W: Failed to fetch http://ppa.launchpad.net/ferramroberto/linuxfreedomlucid/ubuntu/dists/oneiric/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/ferramroberto/linuxfreedomlucid/ubuntu/dists/oneiric/main/binary-i386/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/oneiric/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/oneiric/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

```Thanks for the help and the fast answers anyway. :)

The above locations for Oneric do not exist on ppa.launchppad.net. If you open  [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/) in a browser you will not see an entry for Oneric.

You need to remove them from your /etc/apt/sources.list file or from /etc/apt/sources.list.d/ directory.

Kind regards

---

### Post by kyBorg on 2011-10-14
The main source of softwares were set to the hungarian server... now  I've set it to the main server and tried to update again. Same error  than before. But I tried sudo apt-get upgrade and it downloads something now... It didnt work before, so I hope :)

---

### Post by kyBorg on 2011-10-14
Update installed, notebook rebooted, problem solved :) Thanks for the help :)

---


---
title: "apt-check producing empty output"
date: 2021-05-03
forum: Installation &amp; Upgrades
---

### Post by bkline on 2021-05-03
I have cron jobs on a number of Ubuntu servers (some 18.04 LTS and some 20.04 LTS) which launch ```
/usr/lib/update-notifier/apt-check --human-readable
``` and if the string [FONT=Courier New]"\n0 of these updates are security updates"[/FONT] does not appear in the output then an email message is sent to let me know there are security updates which can be installed for the server. Yesterday and today those scripts were broken, because all of a sudden [FONT=Courier New]apt-check --human-readable[/FONT] produces output which consists solely of a single newline character. This change in behavior of that script is probably related to the fact that at the same time the motd output shown at login started showing an empty hole where a message enumerating how many updates were available (even if there none) used to be. Anyone else seen this? I'm inclined to rule out accidental misconfiguration on the servers, as it happened at the same time on completely independent Ubuntu servers on a variety of hosting setups (including one physical server a few feet away from where I'm sitting). This is what the output used to look like

```
0 updates can be installed immediately.
0 of these updates are security updates.
```

My web searching for the problem has turned up nothing.

---

### Post by Xian on 2021-05-04
Until formally squashed new update-notifier from this PPA will resolve the issue:

[https://launchpad.net/~lamoura/+archive/ubuntu/update-notifier-test-ppa/](https://launchpad.net/~lamoura/+archive/ubuntu/update-notifier-test-ppa/)

```
/usr/lib/update-notifier/apt-check --human-readable
0 updates can be installed immediately.
0 of these updates are security updates.
```

---

### Post by bkline on 2021-05-04
Thanks, Xian.

---


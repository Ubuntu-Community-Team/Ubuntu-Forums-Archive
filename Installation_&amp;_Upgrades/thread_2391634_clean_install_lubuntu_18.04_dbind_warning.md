---
title: "clean install lubuntu 18.04 dbind warning"
date: 2018-05-11
forum: Installation &amp; Upgrades
---

### Post by missmoondog on 2018-05-11
figure this is the best section to post this as it's a direct result of upgrading from 16.04 to 18.04.

i get these errors on all 5 of my clean lubuntu 18.04 installations when installing or uninstalling anything using synaptic:

1567 dbind warning error retrieving accessibility bus address: org.freedesktop

1565 dbind warning error retrieving accessibility bus address: org.freedesktop

doesn't seem to have any effect on how they boot up or run, but have issue when suspending or shutting down sometimes. the screen will go dark but nothing happens and if i move mouse or hit escape, the logout session box comes up displaying that error at bottom and only thing i can do is hold power button in until machine shuts off.

any one have any ideas on what's happening and how to fix this?

thank you

---

### Post by cruzer001 on 2018-05-12
Possibility installing "at-spi2-core" would remove the warning.

[https://github.com/NixOS/nixpkgs/issues/16327](https://github.com/NixOS/nixpkgs/issues/16327)

---

### Post by missmoondog on 2018-05-13
thank you, cruzer

yeah, i saw that in one of my searches and tried it. didn't fix issue. i've now been on a couple other computers that i've upgraded and see that every one of them has a different number in front of the beginning of error message. the message actually starts out saying dpkg preconfig. i had originally thought it was the same dpkg preconfig number on all of them, but it's not, so this will probably be very difficult to pinpoint.

also have noticed that end of installing anything it says frontend warning, or something  like that. only have 1 computer that i ever use suspend on and it works 99% of the time. usually turn any of the other computers off immediately after use which is when i'm done hanging out in basement.

as i said, this issue doesn't effect how any of the computers start up or run, so not going to pull my hair out trying to figure this out, but if anyone has any other suggestions, please feel free to post them. :)

thank you

---

### Post by missmoondog on 2018-05-14
hmm? installing that did seem to fix the issue on this machine which is the one i was on when i originally posted this.

guess i will try it on other machines as at least that package didn't install a ton of other stuff. :)

---

### Post by missmoondog on 2018-05-20
have been on several other computers exhibiting this same behavior although every one has a different number preceding the dbind warning. all no longer show that message when installing or uninstalling anything. marking as solved.

thank you, cruzer :)

---

### Post by hackerb92 on 2018-10-21
Cruzer is correct, but you won't notice the change immediately unless you do this:

```
[INDENT]sudo apt install at-spi2-core
systemctl --user  daemon-reload
systemctl --user restart  at-spi-dbus-bus
[/INDENT]

```[INDENT]
[/INDENT]

---


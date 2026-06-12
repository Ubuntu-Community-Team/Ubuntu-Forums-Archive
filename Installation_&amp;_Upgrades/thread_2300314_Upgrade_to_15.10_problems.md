---
title: "Upgrade to 15.10 problems"
date: 2015-10-25
forum: Installation &amp; Upgrades
---

### Post by dunbrokin on 2015-10-25
I have just upgraded to 15.10 and one of my User Accounts has become corrupted and wont allow me to log in. Fortunately, I have another User Account which also has Admin rights and that one is working properly. I can access the Home folder for User Account 1 (UA1) via sudo nautilus on UA2. I did get in very early on after the upgrade but there was no unity or top bar. I noticed this in the folder for UA1 called .xsessionerrors. How can I reconstruct or uncorrupt UA1?

```
openConnection: connect: No such file or directory
cannot connect to brltty at :0
upstart: no-pinentry-gnome3 main process (2901) terminated with status 1
upstart: upstart-event-bridge main process (2935) terminated with status 1
upstart: upstart-event-bridge main process ended, respawning
upstart: upstart-event-bridge main process (2956) terminated with status 1
upstart: upstart-event-bridge main process ended, respawning
upstart: upstart-event-bridge main process (2957) terminated with status 1
upstart: upstart-event-bridge main process ended, respawning
upstart: upstart-event-bridge main process (2960) terminated with status 1
upstart: upstart-event-bridge main process ended, respawning
Xsession: X session started for root at Sun Oct 25 16:43:57 NZDT 2015
localuser:root being added to access control list
openConnection: connect: No such file or directory
cannot connect to brltty at :0
upstart: unity7 main process (3015) terminated with status 1
upstart: gnome-session (Unity) main process (3018) killed by HUP signal
upstart: hud main process (3009) killed by HUP signal
upstart: unity-settings-daemon main process (3011) killed by HUP signal
upstart: at-spi2-registryd main process (3017) killed by HUP signal
upstart: unity-panel-service main process (3025) killed by HUP signal
upstart: indicator-messages main process (3123) killed by HUP signal
upstart: indicator-keyboard main process (3129) killed by HUP signal
upstart: Disconnected from notified D-Bus bus
upstart: indicator-bluetooth main process (3124) killed by TERM signal
upstart: indicator-power main process (3125) killed by TERM signal
upstart: indicator-session main process (3139) killed by TERM signal
upstart: indicator-application pre-stop process (12788) killed by HUP signal
upstart: gnome-session (Unity) pre-stop process (12789) killed by HUP signal
upstart: indicator-application main process (3155) killed by TERM signal
upstart: indicator-datetime main process (3127) killed by TERM signal
upstart: indicator-printers main process (3135) killed by TERM signal
upstart: indicator-sound main process (3134) killed by HUP signal
```

---


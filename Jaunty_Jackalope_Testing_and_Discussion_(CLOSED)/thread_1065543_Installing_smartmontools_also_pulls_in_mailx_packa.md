---
title: "Installing smartmontools also pulls in mailx packages"
date: 2009-02-10
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by todak on 2009-02-10
I installed smartmontools from the terminal and these three files were also dragged in ```
bsd-mailx mailx postfix
```. How on earth are these three files related to a hard drive utility? Needless to say, I removed them leaving only the desired package, smartmontools.

---

### Post by pressureman on 2009-02-10
smartd uses 'mail' to send notifications of impending failure. And since mailx depends on an MTA, Postfix gets dragged along for the ride too.

Yeah, seems kinda stupid to me too.

---

### Post by MacUntu on 2009-02-10
I've wondered about that dependency too.

Here's the bug at Launchpad: [https://bugs.launchpad.net/ubuntu/+source/smartmontools/+bug/158909](https://bugs.launchpad.net/ubuntu/+source/smartmontools/+bug/158909)

---


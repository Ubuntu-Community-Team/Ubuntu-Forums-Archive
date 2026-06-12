---
title: "libsoprano amd64 fails to update"
date: 2009-01-22
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by ronacc on 2009-01-22
the title says it . I get this error with todays PM updates .
```
E: /var/cache/apt/archives/libsoprano4_2.1.67+dfsg.1-0ubuntu1_amd64.deb: trying to overwrite `/usr/share/soprano/plugins/nquadparser.desktop', which is also in package soprano-daemon

```
filed bug # 320332

---

### Post by dinxter on 2009-01-23
looks like 2.1.67+dfsg.1.0ubuntu2 has just been [built]("https://launchpad.net/ubuntu/+builds?build_text=soprano&build_state=built") with Replaces: libsoprano3, soprano-daemon (<= 2.1.64+dfsg.1-0ubuntu1) added (soprano-daemon seemingly no more). hopefully fixes this when repositories fill.

can try [here]("https://launchpad.net/ubuntu/jaunty/+source/soprano/2.1.67+dfsg.1-0ubuntu2"). (amd64 missing when i tried)

---


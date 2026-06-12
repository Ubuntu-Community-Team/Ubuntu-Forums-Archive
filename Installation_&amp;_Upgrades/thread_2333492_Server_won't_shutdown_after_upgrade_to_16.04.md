---
title: "Server won't shutdown after upgrade to 16.04"
date: 2016-08-10
forum: Installation &amp; Upgrades
---

### Post by Jeff_Maxwell on 2016-08-10
[FONT=arial][SIZE=2]Updated my working 14.04 LTS server install to 16.04 with "[COLOR=#333333]sudo do-release-upgrade" It seemed to go smoothly. Noticed that restart was taking a long time. Since i'm running the machine headless, had to move it and hook up a monitor. This is what I happens when I try to restart. 
[/COLOR][/SIZE][/FONT][ATTACH=CONFIG]270656[/ATTACH]
[SIZE=2][FONT=arial]Any ideas? I have an SSD as the HD and before the update it restarted in about ten seconds.[/FONT][/SIZE]

---

### Post by coldraven on 2016-08-11
> [FONT=arial][SIZE=2][COLOR=#333333]This is what I happens when I try to restart[/COLOR][/SIZE][/FONT]
Your code or image did not get displayed, maybe try it again.

---

### Post by Jeff_Maxwell on 2016-08-11
> **Jeff_Maxwell said:**
> [FONT=arial][SIZE=2]Updated my working 14.04 LTS server install to 16.04 with "[COLOR=#333333]sudo do-release-upgrade" It seemed to go smoothly. Noticed that restart was taking a long time. Since i'm running the machine headless, had to move it and hook up a monitor. This is what I happens when I try to restart. 
[/COLOR][/SIZE][/FONT][ATTACH=CONFIG]270656[/ATTACH]
[SIZE=2][FONT=arial]Any ideas? I have an SSD as the HD and before the update it restarted in about ten seconds.[/FONT][/SIZE]

Just reinstalled 16.04.1, reformatted drive. clean install. still hangs at restart.

---

### Post by bureau on 2016-08-11
Same problem
My syslog in the attachment. As you can see, delay between  stop and start has 30 min. value

---


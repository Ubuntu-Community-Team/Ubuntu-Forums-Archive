---
title: "Persistent Message"
date: 2019-09-15
forum: Installation &amp; Upgrades
---

### Post by mechmecha on 2019-09-15
I keep getting this message "root@LAPTOP-********:~#" , not sure what to do. Can anyone help? Please

---

### Post by guiverc on 2019-09-15
It looks to me like your $PS1 has been set to something unusual. The "root" is likely your $USER (username) however root is disabled by default with Ubuntu so what you are running, LAPTOP-... maybe your box name; the ~ denotes you're in that directory (ie. your home directory which is possibly /root/) and # is the prompt.  How your $PS1 is set can depend on shell used, but are you using Ubuntu? or something else?

The command `echo $PS1` will display the current value of your prompt (if I'm correct and this is what I think you're asking about).

---

### Post by Dev'olution on 2019-09-15
> **mechmecha said:**
> I keep getting this message "root@LAPTOP-********:~#" , not sure what to do. Can anyone help? Please

Is this in a terminal?

Please provide a screenshot or a grab of the code.

---


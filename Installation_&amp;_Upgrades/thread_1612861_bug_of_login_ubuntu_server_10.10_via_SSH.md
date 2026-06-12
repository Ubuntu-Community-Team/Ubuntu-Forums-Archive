---
title: "bug of login ubuntu server 10.10 via SSH"
date: 2010-11-03
forum: Installation &amp; Upgrades
---

### Post by webappl on 2010-11-03
Hi guys,

I encountered a bug when remote logging in ubuntu with a new user account via SSH. After connected, the command prompt was displayed as '$' without quotation marks. As we know, the correct form should be like 'user@machine:~#'. There were also quite a lot of abnormal behaviors, eg, 'source' command didn't work, and up arrow won't recall history but printed gibberish. However, after type in 'bash', the prompt became 'user@machine:~' and the machine seemed normal.

This happened with every new user created by 'useradd' command. However, when logging in with the user created during installation of Ubuntu, the machine is working normally.

Does anybody know what causes this bug? How can I fix it?

Thanks in advance.

Alex

---

### Post by TSJason on 2010-11-03
Alex,

Your new user has the default shell set to /bin/sh, but you want it to be set to /bin/bash. To change the user(s) shell just use the chsh command:

```
sudo chsh username -s /bin/bash
```

---

### Post by webappl on 2010-11-04
> **TSJason said:**
> Alex,

Your new user has the default shell set to /bin/sh, but you want it to be set to /bin/bash. To change the user(s) shell just use the chsh command:

```
sudo chsh username -s /bin/bash
```

Thanks. Problem solved.

---


---
title: "Local startup script"
date: 2010-02-07
forum: Installation &amp; Upgrades
---

### Post by m.milway on 2010-02-07
I need to run a local startup script to finish of a laboratory distribution of Ubuntu 9.10.

Under 8.04 I put a pointer to my script in /etc/rc2.d

This directory exists in 9.10 but the script does not run. I believe there is a new mechanism that I don't yet understand.

How to I invoke my local startup script under 9.10?

Regards,
Michael Milway

---

### Post by suseendran.rengabashyam on 2010-02-08
Hi,

In Ubuntu 9.10 you can place the script in the file /etc/rc.local or you can call the script file from /etc/rc.local

For Example:
'myscript.sh' is present in /home/<user_name>

If you want to execute copy.sh during boot add the following line in /etc/rc.local

```
bash /home/<user_name>/myscript.sh
```

just before the line 'exit 0'.

---


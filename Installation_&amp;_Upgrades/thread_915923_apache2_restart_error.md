---
title: "apache2 restart error"
date: 2008-09-10
forum: Installation &amp; Upgrades
---

### Post by chamkaran on 2008-09-10
Hello guys,
I am getting the error when i want to restart the apache2.
the error is **" apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName"**.
As i checked the apache2 is properly installed.
Yours help be highly appreciated.

Regards

---

### Post by manishtech on 2008-09-10
> the error is **" apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName"**.
As i checked the apache2 is properly installed.
I always get this error, but it doesnt matter, your Apache is running fine I guess. Check whether its running or not using the command
```
ps -A | grep -i apache
```

---


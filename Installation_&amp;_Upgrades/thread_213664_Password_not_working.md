---
title: "Password not working"
date: 2006-07-11
forum: Installation &amp; Upgrades
---

### Post by probingzon on 2006-07-11
Well recently I just did some upgrades on dapper drake then I restarted it the system now I find myself in a perdicament. Whenever I try to change some settings it asks for a root password then when i type it, it gives me a error message back.

Now heres the thing when I use the root password in the terminal it seems to work fine, but when i try to use it in the gui it doesn't work. and im 100% sure that im spelling it right it can't be any easier.

CAN SOMEONE PLEASE HELP ME IT GETTING ME FRUSTRATED?

---

### Post by Sonofmoog on 2006-07-11
> **probingzon said:**
> Now heres the thing when I use the root password in the terminal it seems to work fine, but when i try to use it in the gui it doesn't work. and im 100% sure that im spelling it right it can't be any easier.

Since your password works in a terminal, I'd suggest open a terminal and issue the command

```
 sudo passwd $USER 
```

Substitute your user name for $USER, then issue the same password.  If that doesn't work, change the password to something temporary, then change it back to the password you had ..

---


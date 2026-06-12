---
title: "Can't install or remove applications!!"
date: 2012-07-30
forum: Installation &amp; Upgrades
---

### Post by rebelplankton on 2012-07-30
When I tried to install samba it failed to install it several times. Then when I tried to install or remove other applications using "apt-get install" and "apt-get remove" it gave me the same error "Errors were encountered while processing: samba4" even if I'm trying to install/remove different programs. And if i try to install or remove from Ubuntu Software Center it fails too.

Any answer is fully appreciated!

Thanks!

---

### Post by levlaz on 2012-07-30
> **rebelplankton said:**
> When I tried to install samba it failed to install it several times. Then when I tried to install or remove other applications using "apt-get install" and "apt-get remove" it gave me the same error "Errors were encountered while processing: samba4" even if I'm trying to install/remove different programs. And if i try to install or remove from Ubuntu Software Center it fails too.

Any answer is fully appreciated!

Thanks!

Try 

1. sudo apt-get autoremove 
2. sudo apt-get update
3. sudo apt-get upgrade 

If that doesn't work.. reboot and try the same commands.

---

### Post by rebelplankton on 2012-07-30
> **levlaz said:**
> Try 

1. sudo apt-get autoremove 
2. sudo apt-get update
3. sudo apt-get upgrade 

If that doesn't work.. reboot and try the same commands.

Thanks levlaz!!!

---

### Post by levlaz on 2012-07-30
Youre welcome! :) 

Sometimes things just get hung up and you have to give them a little kick.

---


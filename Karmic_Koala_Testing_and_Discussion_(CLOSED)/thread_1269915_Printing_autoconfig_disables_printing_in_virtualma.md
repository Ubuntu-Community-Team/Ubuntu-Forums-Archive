---
title: "Printing autoconfig disables printing in virtualmachines!"
date: 2009-09-18
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by nanog on 2009-09-18
I print coupons in virtualbox (there is absolutely NO BLOODY WAY TO PRINT COUPONS IN LINUX...grrrr). A new printer autoconfig magically installs the usb printer in ubuntu thus preventing it from being installed in virtual box xp. 

If anyone has a clue what the @#@!#%@#@!!! printer autoconfig  package/binary is I will immediately file a bug.

---

### Post by nanog on 2009-09-19
The culprit is system-config-printer. I have been able to print by uninstalling it. This removes ubuntu-desktop which is not ideal.

---


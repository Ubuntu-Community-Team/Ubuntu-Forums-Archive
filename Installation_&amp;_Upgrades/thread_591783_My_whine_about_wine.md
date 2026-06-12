---
title: "My whine about wine"
date: 2007-10-25
forum: Installation &amp; Upgrades
---

### Post by myolbug on 2007-10-25
I have had an update notification now for over a month telling me that I need to update wine.  I cannot, as the URL is wrong.  What can I do?  I am running Ubuntu 6.06 and I cannot seem to get anywhere.  Can anyone help?  I am fairly new to Ubuntu so I'll need extra help.

I get this error message:  W: Failed to fetch [http://wine.budgetdedicated.com/apt/pool/main/w/wine/wine_0.9.47~winehq0~ubuntu~6.06-1_i386.deb](http://wine.budgetdedicated.com/apt/pool/main/w/wine/wine_0.9.47~winehq0~ubuntu~6.06-1_i386.deb)
  
Can anyone give me a betteraddress I can put itno Synaptic?


Thanks,
Randy

---

### Post by AdotB on 2007-10-25
Add these three lines to your sources.list:

## WineHQ - Ubuntu 6.06 LTS "dapper drake"
deb http://wine.budgetdedicated.com/apt dapper main
deb-src http://wine.budgetdedicated.com/apt dapper main

---

### Post by myolbug on 2007-10-27
Thank you.  I tried it and I think it worked.  I'll post again if I have any problems.

---


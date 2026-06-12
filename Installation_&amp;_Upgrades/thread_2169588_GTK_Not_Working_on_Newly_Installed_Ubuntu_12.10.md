---
title: "GTK Not Working on Newly Installed Ubuntu 12.10"
date: 2013-08-22
forum: Installation &amp; Upgrades
---

### Post by Thomas_Wildeboer on 2013-08-22
I recently upgraded to Ubuntu 12.10. When I logged in I found that there was no GTK on any windows. There was no unity launcher as well. Can anyone tell me how to fix this problem?

---

### Post by Frogs Hair on 2013-08-22
Hello and Welcome  

If you have terminal access via Ctrl + Alt +T you can try the following commands ```
dconf reset -f /org/compiz/
``````
setsid unity
```

---

### Post by Thomas_Wildeboer on 2013-08-26
That doesn`t seem to be working. The commands did nothing. Is there anything else I can do?

Thanks

---


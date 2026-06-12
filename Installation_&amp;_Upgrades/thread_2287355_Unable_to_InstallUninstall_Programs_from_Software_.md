---
title: "Unable to Install/Uninstall Programs from Software Center"
date: 2015-07-18
forum: Installation &amp; Upgrades
---

### Post by shashankvns on 2015-07-18
Hello everyone:

Due to some reasons, I am unable to install and/or uninstall any program(s) from the Ubuntu software center, and I am getting an error message "You don't have the required privileges to perform this action.". When I look into the details, this is what I see: "org.freedesktop.PolicyKit.Error.NotAuthorized: ('system-bus-name', {'name': ':1.99'}): org.debian.apt.install-or-remove-packages".

Could someone please help me to resolve this issue?

Thanks
Shashank

---

### Post by TheFu on 2015-07-18
Open a terminal  and run '**id**' - please post the results.

Any chance either the passwd or group files were modified?

---

### Post by shashankvns on 2015-07-19
Hi, Thank you for your reply, and I am not sure about passwd or group files were modified or not. If possible, could you please help me to fix it.

Thanks

---

### Post by TheFu on 2015-07-19
Results?

---

### Post by Bucky Ball on 2015-07-19
We can't help you do much unless you read and follow our instructions so we can have information to work with.

> **TheFu said:**
> Open a terminal  and run '**id**' - please post the results.



Thanks. :)

---

### Post by shashankvns on 2015-07-21
Hi:

I apologize for not sharing the result earlier, and it seems that the problem is fixed for now. However, I am still copying the results below so that you could find if there are any anomalies.

amrita@amrita:~$ id
uid=1000(amrita) gid=1000(amrita) groups=1000(amrita),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),108(lpadmin),124(sambashare)
amrita@amrita:~$ 

Thanks

---

### Post by Bucky Ball on 2015-07-21
Nope. If the problem is fixed, please outline how you fixed it and mark the thread as solved to help others. See the first link in my signature. Thanks.

---

### Post by shashankvns on 2015-07-22
It may sound a bit strange but I do not recall doing anything to fix the problem; somehow it got fixed on its own (may be after an update). I am sorry I am very new to Ubuntu, and have no idea how it got fixed, and that's why I thought to share the results to get comments from others.

---


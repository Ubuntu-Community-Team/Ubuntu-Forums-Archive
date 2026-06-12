---
title: "w-scan error"
date: 2009-03-27
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by jmore9 on 2009-03-27
Just wondering if anyone has had the following errors with w-scan ?

./w_scan -fa >> channels.conf  gives  
bash: channels.conf: Permission denied

Anyone got any idea what i am doing wrong ?

---

### Post by cariboo on 2009-03-27
have you tried:

```
sudo ./w_scan -fa >> channels.conf 
```?

Jim

---

### Post by jmore9 on 2009-04-03
this what happens

jeff@ubuntu44:/usr/bin$ sudo ./w_scan -fa >> channels.conf
bash: channels.conf: Permission denied

it happens with all the different uses 

./w_scan >> channels.conf

etc

---

### Post by Johan! on 2009-04-03
Try this:
./w_scan |sudo tee -a channels.conf

sudo permissions don't work if you use > or >>
sudo tee or sudo tee -a will work.

---


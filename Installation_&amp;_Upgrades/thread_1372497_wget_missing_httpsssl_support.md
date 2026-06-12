---
title: "wget missing https/ssl support"
date: 2010-01-04
forum: Installation &amp; Upgrades
---

### Post by mateusz16 on 2010-01-04
hi guys 
i have got 1 problem i would like to write one script but i recognized that my wget version do not have https support;/ After that i tried to compile the lastest version(1.12) but ther is still nothing;/
when i tried to run script

```

    #!/bin/bash

    gmail_login="login"
    gmail_password="pass"

    dane="$(wget --secure-protocol=TLSv1 --timeout=3 -t 1 -q -O - \
    https://${gmail_login}:${gmail_password}@mail.google.com/mail/feed/atom \
    --no-check-certificate | grep 'fullcount' \
    | sed -e 's/.*//;s/<\/fullcount>.*//' 2>/dev/null)"

    

```
script is my native language so i cut it but the problem is command after wget
 it gives me
```

wget: unrecognized option '--secure-protocol=TLSv1'


```

do you know what is wrong ?? ;/

---


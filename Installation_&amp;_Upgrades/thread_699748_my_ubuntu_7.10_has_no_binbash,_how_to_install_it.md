---
title: "my ubuntu 7.10 has no /bin/bash, how to install it?"
date: 2008-02-17
forum: Installation &amp; Upgrades
---

### Post by yanyan on 2008-02-17
By any kind of reason, I found that my ubuntu 7.10 has no /bin/bash, and when I used following command:
>ls -l  /bin/sh
 it showed me as /bin/sh-> /dash. 
Is that correct? 

By searching for bash and used 
>sudo apt-get install bash 

 i reinstalled bash but it showed me the message as zero updated. 

But using 
>locate bash
and >locate /bin/bash

I just could not see my bash binary file. What kind of reason could that be? how to solve that? how to reinstall my /bin/bash? thanks a lot.

---

### Post by yanyan on 2008-02-19
Hi, In fact the problem was solved. I deleted the /bin/bash by mistake in linking different files. I solve the problem by copying one /bin/bash file from the other ubuntu system and it can work well.

---


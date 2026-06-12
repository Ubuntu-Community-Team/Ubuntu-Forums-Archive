---
title: "synaptic stopped working"
date: 2010-08-09
forum: Installation &amp; Upgrades
---

### Post by kiridude on 2010-08-09
Hi. For some reason synaptic has ceased to work all of a sudden. Every time I try to install a new program, I get the following error:

```
W: Failed to fetch http://gr.archive.ubuntu.com/ubuntu/pool/universe/a/alarm-clock/alarm-clock_1.2.5-1_i386.deb
  404  Not Found

W: Failed to fetch http://gr.archive.ubuntu.com/ubuntu/pool/universe/f/faad2/faad_2.7-4_i386.deb
  404  Not Found
```

Universe and Multiverse were un-commented and working up until this problem began. 

Does anyone know what's going on here?

Thanks.

---

### Post by pastalavista on 2010-08-09
It may be possible your repository was down or incomplete. I just downloaded alarm-clock and it was fine.

To find the best repositories in your location, click settings/repositories (in Synaptic) First tab--> Download from: select 'other' then click "Find best server" then update/refresh and try alarm-clock again.

---

### Post by halj32 on 2010-08-09
Hi first Synaptic hasn't stopped working, it's either your internet connection is down or the site is down as it can not connect to  (404  Not Found)
[http://gr.archive.ubuntu.com/ubuntu/pool/universe](http://gr.archive.ubuntu.com/ubuntu/pool/universe)
try doing an update packages & fix
sudo apt-get install -f
if all's OK
try
sudo apt-get install alarm-clock -y  or do it in synaptic

good luck

---

### Post by kiridude on 2010-08-09
thanks for the answers guys. 

pastalavista you da man! the server I was using in my country had evidently been changed or had a problem. The "find best server" found me one that was working and now everything is back to normal.

:D

---

### Post by zorba_the_greek on 2010-08-16
> **pastalavista said:**
> It may be possible your repository was down or incomplete. I just downloaded alarm-clock and it was fine.

To find the best repositories in your location, click settings/repositories (in Synaptic) First tab--> Download from: select 'other' then click "Find best server" then update/refresh and try alarm-clock again.

You saved my day, too!! :D

---


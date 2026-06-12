---
title: "Ubuntu 12.04 Upgrade Error"
date: 2012-05-21
forum: Installation &amp; Upgrades
---

### Post by bsmithtridium on 2012-05-21
I'm running Ubuntu 11.10 and was prompted int the Update Manager to upgrade to 12.04. After running a while, it failed with the message

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/mail/libq/libquvi-scripts/libquvi-scripts_0.4.2.1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/mail/libq/libquvi-scripts/libquvi-scripts_0.4.2.1_all.deb) Hash Sum mismatch

After numerous attempts at running apt-get clean, etc. and retrying, I still get the same message. 

Any thoughts?

Regards,
Bill

---

### Post by gordintoronto on 2012-05-21
Do you know what libquvi-scripts is for? Is the message a warning, or more serious?

I would run Software Sources and remove that ppa.

---

### Post by jadtech on 2012-05-21
> **gordintoronto said:**
> Do you know what libquvi-scripts is for? Is the message a warning, or more serious?

I would run Software Sources and remove that ppa.

libquvi-scripts contains the embedded lua scripts that libquvi
uses for parsing the media details

it  a collection of scripts for a media player that requires flash

---

### Post by gordintoronto on 2012-05-21
> **jadtech said:**
> libquvi-scripts contains the embedded lua scripts that libquvi
uses for parsing the media details

it  a collection of scripts for a media player that requires flash

I understand every word you used, but I don't understand how libquvi enhances one's computer usage. I play flash online and offline, but I don't have this package installed.

---

### Post by jadtech on 2012-05-21
I have no Idea myself  oddly I ran across this info in a bug report for this package  for arch linux .. 
how ever  it also comes packaged for mac and windows I gues that  speaks volumes about it ..

---

### Post by bsmithtridium on 2012-05-22
The thing is, I don't have the quvi package currently installed. And am not given the opportunity in the upgrade manager to prevent it's selection.

---

### Post by bsmithtridium on 2012-05-22
I tried it again this morning (after many attempts yesterday :)) and it worked. I'm not sure what changed. I'm sure it was nothing on my side, however, all is good now.

Thx.

---


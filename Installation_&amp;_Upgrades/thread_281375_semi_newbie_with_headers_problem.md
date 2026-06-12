---
title: "semi newbie with headers problem"
date: 2006-10-21
forum: Installation &amp; Upgrades
---

### Post by jnicita on 2006-10-21
I origianlly installed vmware and have long since created my virtual machine using ubuntu as the host.

Its been some time, but I used the  sudo apt-get install linux-headers-`uname -r` back when I originally installed it.

Here is where it gets funky for me, I tried to follow a few of the myth tv docuemnts here that had me redownload the headers and kernel, its never worked. But the write up I followed had me creating sum links and esentially populated my /lib/modules directory with c header files. I remember creating a sym link in the /usr/src/ directory called linux. Anyways, I have gotten all confused, and actually I had to re-run vmware-config which kicked out a error saying that the reported kernel doesnt match the headers, so I figured what the hell, and deleted the /usr/src/ directory contents thinking I could re use the sudo apt-get install linux-headers-`uname -r` command to repopulate the correct files.

Now however when I try to run the vmware confgure its locating the info in the /lib/modules directory and its doing crap that It never did before.

Can someone tell me how to simply start over? with respect to the kernel crap?

Thanks, I hope that makes sense or someone can explain what Ive done so I can try to fix it.
duyal booting sucks when vmware xp is all I really need.

---


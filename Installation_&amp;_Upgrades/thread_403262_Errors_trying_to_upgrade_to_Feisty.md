---
title: "Errors trying to upgrade to Feisty"
date: 2007-04-06
forum: Installation &amp; Upgrades
---

### Post by GregDonohoe on 2007-04-06
I ran a Feisty upgrade successfully a few days ago on my laptop and tried to run one just now on my desktop, but encountered an error.

I ran "sudo update-manager -d" and it failed and said it would run "dpkg --configure -a" but didn't. I then tried running it myself and got "dpkg: command not found" :confused: 

What should I do to fix this?

Thanks.

---

### Post by sharke on 2007-04-06
> **GregDonohoe said:**
> I ran a Feisty upgrade successfully a few days ago on my laptop and tried to run one just now on my desktop, but encountered an error.

I ran "sudo update-manager -d" and it failed and said it would run "dpkg --configure -a" but didn't. I then tried running it myself and got "dpkg: command not found" :confused: 

What should I do to fix this?

Thanks.
sudo update-manager -d updates to the latest version. If you have already updated with this command and it was successfull you than use sudo apt-get dist-upgrade to get updates.

Regards
Sharke

---

### Post by GregDonohoe on 2007-04-06
As I said, it failed and told me to run "dpkg --configure -a" which also failed.
Anyone know what I should do?

---

### Post by zvacet on 2007-04-07
```
sudo dpkg --configure -a
```

---

### Post by GregDonohoe on 2007-04-07
As I said originally "dpkg: command not found".
Please let me know if anyone can help me recover my system!

---

### Post by UNITI&#1048;U on 2007-04-07
> **GregDonohoe said:**
> As I said originally "dpkg: command not found".
Please let me know if anyone can help me recover my system!

You don't run 'dpkg --configure -a' you run '**sudo** dpkg --configure -a' as the previous poster told you.

---

### Post by GregDonohoe on 2007-04-10
I get "sudo: dpkg: command not found" from "sudo dpkg --configure -a", and I've tested sudo on something else to make sure it's not messing up.
Any ideas?
Thanks!

---

### Post by zvacet on 2007-04-11
Go to hte synaptic>edit>fix broken packages.Maybe that way you will solve problem with dpkg and after that will be able to run command.It is just idea,but try it.

---


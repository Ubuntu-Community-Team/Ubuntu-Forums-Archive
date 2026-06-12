---
title: "grub: error:symbol 'grub-term-hightlight-color' not found"
date: 2014-05-16
forum: Installation &amp; Upgrades
---

### Post by Kiesel on 2014-05-16
Hi,

I wanted to update my xubuntu 12.04 to xubuntu 14.04 but the update failed and I couldnt boot. So I decided to reinstall ubuntu as I had home, windows and data on different partitions.

After the installation my Laptop (Samsung RV520, UEFI mode, gpt) greets me with
> error:symbol 'grub-term-hightlight-color' not found

After googling I found this[ bug report ]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1289977") and tried a few of the mentioned solutions, none of them worked. 
So I did a reinstall and let boot-repair create [this]("http://paste.ubuntu.com/7474406/") report.

Can anyone see what I am missing? 

Thanks,
Kiesel

---

### Post by Bashing-om on 2014-05-16
Kiesel; Hi !

Appears you are the victim of an identified bug:
See:
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1289977](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1289977)
For some possible fixes.

[INDENT][INDENT]they be 
[INDENT][INDENT][INDENT]a work'n on it
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Kiesel on 2014-05-16
Thanks, I have seen that report. I managed somehow to fix it but I am not sure what did the trick. It was a wild mixture of all the fixes mentioned in the bug report.
Now I have another problem but I will open another thread for that.

---

### Post by Bashing-om on 2014-05-16
Kiesel; Good deal,

Pleased this little situation is under control.

Please mark this thread solved; aides others seeking the solution, helps keep the forum clean and precludes others miss-directing efforts to aid.

I will look for your other thread, and see what can be done.

[INDENT][INDENT]as we keep on
[INDENT][INDENT][INDENT]keep'n on
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---


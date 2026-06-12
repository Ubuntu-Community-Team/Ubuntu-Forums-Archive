---
title: "How do I move Windows 7 to top of the dualboot list?"
date: 2013-01-06
forum: Installation &amp; Upgrades
---

### Post by Pybro on 2013-01-06
I am dualbooting Windows 7 and Ubuntu, and my installation went great, thanks to the great guides people have written, but there is one thing I wanted to change that I have not been able to find a guide on how to do.

On the dualboot list, there is Ubuntu-64bit and then a bunch of other options available.
[LIST=1]
[*]Do these other options have any significance besides Ubuntu 64-bit, and what could I use them for then?
[*]If I'm probably never going to use them, I don't need them. How do I delete them from the dualboot list?
[*]How can I move Windows 7 to the very top of the dualboot list? I like ubuntu, but I want to keep it my study/programming platform so I still want to be able to boot windows 7 as fast as possible, and have it boot Windows 7 in the event that I do not respond to my computer in time.
[/LIST]

Thank you for the responses! I **really** appreciate the hospitality.

---

### Post by darkod on 2013-01-06
Persoanlly I disable the memory test entries, so only the ubuntu normal and recovery mode entries remain. I move windows to the top like this. Open terminal in ubuntu and execute one by one:
```
sudo cp /etc/grub.d/30_os-prober /etc/grub.d/06_os-prober
sudo chmod -x /etc/grub.d/30_os-prober
sudo chmod -x /etc/grub.d/20_memtest86+
sudo update-grub
```

That will make a new 06_os-prober file, disable the defauls 30_os-prober and 20_memtest86+ files, and update the grub.cfg.

Since the ubuntu script is 10_linux and the new os-prober will have lower number (06), it gets executed before 10_linux end the detected windows ends up on top.

---

### Post by Pybro on 2013-01-06
> **darkod said:**
> Persoanlly I disable the memory test entries, so only the ubuntu normal and recovery mode entries remain. I move windows to the top like this. Open terminal in ubuntu and execute one by one:
```
sudo cp /etc/grub.d/30_os-prober /etc/grub.d/06_os-prober
sudo chmod -x /etc/grub.d/30_os-prober
sudo chmod -x /etc/grub.d/20_memtest86+
sudo update-grub
```

That will make a new 06_os-prober file, disable the defauls 30_os-prober and 20_memtest86+ files, and update the grub.cfg.

Since the ubuntu script is 10_linux and the new os-prober will have lower number (06), it gets executed before 10_linux end the detected windows ends up on top.
Oh boy, that looks complicated. Thank you for your help man. What does memtest do?

---

### Post by offgridguy on 2013-01-06
> **Pybro said:**
> Oh boy, that looks complicated. Thank you for your help man. What does memtest do?
It looks complicated but it's actually the quick way.  You may be more comfortable with
the method found here.

[http://ubuntuforums.org/showthread.php?t=2088216](http://ubuntuforums.org/showthread.php?t=2088216)

---


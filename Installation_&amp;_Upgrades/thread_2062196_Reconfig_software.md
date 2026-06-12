---
title: "Reconfig software"
date: 2012-09-24
forum: Installation &amp; Upgrades
---

### Post by h66m9d on 2012-09-24
Hi.
I want reconfig an installed backage in Ubuntu 12.4
Anyone can help me?

I install kubuntu-desktop in Ubuntu 12.4 but when it warn config screen in terminal I skiped it with press Esc. Now I need reconfig that

---

### Post by jrog on 2012-09-24
> **h66m9d said:**
> Hi.
I want reconfig an installed backage in Ubuntu 12.4
Anyone can help me?

I install kubuntu-desktop in Ubuntu 12.4 but when it warn config screen in terminal I skiped it with press Esc. Now I need reconfig that
Try this:
```
sudo dpkg-reconfigure kubuntu-desktop
```
I'm not entirely sure that it will work, because I believe kubuntu-desktop is a meta-package and I have no idea whether dpkg-reconfigure will work with meta-packages. But dpkg-reconfigure is a standard-ish way of reconfiguring things, so give it a shot.

---

### Post by h66m9d on 2012-09-24
thanks, but your way don't work in this case. do you know what package can set kdm?

---

### Post by jrog on 2012-09-24
> **h66m9d said:**
> thanks, but your way don't work in this case. do you know what package can set kdm?
I don't use KDE or KDM, but the package for kdm should just be 'kdm' (without the quotes). So, you might be able to run 'sudo dpkg-reconfigure kdm' (again without quotes) instead of the command I gave previously, if kdm is what you want to reconfigure.

If that doesn't work, can you try to describe in a bit more detail what it is that you want to do?

---

### Post by h66m9d on 2012-09-24
Dear jrog I can config kdm with your way. 
But I need config kubuntu-desktop meta package
Anyone can help me?

---

### Post by jrog on 2012-09-24
> **h66m9d said:**
> Dear jrog I can config kdm with your way. 
But I need config kubuntu-desktop meta package
Anyone can help me?
What exactly is it that you are trying to do? Are you trying to set your system up so that kdm is your login manager, or something else?

---

### Post by h66m9d on 2012-09-25
> **jrog said:**
> What exactly is it that you are trying to do? Are you trying to set your system up so that kdm is your login manager, or something else?
When I'm installing kubuntu-desktop , it warn me more than one software setting (kdm setting was one of them), I don't know what is that setting. I need review those setting.

---

### Post by jrog on 2012-09-25
> **h66m9d said:**
> When I'm installing kubuntu-desktop , it warn me more than one software setting (kdm setting was one of them), I don't know what is that setting. I need review those setting.
What happened when you entered 'sudo dpkg-reconfigure kubuntu-desktop' (without the quotes)? I think that should have done it. If not, you might try reinstalling; 'sudo apt-get install --reinstall kubuntu-desktop' (again, without the quotes), and that should do it. I'm not aware of another way, at least unless you can be more specific about the software setting you're trying to change.

---

### Post by h66m9d on 2012-09-26
> **jrog said:**
> What happened when you entered 'sudo dpkg-reconfigure kubuntu-desktop' (without the quotes)? I think that should have done it. If not, you might try reinstalling; 'sudo apt-get install --reinstall kubuntu-desktop' (again, without the quotes), and that should do it. I'm not aware of another way, at least unless you can be more specific about the software setting you're trying to change.
OK! & Thanks.

Do you know where is installed program setting?

---


---
title: "Import home directory"
date: 2010-04-23
forum: Installation &amp; Upgrades
---

### Post by anlgalways on 2010-04-23
Hello,
My system got corrupted but I recovered the files in the home directory. So I have /home/gabe on an external hard drive.

Is there any way I can create a new user using the files on my external hard drive for a home directory?

---

### Post by labinnsw on 2010-04-24
Personally, I would not recommend it, for the simple reason that you would need to have the external drive connected at all times.

If I wanted to do this regardless, I would not change the default set up of the system. I would instead make a symlink in /user/home. ```
sudo ln -s /mdeia/externaldrivename/home/gabe /user/home/gabe1.
```

---

### Post by jagan185 on 2010-04-25
Hi I want to upgrade to Ubuntu 10.04 LTS stable version (When it is released). Can I export all my current packages, settings , home directory from Ubuntu 9.10. What about the boot loader. I'm now dual booting with Windows 7. Can I do that after upgrading. What are the issues I may have to face after upgrading, like boot loader, current settings and files (data loss). Please Help me with this and some tips and advises for upgrading with out loosing present data and settings. Looking forward to your valuable tips.

---

### Post by labinnsw on 2010-04-25
> **jagan185 said:**
> Hi I want to upgrade to Ubuntu 10.04 LTS stable version (When it is released). Can I export all my current packages, settings , home directory from Ubuntu 9.10. What about the boot loader. I'm now dual booting with Windows 7. Can I do that after upgrading. What are the issues I may have to face after upgrading, like boot loader, current settings and files (data loss). Please Help me with this and some tips and advises for upgrading with out loosing present data and settings. Looking forward to your valuable tips.

Your Update manager will handle the process for you. It will tell you when the new release is ready. All you will have to do, is chose to upgrade and follow the prompts.

---


---
title: "can not access/open my files at public_html directory"
date: 2010-05-13
forum: Installation &amp; Upgrades
---

### Post by Muhammad Takdir on 2010-05-13
hi,
i need suggestion with this. i've activated userdir with (sudo a2enmod userdir) at ubuntu 10.04.
i can not open my php files via web browser at public_html directori (screenshot.png). but if i move it to /var/www ... it's works (screenshoot-1.png).

need suggestion please ??

---

### Post by Muhammad Takdir on 2010-05-13
> **Muhammad Takdir said:**
> hi,
i need suggestion with this. i've activated userdir with (sudo a2enmod userdir) at ubuntu 10.04.
i can not open my php files via web browser at public_html directori (screenshot.png). but if i move it to /var/www ... it's works (screenshoot-1.png).

need suggestion please ??

ok. SOLVED.
just downgrade php 5.3 to php 5.2. use karmic repository.

---

### Post by dino99 on 2010-05-13
can you report a bug on launchpad about this ? (that will help debugging)

---

### Post by Smiecho on 2010-05-17
I don't know if that is a bug or a feature. Edit file /etc/apache2/mods-available/php.conf  and comment out lines ```
<IfModule mod_userdir.c>
<Directory /home/*/public_html>
php_admin_value engine Off
</Directory>
</IfModule>
```

---

### Post by chris64_cool on 2010-09-25
I am facing exactly the same problem in ubuntu 10.04 32 bit as well as 64 bit. as mentioned by [Muhammad Takdir]("http://ubuntuforums.org/member.php?u=1073278")

---

### Post by chris64_cool on 2010-09-25
> **chris64_cool said:**
> I am facing exactly the same problem in ubuntu 10.04 32 bit as well as 64 bit. as mentioned by [Muhammad Takdir]("http://ubuntuforums.org/member.php?u=1073278")

I got it working had to comment the lines as mentioned by [Smiecho]("http://ubuntuforums.org/member.php?u=173916"). still i wonder why they disabled it by default.

---


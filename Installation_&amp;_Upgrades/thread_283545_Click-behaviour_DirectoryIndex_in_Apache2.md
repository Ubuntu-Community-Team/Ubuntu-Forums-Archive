---
title: "Click-behaviour DirectoryIndex in Apache2"
date: 2006-10-24
forum: Installation &amp; Upgrades
---

### Post by zakhooi on 2006-10-24
Hi,

I've made a directory visible through the web in the apache2 config.
So I see the contents of that directory and I can browser through the directories.

When I want to download a file (e.g. file.exe) it will download it as data and will show it in my browser.
I want to have this behaviour changed so that it will ask me to download the file or open it with a tool I can select in a popup window.

What do I need to change in my config?

My current config is:
```

<directory /var/www/download>
  ForceType text/plain
  Options Indexes
  IndexOptions FancyIndexing NameWidth=* IconHeight=10 ScanHTMLTitles
  AuthType Basic
  AuthName "linuxbak.zakhooi.net"
  AuthUserFile /etc/apache-ssl/users
  AllowOverride None
</directory>

```

Thanks in advance

---

### Post by merkur2k on 2006-10-24
Remove the 'ForceType text/plain' line, that should let it use the correct mime types.

---

### Post by zakhooi on 2006-10-24
That's it!

I don't understand why I haven't thought about that.
Thanks for the eye-opener

---


---
title: "Can proxy user id includes a '\'?"
date: 2010-11-02
forum: Installation &amp; Upgrades
---

### Post by Phil_yang on 2010-11-02
We use a proxy to access Internet and everybody's user id includes a "\", such as kiddomain\pya. But my ubuntu does not work for apt when I input such a user id into /etc/apt/apt.conf. Could anybody help me out? Thanks!
 
Acquire::http::Proxy "[http://kiddomain\pya:Lockman@](http://kiddomain\pya:Lockman@)192.168.0.6:8080" 
Acquire::ftp::Proxy "[http://_[COLOR=#0000ff]kiddomain\pya:Lockman@[/COLOR]_192.168.0.6:8080]("http://kiddomain\pya:Lockman@192.168.0.6:8080")"

---

### Post by Barriehie on 2010-11-02
> **Phil_yang said:**
> We use a proxy to access Internet and everybody's user id includes a "\", such as kiddomain\pya. But my ubuntu does not work for apt when I input such a user id into /etc/apt/apt.conf. Could anybody help me out? Thanks!
 
Acquire::http::Proxy "[http://kiddomain\pya:Lockman@](http://kiddomain\pya:Lockman@)192.168.0.6:8080" 
Acquire::ftp::Proxy "[http://_[COLOR=#0000ff]kiddomain\pya:Lockman@[/COLOR]_192.168.0.6:8080]("http://kiddomain\pya:Lockman@192.168.0.6:8080")"

Who is 'we'.  Is this a school?

---


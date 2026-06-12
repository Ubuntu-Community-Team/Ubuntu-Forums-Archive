---
title: "Install Courier Font"
date: 2006-08-03
forum: Installation &amp; Upgrades
---

### Post by weeds86 on 2006-08-03
Hey guys,

I have a program that needs Courier as a font or it crashes. I have had a look in the systems fonts and there is only Courier 10 Pitch, not Courier.

Does anyone know where and how I can istall the Courier font?

Cheers ;)

---

### Post by ciscosurfer on 2006-08-03
Try this```
sudo aptitude install msttcorefonts
``` If that doesn't work, you may need to enable extra repos.

---

### Post by weeds86 on 2006-08-03
I just tried 'sudo aptitude install msttcorefonts' and nothing happened. I got a message saying 'No candidate version found for msttcorefonts'.

I know that the msttcorefonts has the font Courier New, not Courier. I doubt this will work as my system currently has Courier 10 Pitch and that wasnt compatible.

It was mentioned that I might need to enable extra repos. What does this mean and how do I do it?

Thanks for the help so far!

Cheers ;)

---

### Post by ciscosurfer on 2006-08-03
The msttcorefonts packages installs Microsofts True Type core fonts. It's located in the multiverse repository.  [Read this]("http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories") to understand how to accomplish this task.

---


---
title: "How to manual install any program ?"
date: 2008-04-29
forum: Installation &amp; Upgrades
---

### Post by Zeck on 2008-04-29
Hello,
I'm just newbie for Ubuntu 8.04. I want to manual install PHP, Java, MySQL etc. How can I manual install any program on Ubuntu ?



Regards,
Zeck

---

### Post by iaculallad on 2008-04-29
To install certain application from Repository:

sudo apt-get install application_name

To install MySQL from Repository:

sudo apt-get install mysql-server

Do the same thing with Java and PHP.

Installing application that has been already downloaded on your local drive:

Use: sudo dpkg -i application_name

---

### Post by Zeck on 2008-04-29
> **iaculallad said:**
> To install certain application from Repository:

sudo apt-get install application_name

To install MySQL from Repository:

sudo apt-get install mysql-server

Do the same thing with Java and PHP.

Installing application that has been already downloaded on your local drive:

Use: sudo dpkg -i application_name



Thanks.
):P

---

### Post by housam on 2008-04-29
check this guide :[[COLOR="Red"]_how to install anything in ubuntu_[/COLOR]]("http://monkeyblog.org/ubuntu/installing/")

---

### Post by peakshysteria on 2008-04-29
Java is simple enough to install. Just go to a site you now you need java to see/use. And Firefox will prompt you with the rest. I just did so in my new Ubuntu 8.04 Hardy 64 :) It went even more smooth than on my daughters Gutsy.

---


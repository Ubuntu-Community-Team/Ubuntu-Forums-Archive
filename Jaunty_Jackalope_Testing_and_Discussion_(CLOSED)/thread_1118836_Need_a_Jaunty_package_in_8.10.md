---
title: "Need a Jaunty package in 8.10"
date: 2009-04-07
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by localetc on 2009-04-07
Hi,

I have 8.10 installed and I really need to install Python Reportlab 2.3 for a work project.  I see that it is going to be available in Jaunty:

[https://launchpad.net/ubuntu/jaunty/+source/python-reportlab](https://launchpad.net/ubuntu/jaunty/+source/python-reportlab)

but I am unable to find it in any backports for 8.10.  Is there any way to get this going on 8.10?  I am relatively new to ubuntu and apt-get and I can't find a way to do this.

If I install the source from scratch am I going to have upgrade problems when it does become available?

---

### Post by cariboo on 2009-04-07
You can get the packages you need [here]("http://packages.ubuntu.com/"), just make sure you also download all the dependecies.

Jim

---

### Post by localetc on 2009-04-07
Thanks Jim!  Very easy...

---

### Post by el_itur on 2009-04-07
it's available from the cheeseshop [http://pypi.python.org/pypi/reportlab/2.3](http://pypi.python.org/pypi/reportlab/2.3)

you should be able to easy_install it (sudo easy_install reportlab)

I would recommend you to try it in a virtualenv for safeness' sake

let me know if you need further instructions in the later

---


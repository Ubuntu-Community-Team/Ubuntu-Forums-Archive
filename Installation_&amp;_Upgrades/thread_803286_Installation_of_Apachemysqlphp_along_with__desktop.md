---
title: "Installation of Apache/mysql/php along with  desktop"
date: 2008-05-22
forum: Installation &amp; Upgrades
---

### Post by simonkuriakose on 2008-05-22
Dear Forum Members,

My project is development of a web based application in Linux/Apache/Posetgres/PHP for implementation in 50 Dairy Cooperative Societies in our District. We have limited funds and the hardware proposed for each dairy society is a High end Linux PC with a Laser Printer.

We need all the desktop features to carry out our routine activites along with server features to run the dairy application.

Is it possible to install Apache Web server, Postgres Server and PHP along with Ubuntu Desktop.

Since it is totally free and open source, I would like to use Ubuntu for this project. 
I have initiated my application development in Fedora.

Can you please suggest a solution?

Regards
Simon Kuriakose

---

### Post by nhandler on 2008-05-23
You are able to install Apache, php, mysql/PostgreSQL (You mention one in the thread title, and the other one in the actual thread), and the Ubuntu desktop environment. This is commonly referred to as setting up a LAMP server:
**L**inux
**A**pache
**M**ySQL
**P**HP

Once you install the Ubuntu desktop environment, launch Synaptic Package Manager (System->Administration->Synaptic Package Manager). Now go to Edit->Mark Packages By Task. Check the "LAMP Server" box, and hit the Ok button. Now click on the Apply button. This will install your LAMP server.

---


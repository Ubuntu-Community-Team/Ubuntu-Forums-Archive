---
title: "UBUNTU 12.04 LTS - PHP Manuall Installation"
date: 2013-09-27
forum: Installation &amp; Upgrades
---

### Post by solution.wand on 2013-09-27
Hello Ubuntu Community, 

I install UBUNTU 12.04 LTS desktop on VMWARE Workstation. 

I installed run following commands to create PHP/mySQL environment using terminal.

sudo apt-get install apache2
sudo apt-get install mysql-server
sudo apt-get install php5 libapache2-mod-php5

These three commands worked fine for me but when I run following commands
sudo apt-get install php5-cli
sudo apt-get install php5-cgi
sudo apt-get install php5-mysql 

It displayed dependency error. How to git rid of dependency issue.

---

### Post by swapnil-indore on 2013-09-28
the best way to install php, mysql and apache is using the tasksel

apt-get install tasksel
tasksel
select LAMP Server and OK


--
[Swapnil Jain]("http://www.techpage3.com")

---


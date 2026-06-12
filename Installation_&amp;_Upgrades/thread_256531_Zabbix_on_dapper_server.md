---
title: "Zabbix on dapper server?"
date: 2006-09-13
forum: Installation &amp; Upgrades
---

### Post by Wil0 on 2006-09-13
Ive been trying to install zabbix for a while which has proved hard. I got stuck at one point once i installed most of it, so i started on a clean install, now i cant even start the install! It keeps telling me that:
> Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  zabbix-server: Depends: libsnmp5 (>= 5.1) but it is not installable
E: Broken packages
And i cant find the package anywhere...
how do install the package, and zabbix?
Is there a better snmp monitoring tool, that has a web interface and is compatible with windows servers too...

Thanks
Wil

---

### Post by zlemonz on 2006-09-13
I would like to try Zabbix as well, but am having the same difficulties as you are. I can't find a source for libsnmp5.

Have you had any luck, Wil?

---

### Post by Wil0 on 2006-09-14
no i havent, its driving me insane, really it is.
The thing is, that it started the install before, so im geussing that libsnmp5 is on the install cd? I dont know, but i do know that this is insane, i have libsnmp9 installed, and that doesent solve it either....
Are there any zabbix alternatives that are better?

---

### Post by Wil0 on 2006-09-15
Bump?

---

### Post by ma_xyz on 2006-09-21
i had the same problem, solution for me was to add the following debian repositories to /etc/apt/sources.list

deb [http://ftp.us.debian.org/debian](http://ftp.us.debian.org/debian) sarge main non-free contrib
deb [http://non-us.debian.org/debian-non-US](http://non-us.debian.org/debian-non-US) sarge/non-US main contrib non-free

everything installed ok and is working fine

---

### Post by thefish on 2006-09-29
Heres how I did it : [http://www.subvs.co.uk/server_monitoring_ubuntu_zabbix](http://www.subvs.co.uk/server_monitoring_ubuntu_zabbix)

---

### Post by intranet_man on 2006-11-06
Even after adding the sources mentioned by ma-xyz I had issues.

However, the following link helped get zabbix installed (note: use the --enable-static switch when you configure):

[http://www.zabbix.com/manual/v1.1/install_source_server.php](http://www.zabbix.com/manual/v1.1/install_source_server.php)

---


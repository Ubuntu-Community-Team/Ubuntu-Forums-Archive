---
title: "vmware-server and inetd in edgy"
date: 2006-11-05
forum: Installation &amp; Upgrades
---

### Post by mrkite00 on 2006-11-05
Hi all.

Just installed a fresh ubuntu 6.10! By the way, it looks great.

I am trying to install vmware-server (v1.0.1). When running vmware-config.pl, it ends with the following statement:

[I]
Unable to find any instance of the super-server "inetd" or "xinetd".  It is 
possible that you do not have one of these packages installed on this machine. 
Please install "inetd" or "xinetd".

If you do have "inetd" or "xinetd" installed, make sure that /etc/inetd.conf or
/etc/xinetd.d exists.
The configuration will continue, but you should re-run 
/usr/bin/vmware-config.pl after you fix the super-server.

Hit enter to continue. [/I]

If I hit enter, it returns me to the command prompt. If I try to start vmware, I get the following message:

[I]vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.
[/I]

I know inetd has been replaced in edgy, but it seems that /etc/inted has been kept (for compatibility is suppose?).

Anyone got an idea how to finish the setup?

Thanks

---

### Post by spanella47 on 2006-11-07
similar problem but with new install of vmware server.  I get through the beginning of the install and it tells me:

> Creating a new installer database using the tar3 format.

Installing the content of the package.

In which directory do you want to install the binary files? 
[/usr/bin] 

What is the directory that contains the init directories (rc0.d/ to rc6.d/)? 
[/etc] 

What is the directory that contains the init scripts? 
[/etc/init.d] 

Unable to copy the source file ./installer/services.sh to the destination file 
/etc/init.d/vmware.

Execution aborted.

anything i can do?

---

### Post by FidalgoMike on 2006-11-07
Greetings,

I upgraded to Edgy from Dapper with vmware server installed. I had followed the recipe from: [http://www.howtoforge.com/ubuntu_vmware_server](http://www.howtoforge.com/ubuntu_vmware_server), which included a bunch of prerequisite installs, xinetd among them. After the upgrade, I re-ran apt-get install linux-headers-`uname-r` build-essential, then re-ran the vmware-config.pl script to get vmware working again.

HTH,
Mike

---

### Post by mrkite00 on 2006-11-12
Thanks! Installed it tonight.

I was mixing up inetd and init (which has been replaced). After installing xinetd, everything went nice.

Thanks again.:D

---


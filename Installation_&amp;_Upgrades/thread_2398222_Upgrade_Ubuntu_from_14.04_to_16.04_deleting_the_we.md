---
title: "Upgrade Ubuntu from 14.04 to 16.04 deleting the webmin software"
date: 2018-08-09
forum: Installation &amp; Upgrades
---

### Post by veeruself on 2018-08-09
Hi All

I am trying to upgrade the Ubuntu OS from 14.04 LTS to 16.04 LTS.  However during the upgrade process , it is removing the installed webmin software and after successful reboot of the system , I am not able to access my webmin.

I found the way to re-install latest webmin in Ubuntu 16.04 LTS once the machine got rebooted.  However I want to retain the webmin software and complete the upgrade.


Can anyone throw some light , how to prevent installing webmin software while the system is getting upgraded.  And make my webmin works after successful upgrade to 16.04 LTS.

I have blocked due to this problem since many days.  Any quick help really appreciated.

---

### Post by TheFu on 2018-08-09
Welcome to the forums.

To ensure the upgrade process works as well as possible, non-core repositories are removed.  The upgrade is performed, then you can re-enable the non-core repositories.  That is the process.
I don't know any workaround.

Webmin is not part of Ubuntu supported software.

---

### Post by veeruself on 2018-08-09
It is a really a pain point for me as I am doing upgrade from webmin by running the script. If it removes the webmin during the upgrade process. I totally loosing the control and I have manually go to each and every box to install the webmin again.  We have thousands of Boxes and it is not acceptable to our customers.

Is there any process I can install the webmin post successful upgrade and during the reboot by running any script ? is this again efficient way to do it ?

---

### Post by TheFu on 2018-08-09
Any devops tool will do what you need, assuming you use the version in the Canonical repos.  

If you have thousands of machines, why use webmin at all?

And if you are using virtualization or containers, there are many better solutions.

---

### Post by veeruself on 2018-08-13
Thanks for your response.

All are physical machines with webmin installed without internet connection.  Since the machine doesn't expose to internet connection , I am creating a script which can upgrade the OS.

I am running this script from webmin to upgrade the system.  I did the same for upgrading the OS from 12.04 to 14.04.  During that upgrade webmin was not removed.  However for upgrade from 14.04 to 16.04 , webmin is getting removed.  Due to this reason I am blocked.   Just wanted to understand why webmin is getting removed in this case.  

In general , we install many software's  and those should not be affected because of upgrade. All installed softwares should be there even after successful upgrade.

---

### Post by TheFu on 2018-08-13
> **veeruself said:**
> 
In general , we install many software's  and those should not be affected because of upgrade. All installed softwares should be there even after successful upgrade.

They should if dependencies are impacted.

Nobody here works for Canonical. We are only volunteers.  If you need corporate support, might I suggest a support contract with Canonical?

---


---
title: "upgrade to 8.10 Alpha 4"
date: 2008-08-19
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by BoojiBoy on 2008-08-19
How do I upgrade my Kubuntu 8.04.1 to 8.10 Alpha? I tried "do-release-upgrade" and it says "No new release found". Thanks

---

### Post by overdrank on 2008-08-19
> **BoojiBoy said:**
> How do I upgrade my Kubuntu 8.04.1 to 8.10 Alpha? I tried "do-release-upgrade" and it says "No new release found". Thanks

Hi and you can find info here
[http://www.ubuntu.com/testing/intrepid/alpha4](http://www.ubuntu.com/testing/intrepid/alpha4)
Although intrepid is still in testing stage and is not recommended for a primary system. If you would like to install on a separate partition for testing that is a good idea.

---

### Post by BoojiBoy on 2008-08-19
thanks for the info, but my Kubuntu 8.04.1 doesn't know that "update-manager -d" command.

---

### Post by Slug71 on 2008-08-19
Download the .iso burn it to disc and install from that. When i tried to do the upgrade from Hardy to Intrepid via update-manager-d it didnt work for me.

---

### Post by philinux on 2008-08-19
This might help. 

[http://ubuntuguide.org/wiki/Ubuntu:Hardy#How_to_upgrade_from_Hardy_Heron_to_Intrepid_Ibex_.28for_developers_and_bug_reports_only.29](http://ubuntuguide.org/wiki/Ubuntu:Hardy#How_to_upgrade_from_Hardy_Heron_to_Intrepid_Ibex_.28for_developers_and_bug_reports_only.29)

---

### Post by stevebakerj on 2008-08-24
> **BoojiBoy said:**
> How do I upgrade my Kubuntu 8.04.1 to 8.10 Alpha? I tried "do-release-upgrade" and it says "No new release found". Thanks

Update your sources list /etc/apt/sources.list  from Hardy to Intrepid, then:

```
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by gjoellee on 2008-08-24
it is recommended to upgrade with a CD, the upgrade via internet often crashes the system. This will be fixed ofcourse, but Intrepid is still in alpha, and at the moment there are a lot of bug around as well :S

---

### Post by Spydr4590 on 2008-08-24
> **Slug71 said:**
> Download the .iso burn it to disc and install from that. When i tried to do the upgrade from Hardy to Intrepid via update-manager-d it didnt work for me.


Didn't work for me either. Try this [http://cdimage.ubuntu.com/daily/current/](http://cdimage.ubuntu.com/daily/current/)

---


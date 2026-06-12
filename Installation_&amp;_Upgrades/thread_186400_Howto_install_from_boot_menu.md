---
title: "Howto install from boot menu ???"
date: 2006-06-01
forum: Installation &amp; Upgrades
---

### Post by Uthen Phutneam on 2006-06-01
My notebook is Acer and it use ATI Redeon x700. I can't boot to graphic mode and install from that. So, anyone help me to install from boot menu please.:-|

---

### Post by karthik085 on 2006-06-01
Use recover mode. Add dapper respositories to your sources.list in /etc/apt.
sudo apt-get update
sudo apt-get dist-upgrade

Also, if you want to save same space, you can remove unused packages after install by
sudo apt-get clean
sudo apt-get autoclean

---

### Post by Uthen Phutneam on 2006-06-02
[QUOTE=karthik085]Use recover mode. Add dapper respositories to your sources.list in /etc/apt.
sudo apt-get update
sudo apt-get dist-upgrade

Also, if you want to save same space, you can remove unused packages after install by
sudo apt-get clean
sudo apt-get autoclean[/QUOTE]

I just want to know how to install from live cd after i insert it and boot form it.
Thanks,

---

### Post by Uthen Phutneam on 2006-06-02
[QUOTE=Uthen Phutneam]My notebook is Acer and it use ATI Redeon x700. I can't boot to graphic mode and install from that. So, anyone help me to install from boot menu please.:-|[/QUOTE]

_Revise_
My notebook is Acer and it use ATI Redeon x700. I can't boot **[COLOR="Red"]from live cd[/COLOR]** to graphic mode and install from that. So, anyone help me to install from boot menu please.

---

### Post by karthik085 on 2006-06-02
[QUOTE=Uthen Phutneam]_Revise_
My notebook is Acer and it use ATI Redeon x700. I can't boot **[COLOR="Red"]from live cd[/COLOR]** to graphic mode and install from that. So, anyone help me to install from boot menu please.[/QUOTE]
Use text based method:
[http://ubuntuforums.org/showpost.php?p=1079841&postcount=18](http://ubuntuforums.org/showpost.php?p=1079841&postcount=18)

You are not the only one with this problem. There were many reports similar to this in the Ubuntu forums.

---


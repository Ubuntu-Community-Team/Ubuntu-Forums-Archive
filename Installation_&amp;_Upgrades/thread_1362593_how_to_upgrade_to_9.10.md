---
title: "how to upgrade to 9.10"
date: 2009-12-23
forum: Installation &amp; Upgrades
---

### Post by mahdiar on 2009-12-23
hi
i cannot upgrade my ubuntu . there is no link in the "update manager" .

---

### Post by Grenage on 2009-12-23
```
sudo apt-get dist-upgrade
```

---

### Post by slakkie on 2009-12-23
> **Grenage said:**
> ```
sudo apt-get dist-upgrade
```

Be more verbose please :)

[https://help.ubuntu.com/community/Upgrades](https://help.ubuntu.com/community/Upgrades)

---

### Post by Grenage on 2009-12-23
Ok, I was a little concise ;)

The above command, used in a terminal, should allow you to upgrade.

---

### Post by mjjna on 2009-12-23
or you can configure the update manager to use not only the Long Term Support version.

---

### Post by mahdiar on 2009-12-24
> **Grenage said:**
> Ok, I was a little concise ;)

The above command, used in a terminal, should allow you to upgrade.

it doesn't work .
i miss some infos . two weeks ago i click on the button to upgrade but i had to stop it . after that the upgrade button disappeared .

---

### Post by Grenage on 2009-12-24
What error do you get?

---

### Post by mahdiar on 2009-12-24
> **Grenage said:**
> What error do you get?
there isnt any error . 

[I]Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

[/I]

---

### Post by slakkie on 2009-12-24
Please run lsb_release -a

And please have a look at the wiki page I showed earlier: [https://help.ubuntu.com/community/Upgrades](https://help.ubuntu.com/community/Upgrades) . Thnx.

---

### Post by mahdiar on 2009-12-24
i don't know why but i cannot open that url .

---

### Post by tachuela on 2009-12-24
Open your Terminal and type: uname -a, then press 'Enter'. Copy and paste the results here.

---

### Post by slakkie on 2009-12-24
> **mahdiar said:**
> i don't know why but i cannot open that url .

Fixed the glitch :)

---

### Post by mahdiar on 2009-12-27
That's it :
Linux ubuntu 2.6.28-17-generic #58-Ubuntu SMP Tue Dec 1 18:57:07 UTC 2009 i686 GNU/Linux

---

### Post by mahdiar on 2009-12-27
> **slakkie said:**
> Fixed the glitch :)
Yeaaaaaaaah you're right 

:D

---

### Post by ZootNerper on 2009-12-28
I have the same probelm with the disppearing "upgrade" button. I cancelled an upgrade and now do not see the button.

I have read the suggested webpage (Updates).

/etc/update-manager/release-upgrades file has prompt=normal

Output from command: lsb_release -a

No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 9.04
Release:	9.04
Codename:	jaunty

Output from uname -a

Linux Bollocks7 2.6.28-17-generic #58-Ubuntu SMP Tue Dec 1 21:27:25 UTC 2009 x86_64 GNU/Linux

Output from sudo apt-get dist-upgrade

[sudo] password for zoot: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

I have also tried apt-get autoremove / clean /dselect-upgrade. All remove nothing.

Any help would be appriciated.

-- Zoot

---

### Post by slakkie on 2009-12-30
A dist-upgrade doesn't automagicly upgrade your OS, you need to specify the correct sources.list for that to happen. Maybe that should be outlined better in the Upgrades wiki page. 

Eitherway, I recommend that you upgrade via do-release-upgrade or the GUI update-manager. Could you run either tool and see what happens? If it doesn't work like expected please post your sources.list in this topic and the output of whatever command you have executed for the upgrade.

---


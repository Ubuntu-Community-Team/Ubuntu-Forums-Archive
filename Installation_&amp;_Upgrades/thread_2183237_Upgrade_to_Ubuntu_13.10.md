---
title: "Upgrade to Ubuntu 13.10?"
date: 2013-10-24
forum: Installation &amp; Upgrades
---

### Post by tommy2k10 on 2013-10-24
Yesterday, Ubuntu 13.04 notified me of Ubuntu 13.10, and I told it to remind me later.  Ever since then I don't get a reminder.  How can I upgrade?

---

### Post by sudodus on 2013-10-24
First of all, if 13.04 is working well for you, I suggest that you wait 2-4 weeks to allow for the worst bugs to be fixed.

I think that if you start the graphical update program, it will show updating to the next version as one alternative.

```
/usr/bin/update-manager
```

---

### Post by Dennis N on 2013-10-24
To upgrade from 13.04 to 13.10, see: 

[http://www.ubuntu.com/download/desktop/upgrade](http://www.ubuntu.com/download/desktop/upgrade)

---

### Post by tommy2k10 on 2013-10-24
I did that thankyou Dennis, but the upgrade hasn't come up anymore!
I think I will wait for a month.

---

### Post by Dennis N on 2013-10-24
Be sure that your system is up to date. Otherwise, I believe distribution upgrade may not be offered. Also, be sure in Settings that notify is set to immediately in both boxes.

You could also try **sudo do-release-upgrade** in the terminal. See second answer here: [http://askubuntu.com/questions/215267/apt-get-dist-upgrade](http://askubuntu.com/questions/215267/apt-get-dist-upgrade)

The man page also mentions an option **-m desktop** for regular upgrades of a desktop system:

**sudo do-release-upgrade -m desktop**

I have never used either of these terminal commands myself so can't advise further. Use at your own risk.

---

### Post by grahammechanical on 2013-10-24
To avoid problems with the upgrade revert the desktop to the default condition, remove any PPAs in Software and Updates, and activate the Nouveau open source video driver instead of any proprietary video driver. But best of all do not be in a hurry unless you want to become a tester of how well Ubuntu 13.04 upgrades to 13.10. You still have 3 months support for 13.04. No need to rush. Oh, and backup your important data.

Regards.

---

### Post by ||0BL1v10N|| on 2013-10-24
You can upgrade at any time in the terminal by using the below sudo code;

Code: sudo apt-get upgrade

However, as advised it is sometimes good to wait a week or two for the all the major bugs to be fixed. If you can't wait (like most of us) I would advise to do a full back-up on an external hard drive "search for back-up" in the unity search. Once completed you can begin the upgrade and should there be any problems, you can reverse back.

Hope this helps,

Niall

---


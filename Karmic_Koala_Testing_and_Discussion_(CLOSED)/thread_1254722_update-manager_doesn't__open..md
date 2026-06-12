---
title: "update-manager doesn't  open."
date: 2009-08-31
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by garvinrick4 on 2009-08-31
rick@ubuntu:~$ update-manager
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 103, in <module>
    app = UpdateManager(data_dir, options)
  File "/usr/lib/python2.6/dist-packages/UpdateManager/UpdateManager.py", line 111, in __init__
    SimpleGtkbuilderApp.__init__(self, datadir+"glade/UpdateManager.ui")
  File "/usr/lib/python2.6/dist-packages/UpdateManager/SimpleGtkbuilderApp.py", line 33, in __init__
    self.builder.add_from_file(path)
glib.GError: Duplicate object id 'image15' on line 1088 (previously on line 957)

anyone have same problem.

---

### Post by anders_c_ on 2009-08-31
Same here, appearance wont open either

---

### Post by MacUntu on 2009-08-31
image15, vbox18, label30, and label31 are used twice in /usr/share/update-manager/glade/UpdateManager.ui

and

hbox1, label4, image3, and label5 in /usr/share/gnome-control-center/ui/appearance.ui.

---

### Post by exploder on 2009-08-31
Same thing here too. Update Manager and Appearance will not open.

---

### Post by zoomy942 on 2009-08-31
confirmed for me too.  anyone file a bug or should i?

---

### Post by terry_gardener on 2009-08-31
looks like it has already been reported
 
[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/417301]("https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/417301")

---

### Post by chrisccoulson on 2009-08-31
I've just fixed gnome-appearance-properties, so it should work again now.

---

### Post by alligoodw on 2009-08-31
GDebi Package Installer fails to open as well. . .same with Appearance and Update Manager.

---

### Post by rburkartjo on 2009-08-31
same problem here

---

### Post by terry_gardener on 2009-08-31
with latest updates update-manager now works

---

### Post by alligoodw on 2009-08-31
Confirmed.  Update-Manager does work.  Appearance and GDebi still not working.

---

### Post by exploder on 2009-08-31
An update just fixed Update Manager.

Edit: Appearance settings are now working again.

---

### Post by MacUntu on 2009-08-31
Appearance dialog fixed.

---

### Post by rburkartjo on 2009-08-31
after last update it is working

---

### Post by nhasian on 2009-08-31
if update-manager fails you can always use:
```

sudo apt-get update && sudo apt-get upgrade
```

or if your real adventurous

```
sudo apt-get dist-upgrade
```

course I did a dist-upgrade this morning and it pulled down the new linux kernel 2.6.31-8 but not the mods, and when i rebooted gnome wouldnt load anymore and i was stuck at a command prompt.

lucky for me i had just backed up my partition with Clonezilla before attempting the dist-upgrade.  so i was able to restore my partition and get back up and running in 10 mins.

I guess I will try again after alpha 5 is released.

---

### Post by tekstr1der on 2009-08-31
> **alligoodw said:**
> GDebi Package Installer fails to open as well. . .

Filed this one earlier today:

[https://bugs.launchpad.net/ubuntu/+source/gdebi/+bug/422096](https://bugs.launchpad.net/ubuntu/+source/gdebi/+bug/422096)

---

### Post by zoomy942 on 2009-08-31
> **nhasian said:**
> if update-manager fails you can always use:
```

sudo apt-get update && sudo apt-get upgrade
```

or if your real adventurous

```
sudo apt-get dist-upgrade
```

course I did a dist-upgrade this morning and it pulled down the new linux kernel 2.6.31-8 but not the mods, and when i rebooted gnome wouldnt load anymore and i was stuck at a command prompt.

lucky for me i had just backed up my partition with Clonezilla before attempting the dist-upgrade.  so i was able to restore my partition and get back up and running in 10 mins.

I guess I will try again after alpha 5 is released.


When update manager doesn't work, I just go to synaptics, do a reload then mark upgrades and apply.

---

### Post by kaanchan on 2009-09-01
You said latest update fixes this. How can I get the latest update without update-manager itself? Any other command?

thanks

---

### Post by zoomy942 on 2009-09-01
> **kaanchan said:**
> You said latest update fixes this. How can I get the latest update without update-manager itself? Any other command?

thanks


see my post above

---


---
title: "polkit-gnome-authorization not found"
date: 2009-10-18
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by linusr on 2009-10-18
anyone having issue with System->Administrations->Authorizations?

linusr@DeepBlue:~$ polkit-gnome-authorization
The program 'polkit-gnome-authorization' is currently not installed.  You can install it by typing:
sudo apt-get install policykit-gnome
polkit-gnome-authorization: command not found
linusr@DeepBlue:~$ 

why was the package removed and menu exists?

---

### Post by VMC on 2009-10-18
Are you saying you don't have policykit inside the Authorizations gui? 

What's here:

```
ls /usr/bin/polkit*
```

---

### Post by linusr on 2009-10-19
> **VMC said:**
> Are you saying you don't have policykit inside the Authorizations gui? 

What's here:

```
ls /usr/bin/polkit*
```

looks there isn't much in that folder,

```
linusr@DeepBlue:~$ ls /usr/bin/polkit*
/usr/bin/polkit-action  /usr/bin/polkit-config-file-validate
/usr/bin/polkit-auth    /usr/bin/polkit-policy-file-validate
linusr@DeepBlue:~$ 
```

---

### Post by tekstr1der on 2009-10-19
The menu item was removed along with the package for me here. Maybe it's just lingering in panel. Have you logged out or rebooted since polkit-gnome was removed? Try:```
killall gnome-panel
```

---

### Post by linusr on 2009-10-19
> **tekstr1der said:**
> The menu item was removed along with the package for me here. Maybe it's just lingering in panel. Have you logged out or rebooted since polkit-gnome was removed? Try:```
killall gnome-panel
```

Yes, I have restarted after update. This menu was there all along...

killall gnome-panel didn't work. May be I have to delete it manually

---


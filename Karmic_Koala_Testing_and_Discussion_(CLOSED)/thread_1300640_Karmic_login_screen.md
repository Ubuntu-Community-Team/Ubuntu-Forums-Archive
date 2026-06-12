---
title: "Karmic login screen"
date: 2009-10-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by arepaking on 2009-10-25
Hi everyone,
I understand that Karmic had implemented a new GDM with less functionality but that supposes to reduce the boot time.

My current login screen presents all the users available and you need to choose among those. Since I do not want to show what users are created in my system... do you know if there is a way to change this so the user can type the username instead of picking it from this list?

Thanks in advance,
AK

---

### Post by plasma-engineer on 2009-10-25
I agree.  One of the security features that I liked about using Ubuntu is that anyone turning on my PC cannot easily see the names of the accounts that exist on it.  Previously they needed to guess the account name as well as the password.  Now the work of the 'hackers' is halved!  Please can someone help us to 'downgrade' again to the old login method?

---

### Post by plasma-engineer on 2009-10-27
Oh come on!!  There must be more that two of us who see this as a security risk!

---

### Post by JillSwift on 2009-10-27
Three.

I am under the impression the lack of themes is a matter of waiting on a more secure theme manager. If this is so, then I'm less annoyed by the forced user list.

---

### Post by picopir8 on 2009-10-27
There is a gconf setting for it, but it did not have any effect on my machine (even after a reboot), might be worth a try for you though.

sudo -u gdm gconftool-2 --type bool --set /apps/gdm/simple-greeter/disable_user_list 'true'

---

### Post by plasma-engineer on 2009-10-28
Thank you so much - that gconf setting worked beautifully for me.

---

### Post by plasma-engineer on 2009-10-28
...and sorry the message board chose that thumbs-down icon for me on the third attempt to submit the message.  It should definitely be a thumbs-up!

---

### Post by rockin_goliath on 2009-10-28
> **picopir8 said:**
> There is a gconf setting for it, but it did not have any effect on my machine (even after a reboot), might be worth a try for you though.

sudo -u gdm gconftool-2 --type bool --set /apps/gdm/simple-greeter/disable_user_list 'true'

I figured out why it did not work for you. You have to set the gconf key as either default or mandatory. Find the key in gconf-editor, right click and click "Set as default" or "Set as mandatory." 

To change it back, run gconf-ediitor as root (gksu gconf-editor), go to File -> New Default Window or File -> New Mandatory Window, find the key, right click and select "Unset Key." Then it should be back to its default setting.

---


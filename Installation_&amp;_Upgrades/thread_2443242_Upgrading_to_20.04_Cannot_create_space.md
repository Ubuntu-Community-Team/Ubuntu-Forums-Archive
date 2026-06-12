---
title: "Upgrading to 20.04: Cannot create space"
date: 2020-05-13
forum: Installation &amp; Upgrades
---

### Post by tapasray on 2020-05-13
My 20.04 upgrade got stuck as there was insifficient space. The error message said I needed to create space by emptying the Recycle Bin and cleaning out temporary files from previous installations with "sudo apt-get clean". I am unable to complete the second operation. Please see below my terminal status:

```
tapas@tapas-HP-Convertible-x360-11-ab0XX:~$ sudo apt-get clean
[sudo] password for tapas: 
tapas@tapas-HP-Convertible-x360-11-ab0XX:~$ sudo apt-get clean
tapas@tapas-HP-Convertible-x360-11-ab0XX:~$ apt-get clean
E: Could not open lock file /var/cache/apt/archives/lock - open (13: Permission denied)
E: Unable to lock directory /var/cache/apt/archives/
E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)
E: Unable to lock directory /var/lib/apt/lists/
```

I shall really appreciate some help with this.

---

### Post by dino99 on 2020-05-13
Apt is locked, that is the problem
Be sure to close other updating tools (synaptic, update manager,software...)

---

### Post by Dennis N on 2020-05-13
Upgrades need some working space in your root partition. Besides cleaning out files as suggested by the message, you may also need to increase size of your partition (or LV) when your root is close to full.

Check available space in / with:```

df -h
```

If you do a new install and overwrite the partition, you can probably get by with the space you have.

---

### Post by cmcanulty on 2020-05-13
I stopped those errors by uninstalling "unanttended-upgrades" . If you try that route make sure you regularly manually update and upgrade.

---

### Post by tapasray on 2020-05-13
Thank you. Will do.

---

### Post by tapasray on 2020-05-13
> **dino99 said:**
> Apt is locked, that is the problem
Be sure to close other updating tools (synaptic, update manager,software...)

Thanks. Will do.

---

### Post by tapasray on 2020-05-13
> **Dennis N said:**
> Upgrades need some working space in your root partition. Besides cleaning out files as suggested by the message, you may also need to increase size of your partition (or LV) when your root is close to full.

Check available space in / with:```

df -h
```

If you do a new install and overwrite the partition, you can probably get by with the space you have.

Let's see. I'll try to delete some data and see if this can be avoided.

---

### Post by tapasray on 2020-05-13
> **cmcanulty said:**
> I stopped those errors by uninstalling "unanttended-upgrades" . If you try that route make sure you regularly manually update and upgrade.

This sounds good. Will set this option. Thank you.

---

### Post by Impavidus on 2020-05-13
> **tapasray said:**
> My 20.04 upgrade got stuck as there was insifficient space. The error message said I needed to create space by emptying the Recycle Bin and cleaning out temporary files from previous installations with "sudo apt-get clean". I am unable to complete the second operation. Please see below my terminal status:

```
tapas@tapas-HP-Convertible-x360-11-ab0XX:~$ sudo apt-get clean
[sudo] password for tapas: 
tapas@tapas-HP-Convertible-x360-11-ab0XX:~$ sudo apt-get clean
tapas@tapas-HP-Convertible-x360-11-ab0XX:~$ apt-get clean
E: Could not open lock file /var/cache/apt/archives/lock - open (13: Permission denied)
E: Unable to lock directory /var/cache/apt/archives/
E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)
E: Unable to lock directory /var/lib/apt/lists/
```

I shall really appreciate some help with this.

It seems to me that you were able to complete the second operation on first try. You ran the first command, entered your password and it gave no errors. So it worked. Then you ran it again, this time it didn't ask for a password because it was less than 15 minutes since you last entered it for sudo, and again it ran without issues (but didn't remove any files, as there were none). The third attempt failed as you didn't use root permissions.

As a rule, if you get no output, the command completed succesfully. If something goes wrong, you get an error message.

The suggestion to empty the trash can and clean up package cache is a standard message. There may not be enough stuff in cache or trash can to make it effective.

---

### Post by tapasray on 2020-05-13
> **Impavidus said:**
> It seems to me that you were able to complete the second operation on first try. You ran the first command, entered your password and it gave no errors. So it worked. Then you ran it again, this time it didn't ask for a password because it was less than 15 minutes since you last entered it for sudo, and again it ran without issues (but didn't remove any files, as there were none). The third attempt failed as you didn't use root permissions.

As a rule, if you get no output, the command completed succesfully. If something goes wrong, you get an error message.

The suggestion to empty the trash can and clean up package cache is a standard message. There may not be enough stuff in cache or trash can to make it effective.

Thanks so much for the explanation. This will help me in future.

---

### Post by tapasray on 2020-05-13
I have been able to install 20.04 after freeing some space by moving some data to another drive. 

Many thanks to all of you.

---


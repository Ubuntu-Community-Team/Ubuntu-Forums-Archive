---
title: "How to update packages"
date: 2018-05-27
forum: Installation &amp; Upgrades
---

### Post by fat61 on 2018-05-27
Hello how I can update packages? I can update 13 packages and they are 10 security updates. I'm using Ubuntu 16.04.4 LTS

Thanks.

---

### Post by deadflowr on 2018-05-27
On Ubuntu Desktop version:
Open Software Updater and click on *Install Now*

On Ubuntu Server version:
run
```
sudo apt update
sudo apt full-upgrade
```
select Y for yes.

You'll need to enter your user password.
(The password field for the server version will be blank (invisible)
so enter as you remember it.)

---

### Post by Bashing-om on 2018-05-27
deadflowr ninja :)

---

### Post by fat61 on 2018-05-27
> **deadflowr said:**
> On Ubuntu Desktop version:
Open Software Updater and click on *Install Now*

On Ubuntu Server version:
run
```
sudo apt update
sudo apt full-upgrade
```
select Y for yes.

You'll need to enter your user password.
(The password field for the server version will be blank (invisible)
so enter as you remember it.)
And this will not upgrade Ubuntu from 16.04 to 18 ?

---

### Post by deadflowr on 2018-05-27
> **fat61 said:**
> And this will not upgrade Ubuntu from 16.04 to 18 ?

No.
It only upgrades the current system.
It does not upgrade Ubuntu releases.

Those require a different set of commands and actions.
For a server version upgrade to another release the command is
```
do-release-upgrade
```
On the Desktop version upgrades (when available) will add an Upgrade option next the Install Now button.
(And it is very clear what it is as you have to navigate several windows to start the upgrade process, and you have the option to cancel at any time before the upgrade finally begins.)

*The upgrade option is currently not normally available anyway for an upgrade from 16.04 to 18.04.
That will be made available sometime in late July or early August.
It is available, currently, if you run the updaters in development mode
```
do-release-upgrade -d
```
And for the software updater
```
update-manager -d
```

Hope it helps

---

### Post by fat61 on 2018-05-27
> **deadflowr said:**
> 
...

Thanks

---


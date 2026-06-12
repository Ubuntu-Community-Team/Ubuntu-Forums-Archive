---
title: "Get Stuck ubuntu 16.4 after updating"
date: 2017-02-27
forum: Installation &amp; Upgrades
---

### Post by sayres561 on 2017-02-27
Hi guys.i have updated my ubuntu and after updating and restarting when i enter pasword for login, ubuntu stuck and nothing is not work.
How can i see where is my problem and how can i fix that?

Edit:
But when i change my linux kernel everything is ok.my new kernel is 4.4.0-64 and when im running ubuntu with this kernel it is stuck.
My previous kernel is 4.4.0-31 and in this kernel everything is ok.
I found out that when i am login with guest user ,ubuntu doesn't stuck but in my user it stuck!!!

---

### Post by Bucky Ball on 2017-02-27
Welcome. Open a terminal and try these three commands, hitting return and letting it do its thing after each command.

```
sudo apt autoremove
sudo apt update
sudo apt full-upgrade
```

That last command will NOT upgrade your release to a newer one. Just all the software in your current one. Reboot and let us know if the new kernel behaves any better.

---

### Post by sayres561 on 2017-02-28
I can not login to my user.where is i have to run these commands?my last kernel?

---

### Post by Bucky Ball on 2017-02-28
Yes. Login to the last working kernel, input those commands, reboot to the new kernel and see if it works.

---

### Post by sayres561 on 2017-02-28
> **Bucky Ball said:**
> Welcome. Open a terminal and try these three commands, hitting return and letting it do its thing after each command.

```
sudo apt autoremove
sudo apt update
sudo apt full-upgrade
```

That last command will NOT upgrade your release to a newer one. Just all the software in your current one. Reboot and let us know if the new kernel behaves any better.

I do that but nothing changed. Ubuntu still stuck after login .
Why i can go to guest user by this kernel?

---

### Post by sayres561 on 2017-02-28
after that i insert my pass and press enter I have switched to console by ctrl+alt+F3 immediately, and see this message:
end kernel panic - not syncing: Fatal exception interrupt and then everything was freezed. 
what can i do?

---


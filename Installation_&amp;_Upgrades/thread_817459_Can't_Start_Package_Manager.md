---
title: "Can't Start Package Manager"
date: 2008-06-03
forum: Installation &amp; Upgrades
---

### Post by ApologetixFan on 2008-06-03
Good afternoon all.

I just today (06.03.2008) upgraded my Ubuntu Hardy installation. Now I cannot start the Synaptic Package Manager. It shows up in the task bar, then goes away without starting. Anybody know what I have done wrong?

Thanks.

---

### Post by Partyboi2 on 2008-06-03
can you open a terminal (Applications>Accessories>Terminal) and post the output to
```
cat /etc/hosts
```

---

### Post by PmDematagoda on 2008-06-03
You would also want to post the output of:-
```
hostname
```

---

### Post by ChameleonDave on 2008-06-03
Another diagnostic that you can do is to start Synaptic by typing this:

```
sudo synaptic
```

... in a console, instead of just clicking on the Synaptic icon.  When Synaptic crashes, it should leave error messages on the console.  You can copy them and paste them here.

Also, can you still install programs?  For example, if you type the following:

```
sudo apt-get install mousepad
```

...does it install Mousepad for you?

---


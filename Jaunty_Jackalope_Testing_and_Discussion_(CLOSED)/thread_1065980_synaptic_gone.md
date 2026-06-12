---
title: "synaptic gone?/"
date: 2009-02-10
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by ubername on 2009-02-10
Hhi

I seem to have lost synaptic from System>Administration menu.

If I try to install it I get:

sudo apt-get install synaptic
[sudo] password for john: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  synaptic: Depends: libapt-inst-libc6.8-6-1.1 but it is not installable
            Depends: libapt-pkg-libc6.8-6-4.6 but it is not installable
E: Broken packages

Any clues

TIA

---

### Post by TCSnyder on 2009-02-10
try to run 

```
gksu synaptic
```

if it runs you just need to make an new menu icon

---

### Post by TCSnyder on 2009-02-10
or you could try to install it with


```
sudo aptitude install synaptic
```

---

### Post by Vaun on 2009-02-10
Depencies are synced now.  

Try :

```
sudo apt-get install --reinstall ubuntu-desktop
```

That should patch things up for you.
:)

---

### Post by ubername on 2009-02-12
> **Vaun said:**
> Depencies are synced now.  

Try :

```
sudo apt-get install --reinstall ubuntu-desktop
```

That should patch things up for you.
:)

Thanks, fixed now.

---


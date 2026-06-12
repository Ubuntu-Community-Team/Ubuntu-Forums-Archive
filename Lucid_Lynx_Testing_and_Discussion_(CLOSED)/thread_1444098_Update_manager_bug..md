---
title: "Update manager bug."
date: 2010-03-31
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by TheNerdAL on 2010-03-31
I don't know where to post bugs so I'm posting it here. When I click "Check" in Update Manager and after it finishes checking it says this: 

"Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Read error - read (5: Input/output error), E:The package lists or status file could not be parsed or opened.'"

---

### Post by lavinog on 2010-03-31
```

ubuntu-bug update-manager

```
I believe you might need to setup a launchpad account first.

---

### Post by TheNerdAL on 2010-03-31
> **lavinog said:**
> ```

ubuntu-bug update-manager

```
I believe you might need to setup a launchpad account first.

It gives me this: "Could not determine the package name" or something like that.

---

### Post by TheNerdAL on 2010-04-01
Bump. Anyone?

---

### Post by TheNerdAL on 2010-04-01
D:

---

### Post by lavinog on 2010-04-01
> **TheNerdAL said:**
> It gives me this: "Could not determine the package name" or something like that.

I just tried it on my lucid machine and it worked.

what happens if you update with the terminal:
```

sudo apt-get update

sudo apt-get upgrade

```

After updating see if the update manager still gives you that error.

---

### Post by cariboo on 2010-04-01
Please don't bump your thread more than once every 24 hours.

---

### Post by dino99 on 2010-04-01
verify that you only ask about legal Lucid repo (no other release, no third party, no ppa)

then clean your cache and update again (using main server)
if problem are still there, remove/purge then reinstall bum

---

### Post by TheNerdAL on 2010-04-01
> **lavinog said:**
> I just tried it on my lucid machine and it worked.

what happens if you update with the terminal:
```

sudo apt-get update

sudo apt-get upgrade

```

After updating see if the update manager still gives you that error.

Thanks Man!!!! :D The updating via terminal seemed to work! Thanks again!

---


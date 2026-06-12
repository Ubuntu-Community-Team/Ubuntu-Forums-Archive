---
title: "software center broken"
date: 2011-04-25
forum: Installation &amp; Upgrades
---

### Post by thedruz on 2011-04-25
I Keep getting a dialogue window prompting me to repair it, it returns the error " E:I wasn't able to locate file for the ultimate-edition-nautilus-scripts package. This might mean you need to manually fix this package.: ", after looking around the forums & trying many of the techniques including creating an empty file & running aptitude -f install as well as a few more commands mentioned in various threads, all to no avail, I am stuck with the same message.
Is there any way to totally uninstall & reinstall apt getting rid of any changes that would be causing this or is there a simpler fix I have just overlooked ?. Help urgently needed. Thanks.

---

### Post by mörgæs on 2011-04-26
Please write the exact commands you have tried and the corresponding error messages.

---

### Post by conradin on 2011-04-26
try 
```

dpkg --configure -a

```

---

### Post by Rubi1200 on 2011-04-26
> **mörgæs said:**
> Please write the exact commands you have tried and the corresponding error messages.

+1 to this suggestion.

Also, if you decide to run it, the command is ```
sudo dpkg --configure -a 
```and not as posted previously.

---


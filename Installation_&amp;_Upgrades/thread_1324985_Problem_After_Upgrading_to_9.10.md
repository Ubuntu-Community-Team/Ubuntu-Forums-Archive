---
title: "Problem After Upgrading to 9.10"
date: 2009-11-13
forum: Installation &amp; Upgrades
---

### Post by arunabhashil on 2009-11-13
Hi,
I am facing a problem after upgrading my Ubuntu 9.04 to 9.10.
Problem is that after the up-gradation process when i loged in again i found my broadband is not working. I just tried to see if all my network settings are ok or not. But I could not, because it says that I don't have sufficient privilege.It also asked for a password at that time and i was giving my user-password what i use for other administrative authentication. 
Anyway, since i could not enter in the edit mode of my broad band connection settings, i am not being able to rectify the problem ........ if any. Again this is not happening for the ethernet connection setting(eth0).

Please somebody help. I am using Ubuntu for just last two weeks. I do not know much about this. So plz help.

---

### Post by MichealH on 2009-11-13
There could be 2 possibilities to why this isn't working:

1)You upgraded the clean install will work better.
2)Your card may be restricted or not supported in 9.10.

---

### Post by JBAlaska on 2009-11-13
If network manager was asking for your password, that is the PW for your router WPA or WEP. Please post your wireless make/model so we have more information.

---

### Post by arunabhashil on 2009-11-13
How would i know about the compatibility of my card??

---

### Post by arunabhashil on 2009-11-13
Dear JBAlaska,
Let me check n try with that password also.

---

### Post by JBAlaska on 2009-11-13
> **arunabhashil said:**
> How would i know about the compatibility of my card??

Try running this command in a terminal:
```
sudo iwconfig
```

Also I'm guessing this a laptop, the make and model will help

---

### Post by arunabhashil on 2009-11-13
> **JBAlaska said:**
> Try running this command in a terminal:
```
sudo iwconfig
```Also I'm guessing this a laptop, the make and model will help

No, it's not.
It,s my Athlon X2 3Ghz with MSI MB desktop.
I would try whatever suggested at night after my office.
Then i would also provide you more specific info.............

---


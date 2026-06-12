---
title: "&quot;victim of the recent change in the linux-firmware-nonfree package”. Is this me?"
date: 2015-05-16
forum: Installation &amp; Upgrades
---

### Post by 0rbit-power2 on 2015-05-16
For the second time, I am now missing an Internet access, both removed during or after installation of Ubuntu!

Could I ask for help, to get my empty 14.04 Ubuntu back on line for normal access with Mother ship. Can anybody help?

I have noticed searching with my Mac on line, that I am not alone. How can we protect ourselves from this serious, time wasting problem? Has this problem moved on and new answers now available?

Cy

---

### Post by steeldriver on 2015-05-16
Hello and welcome to the forums

Can you give us some context please? where did you see "victim of the recent change in the linux-firmware-nonfree package”? what exactly is your issue?

---

### Post by deadflowr on 2015-05-16
Is this broadcom related?
If so, have you read through [chili555's thread]("http://ubuntuforums.org/showthread.php?t=2214110")?

If not, then +1 to post #2 and elaborate on the problem.

---

### Post by Rob Sayer on 2015-05-17
It's rather difficult to say whether linux-firmware-nonfree is a problem without knowing what network hardware and drivers you're using.  Did you install the linux-firmware-nonfree package?  If not I don't think it'd be there by default.

At the least you need to say what adapters you have.  Paste this into terminal:

```
sudo lshw -c network
```

and post the output here, embedded in [code] tags so people can read it.

---

### Post by dino99 on 2015-05-17
for which hardware/chipset did you need to install linux-firmware-nonfree ?
or is it that 'famous' noob habit to install/test everything from the archive without real needs ?

---


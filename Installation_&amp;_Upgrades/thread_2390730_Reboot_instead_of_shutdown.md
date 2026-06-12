---
title: "Reboot instead of shutdown"
date: 2018-05-01
forum: Installation &amp; Upgrades
---

### Post by bellaziciao on 2018-05-01
Hello, 
I'm working on a Dell XPS 15, version 2015, using Ubuntu 18.04 LTS and nvidia driver installed from ubuntu official PPA.
So the problem is, every time I shutdown the PC, it will reboot automatically after some (casual) time.
I tried to remove Nvidia driver, disable the WOL, added (acpi=force apm=power_off) to grub cmd line, but nothing resolved the problem.
The system is dual-boot with kali linux, in a separate partition, booting from bios on Ubuntu partition as primary.
Some help will be really grateful.
Thank you in advance.

[EDIT] The system was upgraded from Ubuntu 16.04 to Ubuntu 18.04 throw the official Software upgrade

---

### Post by Xian on 2018-05-01
Let's hope the quick/easy way works in this case. 

Issue this command in a terminal:

```
sudo update-grub
```

Shutdown the computer.

Any change ....?

---

### Post by bellaziciao on 2018-05-02
Nothing, it doesn't work....
The complicate way?

---

### Post by Xian on 2018-05-02
Not complicated ... but from here it's a scratch pad. 

Disable (or untick) all your networking from the network manager.

Your applet may appear different .... 

[[IMG]http://i.imgur.com/5zgdL5Bt.png[/IMG]]("https://imgur.com/5zgdL5B")

Shutdown computer. And ...... ?

---

### Post by bellaziciao on 2018-05-03
First try, stay down, second attempt, automatically rebooted &#129300;
i forgotted to say I'm running on latest bios, kernel 4.15

> **Xian said:**
> Not complicated ... but from here it's a scratch pad. 

Disable (or untick) all your networking from the network manager.

Your applet may appear different .... 

[[IMG]http://i.imgur.com/5zgdL5Bt.png[/IMG]]("https://imgur.com/5zgdL5B")

Shutdown computer. And ...... ?

---


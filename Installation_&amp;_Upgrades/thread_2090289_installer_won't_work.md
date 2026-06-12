---
title: "installer won't work"
date: 2012-12-01
forum: Installation &amp; Upgrades
---

### Post by iamrandy on 2012-12-01
i just got a usb wireless adapter and the installer disk won't work i have 12.04 if there's anything else you need i'll do it

---

### Post by sudodus on 2012-12-01
In linux, you don't install hardware drivers the same way as in Windows. Common hardware works out of the box, because there are built in drivers in the linux kernel. But it is a bit more complicated with some hardware, for example wifi chips and adapters.

See the following links

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported")
[https://help.ubuntu.com/community/WifiDocs/]("https://help.ubuntu.com/community/WifiDocs/")
[http://beginlinux.com/twitter/1096-ubuntu-wireless-setup]("http://beginlinux.com/twitter/1096-ubuntu-wireless-setup")
[http://www.howtogeek.com/howto/43752/how-to-install-a-wireless-card-in-linux-using-windows-drivers/]("http://www.howtogeek.com/howto/43752/how-to-install-a-wireless-card-in-linux-using-windows-drivers/")

---

### Post by iamrandy on 2012-12-01
ok now the system recognizes the card and it even is telling me that it is connected but when i try to bring up google its giving me a dns error

---

### Post by sudodus on 2012-12-01
> **iamrandy said:**
> ok now the system recognizes the card and it even is telling me that it is connected but when i try to bring up google its giving me a dns error

What card is it? And more exactly, what error is it?

It is interesting to find out how far you can reach.

Can you ping to the router? to the ISP? to Google?

Can you log in to the router via wired connection and check the setup? Can you log into the router via wifi?

What is the output of the terminal command
```
ifconfig
```

---

### Post by iamrandy on 2012-12-01
see i don't know how to do any of that any tips would be extremely helpful

---

### Post by 2F4U on 2012-12-02
> **iamrandy said:**
> see i don't know how to do any of that any tips would be extremely helpful

How to open a terminal:

[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

How to find out router IP address:

[http://ubuntuforums.org/showthread.php?t=940423](http://ubuntuforums.org/showthread.php?t=940423)
[http://www.cyberciti.biz/faq/how-to-find-gateway-ip-address/](http://www.cyberciti.biz/faq/how-to-find-gateway-ip-address/)

If, for example, you are finding that your router IP should be 192.168.0.1, then you can ping the router as follows:

ping -c3 192.168.0.1

Ping Google:

ping -c3 [www.google.com](www.google.com)

---

### Post by iamrandy on 2012-12-02
i've pinged the router and google and this is the resultand this is the error message[ATTACH][ATTACH]228087[/ATTACH][/ATTACH]

---

### Post by sudodus on 2012-12-02
It is obvious that you are not connected to the router.

I understand that you are trying to connect running Ubuntu 12.04.

***What card or adapter is it? It helps us to help if you can specify the exact name and article number, and if possible the chip.***

Can you connect to the router with another computer or adapter or with this adapter and another operating system (another Linux or Windows)?

Are you running the adapter with the built in driver, or are you trying to use the Windows driver via Ndiswrapper?

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by iamrandy on 2012-12-02
ok the adapter is an edimax model 7811un and this is the only computer in my house that doesn't have built in wireless and it's running on the built in drivers

---

### Post by iamrandy on 2012-12-02
this is what the status is telling me[ATTACH]228120[/ATTACH]

---


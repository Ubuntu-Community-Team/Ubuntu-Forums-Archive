---
title: "Edimax USB locks up Linux"
date: 2017-03-14
forum: MINT
---

### Post by mattx28025 on 2017-03-14
Hello, I'm a very new to Linux and I've been having trouble with WiFi. I'm running Linux mint 18.1 Sarah cinnamon 64-bit as a dual boot with Windows 10. I purchased the Edimax eu 7811un from Amazon as it said it was "plug n play". It works perfect when used with Windows 10 but when I plug it in with Linux running it completely locks the system up. It requires a hard reset to use the system again. The light also turns on and stays lit. I've looked for answers to the problem but can't seem to find a fix. I now it's not defective as it works with Windows. Has anyone else ran into this problem? Thanks in advance for any help.

---

### Post by chili555 on 2017-03-15
Gazing into his crystal ball and getting a strange vibration from space, ole Chili wants to see:  ```
cat /var/log/syslog | grep rtl | tail -n20
```As the result may be lengthy, please post the result here and give us the link: [http://paste.ubuntu.com](http://paste.ubuntu.com)

---

### Post by jeremy31 on 2017-03-15
I wonder what kernel is used ```
uname -a
```

After seeing this [bug report](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1666421)

---

### Post by chili555 on 2017-03-15
> **jeremy31 said:**
> I wonder what kernel is used ```
uname -a
```

After seeing this [bug report](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1666421)Please notice in the bug report that both rtl8192cu and rtl8xxxu load. I am interested in blacklisting rtl8xxxu and then rebooting to see if it helps.

Or at least that's the vibe I got from space!

---


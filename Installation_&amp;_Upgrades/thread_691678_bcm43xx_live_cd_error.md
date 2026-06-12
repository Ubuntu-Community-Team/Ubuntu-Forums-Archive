---
title: "bcm43xx live cd error"
date: 2008-02-08
forum: Installation &amp; Upgrades
---

### Post by jdvalim on 2008-02-08
I know that this is a common problem, but I've already tried some solutions and they didn't work.

So I'm installing Ubuntu 7.10 with the Live CD AMD64 in my HP DV6000 series notebook and I got the following error:

bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

After this point, I only get this messages and the installation doesn't go on.

The message is about a compatibility problem with the Wireless Card and I already tried to connect the Ethernet cable and disable the Wifi. Didn't worked. Then I've tried this:

> when install hangs:

click alt+f1 then
sudo -s
killall gdm
rmmod bcm43xx
exit
startx

Install ubuntu
restart
recovery mode
nano /etc/modprobe.d/blacklist
insert this : blacklist bcm43xx
save click ctrl+x then y
reboot

But it didn't work also. I get a message that the gdm process can't be killed.

I've already tried to press F6 at the beginning, put the option "noapic" and run the same commands above, but it didn't worked also.

Maybe I'm doing something wrong... any help? Thanks!

---

### Post by Pumalite on 2008-02-08
Get a router that provides you with DHCP.

---

### Post by jdvalim on 2008-02-09
Not possible in my case!
Modems are provided by the telephony company and you can't change them at all.

Thanks anyway! But there's another option?

---

### Post by pemailid on 2008-02-23
worked for me thanks.

---


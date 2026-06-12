---
title: "remove chainloader"
date: 2012-04-01
forum: Installation &amp; Upgrades
---

### Post by piebaldyea on 2012-04-01
Hello all. i have been using ubuntu on my netbook for about a year now. I just installed 11.10 on my desktop, so now I have a triple boot windows 7, snow leopard and ubuntu setup. 

I use my mac hdd as my boot drive (using the latest version of chimera (tonymacx86)) to select which operating system i want to boot into. in order to get ubuntu to show up, during the install i created a /boot partition, a / partition and a swap partition. now all 3 operating systems show up the way i want them to in chimera, and ubuntu works nicely. 

the issue i am having is that when i select ubuntu on the chimera screen, it then sends me to the grub screen to select which operating system i want to boot into again (giving me the option for windows, ubuntu and osx). i obviously dont need this as it is completely redundant. 

i was looking for some guidance in removing the chainloader so that it automatically boots into ubuntu when i select it in chimera.

thanks in advance for the help!

---

### Post by ottosykora on 2012-04-02
well you could simply remove the chainload entries for the unwanted os and disable the os prober, but personally I would leave it as it is and for example set the menu time to very low value, set ubuntu as default, so it kind of just jumps to booting.

Note that the menu otherwise lets you also boot to other kernels then the latest one, lets you boot to the rescue mode etc, so it has lot of advantages.

---

### Post by Bucky Ball on 2012-04-02
Welcome. 

> **ottosykora said:**
> ... I would leave it as it is and for example set the menu time to very low value, set ubuntu as default, so it kind of just jumps to booting.

Indeed, set the timeout to '0' or comment it out altogether and it will not show at all. You need to:

```
sudo nano /etc/default/grub
```... look for a line like this:

```
GRUB_TIMEOUT="5"
```... and comment it out with a hash:

```
# GRUB_TIMEOUT="5"
```That should work. If not, set it to '0' without the hash and that will.

Once complete using either method and issued whenever you edit this file, issue:

```
sudo update-grub
```> **ottosykora said:**
> Note that the menu otherwise lets you also boot to other kernels then the latest one, lets you boot to the rescue mode etc, so it has lot of advantages.

If you need to get to another kernel, reverse whatever process you did in last step to see grub at boot again. This, of course, will be a bit more difficult if you can't boot into the default (first on the list) kernel but there are ways around it.

---

### Post by piebaldyea on 2012-04-02
ok ill try these when i get home from work and let you guys know how it works out. thanks

---

### Post by piebaldyea on 2012-04-02
> **Bucky Ball said:**
> Welcome. 



Indeed, set the timeout to '0' or comment it out altogether and it will not show at all. You need to:

```
sudo nano /etc/default/grub
```... look for a line like this:

```
GRUB_TIMEOUT="5"
```... and comment it out with a hash:

```
# GRUB_TIMEOUT="5"
```That should work. If not, set it to '0' without the hash and that will.

Once complete using either method and issued whenever you edit this file, issue:

```
sudo update-grub
```

If you need to get to another kernel, reverse whatever process you did in last step to see grub at boot again. This, of course, will be a bit more difficult if you can't boot into the default (first on the list) kernel but there are ways around it.
i first tried to comment the line out, but it still showed the screen for 3 seconds. I wonder if it doesnt see the line, it assumes a default? either way, un-commented it and set the time to 0 and it worked like a charm. thanks for the help!

---

### Post by lJ9%3MR&gt;sa on 2012-04-02
I have a setup like you. Windows, Hackintosh, Xubuntu. I just left the GRUB loader there. It doesn't bother me, but it might bother you. From my knowledge, you MUST keep GRUB there for Ubuntu to be able to boot. Now, you can edit GRUB menu list to disable the menu and immediatly boot to Ubuntu. I think someone posted on your thread how to do it. Try googling for Ubuntu GRUB editor or something like that.
 
-faxmanloveswaffles

---

### Post by Bucky Ball on 2012-04-02
> **piebaldyea said:**
> ... un-commented it and set the time to 0 and it worked like a charm. thanks for the help!

Excellent news! Please mark thread as 'Solved' if this is the case.

Enjoy! ;)

---


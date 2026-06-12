---
title: "Updating to  Ubuntu 11.4 from Xubuntu 10.4"
date: 2011-08-27
forum: Installation &amp; Upgrades
---

### Post by jmarkybb on 2011-08-27
Hiya,


Im trying to update my Xubuntu 10.4 to Ubuntu 11.4.


I have the image of 11.4 on my USB stick but I'm having a bit of trouble.


I want to replace 10.4 with 11.4, **but** 10.4 is partitioned with Vista

[IMG]http://home/ubuntu/Desktop/Screenshot-Install.png[/IMG]

---

### Post by MAFoElffen on 2011-08-27
> **jmarkybb said:**
> Hiya,


Im trying to update my Xubuntu 10.4 to Ubuntu 11.4.


I have the image of 11.4 on my USB stick but I'm having a bit of trouble.


I want to replace 10.4 with 11.4, **but** 10.4 is partitioned with Vista
What if you just did it the "easy" way?  Meaning:

Start Xubuntu. Go to a terminal session.
```

sudo apt-get install ubuntu-desktop
sudo apt-get update
sudo apt-get dist-update

```After the "upgrade" reboot.  At the login screen, select the user... > when the password dialog pops up... look at the botton screen bar > it will have a pull down box that you can select which Flavor you want to use... Select one of the Ubuntu Flavors. > Continue logging in.

This method would be faster, easier, keep all your hardware settings and files, all your personal settings, data in your home directory...

If you decide you didn't want Xubuntu there anymore, you could then remove the xubuntu-desktop with apt-get...

Remember that Ubuntu, Kubuntu, Xubuntu and Lubuntu share the same base system files.

---

### Post by jmarkybb on 2011-08-27
Hiya MAFoElffen


What if you just did it the "easy" way? Meaning:


I tried updating from within Xubuntu, but it said this distro (Xubuntu 10.4) was no longer supported.

---

### Post by snowpine on 2011-08-27
Here are some easy-to-follow instructions for upgrading 10.04 to 11.04:

[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

And easy instructions for switching Xubuntu to Ubuntu:

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by ottosykora on 2011-08-28
>I tried updating from within Xubuntu, but it said this distro (Xubuntu 10.4) was no longer supported.
jmarkybb is offline Report Post   	Reply With Quote<

strange, the 10.04 is supposed to be the LTS and is still supported.

But you may try first to make all updates to the 10.04 as the LTS versions get numbers like 10.04.1 etc during their life.

---

### Post by jmarkybb on 2011-08-28
I apolagise, It was 9.4, confused with the start up screen of Xubuntu. Sorry for the confusion.

I now have 11.4 running along side Vista, Ive signed up for "Ubuntu One" I love the idea of this "The Cloud", thankyou.

I'm trying to find "Ubuntu One" for Windows Vista, so I can drop all my files into it and send the over to "My New OS" :P

At the moment I'm dropping them into DropBox, three, questions Where can I find Ubuntu One for Windows, Does Ubuntu support DropBox & when uploading pics from my Andriod Desire HD, it doesn't give them their names, just a long number, can I am amend this?

---

### Post by dino99 on 2011-08-28
on my side i'll never, never drop my docs/settings outside (cloud, vps, ...) because i care about security, and dont want everyone robbing/glancing at. Just my two cents, not secured at all (remind accounts lost by banks/social networking).

---

### Post by jmarkybb on 2011-08-28
> **dino99 said:**
> on my side i'll never, never drop my docs/settings outside (cloud, vps, ...) because i care about security, and dont want everyone robbing/glancing at. Just my two cents, not secured at all (remind accounts lost by banks/social networking).

Hiya Dino99,

I appreciate that, :) 

Its just whilst I get my files converted over to Ubuntu, they wont be staying there.

---


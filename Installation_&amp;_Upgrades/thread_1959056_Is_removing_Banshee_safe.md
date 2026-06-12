---
title: "Is removing Banshee safe?"
date: 2012-04-15
forum: Installation &amp; Upgrades
---

### Post by vasa1 on 2012-04-15
I understand that Banshee isn't part of 12.04. However, it is present in my current 11.10 which I got by upgrading from 11.04.

Is it correct that the upgrade process will not delete Banshee if it sees it present on my system at the time of upgrade?

I don't use Banshee at all and have no plans to use it in future. So would I being doing something wrong if I uninstall it?

In my list of installed software, I see:
```
banshee
banshee-extension-soundmenu
banshee-extension-ubuntuonemusicstore

```

Should I do
**sudo apt-get purge** for each of the items or just for Banshee?

(I don't have an Ubuntu One account.)

---

### Post by Lemuriano on 2012-04-15
Hi,

I remove it and install rhythmbox and had no issues.

```
sudo apt-get purge banshee  

```

Regards.

---

### Post by vasa1 on 2012-04-15
> **Lemuriano said:**
> Hi,

I remove it and install rhythmbox and had no issues.

```
sudo apt-get purge banshee  

```

Regards.
Okay! I cheated and used Synaptic. It removed all three items. Now, what about this "mono" business. I think Banshee and Tomboy (?) were the only programs that needed mono. Have you removed mono as well?

---

### Post by Lemuriano on 2012-04-15
> **vasa1 said:**
> Now, what about this "mono" business. I think Banshee and Tomboy (?) were the only programs that needed mono. Have you removed mono as well?

Still use Tomboy but it´s a matter of time until remove it all together with mono.

[http://www.ubuntulinuxhelp.com/mono-in-ubuntu-yes-or-no/](http://www.ubuntulinuxhelp.com/mono-in-ubuntu-yes-or-no/)

Regards.

---

### Post by vasa1 on 2012-04-15
I asked about mono over here:
[http://askubuntu.com/questions/122346/will-mono-be-carried-forward-by-upgrading-to-12-04](http://askubuntu.com/questions/122346/will-mono-be-carried-forward-by-upgrading-to-12-04)

---

### Post by Lemuriano on 2012-04-15
Hi,

Indirectly you encourage me to address the mono issue which I have postpone for a while. 
Since I just purge Tomboy, now is time to get rid of mono.;)

Regards.

---

### Post by vasa1 on 2012-04-15
> **Lemuriano said:**
> Hi,

Indirectly you encourage me to address the mono issue which I have postpone for a while. 
Since I just purge Tomboy, now is time to get rid of mono.;)

Regards.

This thread has been updated a bit: [http://askubuntu.com/questions/12897/how-to-remove-mono](http://askubuntu.com/questions/12897/how-to-remove-mono)

According to Manish, the thing to purge is "mono-runtime". The rest will be taken care of.

Edit: I had to lose Pinta :(

All the best!

---

### Post by directhex on 2012-04-16
> **vasa1 said:**
> Edit: I had to lose Pinta :(

You didn't "have to" lose anything.

You sacrificed an app you like, for the sake of hubris.

---

### Post by Lemuriano on 2012-04-16
> **directhex said:**
> You didn't "have to" lose anything.

You sacrificed an app you like, for the sake of hubris. 

For some, to relinquish our convictions is to stop being what we are.

Regards.

---


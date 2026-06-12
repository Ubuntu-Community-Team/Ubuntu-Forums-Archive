---
title: "Using plymouth themes"
date: 2010-03-27
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by vaskark on 2010-03-27
I'm wondering if there's a gui way to configure/change the Plymouth themes? I've read other posts and have only found a text option using *plymouth-set-default-theme* but it isn't appearing on my system (even though I do have the plymouth package installed).

Any help will be greatly appreciated. Thanks.

---

### Post by IanW on 2010-03-27
I understand the command has changed. See [here.]("http://ubuntuforums.org/showpost.php?p=9034192&postcount=510")

---

### Post by grandtoubab on 2010-03-27
in Synaptic I have choice beetween
1) plymouth-theme-fade-in
2) plymouth-theme-glow
3) plymouth-theme-solar
4)plymouth-theme-spinfinity
5)plymouth-theme-ubuntu-logo
6)lubuntu-plymouth-theme

For me the solar one looks nice :D

---

### Post by vaskark on 2010-03-27
K, here's what I did to get the solar theme working:

```
sudo update-alternatives --install /lib/plymouth/themes/default.plymouth default.plymouth /lib/plymouth/themes/solar/solar.plymouth 100
sudo update-alternatives --config default.plymouth
sudo update-initramfs -u
```This did in fact work, but when I tried another theme (spinfinity) I was brought to a purple screen with UBUNTU but no loading animation and it froze there. Can someone tell me what I'm doing wrong?

Thanks.

---

### Post by kawaji on 2010-03-27
I tried spinfinity(0.8.1-1ubuntu1) and got the same problem with it.
It may have a bug.
All the other themes(solar, glow, fade-in...) were ok on my system.

btw, I think running "update-alternatives --install" command is not needed for ones installed using Synaptic.

---

### Post by vishalrao on 2010-03-27
have any of you tried the "ubuntu sunrise" plymouth theme, i liked it a lot myself, though its good for slow booting machines - fast ones it just zips by :D

---

### Post by Rob2687 on 2010-03-27
Where is teh sunrise theme? I don't see it in Synaptic.

---

### Post by brimondyl on 2010-03-27
> **grandtoubab said:**
> in Synaptic I have choice beetween
1) plymouth-theme-fade-in
2) plymouth-theme-glow
3) plymouth-theme-solar
4)plymouth-theme-spinfinity
5)plymouth-theme-ubuntu-logo
6)lubuntu-plymouth-theme

For me the solar one looks nice :D

I don't see any of these in Synaptic?

---

### Post by vishalrao on 2010-03-27
i believe it was "ubuntu space sunrise" a mod of the "space sunrise" theme if you search google for "plymouth ubuntu space sunrise theme" ... ? posted a video of it when i tried it a few weeks ago: [http://www.youtube.com/watch?v=N-4xTkN1_RQ](http://www.youtube.com/watch?v=N-4xTkN1_RQ)

---

### Post by VMC on 2010-03-27
Here' how I see what available and how I installed solar splash:

```
$ plymouth-set-default-theme --list
details
fade-in
glow
script
**solar**
spinfinity
text
ubuntu-logo
```

Then:
```
sudo plymouth-set-default-theme **solar** --rebuild-initrd
```

---

### Post by mc4man on 2010-03-27
> how I installed solar splash:

Interesting - are you updated to plymouth (0.8.1-1) or today to 0.8.1-1ubuntu1

At least here this
> 
plymouth-set-default-theme
is no longer a valid plymoutn command - just returns  plymouth usage (basically plymouth --help

the update-alternatives works fine

---

### Post by VMC on 2010-03-27
> **mc4man said:**
> Interesting - are you updated to plymouth (0.8.1-1) or today to 0.8.1-1ubuntu1

At least here this

is no longer a valid plymoutn command - just returns  plymouth usage (basically plymouth --help

the update-alternatives works fine

No, I'm on an older one "Version: 0.8.0~-17". I do have a newer one installed on another partition, that is the one you listed. Haven't tried installing solar on that one.

Edit: Your right it no longer works with  " 0.8.1-1ubuntu1".

---

### Post by foxmajik on 2010-04-15
> **VMC said:**
> Here' how I see what available and how I installed solar splash:

```
$ plymouth-set-default-theme --list
details
fade-in
glow
script
**solar**
spinfinity
text
ubuntu-logo
```

Then:
```
sudo plymouth-set-default-theme **solar** --rebuild-initrd
```

```
$ sudo plymouth-set-default-theme solar --rebuild-initrd
[sudo] password: 
sudo: plymouth-set-default-theme: command not found
```

---


---
title: "Ati/AMD Catalyst Control Center"
date: 2007-10-22
forum: Installation &amp; Upgrades
---

### Post by Martje_001 on 2007-10-22
Hi,
I have a Radeon RX9550, and restricted drivers installed. I wanted CCC so I maked a .deb from the official installer with:
```
sudo bash ati-driver-installer-8.40.4-x86.x86_64.run --buildpkg Ubuntu/gutsy
```I installed CCC, but when I start it I get this message:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=47273&stc=1&d=1193043936[/IMG]

It's dutch, sorry. It says I have to configure my card with 'aticonfig'. So I did.
```
martijn@gutsy:~$ sudo aticonfig --initial
[sudo] password for martijn:
Found fglrx primary device section
Nothing to do, terminating.

```

It still doesn't work. Help me! :)

---

### Post by ihcnet on 2007-10-22
Did you install the ATi drivers that come with the ATi installer or keep the one from the restricted driver installer? Perhaps the version of the driver has to match the version of the CCC, and the one in the Gutsy repository is a little bit older than version 8.40.4.

---

### Post by Martje_001 on 2007-10-22
> **ihcnet said:**
> Did you install the ATi drivers that come with the ATi installer or keep the one from the restricted driver installer? Perhaps the version of the driver has to match the version of the CCC, and the one in the Gutsy repository is a little bit older than version 8.40.4.
Aah... maby that's it. I'll try it when I'm home!

---

### Post by Lt_Kamikaze on 2007-10-22
Hi!

I'm a newbie when it comes to Ubuntu, but I struggled with this same thing the whole weekend. ATI control center can't initialize because the driver isn't installed or isn't working, in Finnish though.

I just figured what caused the problem for me: xgl. Have you installed it?

I just uninstalled it and CCC (AND 3d games) are working again. I wonder what xgl does so it screws the whole thing around? Don't know, but I'll have to cope without the eye candy before someone figures it out.

P.S. Using 8.40.4, radeon mobility x1600 and installed drivers with Envy.

---

### Post by Martje_001 on 2007-10-22
Do you mean "xserver-xgl" ? Gonna reinstall it right now. I let you know how it turns out ;)

Edit: doesn't work :(

---

### Post by Martje_001 on 2007-10-22
> **ihcnet said:**
> Did you install the ATi drivers that come with the ATi installer or keep the one from the restricted driver installer? Perhaps the version of the driver has to match the version of the CCC, and the one in the Gutsy repository is a little bit older than version 8.40.4.
That's it! The new driver doesn't work for me, so I have to stick with the old drivers, and the old CCC :(.
No Anti Aliasing for me I guess..:(

---

### Post by Lt_Kamikaze on 2007-10-22
Yeah, xserver-xgl. I didn't reinstall, I uninstalled it. Also, I used Envy and the marker in restricted drivers manager is unchecked for ATI, but in use. If I check the marker, the drivers won't work.

Is your marker unchecked?

If not, uncheck, install envy, install ati drivers, reboot, install ati drivers again, reboot. Should work. And no xserver-xgl.... :(

---

### Post by Martje_001 on 2007-10-23
> **Lt_Kamikaze said:**
> Yeah, xserver-xgl. I didn't reinstall, I uninstalled it. Also, I used Envy and the marker in restricted drivers manager is unchecked for ATI, but in use. If I check the marker, the drivers won't work.

Is your marker unchecked?

If not, uncheck, install envy, install ati drivers, reboot, install ati drivers again, reboot. Should work. And no xserver-xgl.... :(
The new driver seems to have a bug for my card.. :'(

---


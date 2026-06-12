---
title: "Strange Installation problem with Ubuntu 10.04"
date: 2010-05-08
forum: Installation &amp; Upgrades
---

### Post by hardenheavy on 2010-05-08
Hi. I'm completely new to Linux and I have a rather strange problem when I try to install Ubuntu 10.04 on my FS Esprimo Mobile v5535 with SiS chipset and graphics.

Just as an intro, I had Ubuntu 9.10 (worked fine!) installed but I formated the HDD due to some other issues, not related to Linux. After that I tries openSUSE but decided to switch back to Ubuntu because SUSE does not have an adequate support for SiS chipsets.

So back to the strange problem. When I boot with the Ubuntu 10.04 Alternate CD, I get the language selection menu and after I select the language I get an awkward flickering screen. Here's the image.
[IMG]http://i185.photobucket.com/albums/x272/roglic/DSC00383.jpg?t=1273337604[/IMG]
This happens regardless of my choice to use standard or text-based install. I had the same problem with Kubuntu 10.04 as well. 

Does someone have any idea what could this mean? Is SiS truly this much incompatible with Linux or what?! I'm asking this because I tried the CDs on my ASUS nVidia desktop and didn't have this issue.

Thanks.

---

### Post by Siskotest on 2010-05-09
> **hardenheavy said:**
> Hi. I'm completely new to Linux and I have a rather strange problem when I try to install Ubuntu 10.04 on my FS Esprimo Mobile v5535 with SiS chipset and graphics.

Just as an intro, I had Ubuntu 9.10 (worked fine!) installed but I formated the HDD due to some other issues, not related to Linux. After that I tries openSUSE but decided to switch back to Ubuntu because SUSE does not have an adequate support for SiS chipsets.

So back to the strange problem. When I boot with the Ubuntu 10.04 Alternate CD, I get the language selection menu and after I select the language I get an awkward flickering screen. Here's the image.
[IMG]http://i185.photobucket.com/albums/x272/roglic/DSC00383.jpg?t=1273337604[/IMG]
This happens regardless of my choice to use standard or text-based install. I had the same problem with Kubuntu 10.04 as well. 

Does someone have any idea what could this mean? Is SiS truly this much incompatible with Linux or what?! I'm asking this because I tried the CDs on my ASUS nVidia desktop and didn't have this issue.

Thanks.

I have the same problem!! any solution?

---

### Post by technochoc on 2010-05-10
Ditto same issue here, assuming it is something to do with the SIS graphics, solution would be nice, or ill have to put Vista back on the wife's laptop !

---

### Post by Sk41m4n on 2010-05-10
I also have this problem...
 
([http://ubuntuforums.org/showthread.php?t=1466637]("http://ubuntuforums.org/showthread.php?p=9221412"))

---

### Post by mhgsys on 2010-05-10
ahum;

You just have to wait a minute or two,(depending on your system) 
The problem is just with plymouth and tty.

Wait a few minutes and ubuntu will be installable;

After that you might want to install the sis 671/771 drivers; 

Read my little explained "howto" here;
[http://ubuntuforums.org/showthread.php?t=958967&page=38](http://ubuntuforums.org/showthread.php?t=958967&page=38)

[COLOR="Blue"]**EDIT: I don't know if Alternate is text-based only but if it is**[/COLOR]
and you really prefer to use the alternate cd
try this;

(although you won't be able to see what you do, commands will still work)

```
echo blacklist vga16fb > /etc/modprobe.d/blacklist-vga16fb.conf
```

followed by
```
update-initramfs -u
```

and then;

```
reboot
```

---


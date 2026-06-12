---
title: "Dual Disk Boot 10.04 Lucid &amp; XP problem"
date: 2010-10-31
forum: Installation &amp; Upgrades
---

### Post by BorisPlankton on 2010-10-31
Hello,
I have installed Lucid 10.04LTS to one SATA Drive with Win XP installed on other SATA drive.
I thought that Lucid would find the other drive and offer me to boot to it but it has not.
If I boot with both drives connected I arrive at Windows XP. And the same applies if I boot with the installation disk in and I am only offered option to install Lucid to the 'Windows' drive. 
If I disconnect the XP drive I boot into Lucid no problems. I did not seem to have any issues with my installation.
Can anyone help me? Do I need to edit the Grub file and if so I will need specific advice on this? I am aiming to have Ubuntu as the default boot.


Any advice gratefully received before I start lashing this up.

Kind Regards,
Paul

---

### Post by BorisPlankton on 2010-11-12
Bump. Anyone? PC boots into whichever hard drive was last connected.
KRs,
Paul

---

### Post by Quackers on 2010-11-12
Please go to the site below and download the boot script to your DESKTOP then open a terminal and run the command given on the first page of that site. This will produce a results.txt file on your desktop. Please copy the contents of that file and paste it between CODE tags in your next post. For CODE tags click on New Reply (not quick reply) and then click on the # symbol in the toolbar.
This will give a full overview of your system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by sikander3786 on 2010-11-12
> If I disconnect the XP drive I boot into Lucid no problems. I did not seem to have any issues with my installation.

You need to setup your Bios to boot from your Ubuntu HDD. I mean make your Ubuntu HDD as the first boot device there and try to boot again. You should be able to boot into Ubuntu this time and if the Grub menu doesn't show Windows listed there, run

```
sudo update-grub
```

from terminal and it should pick up Windows and add it to the Grub menu. Make sure you've not disconnect your Windows drive while you do the above command ;-)

If my suggestion fails, you definitely need to post bootinfoscript as per **Quacker's** instructions. Make sure both your HDDs are connected while you run that script from Live CD.

---

### Post by BorisPlankton on 2010-11-14
Thanks sikander3786 job done. Updated grub found windows. Ironic - finding windows brings the death of windows closer,for one user at least.
Thanks to Quackers as well.
KRs
Paul

---


---
title: "I don't want Ubuntu grub when using Windows 8"
date: 2013-03-05
forum: Installation &amp; Upgrades
---

### Post by rhyswilson92 on 2013-03-05
Hi

I am fairly new to Linux (1 - 2 years experience) and I have an issue. My primary OS is Windows 8 and I have install Ubuntu through wubi.

When I boot my machine I get a windows 8 type screen asking to boot to Windows or Ubuntu, all good so far, but when I boot Ubuntu it then comes up with the Ubuntu grub
asking if I want to boot into recovery mode and a couple other options. Is there a way to boot straight to Ubuntu when clicked and skip the Ubuntu grub screen??

I don't mind working like this at the moment but It is becoming a bit of a hassle when I want to quickly boot into Ubuntu.

Any help would be much appreciated.

Thanks
Rhys

---

### Post by JLeon85 on 2013-03-05
If you go into Win 8 and set Ubuntu as your default OS, then you should only see the Ubuntu grub screen. It's under advanced system settings, but just make sure your signed in as administrator.

---

### Post by rhyswilson92 on 2013-03-05
> **JLeon85 said:**
> If you go into Win 8 and set Ubuntu as your default OS, then you should only see the Ubuntu grub screen. It's under advanced system settings, but just make sure your signed in as administrator.

Thanks for the reply.

If I do this will the Ubuntu grub give me the option of Windows? I ask because in the current setup it doesn't give you the option.

Thanks

---

### Post by JLeon85 on 2013-03-05
It should, but you could also run Grub Customizer in Ubuntu to make sure. 


[http://askubuntu.com/questions/100232/how-do-i-change-the-grub-boot-order](http://askubuntu.com/questions/100232/how-do-i-change-the-grub-boot-order)

---

### Post by rhyswilson92 on 2013-03-05
Okay I'll give that a try. I have just installed ubuntu again only yesterday so I have still to configure the wireless but I will let you know how things go.

Thanks
Rhys

---

### Post by oldfred on 2013-03-05
No you cannot boot Windows from wubi's version of grub. That would be an infinite loop. You can set grub menu to only show for a few seconds. Some change it to 0 but then have issues and cannot get to it, so I suggest 1 or 2 seconds. Default is 10 for 10 seconds:

GRUB_TIMEOUT=10

gksudo gedit /etc/default/grub

If you like Ubuntu it may be time to change to a full install.
 
From the developer of wubi:
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn&#8217;t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

---

### Post by darkod on 2013-03-05
Just turn off the os-prober and it will not detect windows. Boot your wubi, open terminal and do:
```
sudo chmod -x /etc/grub.d/30_os-prober
sudo update-grub
```

That should get rid of the windows entry, and when ubuntu is the only OS detected the grub2 menu doesn't show by default.

---

### Post by rhyswilson92 on 2013-03-07
Hi 

I decided to go with "oldfred" on this one as I decided after some technical difficulties I would
still like to access recovery mode and that worked a treat although I want to add that after you have edited
the grub file you must enter the following code to configure it:

sudo update-grub

This updates the grub.cfg file

Anyway thanks for help

Rhys

---


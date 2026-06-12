---
title: "Upgrading to Ubuntu 10.10 (Netbook) using Ubuntu"
date: 2011-02-26
forum: Installation &amp; Upgrades
---

### Post by JesMFN on 2011-02-26
So I I'm trying to upgrade to 10.10 Ubuntu Net book edition 
so far I have downloaded it from the web cite ([http://www.ubuntu.com/netbook/get-ubuntu/download](http://www.ubuntu.com/netbook/get-ubuntu/download))
I'v used start up disk creator and put put it on my USB (its an Sd card in a converter USB its works the same) and then restarted my computer. from there nothing happens. nothing comes up when I start up and log on. so i tried changing the BIOS to make removable drive at the top of the list. nothing happens and I'v disabled all the others and it says reboot and change BIOS or insert a boot up stuff ect ect. nothing happens. so then i try just opening up. so i open wubi.exe. i tried opening it up with archive manager and nothing seems to happen. then i open it with wine. i press demo and full instilation. when i press reboot nothing happens.  so then i try help me reboot from cd and it says a previouse instillation has been detected it needs to uninstall. (because i had windows but it got a virus. so i downloaded ubuntu. well of course i cant uninstall it if im using it so i get this message) C:/windows/temp/wubi-10.10-rev197.log... so im at a complete loss here. if i did something wrong with archive manager or you have any solution please let me know!!!! thank you

---

### Post by owise1 on 2011-02-26
Try pressing esc during the boot up process - should offer you a choice of what to boot from

---

### Post by owise1 on 2011-02-26
Note that your proposed route will restult in a new install.  You can upgrade from one version to another using the update manager.

Can you provide a few more details - what distro/ dual boot? laptop details

---

### Post by JesMFN on 2011-02-26
i have eeebuntu for distro
and i had dual boot... and still kinda do but windows has a blue screen of death.... so i cant use it  but its there. tried pressing escape does not do anything that i already didnt do.

---

### Post by owise1 on 2011-02-26
What sort of PC - latop or desktop?  Try googling the model to see how to boot from USB.  Why aren't you using update manager to upgrade??  Also how did you get your original eeebuntu onto the machine - wubi?

---

### Post by JesMFN on 2011-02-26
I'm using a netbook (clarified above its an Asus) iv tried booting from the USB (also clarified) its just in the main commands and you change the BIOS id does not read anything out of the USB basically saying its empty. you cant use the update manager to go from eeebuntu to ubuntu. you need to install it.
origonaly my friend did it for me. yea wubi but its not working this time

---

### Post by owise1 on 2011-02-26
OK - a lot clearer now.  I also have an ASUS eeepc running the latest Ubuntu - new machine but blew windows away as no need for it ..for me.  Have a look at [https://help.ubuntu.com/community/EeePC/Installation](https://help.ubuntu.com/community/EeePC/Installation).  You should be able to boot from that USB if you hit ESC during the POST.  

I suspect that the USB is the problem - I have had issues with the USB tool creating bootable sticks in the past.  Found that I needed to run it as root.  There are bug reports on this.

Are you going to keep your window partition?  If you are you may like to re-install windows first using the recovery partition and then install Ubuntu (on my Eeepc there was a "d:" partition setup and I originally was going to use that.  In fact there are four partitions - recovery (hidden), C: D: and another hidden one that is used to speed boot.  I blew all away but should have kept the last one but still boots fast enough

---


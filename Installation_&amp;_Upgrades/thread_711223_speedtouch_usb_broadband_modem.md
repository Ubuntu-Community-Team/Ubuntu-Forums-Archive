---
title: "speedtouch usb broadband modem"
date: 2008-02-29
forum: Installation &amp; Upgrades
---

### Post by the.weavster on 2008-02-29
I can not get connected to the internet, I have a speedtouch usb modem that works fine with xp.

I found the section at the ubuntu site that describes setting up a speedtouch modem but I fall at the first hurdle - it says type in this command:

grep -B 1 "THOMSON" /proc/bus/usb/devices

but I just get an error back saying no such directory. In the file manager I can find /proc/bus/usb but there is no 'devices' sub directory. How do I get Ubuntu to find my modem so I can submit the commands in the first place?

Thanks for any assistance.

---

### Post by ellalan on 2008-02-29
Hi
Go to  this link and download the .deb file and install it, a new menu will appear in the main menu.
Applications>Internet>usb ADSL modem manager.
on the first link look for" How to try it "section.

[http://www.squeezedonkey.com/wiki/li...itle=Main_Page](http://www.squeezedonkey.com/wiki/li...itle=Main_Page)
[http://www.squeezedonkey.com/svn/linux/trunk/releases/ubuntu/32-bit%20i386/](http://www.squeezedonkey.com/svn/linux/trunk/releases/ubuntu/32-bit%20i386/)

Hope this help.

---

### Post by the.weavster on 2008-02-29
Thank you so much for putting me out of my torment!

---

### Post by ellalan on 2008-02-29
Hi the.weavster
you are welcome and enjoy one of the best OS.

---

### Post by Glugglug on 2008-02-29
Search Steven Harper     and you should get a few helpful posts .

---

### Post by the.weavster on 2008-02-29
Well it worked until I rebooted, so it seems my torment is not over yet...

---

### Post by xeth_delta on 2008-02-29
> **the.weavster said:**
> I can not get connected to the internet, I have a speedtouch usb modem that works fine with xp.

I found the section at the ubuntu site that describes setting up a speedtouch modem but I fall at the first hurdle - it says type in this command:

grep -B 1 "THOMSON" /proc/bus/usb/devices

but I just get an error back saying no such directory. In the file manager I can find /proc/bus/usb but there is no 'devices' sub directory. How do I get Ubuntu to find my modem so I can submit the commands in the first place?

Thanks for any assistance.

That is not how you identify connected USB devices, at least not that I know of.
To see a list you can use:
```
lsusb
```
lsusb <-> list usb
To read system messages:
```
dmesg
```

---

### Post by the.weavster on 2008-02-29
> **ellalan said:**
> Hi
Go to  this link and download the .deb file and install it, a new menu will appear in the main menu.
Applications>Internet>usb ADSL modem manager.
on the first link look for" How to try it "section.

[http://www.squeezedonkey.com/wiki/li...itle=Main_Page](http://www.squeezedonkey.com/wiki/li...itle=Main_Page)
[http://www.squeezedonkey.com/svn/linux/trunk/releases/ubuntu/32-bit%20i386/](http://www.squeezedonkey.com/svn/linux/trunk/releases/ubuntu/32-bit%20i386/)

Hope this help.

If I check 'connect as OS boots' I get a connection no problem but if I uncheck that option and try clicking 'connect' once the OS has booted the connection fails.

I don't know why one connects and the other doesn't - the details are the same. It's not a big problem though, I'm happy to have the computer connected all the time I'm using it.

Thanks again for your help everyone.

---

### Post by the.weavster on 2008-02-29
I now have another problem, the utility that makes the connection asks for the root password at boot up and will not make the connection without it.

I don't want to have to log in as root to use the modem.

Any ideas?

---

### Post by xeth_delta on 2008-02-29
> **the.weavster said:**
> I now have another problem, the utility that makes the connection asks for the root password at boot up and will not make the connection without it.

I don't want to have to log in as root to use the modem.

Any ideas?

Sorry for the question, just want to make sure. Does it ask for the root password or for your password to perform a sudo?

---

### Post by the.weavster on 2008-03-01
It's asking for the Ubuntu administrators password not my ISP log-in password. If I don't enter the admin password at boot-up when I try to connect it says no modem is connected to the computer.

---

### Post by xeth_delta on 2008-03-01
> **the.weavster said:**
> It's asking for the Ubuntu administrators password not my ISP log-in password. If I don't enter the admin password at boot-up when I try to connect it says no modem is connected to the computer.

Oh, what I meant is if it asks you for the password you normally use, for example, for "sudo". In that case it is not that you are logging in as root, it just needs administrative privileges to make the connection. There might be a way to automate that, though.

---

### Post by the.weavster on 2008-03-01
Ah, I see - it is the administrative privileges dialog that asks me for my password.

---

### Post by the.weavster on 2008-03-02
If anybody could explain to me how you automate this, particularly on a user by user basis, I would appreciate it.

Thanks.

---

### Post by xeth_delta on 2008-03-02
> **the.weavster said:**
> Ah, I see - it is the administrative privileges dialog that asks me for my password.

That means that it is just asking for adm privileges to connect, not to log-in as root. Let me see if I find out how to avoid this, right now I am not sure how to, but I believe it can be done. In the meantime perhaps some other user more knowledgeable will offer some insight.

---


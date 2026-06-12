---
title: "Error with X server"
date: 2006-04-17
forum: Installation &amp; Upgrades
---

### Post by Vnepomuceno on 2006-04-17
Hello. Recently, I installed in other partition the Linux (ubuntu).
Everything was fine in the installation, but when I tried to log in, it appear to me the following error message:

[[IMG]http://img101.imageshack.us/img101/5262/015rz.th.png[/IMG]](http://img101.imageshack.us/my.php?image=015rz.png)

I other forum, someone told me to execute the following command:

sudo pico /etc/x11/xorg.conf

And I inserted the password, but when the "document" opened it was "empty".

[[IMG]http://img104.imageshack.us/img104/2657/022nn.th.png[/IMG]](http://img104.imageshack.us/my.php?image=022nn.png)

Anyone can help me? Is that i'm very ansious to meet Linux ;)

---

### Post by henryk69 on 2006-04-17
Hi,
First of all you should be looking at /etc/X11/xorg.conf

BUT, you really should check what the xserver is complaining about, by looking at the end of the xserver log file 
```
 less /var/log/Xorg.0.log 
```
are there any error messages at the end?

---

### Post by Vnepomuceno on 2006-04-17
One question. What is and what is the use of the X server? I didn't got it yet.
Here is the error log.

[[IMG]http://img429.imageshack.us/img429/2208/039bo.th.png[/IMG]](http://img429.imageshack.us/my.php?image=039bo.png)

As i understood it is one uncorrect filling of xorg.conf.
I put on that "default", because this is a laptop, and I didn't know what to put on (in device and in screen).

But now I can't get the xorg.conf to edit it.

What should I do?

---

### Post by Vnepomuceno on 2006-04-17
Problem solved, wrong directory in command:

      sudo pico /etc/X11/xorg.conf

Now the only problem is: my computer is a laptop (of low quality, it sucks).
And I don't know what to put in the variable identifier and device of the "screen", because is that that is causing the error,

Anyone can help me?

---

### Post by henryk69 on 2006-04-17
There is probably an error in your your /etc/X11/xorg.conf file. Can you attach this file?

---

### Post by Vnepomuceno on 2006-04-17
Here is the file (I've atached before)

[[IMG]http://img429.imageshack.us/img429/2208/039bo.th.png[/IMG]](http://img429.imageshack.us/my.php?image=039bo.png)

"Undefined Device "Default Device" referenced by Screen "Default Screen".
The problem is that my PC is a notebook ELITEGROUP GREEN 550, and in the device SCREEN I don't know what to put in the "variables" "device" and "identifier"

Someone know what to put there? Someone with a notebook or a normal PC can send a pic of the configuration of the screen?

---

### Post by henryk69 on 2006-04-18
Hi Vnepomuceno,
You are showing us a screenshot of /var/log/Xorg.0.log !
Please _attach_ the file **/etc/X11/xorg.conf **so we can see where the parsing problem is. Without that file I won't be able to help you.

cheers,
Henryk

---

### Post by Vnepomuceno on 2006-04-18
Here is the printscreen of my /etc/X11/xorg.conf file.

[[IMG]http://img435.imageshack.us/img435/5535/044df.th.png[/IMG]](http://img435.imageshack.us/my.php?image=044df.png) [[IMG]http://img150.imageshack.us/img150/7528/050xl.th.png[/IMG]](http://img150.imageshack.us/my.php?image=050xl.png)

Once again ,I think that the error is on Section Screen, on Identifier, Device and Monitor, because my PC is a notebook (ELITEGROUP GREEN550) and I don't know how to put in there.

Can you help me? Never come I can enter Linux :(

---

### Post by henryk69 on 2006-04-18
Your problems have nothing to do with your PC being a notebook. Its just a wrong Identifier in the Device section. 
It should look like this:
> Section "Device"
 Identifier "Default Device"
Changing this should fix your problems.

---

### Post by Vnepomuceno on 2006-04-19
Problem solved by executing the command in root:

dpkg-reconfigure xserver-xorg

(command, to automatically detect computer hardware)
Thanks for the help ;)

---


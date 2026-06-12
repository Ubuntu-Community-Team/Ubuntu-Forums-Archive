---
title: "I can't install the NOAA Weather and Climate Toolkit"
date: 2015-03-20
forum: Installation &amp; Upgrades
---

### Post by nrmadden on 2015-03-20
Good morning,

I downloaded the NOAA Weather and Climate Toolkit  from [http://www.ncdc.noaa.gov/wct/install.php](http://www.ncdc.noaa.gov/wct/install.php) for the Ubuntu Linux Version.  I cannot see how to install this and friends that know a bit more  about Ubuntuthan me can't help either.  I would appreciate if someone could download this small application and tell me what the solution to installing it is.  I have tried changining the permissions of the .jar files and using java -jar wct-3.6.2.jar but it just sits there and looks at me.  I'm running Ubuntu 14.04

Thanks

Neville

---

### Post by PhilGil on 2015-03-20
Here's the terminal command and the output from my system. I'd start with installing icedtea-netx (I don't really want to test it because Java).
```
p####@p######:~$ javaws http://www.ncdc.noaa.gov/wct/wct-jnlp.php
The program 'javaws' is currently not installed. You can install it by typing:
sudo apt-get install icedtea-netx
```
Hope that gets you started.

---

### Post by nrmadden on 2015-03-21
> **PhilGil said:**
> Here's the terminal command and the output from my system. I'd start with installing icedtea-netx (I don't really want to test it because Java).
```
p####@p######:~$ javaws http://www.ncdc.noaa.gov/wct/wct-jnlp.php
The program 'javaws' is currently not installed. You can install it by typing:
sudo apt-get install icedtea-netx
```
Hope that gets you started.

Good afternoon Phil,

Thanks for that info.  Worked perfectly and saved a lot of pulling out of hair.  Will pass this info on to others.

Neville
In sunny Queensland

---

### Post by nrmadden on 2015-03-22
> **nrmadden said:**
> Good afternoon Phil,

Thanks for that info.  Worked perfectly and saved a lot of pulling out of hair.  Will pass this info on to others.

Neville
In sunny Queensland

Good afternoon everybody,

Spoke too soon.  The setup as described by Phil 'installs' the application but unfortunately this method makes a call to  [http://www.ncdc.noaa.gov/wct/wct-jnlp.php](http://www.ncdc.noaa.gov/wct/wct-jnlp.php)  each time the application is required.  What will happen wnen NOAA moves the application location or deletes it?

Can anyone help me?

Thanks

Neville

---

### Post by marcela-suarez on 2015-05-06
Thanks! This helped a lot!

---


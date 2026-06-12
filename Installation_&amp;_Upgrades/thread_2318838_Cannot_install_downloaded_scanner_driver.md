---
title: "Cannot install downloaded scanner driver"
date: 2016-03-29
forum: Installation &amp; Upgrades
---

### Post by stan28 on 2016-03-29
I downloaded the proper version of a driver for my EPSON WF-7620, put it in Downloads, extracted it, and tried to use GDebi to install it.  I got a 'permission denied' message.  I checked Properties for the .deb and for the underlying files, and made sure they were all read and write and the execute box was checked for the install.sh file.  What's going on???

---

### Post by X-RED_Tech on 2016-03-30
You need sudo to run a script. What you don't need is GDebi.

---

### Post by stan28 on 2016-03-30
I tried sudo first and got the same permission errors.

---

### Post by $yl9pAR%t on 2016-03-30
You are writing both about deb file and about sh file. I am not sure what you have, but if you have deb, do not extract it, you should right click this file and choose "Open with GDebi" or something like that. You can also open terminal in your Download folder and execute:

```
sudo gdebi name_of_your_deb_file
```

I expect you have your driver as deb file, but if I am wrong and you really have script (sh file), then use:

```
sudo sh name_of_your_sh_file
```

Edit:

If the above didn't help you, give us more info about your Ubuntu (version/flavour) and link where you downloaded driver.

---

### Post by stan28 on 2016-03-31
Thanks, had tried both recommendations and got same problem.  Downloaded driver file for EPSOM WF-7620 printer/scanner/all-in-one from EPSON website for Linux drivers, did it twice to make sure file was not corrupted.  Inside the tar file is a install.sh file which does not run with sudo or any other way I can think of, including running as root user.  Permissions in properties set to maximum.  Switched to trying gdebi as last resort, got same result.  Ubuntu is 14.04 with all updates.

---

### Post by $yl9pAR%t on 2016-03-31
1. Go to the directory where you extracted your tar file, open it in terminal and give me the output of:

```
ls -l
```

2. Did you setup a password when you were installing Ubuntu?

---

### Post by stan28 on 2016-04-01
I did it twice, once in Downloads, once it etc.  Ls -l gives
total 28
drwxrwxr-x 2 s s 4096 Sep 29  2015 core
drwxrwxr-x 2 s s 4096 Sep 29  2015 data
-rwxrwxr-x 1 s s 6941 Sep 29  2015 install.sh
drwxrwxr-x 2 s s 4096 Sep 29  2015 plugins
-rw-rw-r-- 1 s s 5370 Sep 29  2015 README.rst

2.  Yes, sudo calls for it.  I also tried logging in as root, which calls for it.

---

### Post by ian-weisser on 2016-04-01
Run install.sh using sudo. Show us the complete output.

---

### Post by $yl9pAR%t on 2016-04-01
Give us also output of:

```
sudo -l -U s
```

This will show us, if user "s" (I assume it is your login), has permission to execute sudo.

---

### Post by stan28 on 2016-04-02
install.sh ran today.  I have no idea why.  I've rebooted several times, changed a few things, but noting related to this install.sh .  It would not run before, but now it did and I am a happy camper.  Thanks for your response.

---

### Post by Russ_Spencer on 2016-04-28
I'm newer than a newbie and I'm having trouble with getting the printer drivers installed and the printer working.  I've downloaded the printer drivers and that's about as far as I've gotten.  Terminal is my enemy, but following along here, I can pretty well get it right.  BUT - I'm not getting the drivers recognized and/or the drivers in the right location to be recognized.   I'm working with ubuntu 14.04 and a Canon MX494 printer.  Any help will be greatly appreciated.  Keep in mind, although I have Terminal open, doesn't mean I know what's going on. lol  Thanks for your time.

---


---
title: "perl: warning: Setting locale failed"
date: 2005-10-13
forum: Installation &amp; Upgrades
---

### Post by hanzj on 2005-10-13
Hello, everyone. I'm getting the following error. 

> perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en_JP:en",
        LC_ALL = (unset),
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory


I upgraded with the following steps:
1.sudo apt-get update
2.sudo apt-get dist-upgrade
3. sudo apt-get install ubuntu-base ubuntu-desktop
4. a command like "sudo install -f" or something



When I ran step 3 (sudo apt-get install ubuntu-base ubuntu-desktop), it suggested I do "sudo install -f" or something like that because of something to do with dependencies.
So I did. It's when I did step 4 that I got the error at the top of this message.


My Ubuntu is in English, but I've installed Japanese text input support also.

I also get this error when I ran "irc" from the terminal. I'm guessing I'd get this error in many, many other commands/programs.

---

### Post by skarg on 2006-05-23
Under Ubuntu 5.10 (breezy), just issue the following command:
```
$ sudo dpkg-reconfigure locales
```

Then you can select whichever locale is native to you.  For me, I selected:
en_US ISO-8859-1

If you had installed the localeconf package, remove it before running the dpkg-reconfigure:
```
$ sudo apt-get remove localeconf
```

Best Regards,

Steve

---

### Post by asmallerbrain on 2006-11-01
If you're having this problem on dapper/edgy, you may have to regen the locales using "locale-gen <localename>" where localename is the name of the locale you want to regenerate (e.g. "en_US.UTF-8"), then "dpkg-reconfigure locales".

---

### Post by dannyboy79 on 2007-05-09
this didn't work for me! i had a system that was at dapper forever. then I upgraded to edgy using update-manager, then to feisty and I kept getting the above error. so I issued

sudo aptitude install locales

and now the error stopped appearing.

---

### Post by alanhaggai on 2008-06-19
The following command helped me:
```
sudo locale-gen
```

---

### Post by Casla on 2008-06-29
Thank you asmallerbrain, locale-gen fixed my problem.

---


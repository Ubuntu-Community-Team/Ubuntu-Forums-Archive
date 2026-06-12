---
title: "Trouble installing  v11.10"
date: 2012-04-18
forum: Installation &amp; Upgrades
---

### Post by xXxTommy316xXx on 2012-04-18
I have attempted to install this several times with no success. I keep getting an error message that says "Permissions Denied" and then it tells me, for more info. see the following log file, which is in a nonexistent path. Needless to say, I am at a loss, currently. Can anyone help me out with this please ?

---

### Post by codemaniac on 2012-04-18
Hello xXxTommy316xXx ,

Warm greetings and welcome to the Ubuntuforums .
It would be helpful if you provide more information on the above issue .Are you talking about installation of a new application or 11.10 version of ubuntu .

Best Regards,
Codemaniac

---

### Post by xXxTommy316xXx on 2012-04-20
> **codemaniac said:**
> Hello xXxTommy316xXx ,

Warm greetings and welcome to the Ubuntuforums .
It would be helpful if you provide more information on the above issue .Are you talking about installation of a new application or 11.10 version of ubuntu .

Best Regards,
Codemaniac


A new application, I downloaded the "wubi" installer to run Ubuntu alongside windows.

---

### Post by codemaniac on 2012-04-20
Wubi is good as a stepping stone to ubuntu linux and will give you a taste of Ubuntu .However when you start feeling comfortable , you may do a normal installation .

---

### Post by xXxTommy316xXx on 2012-04-20
Oh I did not know that. However I cannot install Ubuntu, which is my problem.

---

### Post by bcbc on 2012-04-20
That nonexistent path exists and you can get there with this shortcut (environment variable): %TEMP%
If you navigate step by step you'll fail as some parts are hidden by windows (default setting).

---

### Post by codemaniac on 2012-04-20
I believe until now you have played with the live Ubuntu cd/usb in windoes environment .Had you by any chance given a try booting off from the CD , it will let you play with options like Try Ubuntu / Install Ubuntu .
What error exactly yoyu are getting when you try to boot from the CD , can you please post  ?

---

### Post by jadtech on 2012-04-21
when installing WUbi when you get the  error just do a reboot and wubi will continue to set up and boot..

I installed 3x  on this lap top with wubi  and everytime the same error and the install is working fine, for some reason the wubi installer can not bring up the reboot now notice  ..

---

### Post by jadtech on 2012-04-21
in finding that the wubi install is going strong im sure a full install would be way better, it is a bit resistant to upgrade to 12.04 beta 2 but finally got info that got it to work on the AMD 64bit with the AMD ati video  card today ..

if you give your self a big enough partition to play on it it could run this way for a long while , most important thing to remember is  don't be afraid to do things don't get upset or frustrated if  things go wrong while learning  and you need to re-install thats what learning is all about :)

---

### Post by bcbc on 2012-04-21
> **jadtech said:**
> when installing WUbi when you get the  error just do a reboot and wubi will continue to set up and boot..

I installed 3x  on this lap top with wubi  and everytime the same error and the install is working fine, for some reason the wubi installer can not bring up the reboot now notice  ..
That's true, but only if it's bug [lpbug]862003[/lpbug]. There are other possible reasons for failure where that won't work.

---

### Post by xXxTommy316xXx on 2012-04-21
Thanks for the feedback, I will try to install Ubuntu from the Wubi again, only this time rebooting afterwards. If that does not work I will copy the error message and post it. Thanks again !

---


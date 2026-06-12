---
title: "Canon LBP6020B and 14.04 lts installation problem"
date: 2016-01-05
forum: Installation &amp; Upgrades
---

### Post by ayhan3 on 2016-01-05
hi guys . i am new user . i wanna install my printer but it doens't work. i have 64 bit 14.04 trusty system.

[how i install link.]("http://random0musings.blogspot.com.tr/2014/06/ubuntu-1404-and-canon-lbp6020b-laser.html")

i did everything in this link but when i clink print my printer has no action.

but in the final lines there is 
```
sudo service ccpd status
```


when i write this code i have just 1 number.

```


/usr/sbin/ccpd: 1054

```


when i look for errors. 

```
cat /var/log/cups/error_log
```  

with this i have this answer: 

```
W [04/Jan/2016:01:03:25 +0200] AddProfile failed: org.freedesktop.ColorManager.Device.ProfileAlreadyAdded:profile object path '/org/freedesktop/ColorManager/profiles/Canon_LBP6020_Gray__' has already been added
W [04/Jan/2016:01:07:47 +0200] AddProfile failed: org.freedesktop.ColorManager.Device.ProfileAlreadyAdded:profile object path '/org/freedesktop/ColorManager/profiles/Canon_LBP6020_Gray__' has already been added
W [04/Jan/2016:01:22:29 +0200] AddProfile failed: org.freedesktop.ColorManager.Device.ProfileAlreadyAdded:profile object path '/org/freedesktop/ColorManager/profiles/Canon_LBP6020_Gray__' has already been added
W [04/Jan/2016:01:24:20 +0200] AddProfile failed: org.freedesktop.ColorManager.Device.ProfileAlreadyAdded:profile object path '/org/freedesktop/ColorManager/profiles/Canon_LBP6020_Gray__' has already been added
E [04/Jan/2016:01:26:05 +0200] [Client 8] Returning IPP client-error-not-possible for Cancel-Job (ipp://localhost/jobs/57) from localhost
E [04/Jan/2016:01:29:42 +0200] [Job 57] Stopping unresponsive job.
E [04/Jan/2016:01:30:47 +0200] [Job 58] Stopping unresponsive job.
```

can u help me about that . or i will buy new printer :)  . i hope my english is enough for my problem... Thanks .

---

### Post by ayhan3 on 2016-01-06
is there anyone can help me ?

---

### Post by ayhan3 on 2016-01-07
finally i did it  myself. Thanks for your help :p

[http://askubuntu.com/questions/463289/cant-get-my-canon-lbp-printer-to-run-under-ubuntu-14-04](http://askubuntu.com/questions/463289/cant-get-my-canon-lbp-printer-to-run-under-ubuntu-14-04)

i use that link when i install printer. u can do it . but u can install it a few times . and it shouldn't print a few times maybe . but dont give up :)

---


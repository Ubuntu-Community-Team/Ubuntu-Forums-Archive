---
title: "Sorry, password authentication didn't work. Please try again"
date: 2023-08-12
forum: Installation &amp; Upgrades
---

### Post by rbrookes on 2023-08-12
Hi all,

I've installed 23.04 into a VMWare Workstation (17.0.2 build-21581411) VM and every time I try to log in with the credentials I provided at installation, I get the following error:

Sorry, password authentication didn't work. Please try again

I've downloaded the ISO 3 times and installed 3 times

Please tell me I'm doing something daft,

Thanks

Richard

---

### Post by crip720 on 2023-08-12
The most common cause of this problem is the caps lock key.    If it is accidentally turned on when inputting password/credentials then you get this problem.

---

### Post by rbrookes on 2023-08-12
I've used the 'Reveal password' option so I know it's correct and it's on 3 different installs.

---

### Post by TheFu on 2023-08-12
> **rbrookes said:**
> I've used the 'Reveal password' option so I know it's correct and it's on 3 different installs.

I'd check the LANG and Locale settings.  Sometimes a different keyboard will cause issues with password entries.

Also, rather than downloading the ISO over and over, why not just validate it is correct using the sha256sum tool and the posted answers?

---

### Post by jmac-pt87 on 2023-12-05
> **rbrookes said:**
> Hi all,

I've installed 23.04 into a VMWare Workstation (17.0.2 build-21581411) VM and every time I try to log in with the credentials I provided at installation, I get the following error:

Sorry, password authentication didn't work. Please try again

I've downloaded the ISO 3 times and installed 3 times

Please tell me I'm doing something daft,

Thanks

Richard


I have a similar problem! The most frustrating part is that when I try to redefine the password, I input the password and right after when is necessary to confirm the new password, it says that the input password is not equal!

Honestly, I do not know what is wrong!

Already checked the key board setting, language, if the caps is on when I type the password and nothing...

For context, I'm running a Ubuntu v22.04.3 LTS machine in VMWare Fusion.
My machine is a MacBook Pro model A1398.

Any help will be more than welcomed

---

### Post by Claus7 on 2023-12-05
Hello,

> **jmac-pt87 said:**
> ... and right after when is necessary to confirm the new password, it says that the input password is not equal!

...

do you copy-paste from the first input, or type it anew? I would try the latter and see if things are getting fixed. 

Regards!

---


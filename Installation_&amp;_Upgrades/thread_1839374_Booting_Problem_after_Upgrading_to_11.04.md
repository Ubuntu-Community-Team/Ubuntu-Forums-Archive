---
title: "Booting Problem after Upgrading to 11.04"
date: 2011-09-05
forum: Installation &amp; Upgrades
---

### Post by awd01 on 2011-09-05
Hello guys, I have the following problem and I think you can help me:

Yesterday I run the update manager and I decided to upgrade my 10.10 Ubuntu to the newest version.. 11.04 . So the system started the steps. Step 1 delete unsupported application Step 2 download etc etc etc which I don't remember. However I had to leave so I normally turn off my computer.. ( I noticed some commands in the black screen before the computer turns off and I dont know when this stopped cause I left.

Today, I turn it on and I recieve the following message:

```
init :  udevtrigger main process (434) terminated with status 1
init :  udevtrigger post-stop process (437) terminated with status 1
init :  udevmonitor main process (433) killed by TERM signal
The disk drive for / is not ready yet or not present
```Continue to wait; or Press S to skip mounting or M for manual recovery

-If I wait nothing happens
-If I press S  I get message:

```
The disk drive for /tmp is not ready   
```    (..some other stuff and then..)
```
mountll : Plymouth command failed
mountll : Disconnected from Plymouth
```ps I havent try the manual recovery cause I dont know what to do...
As you easily noticed I am a new Linux user.. :D

---

### Post by mörgæs on 2011-09-05
Plymouth is a fundamental part of the new Ubuntus. If it is not working properly, I don't think it is worth the time to troubleshoot; better to back up your files and reinstall.

---

### Post by awd01 on 2011-09-06
Yeh after some research I found out that its too hard to troubleshoot and many people have similar problems with this version so I am gonna install the 10.04 . However I don't know how to back up from the live cd but I think that I am gonna find the solution :D 

Thank you for your time and your answer! :)

---


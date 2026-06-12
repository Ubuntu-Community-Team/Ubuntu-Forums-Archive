---
title: "Auto mounting Errors after upgraded to 12.10"
date: 2012-11-18
forum: Installation &amp; Upgrades
---

### Post by nagubhai on 2012-11-18
Hello,
 
I am having errors while booting into Ubuntu 12.10 after upgrarding to it like below.
 
Error occured while mounting /320-dump 
Press S skip mounting it.
 
Is this upgrade issue? I dont have it in 12.04. 
 
If this is discussed already please redirect me to the thread.
 
PS : Drives are automounting without any issues anyway
 
Thanks
Nagesh

---

### Post by philhughes on 2012-11-18
Could it be related to these bugs??

[https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/1059726](https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/1059726)
[https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/1059471](https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/1059471)

Try removing the dash from the name.

---

### Post by nagubhai on 2012-11-19
> **philhughes said:**
> Could it be related to these bugs??

[https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/1059726](https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/1059726)
[https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/1059471](https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/1059471)

Try removing the dash from the name.

I think that is not an issue. I have another drive with name Windows 7 also giving same message.
Any workarounds?

---

### Post by philhughes on 2012-11-21
The space in "Windows 7" will definitely cause the problem as shown in the first bug. Not sure about the dash. As shown in the second bug report, a fix fror mountall is in proposed. Only work around I know is to rename the drives.

---

### Post by Morbius1 on 2012-11-21
If this is still an issue please post the output of the following commands:
```
sudo blkid -c /dev/null
``````
cat /etc/fstab
```

---

### Post by nagubhai on 2012-11-21
> **Morbius1 said:**
> If this is still an issue please post the output of the following commands:
```
sudo blkid -c /dev/null
``````
cat /etc/fstab
```


Reinstalled ubuntu 12.04. 8-[ No issues now

---


---
title: "How to fix windows boot?"
date: 2014-10-04
forum: Installation &amp; Upgrades
---

### Post by thumper2 on 2014-10-04
Hello guys,

I have installed windows 8 then i installed ubuntu (dualboot) but when i start my machine i only can boot in ubuntu. 

When i installed ubuntu i saw this msg: [http://virtualupload.net/images/39065607293111354449.jpg](http://virtualupload.net/images/39065607293111354449.jpg) , I followed tutorial from youtube how to make dualboot.

And here is error msg when i open boot repair: [http://virtualupload.net/images/11872269992230103604.png](http://virtualupload.net/images/11872269992230103604.png)

Lenovo g500
Windows 8.1 x64 & last version of ubuntu x64

Hope some1 can help.

Thanks!

---

### Post by kc1di on 2014-10-04
You need to have both Ubuntu and Windows on the same kind of Drive. That is if you boot Ubuntu from MBR with regular partioning you'll have to do the same with Windows in order to get them both working. 

So Make sure Windows 8 is set up to boot from UEFI or MBR and tha Ubuntu is the same.

---

### Post by thumper2 on 2014-10-04
Yeah, both windows and ubuntu are installed in same kind of Drive (MBR)

---

### Post by yancek on 2014-10-04
> Yeah, both windows and ubuntu are installed in same kind of Drive (MBR) 		

The second image you posted shows it detected GPT partitioniing and that you need to create the 1MB partition.
The first image you posted shows you are using UEFI/GPT and that you need to create an EFI partition.  It also does not show any windows partitions.  Is windows on another drive?

---

### Post by Dennis N on 2014-10-04
Your installer "Something Else" screenshot shows only one OS partition usin 990 GB of the disk (which must be 1 TB) and since it is ext4, would be for Linux. No sign of a Windows installation on here. It looks like something the Ubuntu installer might do if told to use the entire disk instead of "something else". (a minor point: the swap space is pretty large - 10GB - 4 GB would be sufficient)

A Lenovo G500 laptop has only 1 drive as far as I can tell.

Posting a boot info script output would help to get the entire picture.

---

### Post by thumper2 on 2014-10-04
Hello guys,

Thanks for your reply!

I formated my HDD (samsung 1TB HDD) and installed ubuntu x64 fist, here is how my partitions looks: [https://i.imgur.com/zBrxH0J.png](https://i.imgur.com/zBrxH0J.png)  and now im trying to install windows 8.1 (x64) but i see this error code: [https://i.imgur.com/MEUgiyO.jpg](https://i.imgur.com/MEUgiyO.jpg) 

I dont know why partition type is changed to GPT (after im installing ubuntu): [https://i.imgur.com/MEUgiyO.jpg](https://i.imgur.com/MEUgiyO.jpg)   Im sure that my disk type was MBR but for some reason ubuntu changed it :(

Can i change just just partition 4 (200gb) from GPT to MBR ([https://i.imgur.com/MEUgiyO.jpg](https://i.imgur.com/MEUgiyO.jpg)) in ubuntu? Because i want to install ubuntu in this partition.

If some1 can help me would be great... If you can just guide me how to install ubuntu x64 with windows 8 x64... I can format my HDD again if that is necessary, all i need to make it work.

Thank you again!
Thumper

---

### Post by thumper2 on 2014-10-04
Edit: i fixed it. Thanks!

---


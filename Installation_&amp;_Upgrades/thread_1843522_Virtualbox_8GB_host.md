---
title: "Virtualbox 8GB host"
date: 2011-09-13
forum: Installation &amp; Upgrades
---

### Post by gurtej14 on 2011-09-13
Hi Everyone,

I am new to this forum and am not sure if I am posting my question in the correct section. 

I have 32-bit ubuntu 11.40 running as host and on Virtualbox I wish to install xp. I did kernel update (fix) to accommodate 8GB for ubuntu 11.04. However, my virtualbox still detects on 3.5GB. 

Any advice. 

Thank you all anyway. 

Guru

---

### Post by haqking on 2011-09-13
> **gurtej14 said:**
> Hi Everyone,

I am new to this forum and am not sure if I am posting my question in the correct section. 

I have 32-bit ubuntu 11.40 running as host and on Virtualbox I wish to install xp. I did kernel update (fix) to accommodate 8GB for ubuntu 11.04. However, my virtualbox still detects on 3.5GB. 

Any advice. 

Thank you all anyway. 

Guru

Hi and welcome to the forums.

enable PAE from the VM settings.

However if you have 8GB on your host, you dont want to be assigning more than half to your VM anyways. Your VM should see what you assign to it

---

### Post by CharlesA on 2011-09-13
I'd suggest just installing 64-bit OS but if you don't want to reinstall, do what haqking suggests.

---

### Post by haqking on 2011-09-13
> **CharlesA said:**
> I'd suggest just installing 64-bit OS but if you don't want to reinstall, do what haqking suggests.


yes he could do that.

If you do decide to install a x64 bit guest on a 32 bit host i would refer you to here:

[http://www.virtualbox.org/manual/ch03.html#intro-64bitguests](http://www.virtualbox.org/manual/ch03.html#intro-64bitguests)

---

### Post by gurtej14 on 2011-09-13
Thank you for the quick reply. I tried and could not find any setting for enabling PAE for virtualbox. 

Regards,
Guru

---

### Post by haqking on 2011-09-13
> **gurtej14 said:**
> Thank you for the quick reply. I tried and could not find any setting for enabling PAE for virtualbox. 

Regards,
Guru


What version are you using ?

you can see here in the manual [http://www.virtualbox.org/manual/ch03.html#settings-processor](http://www.virtualbox.org/manual/ch03.html#settings-processor)

---

### Post by gurtej14 on 2011-09-13
Hi 
I am using oracle virtualbox 4.1.2 , can't find PAE setting. 

Regards,
Guru

---

### Post by CharlesA on 2011-09-14
It should be listed under 'processor' in System properties of the VM.

---

### Post by haqking on 2011-09-14
> **gurtej14 said:**
> Hi 
I am using oracle virtualbox 4.1.2 , can't find PAE setting. 

Regards,
Guru


as it mentions in the instructions i sent you in my last post and as CharlesA says above me, it is on processor tab.

see attachment

---

### Post by gurtej14 on 2011-09-16
Hi Haqking,

Is the option available after XP install in Virtualbox ? Because I don't get these options. 


Regards,
Guru

---

### Post by gurtej14 on 2011-09-16
> **haqking said:**
> as it mentions in the instructions i sent you in my last post and as CharlesA says above me, it is on processor tab.

see attachment

Hi Haqking,

Are these options available after XP install. Because I don't them yet. 

Regards,
Guru

---

### Post by haqking on 2011-09-16
> **gurtej14 said:**
> Hi Haqking,

Are these options available after XP install. Because I don't them yet. 

Regards,
Guru


Yes, show us a screen dump of your options then.

You access the processor tab from settings of the VM, make sure the VM is not running.

Did you read the link i posted to the refernce about PAE in the Vbox manual online ?

It might be that you are enabling PAE on a host system that is also using PAE.

It might be better for you to install a x64 bit host if you can

---


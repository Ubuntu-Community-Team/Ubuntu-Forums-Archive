---
title: "upgrade firefox to 43.0.4"
date: 2016-01-26
forum: Installation &amp; Upgrades
---

### Post by PedroPV on 2016-01-26
Will someone show me how to upgrade my firefox 33.0 that came with Ubunto 14 to firefox 43.0.4? Whta is the command line?
Thanks
Pedro

---

### Post by kansasnoob on 2016-01-26
> **PedroPV said:**
> Will someone show me how to upgrade my firefox 33.0 that came with Ubunto 14 to firefox 43.0.4? Whta is the command line?
Thanks
Pedro

It should be upgraded along with standard updates. How long ago did you install Ubuntu? When did you last update it?

---

### Post by PedroPV on 2016-01-27
Long time ago. Should I try sudo apt-get update
or sudo apt-get upgrade ?

---

### Post by LukeMorrison on 2016-01-27
You will need to run both of them. 

```
sudo apt-get update 
``` will update the list of the software that is installed on your machine
```
sudo apt-get upgrade 
``` will actually upgrade the software.

Post back any warnings / errors that may be returned

---

### Post by kansasnoob on 2016-01-27
Today Firefox 44.0 showed up in security updates. I'm curious why you're not getting regular security update notifications :confused:

---

### Post by yoshii on 2016-01-27
check your preferences for Software Update and Ubuntu Software Center and Synaptic Package Manager.  
I think you could just type "sudo apt-get install Firefox" and it will check the vesioning automatically.  
You don't have to update/upgrade your entire system.

---


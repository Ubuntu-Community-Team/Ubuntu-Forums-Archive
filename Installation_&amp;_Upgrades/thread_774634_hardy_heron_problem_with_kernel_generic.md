---
title: "hardy heron problem with kernel generic"
date: 2008-04-29
forum: Installation &amp; Upgrades
---

### Post by rahulsharma on 2008-04-29
hey guys i have some problem with hardy heron. I upgraded from gutsy to hardy through online but i am facing some problem now at the boot up i have to kernel generic one is 2.16.24-16 and other one is 14. when i boot up using 16 its gets stuck with an error as follow

[16.867434]ACPI : EC :acpi_ec_wait time out, status=0, expect even=1
[16.867482]ACPI : EC :read time out , command=128

however there is no problem booting with kernel 14 but after logging in i faced a weird problem, I can only get sound in either rythmbox or youtube depending on which application i start first. To get sound in other one i need to do alt+ctrl+del and then start the other application. 

I don't understand what is the problem should i just install gutsy and upgrade it again or there is some solution for that.

Rahul

---

### Post by martrn on 2008-04-29
Have you tried 

sudo apt-get install linux-rt

+ reboot with realtime kernel. ?

---

### Post by rahulsharma on 2008-04-30
no i haven't cuz i never found out that command. would you be able to tell me what this command would actually do before i go ahead and use it 
i hope its alright to upgrade through internet cuz i don't have cd

---


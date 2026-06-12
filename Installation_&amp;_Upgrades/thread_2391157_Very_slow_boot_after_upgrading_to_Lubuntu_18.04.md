---
title: "Very slow boot after upgrading to Lubuntu 18.04"
date: 2018-05-06
forum: Installation &amp; Upgrades
---

### Post by pichuchikid on 2018-05-06
Hi I was using Lubuntu 17 for my old PC and it was working great. Recently I upgraded to 18.04 and the boot time increased more or less from 1.5 minutes to at least 4 minutes. Since I didn't worried much about my contents I installed Lubuntu 18.04 again from scratch, and the problem didn't recovered. I executed cat /var/log/boot.log in console and this is what it encountered:
[https://mega.nz/#!4cZyVI5a!_1l4FmFwzG_VUF-ze-L3AxiAtciTw0G2VmFxsLmK_TE](https://mega.nz/#!4cZyVI5a!_1l4FmFwzG_VUF-ze-L3AxiAtciTw0G2VmFxsLmK_TE)
I didn't know which parts where important so I uploaded the entire file

Is there any paramater I should change to make it faster? I could reinstall Lubuntu 17 otherwise.
Thanks!

---

### Post by Xian on 2018-05-06
You are getting a lot of timeouts similar to:

```
[    **] A start job is running for Hold until boot process finishes up (3min 8s[   ***] 
A start job is running for Hold until boot process finishes up (3min 8s[  *** ] 
A start job is running for Hold until boot process finishes up (3min 9s[ ***  ] 
A start job is running for Hold until boot process finishes up (3min 9s[***   ] 
A start job is running for Hold until boot process finishes up (3min 10[**    ] 
A start job is running for Hold until boot process finishes up (3min 10[*     ] 
A start job is running for Hold until boot process finishes up (3min 11       ]
Stopping Session c1 of user lightdm.
[  OK  ] Stopped Session c1 of user lightdm.
```

So let's start with the lightdm configuration. 

From a terminal type these commands:

```
sudo dpkg-reconfigure lightdm
```

[COLOR=#111111][FONT=Ubuntu]At the prompt you should select 'lightdm'. 

[/FONT][/COLOR]Reboot system.

---

### Post by pichuchikid on 2018-05-06
I entered that command and there was no prompt.
I rebooted and it made no difference :s.

---

### Post by Xian on 2018-05-06
Do you have lightdm installed?
```
sudo apt-get install lightdm
```
By using the command 
```
sudo dpkg-reconfigure lightdm
```
You should get windows similar to this:

[[IMG]http://i.imgur.com/kB2ehQVl.png[/IMG]]("https://imgur.com/kB2ehQV")

[[IMG]http://i.imgur.com/c6HVQKWl.png[/IMG]]("https://imgur.com/c6HVQKW")

---

### Post by pichuchikid on 2018-05-06
It was already installed, nothing happens after I enter that command still. Could it be a problem with plymouth-start.service??

---

### Post by Xian on 2018-05-07
From this I wonder ... 

Is it possible that you have more than one user with the same UID?

```
[  OK  ] Started Session c1 of user lightdm.[  OK  ] Started User Manager for UID 106.
[    **] A start job is running for Hold until boot process finishes up (3min 8s[   ***] 
A start job is running for Hold until boot process finishes up (3min 8s[  *** ] 
A start job is running for Hold until boot process finishes up (3min 9s[ ***  ] 
A start job is running for Hold until boot process finishes up (3min 9s[***   ] 
A start job is running for Hold until boot process finishes up (3min 10[**    ] 
A start job is running for Hold until boot process finishes up (3min 10[*     ] 
A start job is running for Hold until boot process finishes up (3min 11         
Stopping Session c1 of user lightdm.
[  OK  ] Stopped Session c1 of user lightdm.
         Stopping User Manager for UID 106...
[  OK  ] Created slice User Slice of lucas.
         Starting User Manager for UID 1000...
[  OK  ] Started Session c2 of user lucas.
[  OK  ] Stopped User Manager for UID 106.
[  OK  ] Removed slice User Slice of lightdm.
[  OK  ] Started User Manager for UID 1000.
```

---

### Post by Xian on 2018-05-07
You can also read here to see if any solutions posted helps:

[https://askubuntu.com/questions/760825/cannot-boot-system-due-to-start-job-running-for-hold?](https://askubuntu.com/questions/760825/cannot-boot-system-due-to-start-job-running-for-hold?)

---


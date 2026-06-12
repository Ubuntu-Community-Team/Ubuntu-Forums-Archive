---
title: "Problem installing 10.04"
date: 2011-04-09
forum: Installation &amp; Upgrades
---

### Post by snhapratyush on 2011-04-09
**[COLOR=Sienna][SIZE=3][FONT=Arial]I want to install ubuntu 10.04 in a particular drive say[/FONT][/SIZE][/COLOR]** **[FONT=Arial][SIZE=2][COLOR=Sienna]D DRIVE[/COLOR][/SIZE][/FONT]**.[SIZE=3]**[COLOR=Sienna][FONT=Arial]While [/FONT][/COLOR][FONT=Arial][COLOR=Sienna]booting from Ubuntu CD [/COLOR][/FONT]**[/SIZE][B][FONT=Arial][SIZE=3][COLOR=Sienna]and following the steps i get stuck where it asks to prepare disk space it is showing only two options 1. Erase and use the entire disk & 2. Specify partitions  manually. I am selecting the second option but can't specify the size i.e. say 20 GB for ubuntu. I can't do that !! Plz help me out.

Thanx .[/COLOR][/SIZE][/FONT][/B]

---

### Post by Dutch70 on 2011-04-09
Have you tried selecting "Try Ubuntu" instead of install? Do this to make sure it works well with your hardware.

Do not mess with the windows partitions from Ubuntu, or anything other than windows for that matter. 
Are you talking about windows XP? Vista?

---

### Post by Hedgehog1 on 2011-04-10
> **snhapratyush said:**
> I want to install ubuntu 10.04 in a particular drive say D DRIVE. While booting from Ubuntu CD and following the steps i get stuck where it asks to prepare disk space it is showing only two options 1. Erase and use the entire disk & 2. Specify partitions  manually. I am selecting the second option but can't specify the size i.e. say 20 GB for ubuntu. I can't do that !! Plz help me out.

Thanx .

To install Ubuntu in a dual boot using the space your 'D DRIVE' is using, we would typically have you use the Windows Disk Administrator and delete the partition that is the 'D drive'.

**HOWEVER, BEFORE YOU DELETE ANYTHING**, please do this from the Ubuntu LiveCD/LiveUSB and lets be sure what your disk partition layout really looks like.

Please boot off the LiveCD/Live USB, select 'TRY', and then:

In the Terminal (Menu to: Applications >> Accessories >> Terminal), please run this command:  (the -'l' is a lower case 'L')
```
sudo fdisk -lu
```
Then copy the text from the output and paste it into your next post.


***The Hedge***

:KS

---

### Post by Dutch70 on 2011-04-10
Glad to see it's solved. :)

Would you mind telling us what you did to solve your problem?

---


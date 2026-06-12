---
title: "Help  I need choose between &quot;\&quot; , &quot;\boot&quot; or &quot;\home"
date: 2011-03-13
forum: Installation &amp; Upgrades
---

### Post by javiersc on 2011-03-13
:shock:   I try to install [SIZE=2]**edubuntu**[/SIZE] but the[COLOR=Red]** installation fails**[/COLOR] after 10  minutes, so I delete the partitions and now I have to install manually so I am not sure about what to choose for mount point so please help me I got 
[SIZE=2][B]Windows 7 
Linux Mint [/B][/SIZE]
and now go for **[SIZE=2]Edubuntu[/SIZE]**

so I Choose the [COLOR=Red]**free space**[/COLOR]

[IMG]http://farm6.static.flickr.com/5134/5521442735_ef81b4b577_b.jpg[/IMG]

I believed is[SIZE=2][COLOR=Blue] **/boot**[/COLOR][/SIZE]    but I'm not really sure. please tell me I don't know 
maybe is[SIZE=2][COLOR=Blue] **/        **[/COLOR][/SIZE]  my mount point. :confused:



[IMG]http://farm6.static.flickr.com/5057/5522007200_d6b33babc8_b.jpg[/IMG]

---

### Post by Hedgehog1 on 2011-03-13
Please do not define the '/boot', it will follow '/' and that is OK.

May I suggest:

```

**sda5** '/'     ext4  15 gigs
**sda6** 'swap'        2.2 gigs
**sda7** '/home' ext4 (whatever space is left inside extended partition **sda3**
```
Go ahead and format **sda5** & **sda7**

Also, leave 'Device for boot loader operation' set to:
```
**/dev/sda** ATA Toshiba... 
```

DO NOT choose a **sda_1_** or **sda_2_**, just **/dev/sda**.

***The Hedge***

:KS

---

### Post by srs5694 on 2011-03-13
I concur with Hedgehog1. Note that following this advice will necessitate first deleting the existing /dev/sda5, /dev/sda6, and /dev/sda7 partitions. This also assumes that your current /dev/sda5 is not used for anything (like another Linux installation). If you've already got a Linux installation that uses /dev/sda5, don't delete it. That will leave you with relatively little space for Ubuntu, though.

---


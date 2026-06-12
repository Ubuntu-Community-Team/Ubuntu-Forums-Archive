---
title: "laptop mode still killing my drive"
date: 2009-03-10
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by mariuz on 2009-03-10
seems that on dell vostro a860 the base model 
[http://www.dell.com/content/products/productdetails.aspx/laptop-vostro-a860?c=us&cs=04&l=en&s=bsd](http://www.dell.com/content/products/productdetails.aspx/laptop-vostro-a860?c=us&cs=04&l=en&s=bsd)

 Load_Cycle_Count is increasing when i'm on battery 

I can hear the heads parking once at 5sec also i have checked the smart values

sudo smartctl -a /dev/sda | grep Load_Cycle
i disabled it for the moment and now i can relax on NOT hearing the heads going offline and back fast :P

$ sudo hdparm -B 255 /dev/sda

ps:maybe i should remove acpi ?
is in the list of autoremovable packages

---

### Post by yelo3 on 2009-03-11
hdparm is set in /etc/acpi/*.d/90-hdparm.sh

You can edit those files to -B 200 to get some power management. This is what I've done.

---

### Post by nyarnon on 2009-03-11
You might also consider reading:

[https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/317781/comments/45](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/317781/comments/45)

Where theo explains some changes made to laptop mode. Although thats tailerd to prevent multiple activity it could be that your normal drive doesn't react to well to the SDD optimation?

---

### Post by mariuz on 2009-03-12
> **yelo3 said:**
> hdparm is set in /etc/acpi/*.d/90-hdparm.sh

You can edit those files to -B 200 to get some power management. This is what I've done.

Ok thanks i see that by default is  128

> hdparm -B 128

---

### Post by Mad_Gouki on 2009-04-15
I guess there's no patch ever arriving for this?  I assume that the power management values used are compatible with most controllers and drives.  This has been a known issue for years now.  It would be nice if they included some easy way to fix this other than going in and editing the configuration files every install.

---


---
title: "installed ubuntu on external hard drive, confused about booting"
date: 2009-11-18
forum: Installation &amp; Upgrades
---

### Post by whitebear1029 on 2009-11-18
i have installed ubuntu on an external hard drive. ive followed instructions from other sites on how to do this and it seemed to go just fine.

many of the posts said to install grub onto (hd1) instead of the default (hd0). after ubuntu is installed and you boot, they say you get an error 17 or something and that you need to change the root from (hd1,0) to (hd0,0) in the boot menu.

however, when i installed ubuntu i didnt bother to change this in the boot menu and it booted just fine with no problems. 

im wondering if i still need to change this.

ubuntu loads when the external drive is plugged in, and vista loads when it isnt.


external drive is a 500GB seagate freeagent go
-100GB partition for ubuntu
-363GB formatted NTFS
-2GB of swap
laptop is a toshiba satellite A205 S5804
ubuntu is version 9.10

any more info, just ask

any help appreciated!

---

### Post by raymondh on 2009-11-18
> **whitebear1029 said:**
> i have installed ubuntu on an external hard drive. ive followed instructions from other sites on how to do this and it seemed to go just fine.

many of the posts said to install grub onto (hd1) instead of the default (hd0). after ubuntu is installed and you boot, they say you get an error 17 or something and that you need to change the root from (hd1,0) to (hd0,0) in the boot menu.

however, when i installed ubuntu i didnt bother to change this in the boot menu and it booted just fine with no problems. 

im wondering if i still need to change this.

ubuntu loads when the external drive is plugged in, and vista loads when it isnt.


external drive is a 500GB seagate freeagent go
-100GB partition for ubuntu
-363GB formatted NTFS
-2GB of swap
laptop is a toshiba satellite A205 S5804
ubuntu is version 9.10

any more info, just ask

any help appreciated!

If it is working as you wished .... then congratulations .... no need to change anything. Unless, you plan to have the external permanently plugged to your laptop and just select the OS upon start-up.

I think that set-up is fine.  This way, no one messes with your ubuntu unless they have physical access to your seagate ;)

Happy ubuntu-ing.

---

### Post by whitebear1029 on 2009-11-18
thankyou for your help, im not sure why these people had to change this stuff, but i was concerned when i had to do nothing at all. maybe the new version fixed any previous problems

---

### Post by raymondh on 2009-11-18
> **whitebear1029 said:**
> thankyou for your help, im not sure why these people had to change this stuff, but i was concerned when i had to do nothing at all. maybe the new version fixed any previous problems

You're welcome.

Grub has certainly gotten stronger (it now uses uuid to identify) since intrepid.

Regards,

---


---
title: "[SOLVED] How to chroot into intrepid installation"
date: 2008-07-13
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by super.rad on 2008-07-13
I have hardy installed as my main os but recently installed intrepid alpha 1 on a seperate partition, i know it's possible to login to intrepid through the terminal using chroot to install updates etc but I don't know how. If someone could tell me how i do it that would be great, the partition its installed on is /dev/hda2 and it uses the same /home partition as my hardy installation (different usernames though)

---

### Post by super.rad on 2008-08-19
Ok well since posting I've installed Debian instead of Hardy but still have Intrepid aswell and after some updates this morning I can't login so if anyone knows the how I can login and run updates from Debian using the terminal that would be great. Thanks

---

### Post by meindian523 on 2008-08-19
```
sudo mkdir /media/Intrepid
sudo mount /dev/sda2 /media/Intrepid
sudo chroot /media/Intrepid
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by super.rad on 2008-08-19
Brilliant, didn't realise it was as easy as that. Thanks

---

### Post by meindian523 on 2008-08-19
Thanks,but I really don't deserve to be called brilliant,it's just a matter of experience.I've rescued my system after at least two bad installs and through a plethora of Grub errors.All you need is an idea what you want and the man pages.

---


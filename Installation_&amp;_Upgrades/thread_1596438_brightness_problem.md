---
title: "brightness problem"
date: 2010-10-14
forum: Installation &amp; Upgrades
---

### Post by skkmaths on 2010-10-14
i have inspiron n4010 lap top . i  installed ubuntu 10.10 , now brightness control is not working .
please help me to resolve this problem .....

---

### Post by axelfpm on 2010-10-18
First sorry for my english it's not my native language 

Go here [https://bugs.launchpad.net/dell/+bug/568611](https://bugs.launchpad.net/dell/+bug/568611) and install kamal ppa 

ppa:kamalmostafa/linux-kamal-mjgbacklight


then update system and you are done.

boot from new kernel with this all is working

byee

---

### Post by skkmaths on 2010-10-20
dear friend
many many thanks for ur reply.
stil  i was unable to do this.  i do not know what to install. could you tell me in detail how to do it ..
i use ubuntu 10.10.
expecting your reply...









> **axelfpm said:**
> First sorry for my english it's not my native language 

Go here [https://bugs.launchpad.net/dell/+bug/568611](https://bugs.launchpad.net/dell/+bug/568611) and install kamal ppa 

ppa:kamalmostafa/linux-kamal-mjgbacklight


then update system and you are done.

boot from new kernel with this all is working

byee

---

### Post by axelfpm on 2010-10-20
Ok I try to make easy

open terminal and type this


sudo add-apt-repository ppa:kamalmostafa/linux-kamal-mjgbacklight

then 

sudo apt-get update

then you will see 2 new updates one is a kernel named 2.6.35.23.generic and a gnome-power-manager or somthing like that
install both reboot and you are done

---

### Post by skkmaths on 2010-10-20
dear  friend  i still did not understand how to install it and what to install . i did  not find any package in the link that u have given....please help me ...

---

### Post by skkmaths on 2010-10-20
dear  friend i run the command 
sudo add-apt-repository ppa:kamalmostafa/linux-kamal-mjgbacklight

but i got the error 
Error reading [https://launchpad.net/api/1.0/~kamalmostafa/+archive/linux-kamal-mjgbacklight:](https://launchpad.net/api/1.0/~kamalmostafa/+archive/linux-kamal-mjgbacklight:) <urlopen error [Errno 110] Connection timed out>

what i will do now?

---

### Post by axelfpm on 2010-10-21
Sorry man i don't know what this error mean. Try again later, maybe was a problem with the ppa.

---

### Post by willy1946 on 2010-10-21
Before trying to install additional packages, you might try this mod to the Grub configuration. It solved the backlight prob on my Asus laptop:

Go to the config file /etc//default/grub and change the line that starts with GRUB_CMDLINE_LINUX_DEFAULT

from
    GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
to
    GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux acpi_backlight=vendor"

then regen your Grub menu using "sudo grub-mkconfig" from a command line. Reboot. It may fix your problem.

---

### Post by axelfpm on 2010-10-21
> **willy1946 said:**
> Before trying to install additional packages, you might try this mod to the Grub configuration. It solved the backlight prob on my Asus laptop:

Go to the config file /etc//default/grub and change the line that starts with GRUB_CMDLINE_LINUX_DEFAULT

from
    GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
to
    GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux acpi_backlight=vendor"

then regen your Grub menu using "sudo grub-mkconfig" from a command line. Reboot. It may fix your problem.

Thanks for the tip man but that dosen't work on this laptop.
I try that prior to install the kernel and the gnome power managment from kamal ppa

---


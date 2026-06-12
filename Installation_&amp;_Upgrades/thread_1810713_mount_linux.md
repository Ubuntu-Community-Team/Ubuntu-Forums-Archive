---
title: "mount linux"
date: 2011-07-23
forum: Installation &amp; Upgrades
---

### Post by eslam elbyaly on 2011-07-23
hi folks , it is the first time to use linux(ubontu) and linux in generally , and 
i have some questions .

1- can i mount the .iso file of linux after downloading it , then copy the contents of the cd
to a flash memory or mobile ?
2- must the mobile or the flash memory be empty to burn linux on it ? or it can has other 
files and folder (contents) too ?
3- can not i mount the .iso file of linux , then run the wubi.exe from windows to try the linux or to install it , or i have to burn it on a cd ?

thanks in advance

---

### Post by eslam elbyaly on 2011-07-23
any help pleasssssse ?

---

### Post by bcbc on 2011-07-23
If you want to create a USB follow instructions here:  [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download) (step 2, select USB, click Show me how.

You don't need to mount it to run wubi.exe or burn it to a CD. You can download the wubi.exe and save it in the same directory as the ISO and run wubi from there - it will find the ISO and use it.

You can mount it and run wubi.exe but if you're just 'opening it as an archive' running wubi.exe will not detect the ISO and it will download a new copy of the ISO.

Refer to the [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide) for more info

---

### Post by eslam elbyaly on 2011-07-23
a lot of thanks to you bc , but 
i did not find any answer to my questions , sure not because of you ,
 may be because it is the first time to me .

but let us talk about my original situation which is , i am trying to install ubuntu on my pc 

i downloaded ubuntu from the site , and i have my mobile (memory 1GB) just my mobile 
there is no flash memory or cd , 

what should i do now ?

regards

---

### Post by eslam elbyaly on 2011-07-23
helpppppppppp?

---

### Post by bcbc on 2011-07-23
You have downloaded Ubuntu on your mobile phone? Take out the mini SD, stick it in an SD card adaptor, then in your computer and copy it. Burn it to CD or create a bootable USB.

I don't think you can do much with it on your mobile.

---

### Post by eslam elbyaly on 2011-07-23
you did not get me bc 
i downloaded ubuntu on my pc , then i tried to burn it on my mobile ? and it did work , but there was errors when restart like (no configuration file , and other error)

or mount it in my computer , then copy the contents into my mobile ?


sure my mobile has other contents , is that reflect booting ?

regard the mentioned processes , what about it ?

regards

---

### Post by marekrndr on 2011-07-23
Bet ya ten beans OP^ will go 'helpppppppppppppp?' in ten minutes.

---

### Post by Tea4all on 2011-07-23
You want to boot the Ubuntu installation using your phone as an sd card?

---

### Post by eslam elbyaly on 2011-07-23
i hope to install linux in anyway and i have nothing but my mobile with (1gb memory) 

but 
i finally downloaded wubi.exe , and i ran it , then followed the instructions , then 

after a long waiting , it asked me to restart , i did , but it did not boot , it logged in windows xp , there were no other options ? why ? why ?

please guide me in a hurry , do not hesitate to help me 

thanks in advance

---

### Post by Tea4all on 2011-07-23
Uninstall wudi from the windows installer. Use unetbootin to create a bootable disk with the sd card. Then restart, and go into the boot menu in your BIOS. Select boot from usb. If you have a card reader, it would work better. 
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by bcbc on 2011-07-24
> **eslam elbyaly said:**
> i hope to install linux in anyway and i have nothing but my mobile with (1gb memory) 

but 
i finally downloaded wubi.exe , and i ran it , then followed the instructions , then 

after a long waiting , it asked me to restart , i did , but it did not boot , it logged in windows xp , there were no other options ? why ? why ?

please guide me in a hurry , do not hesitate to help me 

thanks in advance

right click on "My computer", Properties, Advanced, Startup & recovery settings. Check the "time to display list of operating systems" is greater than 0. Set it to 15 if it's zero.

If that's not the issue, you can copy and paste the contents of your C:\boot.ini

---


---
title: "I need help from someone who knows good!"
date: 2008-03-21
forum: Installation &amp; Upgrades
---

### Post by ioannou.alexandros on 2008-03-21
Hi guys!

I am trying to install Ubuntu 7.10 on my laptop alongside with Windows Vista Home Premium 32 bit !
My laptop is 64 bit compatible and I am trying to boot from the 64 bit live cd that I requested for free from Ubuntu....the main problem is when I boot from it , in some stage at the begining where is loading it freeze and it dosen't actually let me anything to do. I checked it many times and the same thing comes again and again!

The stage that it stucks is the following two lines

Checking battery status.......
and something else here but I don't remember.

This is exactly the stage that it stacks!


I also downloaded the 64bit version and checked it again and nothing works again!   

What you might thing is going wrong?

Sorry that I cannot explain it more specifically now..... i will 2mrow as I have to go to sleep:lolflag:

I am so tired! :lolflag:

Hopefully someone understand it and may help me!

---

### Post by ayet on 2008-03-21
what the orientation of your hdd? is there a primary/slave? is vista on drive C?

---

### Post by Pumalite on 2008-03-21
When you wake up do md5sum on iso, burn new CD at 4x or less, check CD integrity after burn and before install. If everything is OK. , go for install. (partition has to be done with Vista partitioner before attempting install, since you cannot partition with the Ubuntu CD)

---

### Post by xzaloox on 2008-03-22
change in grub  this line  

kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=0a3992d4-f874-4a08-af8f-b406843cdf45 ro quiet splash



after "ro" replace  "quiet splash" with     noapic noapci

---

### Post by ioannou.alexandros on 2008-03-22
> **Pumalite said:**
> When you wake up do md5sum on iso, burn new CD at 4x or less, check CD integrity after burn and before install. If everything is OK. , go for install. (partition has to be done with Vista partitioner before attempting install, since you cannot partition with the Ubuntu CD)

Everything should be alright with that, since the cd I got is from ubuntu!

My hard disk is a sata 160GB 7,200rpm on a laptop!
Why I cannot partition it with the cd of ubuntu?

I can also use the alternate cd to installing and which I thing it would work but I need to know why the LIVE 64bit cd cannot boot..! I s it a general problem?

Is it a problem with the operating system, my ram I don't know!

---

### Post by Pumalite on 2008-03-22
You cannot partition with the Ubuntu CD because if you don't do it from WITHIN Vista, Vista will not let you run anything in that computer. Compliments of Bill Gates.

---

### Post by ioannou.alexandros on 2008-03-22
> **Pumalite said:**
> You cannot partition with the Ubuntu CD because if you don't do it from WITHIN Vista, Vista will not let you run anything in that computer. Compliments of Bill Gates.

Thanks for your information. I didn't know that!

Anyway can you also answer my previous question?

Why I cannot boot into live 64bit cd!

I also check it with the 32bit version and everything works fine but with the 64 bit in some point it stacks!
I checked. Is that a reason that it cannot boot from the 6 bit cd?

Thanks again!

---

### Post by Pumalite on 2008-03-22
You should install with the Alternate CD 64 bit. Download from here:
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
Mark the box below sign 'Start Download'
Follow this guide:
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)
Do md5sum on the iso, burn at 4x or less on CD-R, check CD integrity after burn and before install.

---


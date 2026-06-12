---
title: "Ubuntu 10.10 cd hangs after logo screen"
date: 2011-03-03
forum: Installation &amp; Upgrades
---

### Post by emzbuntu on 2011-03-03
Hi, i just downloaded unbuntu 10.10 and sucessfully installed it on a vmware machine within windows7. I am now ready to install on my hard drive and dual boot windows 7 / ubuntu. 

Unfortunately, when the computer boots on the cd, it hangs after the logo screen. I cant get to the boot menu. I did run MD5 checksum successfully.

Here are my specs.

ubuntu 10.10 desktop i386
asus maximus formula motherboard
intel core 2 duo E8400 3.0ghz
4 GB ram
ati radeon hd 3870
raid 0 array splited in two logical partition (1 for windows 7 and one for ubuntu)
logitech Wireless keyboard and mice

Any suggestions?

---

### Post by sikander3786 on 2011-03-03
Welcome to the forums :-)

Try using the 'nomodeset' boot parameter.

[http://ubuntu4beginners.blogspot.com/2011/01/ubuntumaverick-blank-screen-problem.html](http://ubuntu4beginners.blogspot.com/2011/01/ubuntumaverick-blank-screen-problem.html)

Or you might need to put in some other boot parameter like acpi=off or noapic. There are 6 of them and you might need to try all of them one-by-one.

[https://help.ubuntu.com/community/LiveCDBootOptions#Main%20Page%20Options](https://help.ubuntu.com/community/LiveCDBootOptions#Main%20Page%20Options)

---

### Post by emzbuntu on 2011-03-03
Thank you! i will give it a try tonight and will post the result :)

---

### Post by emzbuntu on 2011-03-03
hi, i just tried the nomodeset option and the cd still hangs.

I also tried the 6 different parameters with no luck.
I am going to try the alternate cd and the dvd i386 cd

---

### Post by emzbuntu on 2011-03-04
Hi, i just tried the alternate CD and the DVD i386 desktop and still the same problem.

When i boot the cd with the nomemset option, after few minutes, a green message appears at the top of the screen for few seconds and it disapears. I dont even have the time to read what it says.

Anything else i could try? Maybe try to install ubuntu 9 and update it to 10.10?

Thank you

---

### Post by emzbuntu on 2011-03-04
Hi guys,

good news i just installed unbuntu 10.10 successfully!

i was burning the iso files on dvds instead of cdr. I used the free software suggested on the ubuntu site and 

did burn the iso at the lowest the speed possible and bang!!! The cd booted just fine, no special parameter needed.

Case solved!!:)

---

### Post by skunkhead on 2011-03-04
hi,
 
I'm merely having the same problem as yours. Once the Ubuntu 10.10 cd boots, there will be a message sort like "checking battery stats..." and then the screen goes blank, nothing happens after that. I tried burning with dvd and cd but no different, the same. But i use windows burning tools to burn the cds.
 
Your experience might helps me out of this. 
Still confused!!
 
Thanks,
Skunkhead :)

---

### Post by kiddo46 on 2011-03-05
hi, I have the same problem too.
Actually, I did burn the iso file with high speed using free software on Windows.

I am giving your method a try.

thanks.

---


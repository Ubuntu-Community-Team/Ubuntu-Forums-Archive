---
title: "Install to USB &lt; 2 GB"
date: 2006-06-05
forum: Installation &amp; Upgrades
---

### Post by mht on 2006-06-05
Hey Fellas
i got to install my Dapper to a 2 GB ( actually 1.9 GB ) USB Flash memory , and with installer , i got an error message saying i shoud have more Storage , but i dont have more Storage , thought maybe there are some hacks or tricks i con install Standard Dapper on my USB Stick , i really dony want all Dapper packages and a sub-set of them is good to me , but i also dont know how to do a custom (expert? ) Installation , any hint is appeciated 

btw : please do not write down "go buy a bigger Storage , i know i can buy a bigger storage and solve the problem , the question is asked for a better way

thanks and regards :KS

---

### Post by Chickenmonger on 2006-06-05
A fellow forumer found a way to install Breezy on an external USB drive. My guess is Dapper would be a similar process.

[http://www.ubuntuforums.org/showthread.php?t=80811](http://www.ubuntuforums.org/showthread.php?t=80811)

---

### Post by mht on 2006-06-06
i've read that post , his Storage was 40 GB , not 2 GB
after all is there any hope ? i really want my dapper to be installed on this 2 GB USB Stick , isnt any custom installation avaliable at all ? is there any hack for installer program to ignore Storage limitation ? ot any way to change paritation schemas ?

](*,) ](*,)

---

### Post by rcarring on 2006-06-06
Even allowing for the fact that the installer creates many temporary files etc, you will still need more than 3GB just to get Dapper installed, regardless that you can then remove OpenOffice and The Gimp.

The only option you have is to install Dapper server and then build on to it the X Windows support and some basic Window Manager, but a lot of the tools that are very useful for day to day running won't be there.

AFAIK there is no way of picking packages to install at install time using either the Live CD installer or the Alternate CD installer.

Having said that, there may be one godawful munge to do this:

Install Dapper to a bigger drive, rip the guts out of it, and then see if you can image the hard drive that Dapper is installed to and then reimage the usb stick.

I really would advise you to consider an external usb hard disk. These cost about $100 and may be cheaper than a usb stick solution. The first big pile of updates will probably fail as you won't have room to expand the packages and install them.

In any case if you have 512mb Ram the swap file alone will be at least equal to this value probably more.

My suggestion is:

Download the Server Alternate CD and try that, you may not have agui but at least you will have Dapper.

---

### Post by mht on 2006-06-06
Thanks
i "should" install Dapper to my 2GB USB , no choice .

two more Q about your answer :

1-how could i install Dapper then rip some nonsense-ware and make my image working on USB ? any instructions ? this could be my answer , and its very nice if i can install my dapper somewhere good and remove useless packeges then copy the whole thing to my USB and make some changes (?) to boot correctly , can you help me with this ?

2- i have Dapper Server iso , is this good enough ?

Regards

---

### Post by mht on 2006-06-06
by the way 
i just installed Server release on my USB stick , and everything done fine , i selected this kernel : kernel-image-server , and it didnt boot from the usb correctly , does this kernel support USB modules ? what else can i do ?

Thanks

---

### Post by NZ-Wanderer on 2006-10-02
I too have been playing with a 2gb stick as well...

No luck installing dapper onto it tho :( 

I am a little annoyed that there is no "manual" mode install where you can tell it what you want installed or not..

Am presently playing with this, but it is not a true install..

[http://www.ubuntuforums.org/showthread.php?t=71567&page=7&highlight=ubuntu+ram+stick](http://www.ubuntuforums.org/showthread.php?t=71567&page=7&highlight=ubuntu+ram+stick)

---


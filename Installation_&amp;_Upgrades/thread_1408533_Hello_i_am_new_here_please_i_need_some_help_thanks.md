---
title: "Hello i am new here please i need some help thanks"
date: 2010-02-16
forum: Installation &amp; Upgrades
---

### Post by balkrish999 on 2010-02-16
Hello i am new here and i am excited about ubuntu 

first i have a laptop which has windows 7 home premiumum and its a 64bit version

and its got 2 hard drives  1st  has the os 7 on it and has 280gb free space     out of 320gb

2nd hard drve   i have the revoery which is only 12gb  and i have 9mb free 

i want a dual boot with 7 and ubuntu linux
correct me if im wrong
i know that i will have to partion my 320gb hard drive and make another hard drive which i think will be around 80gb hd

and then i wll install ubuntu on that 80gb hard drive   


first  if i put ubuntu on my laptop with a dual boot  (so i get windows 7 and ubuntu)  will it cause any problems for windows 7 os
 
then when i burn the iso on a cd shall i boot it from the boot menue  or shall i go on my windows 7 then click on the dvd drive and install it from there???

also can someone give me a step by step guide on how to install ubuntu with windows 7 and on a seprate hardrive   

thanks :):):)::)

---

### Post by Satoru-san on 2010-02-16
> **balkrish999 said:**
> Hello i am new here and i am excited about ubuntu 

first i have a laptop which has windows 7 home premiumum and its a 64bit version

and its got 2 hard drives  1st  has the os 7 on it and has 280gb free space     out of 320gb

2nd hard drve   i have the revoery which is only 12gb  and i have 9mb free 

i want a dual boot with 7 and ubuntu linux
correct me if im wrong
i know that i will have to partion my 320gb hard drive and make another hard drive which i think will be around 80gb hd

and then i wll install ubuntu on that 80gb hard drive   


first  if i put ubuntu on my laptop with a dual boot  (so i get windows 7 and ubuntu)  will it cause any problems for windows 7 os
 
then when i burn the iso on a cd shall i boot it from the boot menue  or shall i go on my windows 7 then click on the dvd drive and install it from there???

also can someone give me a step by step guide on how to install ubuntu with windows 7 and on a seprate hardrive   

thanks :):):)::)

First welcome to the forums :)

Second, you want to burn the .iso for ubuntu on your windows. Then boot the cd and say try without changeing my harddrive.

Then you want to open a program called gparted and resize your windows partition so you have 80 gigs of unpartitoned space, and apply these changes.

Then you want to reboot and then select install ubuntu from the menu. And when it gets to paritioning make sure it chooses to install in the empty space.

When it is all done, you will get a menu at boot to choose windows or ubuntu. If you dont see a menu come up and it boots exclusivly into either system, on the next boot hold down the shift key.

:D Welcome to the forums! Enjoy it here! :D
**DONT BLINDLY RUN COMMANDS THAT PEOPLE ON THE FORUMS TELL YOU**
[i]some times people will post malicious command that will destroy your
install[/i]
If you have any questions about what the commands do, ask someone!

---

### Post by 2hot6ft2 on 2010-02-16
The widows partition should be resized using the windows disk management utility instead of using Gparted. Right click on My Computer > Manage > Disk Management
Other than that Satoru-san has the right idea.

---


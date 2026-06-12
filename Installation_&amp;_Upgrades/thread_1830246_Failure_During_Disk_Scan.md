---
title: "Failure During Disk Scan"
date: 2011-08-21
forum: Installation &amp; Upgrades
---

### Post by patriciad on 2011-08-21
Here are my specs to start off...

OS: Corrupted Windows XP, Home Edition
CPU: Pentium 4 2.8GHz
RAM: 1gb
Graphic Card: nVidia GeForce 8600 GS

So I corrupted my Windows OS by doing something stupid so I decided to install Unbuntu. I tried installing it over my windows OS, but as it's scanning the disk it fails and says "Apt configuration failure" and then "installation failure". I can't upload my partitions because I can't run my OS to find them. 

I know the information is limited, but is there anyway someone could help? I've considered trying to install a different linux OS or even format my entire harddrive (I would really prefer NOT to do that since I'd have to install all the drivers off the internet). 

Thanks!

---

### Post by dave01945 on 2011-08-21
if you want to install it over windows because windows doesn't work (remove windows) then formating will not affect ubuntu it needs to format to install it anyway

---

### Post by dino99 on 2011-08-21
boot on a livecd like partedmagic & format the whole disk, then prepare installation following this howto:

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by patriciad on 2011-08-21
Dave: But I guess my question is will I be able to find all the drives I need for my system online? This isn't a factory restore, but a full format. My computer is 5 years old so that was what I was worried about.

Dino: Could you explain a little further, I don't really understand your instructions. Are you saying to boot this OS, install, format the disk and then install unbuntu? Also for the install instructions could you clarify those as well? I'm not really "advanced" in computers, I only know enough to get by.

Thank you both for your swift replies and your help!

---

### Post by dave01945 on 2011-08-21
with ubuntu most the drivers a built into the system the only driver i had to download was one for the graphics card and that is because it is licensed by nvidia and is not open source

as for the install do you have ubuntu on a cd if you do you just need to boot from the cd might have to change the boot order in your bios and then you will be presented with a menu on that menu there in an option to install ubuntu click that and follow the instruction if you are only installing ubuntu the easiest way would be to use the option to use the entire disk it is a good idea to set up separate partitions (all done with the option on the ubuntu cd) 

you would want to make one about 15gb formatted as ext4 mounted on /

ones about 2gb formatted as swap

and the rest formatted as ext4 mounted on /home this one will be for your user files


i'll have a look see if i can find a detailed guide through the setup options


--edit--

if you can this videos will show you how it's done he does't show you how to setup seperate partitions but he does show you the option so you can see were you enter mountpoint and format types

[http://www.youtube.com/watch?v=IKeFgxKYorY&feature=related](http://www.youtube.com/watch?v=IKeFgxKYorY&feature=related)

when i first installed ubuntu i went for the easy option and installed alongside windows but if your windows is broken you may aswell use entire disk

though it is a good idea to create a seperate partition for /home cause then if you need to reinstall ubuntu your user data is not affected if you wanted to try that here is a video that goes through the partitioning steps and just use my info above as a guide

[http://www.youtube.com/watch?v=qBCHsgry2RQ](http://www.youtube.com/watch?v=qBCHsgry2RQ)

---

### Post by patriciad on 2011-08-21
Well that worked perfectly! Once I separated the partitions it installed! Thank you both for your help :). And an extra thank you for finding those videos to help me.

---


---
title: "A few things which need to be worked on in ubuntu"
date: 2006-10-17
forum: Installation &amp; Upgrades
---

### Post by cryptonic on 2006-10-17
First of all, Il start by saying that I really want to use ubuntu, really I do. But like every other time Iv tried and every other distrubution I always have major problems with it. This time it was simply installing the system. when I tried to install ubuntu I was greeted with an error " Kernel Panic - not syncing : IO - APIC + timer doesnt work! Try using the noapic 'Kernel parameter' . I searched the net for problems like this and found out it has something to do with am2 socket support under ubuntu. Now that seems a bit odd to me seeing as i was using the amd 64bit edition of ubuntu but fair enough. I got the installation going after I used the noapic command. Before I was using ubuntu I was using windows xp 64bit edition and unfortunatly with windows xp 64bit edition install you cant partition the drive under fat32 so your forced to use ntfs. I was unable to resize the ntfs partition under ubuntu and I had to totally remove windows from the hardrive in order to install ubuntu. After installing I had some issues with my belkin usb adapter and because it was connecting me to my router had no way of checking to see if there were any fixes for the problem on the net. I tried ndswrapper to install two different drivers on ubuntu. 64bit and 32bit and neither worked so in the end I was forced to try and resize my new linux partition and boot windows on the unpartioned space but guess what the good old partition manager didnt want the resize linux partions either , saying check for drive errors, What i dont understand is how i can deleate the partion and then repartition without errors but i am unable to resize, so i will presume it is an issue with the partition manager itself. The version of ubuntu i used was edgy and my wireless card was the belkin F5D7051.

---

### Post by Kateikyoushi on 2006-10-17
I think you should post it after making it a bit more readable  [here]("http://ubuntuforums.org/forumdisplay.php?f=103").

I did not resize my partitions but I did not hear complains about it so far. USB adapters are a bit more problematic than usual ones.

---

### Post by bulldog on 2006-10-17
Well Cryptonic,maybe you had a bit of bad luck with your Ubuntu install.

To choose for a Beta release [Edgy] is not very wise eather,try to install Dapper 6.06 to have a better chance to get it to work.
If your not familiar with Linux you better not try to install a Beta.

Why the partitioner not did what it should do beats me,never had a problem with it,however there should be some more explanation with it.

The best thing you can do is reinstall windows and remove Edgy from your disk.

Then,if you still want Edgy,read a lot first to see which problems you could encounter before to attempt to install.

But I'm sorry to read you have so much bad luck.

---

### Post by TheWizzard on 2006-10-17
if you want dual boot, always install windows first. 
if possible, do not install windows on your entire hdd, but on a smaller partition so you have space to install ubuntu. 
you can also make your windows partition smaller from within windows with programms like partition magic.

i agree with bulldog that a stable release is better if you're not a linux expert. 

also, consider installing the 32 bit version. the performance differences are small (exept when video editing) and it makes life a lot easier.

---


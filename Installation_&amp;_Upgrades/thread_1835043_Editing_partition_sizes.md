---
title: "Editing partition sizes"
date: 2011-08-28
forum: Installation &amp; Upgrades
---

### Post by MudOilnGears on 2011-08-28
Hello
Some months ago I did a dual boot on a HP laptop with four partitions from the factory. Here's the link to all the help you guys gave me:[http://ubuntuforums.org/showthread.php?t=1700994&page=4](http://ubuntuforums.org/showthread.php?t=1700994&page=4)

Here is a screenshot of my partition setup.

[IMG]http://i916.photobucket.com/albums/ad6/MudOilnGears/Screenshot-1.png[/IMG]


Needless to say I have run out of space on sda3 which is the Ubuntu partition.

Here's the question, how do I resize the Large Windows partition (without frying the files on it) and add that space to my windows partition?
I suppose it's pretty simple, but I don't really want to mess anything up by trial and error.
Thanks in advance
Hector

---

### Post by Old_Grey_Wolf on 2011-08-28
Are you wanting to shrink the Windows partition to make more room for Ubuntu or are you wanting to remove the Ubuntu partition? I wasn't sure from the way the question was worded.

---

### Post by MudOilnGears on 2011-08-28
Sorry I didn't make myself clear. Yes I need to shrink the large windows partition to make more room for Ubuntu, say maybe shrink the Windows one by half, and then merge that space with the existing Ubuntu partition. All without affecting existing installs/files, if such a thing is possible at least...
Thanks

---

### Post by MAFoElffen on 2011-08-28
> **MudOilnGears said:**
> Needless to say I have run out of space on sda3 which is the Ubuntu partition.

Here's the question, how do I resize the Large Windows partition (without frying the files on it) and add that space to my windows partition?
I suppose it's pretty simple, but I don't really want to mess anything up by trial and error.
Thanks in advance
Hector
Windows // Linux and changing the size of partitions... The fastest and safest way I've found is to boot from a LiveCD of GParted and use the Move/Resize function.

The reason I recommend doing this externally is that partitions with data have to be unmounted and sometimes have problems being moved and resized if you are booted and running from the partition being worked on... Besides, the Gparted LiveCD can verify that the data has been moved.

---

### Post by MudOilnGears on 2011-08-28
> **MAFoElffen said:**
> Windows // Linux and changing the size of partitions... The fastest and safest way I've found is to boot from a LiveCD of GParted and use the Move/Resize function.

The reason I recommend doing this externally is that partitions with data have to be unmounted and sometimes have problems being moved and resized if you are booted and running from the partition being worked on... Besides, the Gparted LiveCD can verify that the data has been moved.


Thanks! I recall having read somewhere that Windows doesn't like its partitions being modified by foreign programs, is that so, or a myth? I hadn't thought about the advantage of working from a CD!

---

### Post by MudOilnGears on 2011-08-28
Ahh, now I reread my original post I said that I wanted to add the space to the windows partition when I really *meant* Ubuntu. Now I see where the confusion came from ;)

---

### Post by Old_Grey_Wolf on 2011-08-28
> **MudOilnGears said:**
> Sorry I didn't make myself clear. Yes I need to shrink the large windows partition to make more room for Ubuntu, say maybe shrink the Windows one by half, and then merge that space with the existing Ubuntu partition. All without affecting existing installs/files, if such a thing is possible at least...
Thanks

Make sure you defrag Windows. Then use Windows Disk Manager to shrink the Windows partition. It is not advised to modify the Windows partition with Gparted. After that you can use Gparted from a Live CD/USB to grow the Ubuntu partition. I think most of that is explained in the post you linked to. If not, post back here for more help.

---

### Post by Old_Grey_Wolf on 2011-08-28
> **MudOilnGears said:**
> Thanks! I recall having read somewhere that Windows doesn't like its partitions being modified by foreign programs, is that so, or a myth? I hadn't thought about the advantage of working from a CD!

You are correct; however, it depends on the version of Windows you are using. I would avoid problems by using Windows to shrink Windows partitions.

You have to use a live CD/USB to grow the Ubuntu partition. You can not change the partition size of a Linux partition if it is mounted as the currently running OS.

---

### Post by MAFoElffen on 2011-08-28
> **Old_Gray_Wolf said:**
> It is not advised to modify the Windows partition with Gparted.
@ Old_Gray_Wolf - I get paid to do just that.  We do it all the time at our shop.  We use what works best and what we can guarantee with our work.  (Installs, upgrades, repairs, data recovery, etc...)

(And no, I'm not talking about the Gparted version included with Ubuntu.)

I understand that people use what they are familiar with.  The more we are familiar with the myriad of tools available... then we have a toolbox of tools that will work for various situations.  

And as I have heard you recommend to people, if you vakue the data that's there, do a backup before modifying partitions.  > "He who laughs last, had a good backup..."

---

### Post by MudOilnGears on 2011-08-28
Success! Thanks all!
[IMG]http://i916.photobucket.com/albums/ad6/MudOilnGears/Screenshot-2.png[/IMG]
I defragmented in Windows, shrank the partition in windows and used Gparted from a live CD for the rest, worked like a charm!
I am always impressed at how you guys are always willing to help a newbie. Thanks a million!

---

### Post by Hakunka-Matata on 2011-08-28
> 
Quote:
                                                                      Originally Posted by **Old_Gray_Wolf**                     [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=11196681#post11196681")                 
                 [I]It is not advised to modify the Windows partition with Gparted. 
[/I]
> **MAFoElffen said:**
> @ Old_Gray_Wolf - I get paid to do just that.  We do it all the time at our shop.  We use what works best and what we can guarantee with our work.  (Installs, upgrades, repairs, data recovery, etc...)

([COLOR=Red]And no, I'm not talking about the Gparted version included with Ubuntu[/COLOR].)

I understand that people use what they are familiar with.  The more we are familiar with the myriad of tools available... then we have a toolbox of tools that will work for various situations.  

And as I have heard you recommend to people, if you vakue the data that's there, do a backup before modifying partitions.

@ MAFoElffen:  Well then, [COLOR=Red]that comment[COLOR=Black] is a **non sequitur**.  It does not apply, As[/COLOR][/COLOR] **Old_Gray_Wolf **is obviously referring to the GParted that IS packaged with Ubuntu.  What is the GParted version you're so fond of?

---

### Post by Old_Grey_Wolf on 2011-08-29
> **Hakunka-Matata said:**
> @ MAFoElffen:  Well then, [COLOR=Red]that comment[COLOR=Black] is a **non sequitur**.  It does not apply, As[/COLOR][/COLOR] **Old_Gray_Wolf **is obviously referring to the GParted that IS packaged with Ubuntu.  What is the GParted version you're so fond of?

Actually, MAFoElffen is correct that you can use Gparted to resize Windows partitions; however, if you aren't eperienced, and prepard to solve problems, I recommend using Windows to shrink Windows. It's less work for me and less frustrating for the person asking for help on the forum. 

If you use Gparted, you have to uncheck the "round to cylinders" box , otherwise Gparted will take a long time moving the partition to align it with cylinder boundaries. This can result in booting problems; because, the Windows boot loader uses block addressing to find parts of itself. When the partition is moved, it gets messed up and Windows won't boot. There seem to be other causes for Windows not booting after the partition is resized with a program outside of Windows; however, I don't know what the cause is. Sometimes Windows can fix itself automatically but other times it requires booting from the Windows Installation Disk to run a repair.

Like I said though, it's less work for me and less frustrating for the person asking for help on the forum if I just recommend using Windows to shrink Windows.

Sure, Gparted can do it faster; however, home computer users with only a few computers don't resize partitions very often. Home computer user don't usually have enough experience with resizing a partition to know how long it should take.

---


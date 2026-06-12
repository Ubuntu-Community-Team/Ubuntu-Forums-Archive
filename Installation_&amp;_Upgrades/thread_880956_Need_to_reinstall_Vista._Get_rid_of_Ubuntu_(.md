---
title: "Need to reinstall Vista. Get rid of Ubuntu :("
date: 2008-08-05
forum: Installation &amp; Upgrades
---

### Post by nbotticelli on 2008-08-05
Hey All,

Unfortunately I need to completely ged rid of all remnants of Ubuntu and reinstall Vista on a couple of Toshiba Portege m400 tablets.

I'm a total convert to (Edu)buntu but in this case I have to have Vista on these machines as they are work machines and certain things just don't play well enough with Ubuntu and our domain at this point and I'm going to need to give these back out to teachers again when school starts.

When I try to go in a reinstall Vista it says that it can't delete or reformat any of the Ubuntu partitions or even recognize them pretty much either. 

So I go into LiveCD and use GParted to try and delete them. It said that I was able to delete the first main partition but it won't let me touch the swap/extended partition at all.

Is there somethig that I'm missing?

I just want to be able to completely overwrite Ubuntu with Vista for now on these machines....I did hve a dual boot originally for a while on these but the hard drives are just a bit too small and so I went completely to Ubuntu for a couple of summer camps that I was running but need to get Vista back on asap.

Thanks for any help!

---

### Post by redraiderbum on 2008-08-05
For tasks like this I usually employ the ultimate boot cd found here:

[http://www.ultimatebootcd.com/download.html](http://www.ultimatebootcd.com/download.html)

It has tons of tools for these occasions.  I am assuming you are relatively familiar with keyboard only interfaces because that's all it is.

---

### Post by nbotticelli on 2008-08-05
I'll download that and give it a try. It might be a while until I am able to get the ultimate boot cd though unfortunatel.

Is there a reason that vista wouldn't be able to at least delete the ubuntu partitions? And why would GParted not be able to touch the swap partition? (there was a key symbol next to it plus all options were grayed out)

---

### Post by bigken on 2008-08-05
use the [gparted]("http://gparted.sourceforge.net/download.php") liveCD

---

### Post by toucher5 on 2008-08-05
The problem that you are having with the swap is that the live CD on boot turned on swap to give it more room to play with. Basically all you have to do is open the terminal program and type in swapoff and then try deleting it again. Have you tried Linux Mint on these machines? it is a branch off of Ubuntu and comes with all of the non-free plugins. I just recently tried it and it is great for users coming from the Windows world. It doesn't have the ed-ubuntu packages but it is joined to the ubuntu repositories. so you can install those packages for those programs. I wouldn't install the desktop package, just the educational packages. [http://www.linuxmint.com/](http://www.linuxmint.com/)

On a side note: what didn't work? Maybe it could be something that can be brought up and running.

---

### Post by nbotticelli on 2008-08-06
I have not tried mint yet. I have no problem with installing all the plugins and pretty much getting most of the tablet functions to work under ubuntu. 

I used the "ultimate multimedia how-to" thread to get all the necessary codecs. 

It's just that we're a pretty heavily microsoft reliant school system at this point and other than making a small edubuntu mini lab I'm not going to be able to start putting it on teachers' machines yet....Close though!

On the other hand for the most part I find using Ubuntu to administer our windows 2003 servers easier than through Vista!

I will try that swapoff thing you mention....

I just don't understand why Vista can't just totally delete the ubuntu partitions and reformat the whole drive! Strange.

Thanks!
-Nicco

---

### Post by nbotticelli on 2008-08-06
Hmm tried swapoff -a and you were right. I was able to delete all partitions completely but when I went back into the Vista install procedure it comes up saying that it had an error creating the system volume.

Maybe I'll try going back to Gparted and repartitioning the drive through there.

---

### Post by Perkins on 2008-11-11
Theoretically the windows installer disk should have its own partition editor which you should be able to use to put it all back.  Just delete all the partitions and then repartition and reformat.

Of course, if it doesn't work properly in Vista, that wouldn't surprise me at all.  In my experience, almost nothing works properly in Vista...  So, my recommendation would be, unless there is some reason that you *have* to use Vista, use XP professional instead.  Especially in a networked environment, Vista has some really noxious quirks that can totally destroy its functionality.  Last I heard, MS had updated their license agreement so that if you don't like Vista, you are free to downgrade to XP at no charge.

---


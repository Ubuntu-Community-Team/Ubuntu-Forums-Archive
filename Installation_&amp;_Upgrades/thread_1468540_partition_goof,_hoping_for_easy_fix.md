---
title: "partition goof, hoping for easy fix"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by djmoore85 on 2010-05-01
I installed UNR 10.04 the other day, and it was my second time to install due to complications in the first go around. I goofed a little bit though and am hoping there is a way to fix it without losing my setup. I installed UNR specifying partitions manually, and erased my first install and used that partition for my current one. In the process I shrank the swap area from 5G to 2G in order to match up to my RAM and free up 3G of space I could now use. Here is where I goofed: I was left with around 114G of free space, then the 2G of swap, then 3G of more free space. Well I specified the 3G to be mounted at /home hoping it would just add that free space to the big 114G space. But, alas, now I have a home folder that has only 1G of free space, and more music and movies I wish to save. How can I get more room in my /home folder or merge it somehow to all be in the main install space? Thank you all for any assistance

---

### Post by prshah on 2010-05-01
> **djmoore85 said:**
> I specified the 3G to be mounted at /home... now I have a home folder that has only 1G of free space

You can relax, the fix is quite easy. Boot into recovery mode, and copy your /home to your main partition under some other name, eg```
cp -p /home /homew
``` The "-p" will maintain file permissions and ownerships.

Then unmount your "/home" partition, and edit it out of your /etc/fstab```
cd
umount "/home"
nano /etc/fstab
#comment out the lines belonging to youor 3G home partition
#Ctrl+X to quit, save when asked

```

Reboot ```
sudo reboot
``` and AGAIN select recovery mode. Now rename your temp homew to home```
mv /homew /home
``` and reboot once again. Everything should be fine now.

If for some reason you are not allowed to unmount the "/home" partition then you will have to do things from the live CD. Post back if you want information on this.

When everything is done fine, you can move your swap partition into the unused 3GB space, and then extend your main partition to include the 3GB unused space. It's better to move the swap partition than delete and re-create it, because if the re-creation is not done properly, you will break hibernation capability. Post back if you want information on how to re-create swap correctly without breaking hibernation.

---

### Post by Robertjm on 2010-05-01
If I'm understanding you correctly, you've got three partitions:

114gb mounted as /
2gb mounted as swap
3gb mounted a /home

If you don't already have it, download a copy of [GParted]("http://gparted.sourceforge.net/") and burn a CD. You will be using this to boot.

[COLOR="Blue"]SCENARIO A (no separate /home partition):

First off, back up anything in the 3gb /home folder that you want to keep because you're going to lose it in this fix. I'd suggest copying it to a thumb drive if you have one big enough. If not, burn it to DVD or sign up for one of those online storage places.

Restart your computer, booting from your burnt GParted CD.

Once inside GParted select the 3gb partition and delete it. This will become listed as Free Space. Don't worry about formating it s you're going to combine it with the main partition.

Next, use your mouse and drag the Swap Space to the far right so it's at the very top of your drive map.

Next, right click on the 114gb partition and select Enlarge (or whatever it's called. I'm doing this from memory). Drag the right side of that partition all the way to the right so it eats up all the free space.

Select the Apply Changes button and it will make those changes for you. Depending on the speed of the drive it may take a bit of time.

THIS IS NON-REVERSIBLE so make sure this is what you want to do before doing it!!!

Once it is completed select the option to restart your computer. You can now add anything you saved back into the /home in your installation. Bear in mind that under the scenario you do NOT have a separate /home partition on your system so if you ever update your OS you're going to have to back up your /home folder or lose all your data!!

You might want to take the extra time to maintain a separate /home partition.

[/COLOR][COLOR="SeaGreen"]SCENARIO B (separate /home partition):

Log into GParted as above.

Next thing you want to do is SHRINK your 114gb partition some. How much depends on how much you think you're going to have in your /home folder. I'd probably go for 40gb if it will allow you, though your usage may be different than mine.

Move the swap partition all the way to the left in the diagram so it butts up against your current large partition.

Right click on the /home partition and enlarge it to suck up the large amount of free space you created when you shrunk your main partition.

Apply your changes and restart your computer. When your computer is logged in you should now have a large /home partition with anything that's currently there still there!![/COLOR]

Hope that helps.

Robert

> **djmoore85 said:**
> I installed UNR 10.04 the other day, and it was my second time to install due to complications in the first go around. I goofed a little bit though and am hoping there is a way to fix it without losing my setup...How can I get more room in my /home folder or merge it somehow to all be in the main install space? Thank you all for any assistance

---

### Post by Robertjm on 2010-05-01
Looks like two of us were answering you at the same time.

If you want to combine your /home into your main partition his method probably easier than mine.

If you want to keep a separate /home partition follow my Scenario B. Yes, you could do something similar with recovery and not a separate application. I just like using the GUI of GParted myself.

Robert

---

### Post by djmoore85 on 2010-05-01
> **prshah said:**
> You can relax, the fix is quite easy. Boot into recovery mode, and copy your /home to your main partition under some other name, eg```
cp -p /home /homew
``` The "-p" will maintain file permissions and ownerships.

Then unmount your "/home" partition, and edit it out of your /etc/fstab```
cd
umount "/home"
nano /etc/fstab
#comment out the lines belonging to youor 3G home partition
#Ctrl+X to quit, save when asked

```

Reboot ```
sudo reboot
``` and AGAIN select recovery mode. Now rename your temp homew to home```
mv /homew /home
``` and reboot once again. Everything should be fine now.

If for some reason you are not allowed to unmount the "/home" partition then you will have to do things from the live CD. Post back if you want information on this.

When everything is done fine, you can move your swap partition into the unused 3GB space, and then extend your main partition to include the 3GB unused space. It's better to move the swap partition than delete and re-create it, because if the re-creation is not done properly, you will break hibernation capability. Post back if you want information on how to re-create swap correctly without breaking hibernation.

Thanks for the quick responses. Unfortunately when I commented out the device line dealing with /home I got a bunch of Nautilus errors upon login. I also from the root prompt in recovery could not do the last step mv /homew /home, I received an error of no such directory.

*Edit: Followed GParted solution using LiveCD. Worked weel. Oddly enough there was 7MB left unallocated that can't be tacked on anywhere. But I have an 80GB /home folder now. And still plenty of room to expand my base system. thank yall again for the help*

---


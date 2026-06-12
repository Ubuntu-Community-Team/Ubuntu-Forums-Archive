---
title: "Reinstall Ubuntu (10.10) without affecting windows 7"
date: 2011-04-15
forum: Installation &amp; Upgrades
---

### Post by Dudutzu on 2011-04-15
Hello ! 

   Well the moment to reinstall Ubuntu is finally here ( or I think sow).
Due to heavy experimenting and a bunch-load of crap installed. I tried uninstalling  everything I don't need but now I get several errors that are random and a sluggish experience. although it's fully customise to my needs (customising that took me over 6 months).

My system basic config : 

Storage:  2x 1 Tb HDD configured in RAID 0
Partitions :
[LIST][*]250 Gb Window 7 Boot [*] 250 Gb Ubuntu [*] 1Gb Swap [*] 1 Tb Storage [*] 500 Gb Unasgined [/LIST]
           
OS (dual-boot): [LIST] [*]Ubuntu 10.10 [*] Windows 7 [/LIST]

Please help me reinstalling Ubuntu without cripple Windows.
Thanks in advance for your time and help.

---

### Post by Blasphemist on 2011-04-15
I recently did just this after having gone alpha with natty. I had done the updates consistently but with all the ubuntu and web development stuff I'd been using to learn, I wanted to go clean. 

Back up your home first. I didn't need anything else but think about whether you do. Download and make your live cd. When you install you'll be prompted for allocate drive space options. Don't choose erase disk and reinstall or you will loose Windows. Choose something else if you want to change your partioning. That leaves erase ubuntu and reinstall or upgrade ubuntu. I choose to erase and reinstall, having already backed up home. That option will erase home but leaves you with a totally clean install. I then copied back in my documents, pictures, videos, music and templates. The upgrade option tries to leave in place your files and programs. 

With your time spent in customization, you'll likely want to try the upgrade option (even if it isn't really a version upgrade). Or, your customization may be the cause of you wanting to do this to begin with. I did this with natty and am glad I'm on it but as you can see in these forums not everyone feels that way about new releases.

---

### Post by Dudutzu on 2011-04-15
There is no problem when it comes to back-up home (I have  another 1.4 Tb of external storage available) 

And yes I want to make some changes, like making home a single partition and a few others.

The customisations aren't the problem ( or at least I hope the errors don't come from there).
[B]
If I choose Ubuntu reinstall won't that affect Grub (meaning that grub won't "see" windows) ? [/B]

By no means is not apocalyptic if I lose windows but I need it for photoshop (when in wine I cant use text).

---

### Post by Blasphemist on 2011-04-15
Choosing to upgrade and reinstall Ubuntu will not erase your windows partition nor remove that boot option from Grub2. When you finish your partition changes (don't change the windows partition) you'll be prompted about where to put Grub2. It is now I'd think and should be then on /dev/sda, your first hard disk, not /dev/sda1 which is likely the windows partition. This link isn't specific to the same thing you are doing but you can see use of the allocate disk space options with multiple hard disks and where to put Grub2. [http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html) 
Herman did a great job with this and you'll need to look at the part about Grub.

---

### Post by Dudutzu on 2011-04-15
Thanks, will give this a try a.s.a.p. 
Also  I'll return with the results.



Later Edit : 


Due to some problem from my RAID controller I ended by removing RAID and installing only Ubuntu ( I hope to get adobe photoshop working correctly)
Thanks again for your help.

---


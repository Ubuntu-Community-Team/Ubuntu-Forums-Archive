---
title: "Have WinXP, want to install Ubuntu 9.1 on same hard drive.  How?"
date: 2009-11-26
forum: Installation &amp; Upgrades
---

### Post by SNYP40A1 on 2009-11-26
Title describe it.  I have Windows XP installed on my computer and I want to add Ubuntu as a boot option.  I only have one HDD with more than enough space for a Ubuntu install.  What's the easiest way to do this?

---

### Post by wilee-nilee on 2009-11-26
You want to defrag XP then shrink the XP with windows or gparted or partition manager, leaving a open space not allocated partition. Then if you have used the XP to shrink or gparted just restart the XP to make sure if a disc check needs to done it is done automatically, you might also check that XP is still intact by just looking through the basic workings. Then install Ubuntu with a booted live CD follow the instructions and when you get to the partition GUI choose install in largest free space or side by side if you choose side by side look at the slider at the bottom to make sure it has defaulted to where you want the partitions to be. Get a cup of your favorite beverage and a little knosh and enjoy. Post if you want the codecs info for media as well.

So this is the dual boot option if you want to run Ubuntu in wubi install with the on board wubi provided in the download ISO; after reading your post again a boot option is kind of vague when you describe a large enough HD space to run two OS.

---

### Post by presence1960 on 2009-11-26
> **wilee-nilee said:**
> You want to defrag XP then shrink the XP with windows or gparted or partition manager, leaving a open space not allocated partition. Then if you have used the XP to shrink or gparted just restart the XP to make sure if a disc check needs to done it is done automatically, you might also check that XP is still intact by just looking through the basic workings. Then install Ubuntu with a booted live CD follow the instructions and when you get to the partition GUI choose install in largest free space or **_*side by side if you choose side by side look at the slider at the bottom to make sure it has defaulted to where you want the partitions to be*_**. Get a cup of your favorite beverage and a little knosh and enjoy. Post if you want the codecs info for media as well.

So this is the dual boot option if you want to run Ubuntu in wubi install with the on board wubi provided in the download ISO; after reading your post again a boot option is kind of vague when you describe a large enough HD space to run two OS.

If you use this option it will divide the XP partition into 2 partitions- one each for XP & Ubuntu- leaving the free space untouched.

If you want to use the side by side option, defrag XP at least once or twice, make sure you have your data backed up & don't create any free space as the side by side option splits the XP partition and makes a partition for Ubuntu as big as you specify with the slider.

Maybe willee-nillie knows this but the way it is worded isn't very clear on this. It seems to me willie-nillie says create free space and then boot the Live CD and choose between "use largest continuous free space" or "side by side".

---

### Post by wilee-nilee on 2009-11-26
> **presence1960 said:**
> If you use this option it will divide the XP partition into 2 partitions- one each for XP & Ubuntu- leaving the free space untouched.

If you want to use the side by side option, defrag XP at least once or twice, make sure you have your data backed up & don't create any free space as the side by side option splits the XP partition and makes a partition for Ubuntu as big as you specify with the slider.

Maybe willee-nillie knows this but the way it is worded isn't very clear on this. It seems to me willie-nillie says create free space and then boot the Live CD and choose between "use largest continuous free space" or "side by side".

Maybe I am missing something but it wont divide the shrunken XP but the HD.

---

### Post by raymondh on 2009-11-26
> **wilee-nilee said:**
> Maybe I am missing something but it wont divide the shrunken XP but the HD. I think the wording is faulty in this section.

@Wilee-nilee"it will divide the XP partition into 2 partitions- one each for XP & Ubuntu- leaving the free space untouched" 

What I meant was it will divide the HD into a XP partition and a blank area for the Ubuntu install, Good call though we want to be clear. ;)

I think this was the confusion from your first post ... that presence tried to clarify

**choose install in largest free space or side by side**  .... this sentence after suggesting to shrink XP.

What presence tried to say was that if OP shrunk XP and then chose "side-by-side" instead of "continuous free space"..... ubiquity would further shrink XP to install root and swap....... and would have left the recently-unallocated (as you had suggested earlier)  alone.

---

### Post by wilee-nilee on 2009-11-26
Edit: accidental double post.

---

### Post by wilee-nilee on 2009-11-26
> **raymondh said:**
> I think this was the confusion from your first post ... that presence tried to clarify

**choose install in largest free space or side by side**  .... this sentence after suggesting to shrink XP.

What presence tried to say was that if OP shrunk XP and then chose "side-by-side" instead of "continuous free space"..... ubiquity would further shrink XP to install root and swap....... and would have left the recently-unallocated (as you had suggested earlier)  alone.

It would only shrink the XP further if you use the slider to adjust the dual partitions. Side by side on the installs I have done has been a dual boot outcome using the open space as the install for Ubuntu. And I actually quoted presences response mistakenly as my own sorry.

I think the side by side option is for somebody having not created a open space or formatted partitions for the Ubuntu installation. I could be wrong here but both work the same basically except side by side allows you to adjust the partition sizes during install. I have never seen a side by side install inside the other partition, but in the allocated partition freed up by the slider.

I think what both of you are refering to is an area I am not familiar with is primary etc partitions.

---

### Post by presence1960 on 2009-11-26
> **wilee-nilee said:**
> Maybe I am missing something but it wont divide the shrunken XP but the HD.

That is not possible if you choose side by side option : if you shrink XP and create free space you now have a primary partition & unallocated space (free space) on the HD. Now how can the partitioner divide the whole HD if there are two separate components (XP primary partition + free space) on the HD?

When you choose the side by side option it uses the XP partition and resizes that only to install them "side by side". The slider is there to allow you choose how much of XP's partition to give to Ubuntu. This option only touches the partition of the OS you are installing side by side with, it leaves all other parts of the HD untouched. So if you created free space prior to using the install side by side option that free space will remain as is after Ubuntu is installed.

If you created free space and choose "use largest continuous free space" then 100% of that free space will be used for the Ubuntu install.

Now let's examine your statement: 

> You want to defrag XP then shrink the XP with windows or gparted or partition manager, leaving a open space not allocated partition. Then if you have used the XP to shrink or gparted just restart the XP to make sure if a disc check needs to done it is done automatically, you might also check that XP is still intact by just looking through the basic workings. Then install Ubuntu with a booted live CD follow the instructions and when you get to the partition GUI choose install in largest free space or side by side if you choose side by side look at the slider at the bottom to make sure it has defaulted to where you want the partitions to be

Your instructions say to defrag windows create free space by shrinking XP. **_Then you say to choose side by side OR use largest free space._**
That is where the issue lies. if free space was created first, when you choose side by side that free space will not be touched, only the XP partition will be resized by the slider. The free space will remain as is on the HD.

---

### Post by wilee-nilee on 2009-11-26
I disagree with you, but that doesn't mean you are incorrect, but the main issue here is this conversation actually helping the person who wants to know what to do. I suggest you just give a better explanation that way the OP is served. I have never had a problem with any dual booting situation so I will continue to not have a problem, and the next time I do it I will take into consideration what your saying. 

I am not quite sure why you just didn't reply with the correct way rather then spend this time trying to prove me wrong and making it more confusing. ;) No harm done to me but the person who needs help is not me. 

I have used the side by side with a blank area and had no problems, and had 2 primary partitions. It may be that the Karmic partition manager is different then previous one I don't know.

---

### Post by presence1960 on 2009-11-27
A picture is worth a thousand words. I booted off a Live USB, shrunk sdb and created about 6.5 GB free space. Then I started the install and chose side by side. You can see for yourself that the free space will remain unused and that the space for Ubuntu is taken from sdb1 not using the free space at all.

Note in the first pic you have sdb1 and free space. Now I move the slider and note in pic 2 that the value from the Ubuntu partition for the installation is only taken from sdb1, the free space is not touched and will remain as free space. 

So the OP is being served by understanding not to create free space if using the side by side install method because the OP will wind up with unused free space on their hard disk.

This proves that when using the side by side method only the existing partition (not free space) is used to create a partition for Ubuntu-leaving the free space untouched and as is.

---

### Post by presence1960 on 2009-11-27
> **wilee-nilee said:**
> I disagree with you, but that doesn't mean you are incorrect, but the main issue here is this conversation actually helping the person who wants to know what to do. I suggest you just give a better explanation that way the OP is served. I have never had a problem with any dual booting situation so I will continue to not have a problem, and the next time I do it I will take into consideration what your saying. 

I am not quite sure why you just didn't reply with the correct way rather then spend this time trying to prove me wrong and making it more confusing. ;) No harm done to me but the person who needs help is not me. 

I have used the side by side with a blank area and had no problems, and had 2 primary partitions. It may be that the Karmic partition manager is different then previous one I don't know.

I think your ego is running with this. I was not trying to prove you incorrect, but was explaining why creating free space first then choosing side by side will not use the free space in the installation of Ubuntu.

As far as I am concerned it is principles before personalities. It is not who is "right", but rather it is what is "right" which should be our guiding principle in here.

I never complained when caljohnsmith or a few others corrected me a number of times on posts I had made concerning certain commands from the Live CD. Rather than taking it personally I booted my Live CD to see whether what they told me was correct or not. They were correct and I was not. I learned something...something about Ubuntu and also that their pointing my mistakes out to me is not a personal attack. It actually helped me learn more about Ubuntu. Suck it up big guy.

---

### Post by wilee-nilee on 2009-11-27
> **presence1960 said:**
> I think your ego is running with this. I was not trying to prove you incorrect, but was explaining why creating free space first then choosing side by side will not use the free space in the installation of Ubuntu.

As far as I am concerned it is principles before personalities. It is not who is "right", but rather it is what is "right" which should be our guiding principle in here.

I never complained when caljohnsmith or a few others corrected me a number of times on posts I had made concerning certain commands from the Live CD. Rather than taking it personally I booted my Live CD to see whether what they told me was correct or not. They were correct and I was not. I learned something...something about Ubuntu and also that their pointing my mistakes out to me is not a personal attack. It actually helped me learn more about Ubuntu. Suck it up big guy.

Your projecting, ego how Freudian, so where is the id and super ego. why don't you give the OP a correct explanation to what to do. As I said I have used the method with no problems and I said I disagreed but that doesn't mean your wrong. You don't know anything about me or my ego state your only applying your assumed knowledge in a response.

It could be that my memory of doing this is faulty, and that is why I suggested that you may be correct I just don't remember it that way I installed a dual boot about 2 weeks and used the fill empty option, but my yes my possible faulty memory remembers doing it the same way with a side by side a month before.

---

### Post by wilee-nilee on 2009-11-27
So for the OP and my colleague who questions the possibilities of a method I suggest I present this.
[http://www.dedoimedo.com/computers/dual-boot-windows-7-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-7-ubuntu.html)

---

### Post by wilee-nilee on 2009-11-27
> **presence1960 said:**
> A picture is worth a thousand words. I booted off a Live USB, shrunk sdb and created about 6.5 GB free space. Then I started the install and chose side by side. You can see for yourself that the free space will remain unused and that the space for Ubuntu is taken from sdb1 not using the free space at all.

Note in the first pic you have sdb1 and free space. Now I move the slider and note in pic 2 that the value from the Ubuntu partition for the installation is only taken from sdb1, the free space is not touched and will remain as free space. 

So the OP is being served by understanding not to create free space if using the side by side install method because the OP will wind up with unused free space on their hard disk.

This proves that when using the side by side method only the existing partition (not free space) is used to create a partition for Ubuntu-leaving the free space untouched and as is.

This is faulty because there is no operating system on there. Just a formatted partition probably in a ext? format and a free space, If the sdb was a NTFS the partition would act differently I suspect. Of course it will install in a free space you have over 400 gigs of free space. It is installing in the largest free space. Free space=no operating system (the largest) or unallocated if there is a OS in a partition already.

If you look at my link the final instruction is to do a manual install but the option of side by side is okay except that the person who wrote the instructions says he doesn't trust auto partitioning. The only thing I left out in the original post was that when I have used the side by side I moved the slider to keep the MS the same as the shrunken size so that it would not be disturbed while the open space was made into a 2nd primary and swap.

---

### Post by lisati on 2009-11-27
My $0.02: My preference is to defrag, shrink and check the XP partition, then tell the installer to use the largest continuous free space.

---

### Post by wilee-nilee on 2009-11-27
> **lisati said:**
> My $0.02: My preference is to defrag, shrink and check the XP partition, then tell the installer to use the largest continuous free space.

That is mine to but I gave the option of side by side for a full possibility experience. I also looked at the OP's previous posts a saw that they were not a complete newbie and had been using a Linux system previously.

This was a ridiculous exchange I apologize to the OP for this but my original instructions are perfectly valid.

---

### Post by SNYP40A1 on 2009-11-28
Thanks for the help.  I will try the side-by-side installation.  I remember doing an Ubuntu + WinXP install a couple years ago.  I think that was with Ubuntu 7.1.  Anyways, I had to go through several steps including creating the required partitions.  I am glad to see that they made the process easier with the side-by-side install option.

---

### Post by wilee-nilee on 2009-11-28
Checkout this thread by presence1960 in case you run into a problem as described.
[http://ubuntuforums.org/showthread.php?t=1339631](http://ubuntuforums.org/showthread.php?t=1339631)

---

### Post by voneacc on 2009-11-28
Using wubi is best way.Make a partition from the free space in windows xp(use comp. management).Preferably format the new partition with NTFS file system.Then run the wubi installer.It will provide a simple way to install Ubuntu.After the windwos based installation completes,just reboot the sytem & u will see the Ubuntu in boot menu.Select it for further installation.Ones it is completed,u r ready to use ur ubuntu os.
ps:This procedure is very fragile & risky.U should go for dual boot using ubuntu installation instead.

---

### Post by wilee-nilee on 2009-11-28
> **voneacc said:**
> Using wubi is best way.Make a partition from the free space in windows xp(use comp. management).Preferably format the new partition with NTFS file system.Then run the wubi installer.It will provide a simple way to install Ubuntu.After the windwos based installation completes,just reboot the sytem & u will see the Ubuntu in boot menu.Select it for further installation.Ones it is completed,u r ready to use ur ubuntu os.

If you took the time to look at this posters history he is not a unexperienced user, a wubi install is a transitional try out to a eventualy dual boot which is much safer and faster. AS wubi install can leave you with 2 unusable OS if the MS gets corrupted.

---

### Post by voneacc on 2009-11-28
> **wilee-nilee said:**
> If you took the time to look at this posters history he is not a unexperienced user, a wubi install is a transitional try out to a eventualy dual boot which is much safer and faster. AS wubi install can leave you with 2 unusable OS if the MS gets corrupted.

  Agreed.But instaling a boot loader & then messing with partitions might leave ur system unbootable.Thats what happened with me.So i think Wubi is best if u r not a performance seeker.

---

### Post by presence1960 on 2009-11-28
> **voneacc said:**
> Agreed.But instaling a boot loader & then messing with partitions might leave ur system unbootable.Thats what happened with me.So i think Wubi is best if u r not a performance seeker.

wubi is not a permanent installation but rather a trial to see if you like Ubuntu prior to partitioning your disk(s).

Read these for more info- especially the last one from a developer of wubi.

[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi) -pay attention to the first sentence and the word "try".

[http://en.wikipedia.org/wiki/Wubi_(installer)](http://en.wikipedia.org/wiki/Wubi_(installer))

[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)

While definitely easy & convenient wubi is not built to be a permanent installation, nevertheless I know some are trying that.

---

### Post by wilee-nilee on 2009-11-28
> **voneacc said:**
> Agreed.But instaling a boot loader & then messing with partitions might leave ur system unbootable.Thats what happened with me.So i think Wubi is best if u r not a performance seeker.

None of us likes to see anybody with a borked setup, but you have to research a little bit to make sure you know what your doing. Then back up your systems in case of an error. Personally none of my computers have failed to do what I hit the button to tell them to do but I have hit the wrong button on several times and learned from it.

The description that is on this thread of doing a dual boot describes how to ensure that the MS system is intact before installing Ubuntu, which one of the last things that happens it the loading of the bootloader. This site and the web is full of information on how to fix a borked MBR.

---

### Post by raymondh on 2009-11-28
> **wilee-nilee said:**
> If you took the time to look at this posters history he is not a unexperienced user, a wubi install is a transitional try out to a eventualy dual boot which is much safer and faster. AS wubi install can leave you with 2 unusable OS if the MS gets corrupted.

+1

Also .... a wubi-installed ubuntu performance/responsiveness is quite dependent on a healthy, clean and defragged windows.

---

### Post by eunuch on 2009-11-28
I am trying to install Windows XP AND Ubuntu 9.1

I have tried several times, several ways and can boot Ubuntu but when I choose to boot Windows I get a blue screen that tells me something is wrong and the system has been halted.

Running CHDSK from the Windows Install Disk tells me there are "unrecoverable errors."

All this leaves me nowhere.

Reading this thread has not helped me.

Any ideas what I can do to get the "Dual Boot" configuration to perform as promised in the instructions?

Thanks.

---

### Post by presence1960 on 2009-11-28
> **eunuch said:**
> I am trying to install Windows XP AND Ubuntu 9.1

I have tried several times, several ways and can boot Ubuntu but when I choose to boot Windows I get a blue screen that tells me something is wrong and the system has been halted.

Running CHDSK from the Windows Install Disk tells me there are "unrecoverable errors."

All this leaves me nowhere.

Reading this thread has not helped me.

Any ideas what I can do to get the "Dual Boot" configuration to perform as promised in the instructions?

Thanks.

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by eunuch on 2009-11-30
> **presence1960 said:**
> Let's get a better look at your setup & boot process... highlight all text and click the # sign on the toolbar to place code tags around the text.

Thanks.

I tried yet again - (The XP installation takes FORever!)

I think the problem was that formatting the drive only formatted PART of the drive space (XP is not too bright) so when the Ubuntu installation adjusted the partitions, Windows got VERY confused.

This last time I formatted the rest of the drive space after installing SP2

Ubuntu installation was slick as always, but now I can also boot into the (useless?) XP  ;-)

The problems were with XP, not Ubuntu!

Thanks again.

---


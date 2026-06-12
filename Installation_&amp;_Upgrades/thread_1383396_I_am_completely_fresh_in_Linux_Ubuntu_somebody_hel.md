---
title: "I am completely fresh in Linux Ubuntu somebody help"
date: 2010-01-17
forum: Installation &amp; Upgrades
---

### Post by mrhellboy86 on 2010-01-17
Hi
I just installed the Ubuntu successfully the night before
with the fist time I booted on the Ubuntu, I used Software Center to download some software, and install them , and I used automatic Updater to update my Ubuntu that was 9.10 and I just didn't notice what was that updates I just clicked update button and went to bed, at the morning when i restarted the ubuntu a black screen appeared and the tree LED that are capslock , scrolllock and numlock started to blink
if it is a special sign of something please help me
i just confused and upset to have my ubuntu down just after i installed it
i thought it should be a reliable operating system

---

### Post by kansasnoob on 2010-01-17
> **mrhellboy86 said:**
> Hi
I just installed the Ubuntu successfully the night before
with the fist time I booted on the Ubuntu, I used Software Center to download some software, and install them , and I used automatic Updater to update my Ubuntu that was 9.10 and I just didn't notice what was that updates I just clicked update button and went to bed, at the morning when i restarted the ubuntu a black screen appeared and the tree LED that are capslock , scrolllock and numlock started to blink
if it is a special sign of something please help me
i just confused and upset to have my ubuntu down just after i installed it
i thought it should be a reliable operating system

What type of installation? Is Ubuntu the only OS? Or is it a dual boot? Or a Wubi install?

Did you manage to get it to restart?

---

### Post by kansasnoob on 2010-01-17
Example of a Wubi install:

[http://www.psychocats.net/ubuntu/wubi](http://www.psychocats.net/ubuntu/wubi)

Example of a dual boot:

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=3](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=3)

I looked at your other posts and figured out you also have Windows but need to know if it's a Wubi install or an actual dual boot.

---

### Post by mrhellboy86 on 2010-01-17
> **kansasnoob said:**
> What type of installation? Is Ubuntu the only OS? Or is it a dual boot? Or a Wubi install?

Did you manage to get it to restart?
I have XP on my laptop and I used my Ubuntu 9.10 CD to boot for installation
then I used the most free space for installing Ubuntu alongside XP
so it is dual boot and I didn't used Wubi
and as i mentioned i did updated Ubuntu

---

### Post by mrhellboy86 on 2010-01-17
> **kansasnoob said:**
> Example of a Wubi install:

[http://www.psychocats.net/ubuntu/wubi](http://www.psychocats.net/ubuntu/wubi)

Example of a dual boot:

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=3](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=3)

I looked at your other posts and figured out you also have Windows but need to know if it's a Wubi install or an actual dual boot.
i did manage installation successfully
and I entered to my desktop in Ubuntu
then after a restart this happened
it is not a wubi install it is a normal installation with cd and i partitioned the disk with the Most Continues Space in hard disk option
and now i can choose with OS i go in
and Windows is working well
just ubuntu doesn't work

---

### Post by mrhellboy86 on 2010-01-17
i say, i didn't have any problem in installation process
just after installing some Apps and updates this have happened

---

### Post by mrhellboy86 on 2010-01-17
is there any tools for ubuntu to backup the whole things with a boot CD 
I have an External HDD and i can backup all of my ubuntu partition
if it is very hard to rollback the things happend to me
please introduce me a full backup software 
so i install the ubuntu again and i backup my ubuntu

---

### Post by houseworkshy on 2010-01-17
Well there is a partial roll back.  First I'd try using the recovery mode one second from the top in your boot menu.  This will lead you to some more choices, choose the fix x servor one ( this will try to fix, among other things your screen ).  Should it work you will be in safe graphics mode.  If that works the first thing to do is to install the appropriate hardware drivers ( esp graphics ).  You can find that in System>Administration>hardware drivers.  The process is fairly automatic.  Should be ok after that.

If not try going back to the previous kernel from the boot screen, this also has a system recovery mode below it but try it "as is" first.

---

### Post by kansasnoob on 2010-01-17
> **houseworkshy said:**
> Well there is a partial roll back.  First I'd try using the recovery mode one second from the top in your boot menu.  This will lead you to some more choices, choose the fix x servor one ( this will try to fix, among other things your screen ).  Should it work you will be in safe graphics mode.  If that works the first thing to do is to install the appropriate hardware drivers ( esp graphics ).  You can find that in System>Administration>hardware drivers.  The process is fairly automatic.  Should be ok after that.

If not try going back to the previous kernel from the boot screen, this also has a system recovery mode below it but try it "as is" first.

I think Karmic dropped "fix X" from the options in recovery mode" :(

I was going to suggest booting an older kernel.

I'm in Lucid right now but I think Karmic initially installs with 2.6.31-14-generic & is now up to 2.6.31-18-generic. I may have the numbers wrong though (I'm relying on my memory).

But it may boot into the older kernel.

All that said Karmic just never was stable on my hardware. Jaunty and Hardy both are and so far Lucid appears to like my hardware, but Karmic just didn't! 

And it was just impossible to troubleshoot, I'm sure it was an Xorg thing beacuse installing the Xorg edgers PPA helped and I also tried running the Karmic kernel in Jaunty and it was fine, but the freezes, lockups, and crashes were too frequent to even be able to gather the logs needed to troubleshoot the bug :(

---

### Post by houseworkshy on 2010-01-17
Ah yes  THAT releace.  Thanks I read the post too quickly.  I've got it running now but it was a nightmare, especially for graphics, no xorg.conf and a beta loader.  Well it can be done ( posting from it now ) but I won't send someone new through that maze even if I can remember the way.  Strike my earlier advice Mrhellboy, sorry about that, and just put in 8.04lts instead it's supported until april next year and works really well without any fuss.  Sorry for not paying attention. PS Rules for super heros 1/ don't put your hand in the hole in wall, 2/ don't mess with 9.10.

Once you are up and running this free book

[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)

Is really good for getting started.

---

### Post by kansasnoob on 2010-01-17
Well I should also have added that many people have had great success with Karmic. I think it's that way with every release.

For me Gutsy was great, everything just worked. 

Hardy drove me nuts for about the first 4 months until pulse audio got straightened out, but it's great for me now.

Intrepid worked fairly well but I actually just preferred Hardy.

Jaunty was and still is the most stable for me since Gutsy. Everything just works, but from reading the forums I know that was not the case for everyone.

Karmic is impressive to me other than the constant hard lockups. It's noticeably faster and I actually really like grub2. 

Lucid is looking very good so far.

To me the bottom line is, from one version to another, I think it's unrealistic to expect every set of hardware to work perfectly. Right now Hardy works quite well for me and it's supported for another 16 months. Jaunty is even better  and it's still supported for another 10 months.

---

### Post by houseworkshy on 2010-01-17
I agree with all that.  I suggested 8.04 due to the long term support and because it has been road tested so long. Best chance of hassle free use.  I'd like to add that for me it was a blessed releif how little time I had to spend fixing things, like viruses, malware, patches, and the continual downtime I had with a commercial system.  Ubuntu is a very good choise and well worth a little fiddling around at the set up stage. Once it's in it is very stable.

---

### Post by mrhellboy86 on 2010-01-18
Despite all, 
I talked to a friend of mine
and he said all the bad things was because of that update
Personally I think it WAS because of updating ubuntu
because my system didn't have any problem
so I decided to install the Ubuntu 9.10 again
I did it alongside the old Ubuntu9.10 that was corrupted 
so that some of my disk are occupied by that 
I would be thankful if someone tell me how could I install Ubuntu
on old Ubuntu, while there is a win xp (dual boot) situation
(actually now I did waste about 6 Gig of my disk)

---

### Post by Bartender on 2010-01-18
If it were me I'd delete all Ubuntu partitions and start over.  XP will not start up after you've wiped all the Ubuntu partitions because GRUB installed Stage 1 to the Windows MBR.
Don't let that freak you out.  Just reinstall Ubuntu, use it for a few days to make sure it's working, then try an update.  Or some package downloads.  Don't try to do too much at one time without checking to make sure Ubuntu's still working.

I prefer the stand-alone GParted LiveCD (link below) for partitioning work.  Wipe out all Ubuntu partitions, create one extended partition out of the space, then install Ubuntu ONE time, not two ;)

---

### Post by mrhellboy86 on 2010-01-19
> **Bartender said:**
> If it were me I'd delete all Ubuntu partitions and start over.  XP will not start up after you've wiped all the Ubuntu partitions because GRUB installed Stage 1 to the Windows MBR.
Don't let that freak you out.  Just reinstall Ubuntu, use it for a few days to make sure it's working, then try an update.  Or some package downloads.  Don't try to do too much at one time without checking to make sure Ubuntu's still working.

I prefer the stand-alone GParted LiveCD (link below) for partitioning work.  Wipe out all Ubuntu partitions, create one extended partition out of the space, then install Ubuntu ONE time, not two ;)
I am really confused I did install the Ubuntu9.10 twice and i am going to do that again for the third one just in a 3 day
everyday has its own Ubuntu
how can I be strong to continue using ubuntu while i should install it everyday
does any one have any idea?
what people do when OS hang? I just turn off the laptop by power button
and the grub is gone
the previous time i just installed the updates of ubuntu and the whole thing were gone
maybe something important exist that I don't know

---

### Post by houseworkshy on 2010-01-19
Whilst xp can't read linux. linux CAN read xp.  So to back up data easily put whatever you want to keep on the xp side.  To do this go to places where the xp bit will show as media with however many gig it is.  Click on it and you will be asked to use your Ubuntu password.  After that it is a simple copy and paste operation for your work.  Then I'd recommend doing a clean install of Ubuntu on all of the non windows part of your drive.  You will be able to tell which that is because it will be using the ntfs file system.  That should get you back to a duel boot.  Once that is done, reboot as asked, update and just do the mounting of the xp drive again and copy paste your work back.  I hope this helps.  I strongly recomend the Ubuntu pocket guide to learn the essential basics, you can get as a free pdf download from here  [http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)

---


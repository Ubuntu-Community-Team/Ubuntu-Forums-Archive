---
title: "Can anyone REALLY help me as a novice here"
date: 2008-09-24
forum: Installation &amp; Upgrades
---

### Post by gavmoulds on 2008-09-24
Hi everyone.

I have managed to successfully instal ubuntu and partition my drive with my existing winxp.

Problem..I can no longer boot the xp.

It is listed in the post screen and I can select it. All that happens is a message saying 'starting' and a flashing cursor.

This has really p''''''ssed me off to say the least.

I just completed a complete re install after getting rid of crappy vista..now everything is lost to ubuntu.

I want to turn back this error

---

### Post by Pumalite on 2008-09-24
Edit your menu.lst and add an entry for XP below the AUTOMAGIK line
title  Windows
root  (hd0,0) or whatever)
makeactive
chainloader +1

---

### Post by gavmoulds on 2008-09-24
> **Pumalite said:**
> Edit your menu.lst and add an entry for XP below the AUTOMAGIK line
title  Windows
root  (hd0,0) or whatever)
makeactive
chainloader +1


Could you say that in english please

---

### Post by Pumalite on 2008-09-24
Post:
sudo fdisk -lu
cat /boot/grub/menu.lst

---

### Post by sneeks on 2008-09-24
what he means is you have to change xp to hda0,if that was the first install on the system.
i will find the thread that does this in normal blokes talk when i get a minite.

---

### Post by gali98 on 2008-09-24
Okay first, you really shouldn't have used that title.. First it does not help anyone know your problem, Second it is just pure idiotcy to put a title like that.
Anyway, you might just try running the command
update-grub
and see if that helps.
Kory

---

### Post by Pumalite on 2008-09-24
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)

---

### Post by Pumalite on 2008-09-24
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by sneeks on 2008-09-24
found two for you,but not the one i really wanted to show ya(have limited time,but will check tomorrow on.)
sneeks.
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

---

### Post by gavmoulds on 2008-09-25
> **gali98 said:**
> Okay first, you really shouldn't have used that title.. First it does not help anyone know your problem, Second it is just pure idiotcy to put a title like that.
Anyway, you might just try running the command
update-grub
and see if that helps.
Kory

What is your problem...theres plenty of posts in here entitled help.

Perhaps you should read up on your spelling before having a go at anyone else.

Or even have a go at the bloke who replied to my post with complete techno geeky stuff.

Sorry but I thought this was a place for 'friendly' help one another people.

You muppett.

---

### Post by Elfy on 2008-09-25
If you want people to help you then you need to help us help you and that includes thread titles.

If you need help with how to achieve what people have requested then say so. The forum is generally helpful.

Sometimes 'complete techno geeky stuff' is what is needed for us to find out how to help you. 

Personal attacks on other users will not be welcomed by anyone.

If you still need help then say so, I will add that the Absolute Beginners forum is more likely to start at the beginning and give more implicit help.

---

### Post by gavmoulds on 2008-09-25
> **forestpixie said:**
> If you want people to help you then you need to help us help you and that includes thread titles.

If you need help with how to achieve what people have requested then say so. The forum is generally helpful.

Sometimes 'complete techno geeky stuff' is what is needed for us to find out how to help you. 

Personal attacks on other users will not be welcomed by anyone.

If you still need help then say so, I will add that the Absolute Beginners forum is more likely to start at the beginning and give more implicit help.


I appreciate that and I do not welcome his personal attack on me. In my opinion that gives me full authority to reply which is what I have done.

Is this another forum where the new user gets singled out just because he isnt in the click. If not then tell him the rules too..not me.

---

### Post by Elfy on 2008-09-25
No this isn't a forum where new users get singled out.

So, do you need help still - if you do, then we still need the information pumalite requested.

If you haven't used the terminal yet then it can be found in accessories, the first of the 2 commands will ask for the password - this is your normal password. Be aware that it will not show as you type it - nor will you get * it will be invisible.

Once you have ran the commands please paste both outputs into a new reply please - could you also put them in code tags - on the new reply text box there is a small toolbar, highlight the pasted text and click the # - it makes it easier to read.

Thanks - I'm about for a while if you want to try and get xp working.

---

### Post by gavmoulds on 2008-09-25
I risk criticism for this but I just DO NOT UNDERSTAND WHAT YOU ARE ALL TALKING ABOUT.

I cannot access my win xp partition.

It hangs and says

Starting...

and the cursor flashes..thats it

Can yantyone please tell me what to do.

---

### Post by fourthofjuly on 2008-09-25
if you have a live cd, boot from it

---

### Post by gavmoulds on 2008-09-25
Well...what can I say...obviously I am not speaking ENGLISH here.

I dont understand...boot what from live cd. There is no such thing as live cd for windows.

Dont you people actually read what it says in the post before replying.

I NEED SERIOUS HELP HERE.

---

### Post by tuxxy on 2008-09-25
Is your windows XP partition displayed in your GRUB menu?

---

### Post by semitone36 on 2008-09-25
> **gavmoulds said:**
> Well...what can I say...obviously I am not speaking ENGLISH here.

I dont understand...boot what from live cd. There is no such thing as live cd for windows.

Dont you people actually read what it says in the post before replying.

I NEED SERIOUS HELP HERE.

Okay, how about this: CALM DOWN!

A live CD is the original disk that had XP on it that you used to install XP on your computer.  Booting from live CD means putting that original CD into your disk drive and then configuring you computer to run its OS from the CD drive instead of your hard drive (default)

But I dont believe that will get you anywhere fast.  Let's start out by doing this.  If you can still run Ubuntu normally, go to Places -> Computer and see if there is an icon for your windows partitions.

---

### Post by gavmoulds on 2008-09-25
grub no longer loads..error 22 but the winxp partition was there before...it just wont boot

---

### Post by semitone36 on 2008-09-25
That is not good.  Lets try this. Boot from your Ubuntu live CD and follow the directions on this post: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Hopefully this will get your grub back up and running.  Was this the same problem all along or is this different from the problem where you could not access XP?

---

### Post by semitone36 on 2008-09-25
Another option (if you dont have any reason to keep XP) is to just do a fresh install with Ubuntu and over write XP.  I had a very similar problem to this when I first tried Ubuntu (you are not alone).  In the end I just said screw it and wiped my HD.
[http://ubuntuforums.org/showthread.php?t=880116](http://ubuntuforums.org/showthread.php?t=880116)

Ubuntu does have a learning curve.  It took me about a month or so to get used to it but I have never had such efficiency with a computer before.  It was very worth it to me.:)

---

### Post by melojo on 2008-09-25
If all you want to do is to get windows to boot then put your windows install cd in the cdrom and reboot-goto the recovery console and type this.

fixmbr and then fixboot

This will restore the masterboot record and I believe the ntldr which is windows boot loader.

this will not give you a choice to boot into ubuntu, you will have to use grub to fix that.

---

### Post by bobbob1016 on 2008-09-25
It might also help if you can be more specific.  As in what can't read your XP partition, Ubuntu or Windows?  What did you do to get this problem, or has it always been there?  What hardware are you using?

You have to be as descriptive as possible with posts.  You basically are saying "My car is making a funny noise.  It won't start anymore.  Please tell me how to fix it."  I'm not trying to offend you, just letting you know how hard it is to diagnose your issue from what you said.

---

### Post by gavmoulds on 2008-09-25
> **semitone36 said:**
> That is not good.  Lets try this. Boot from your Ubuntu live CD and follow the directions on this post: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Hopefully this will get your grub back up and running.  Was this the same problem all along or is this different from the problem where you could not access XP?


That just doesnt work.

It does not actually get you into grub

---

### Post by jpeddicord on 2008-09-25
Duplicate threads merged.

---

### Post by bobbob1016 on 2008-09-25
> **gavmoulds said:**
> What is your problem...theres plenty of posts in here entitled help.

Perhaps you should read up on your spelling before having a go at anyone else.

Or even have a go at the bloke who replied to my post with complete techno geeky stuff.

Sorry but I thought this was a place for 'friendly' help one another people.

You muppett.

First, your post "Help.... I am suicidal" isn't the best way to start it.

Secondly, asking for help with your computer in non-technical ways doesn't really make sense.  Linux isn't really point and click as much as Windows is.  At first this can be daunting, but if you think about it, you don't have to hunt through menus to find the options.

When they said to post the results of the commands, they meant to go to Applications -> Accessories -> Terminal and then type those commands one line at a time, press enter after each line, then copy and paste the results here.  But saying they aren't speaking english is a hostile response.

I get that you are frustrated since you started with Ubuntu and now can't start XP, but you're anger is apparent and putting people off from helping you.  If you post the results from the commands they said to run on the first page, we'll be able to help more.  There are a million different things that can be happening, those commands will tell us what to do.  There is no one answer to fix your Windows.

---

### Post by issih on 2008-09-25
Believe it or not you have had a lot of good advice here...you just are too new to know it.

First of all, all the advice you have been given made the assumption that as your xp install is borked you were not using xp, rather that you were using ubuntu.

As you now can't get grub to function at all we will assume you are booting from the ubuntu live cd (i.e. place ubuntu install cd in drive and reboot pc, choosing to boot from cd ahead of hard drive)

Once ubuntu is running (i.e. you have selected to try ubuntu without changes to your computer...and waited a fair while)

You should now try a few of the things suggested already by other people.

Open a terminal (Applications->Accessories->Terminal)
then type in:

```
sudo fdisk -lu
```

and hit enter. copy and paste (using the mouse) the output to the forum, that will let us see the structure of the partitions on your hard drive so we can be sure that things are ok on that front.

if the xp partition is ok, then you have options:
1) Reinstall grub as the post [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351) suggests...this information is correct, but needs to be done from a terminal in a live cd environment, as described above.

2) Completely reinstall ubuntu as before into the existing ubuntu partition. this will reinstall grub too and hopefully fix your problem

3) Use a windows xp install cd to reinstall the windows bootloader. this requires booting from the windows install cd entering recovery console and entering the command fixmbr.

N.B. 3) will only leave you able to boot windows.

Finally I feel that someone should point out that the original thread title was insensitive to anyone who has had their life touched by suicide, or suicidal people, and your response to it being criticised was out of proportion. In addition, it is very common for people to be told to use descriptive thread titles, because as you pointed out there are hundreds that say "help" and all the people trying to help then have to enter the thread to find out if they have any chance of being useful or not. Descriptive thread titles help us help you (to steal an awful cliche) as for the rest, this isn't you talking to your friends, it is a public forum, and consequently there are potentially people who are sensitive to any controversial issue...bear that in mind when posting.

---

### Post by gavmoulds on 2008-09-25
> **issih said:**
> Believe it or not you have had a lot of good advice here...you just are too new to know it.

First of all, all the advice you have been given made the assumption that as your xp install is borked you were not using xp, rather that you were using ubuntu.

As you now can't get grub to function at all we will assume you are booting from the ubuntu live cd (i.e. place ubuntu install cd in drive and reboot pc, choosing to boot from cd ahead of hard drive)

Once ubuntu is running (i.e. you have selected to try ubuntu without changes to your computer...and waited a fair while)

You should now try a few of the things suggested already by other people.

Open a terminal (Applications->Accessories->Terminal)
then type in:

```
sudo fdisk -lu
```

and hit enter. copy and paste (using the mouse) the output to the forum, that will let us see the structure of the partitions on your hard drive so we can be sure that things are ok on that front.

if the xp partition is ok, then you have options:
1) Reinstall grub as the post [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351) suggests...this information is correct, but needs to be done from a terminal in a live cd environment, as described above.

2) Completely reinstall ubuntu as before into the existing ubuntu partition. this will reinstall grub too and hopefully fix your problem

3) Use a windows xp install cd to reinstall the windows bootloader. this requires booting from the windows install cd entering recovery console and entering the command fixmbr.

N.B. 3) will only leave you able to boot windows.

Finally I feel that someone should point out that the original thread title was insensitive to anyone who has had their life touched by suicide, or suicidal people, and your response to it being criticised was out of proportion. In addition, it is very common for people to be told to use descriptive thread titles, because as you pointed out there are hundreds that say "help" and all the people trying to help then have to enter the thread to find out if they have any chance of being useful or not. Descriptive thread titles help us help you (to steal an awful cliche) as for the rest, this isn't you talking to your friends, it is a public forum, and consequently there are potentially people who are sensitive to any controversial issue...bear that in mind when posting.

 it reads like this

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders, total 488281250 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe0000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   314377047   157187500    7  HPFS/NTFS
/dev/sda2       314392050   488279609    86943780    5  Extended
ubuntu@ubuntu:~$

---

### Post by issih on 2008-09-25
Ok that looks hopeful that xp at least is still alive (an ntfs partition still exists)

From a terminal in the live cd environment try doing the steps from the thread posted previously

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

As that ought to reinstall grub onto your hard drive's mbr which will hopefully solve things for you.

If the process fails at some point, let us know where, what error messages if any were printed to the command line, etc

---

### Post by gavmoulds on 2008-09-25
> **issih said:**
> Ok that looks hopeful that xp at least is still alive (an ntfs partition still exists)

From a terminal in the live cd environment try doing the steps from the thread posted previously

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

As that ought to reinstall grub onto your hard drive's mbr which will hopefully solve things for you.

If the process fails at some point, let us know where, what error messages if any were printed to the command line, etc

I have re installed this now and it still wont boot my xp partition.

This is supposed to be better than windows...its a bloody nightmare.

What I need to know is why cant I get rid of this rubbish and get back my xp

---

### Post by linux5uper on 2008-09-25
> **gavmoulds said:**
> I have re installed this now and it still wont boot my xp partition.

This is supposed to be better than windows...its a bloody nightmare.

What I need to know is why cant I get rid of this rubbish and get back my xp

Okay, from what I understand, you followed the instructions and restored grub. Now you can boot into ubuntu but not into xp? The XP boot hangs with a mouse cursor and blank screen, right?

That most probably means that the XP installation is somehow corrupted. You have to use windows tools to try to recover it, as far as I know. If you're as unlucky as I have been with windows, this might mean you have to reinstall. This is not because Ubuntu is rubbish, but because you most probably did not learn enough in advance about how to set up a dual boot environment safely.

---

### Post by gavmoulds on 2008-09-25
> **linux5uper said:**
> Okay, from what I understand, you followed the instructions and restored grub. Now you can boot into ubuntu but not into xp? The XP boot hangs with a mouse cursor and blank screen, right?

That most probably means that the XP installation is somehow corrupted. You have to use windows tools to try to recover it, as far as I know. If you're as unlucky as I have been with windows, this might mean you have to reinstall. This is not because Ubuntu is rubbish, but because you most probably did not learn enough in advance about how to set up a dual boot environment safely.


I have spent all...f.......g afternoon..re installing...fix mbr....fixboot and nothing bloody changes.

As for dual booting I did exensive research and followed the bloody instructions on these forums on how to do it correctly.

This is just pathetic..I have all the information on my hd yet I cannot access it..and people have the nerve to call windows crap.

UBUNTU is a blodoy joke..when it goes wrong you need a bloody masters degree in crap to fix it.

---

### Post by semitone36 on 2008-09-25
> **gavmoulds said:**
> I have spent all...f.......g afternoon..re installing...fix mbr....fixboot and nothing bloody changes.

As for dual booting I did exensive research and followed the bloody instructions on these forums on how to do it correctly.

This is just pathetic..I have all the information on my hd yet I cannot access it..and people have the nerve to call windows crap.

UBUNTU is a blodoy joke..when it goes wrong you need a bloody masters degree in crap to fix it.

You know what? I would have loved to help you out.  But quite frankly you annoy me.  I had nearly identical problems with installation when I first tried but I was fully aware of the risks I was taking.  Its not our fault that you weren't smart enough to research into what you were doing before you went ahead and tried to repartition your hard drive.  Everything comes with risks but dual-booting is an ESPECIALLY risky job.

Get a better attitude and listen to the advice you are given.  Otherwise I hope you enjoy using your computer as a doorstop for the rest of its existance.

---

### Post by melojo on 2008-09-26
> **semitone36 said:**
> You know what? I would have loved to help you out.  But quite frankly you annoy me.  I had nearly identical problems with installation when I first tried but I was fully aware of the risks I was taking.  Its not our fault that you weren't smart enough to research into what you were doing before you went ahead and tried to repartition your hard drive.  Everything comes with risks but dual-booting is an ESPECIALLY risky job.

Get a better attitude and listen to the advice you are given.  Otherwise I hope you enjoy using your computer as a doorstop for the rest of its existance.

+1
exactly what semitone36 said.
I love Linux (Ubuntu) and if it wasn't for the rest of my family I wouldn't have MS windows period.

---


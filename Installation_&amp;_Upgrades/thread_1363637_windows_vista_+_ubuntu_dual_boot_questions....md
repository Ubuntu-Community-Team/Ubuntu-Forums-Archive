---
title: "windows vista + ubuntu dual boot questions..."
date: 2009-12-24
forum: Installation &amp; Upgrades
---

### Post by drink_stir on 2009-12-24
kinda new and i jsut have a few questions about setting up a dual boot with vista and ubuntu 9.10.

i have set up a raw partition of 20 gigs, well its not exactly a partition its just unallocated space. from what i have read when i install ubuntu i need to edit the grub to get back to windows. 

my question is will there be a load os option like when u dual boot vista and xp on the bios screen? i would like to set up ubuntu as my main os but still would like to get back to windows without having to edit the grub everytime.

and second my partition is at the end of my disk how much will that effect performance?

i ask because i dont have a vista disk or i would just set up ubuntu first.

and third i booted from cd and all of my hardware works fine. will that change with a hd install?

---

### Post by drink_stir on 2009-12-24
anybody? i would realy like some help. i cant find anything with google.

---

### Post by Sef on 2009-12-24
Please wait 24 hours before bumping your post.  This a volunteer site and sometimes answers are quick and sometimes they are slow.   Yes, it is fustrating to wait, but with patience you can get your questions answered.

---

### Post by Herman on 2009-12-24
> from what i have read when i install ubuntu i need to edit the grub to get back to windows. my question is will there be a load os option like when u dual boot vista and xp on the bios screen? i would like to set up ubuntu as my main os but still would like to get back to windows without having to edit the grub everytime.
 In almost all cases Windows will be detected when Ubuntu is being installed, and automatically added to your boot menu. It always works perfectly for me at least. Still, there are a few people who seem to have bad luck. If you have a normal Windows installation it should be simple, but I don't know anything about RAID arrays or special arrangements like that.
> and second my partition is at the end of my disk how much will that effect performance?The difference probably won't be noticeable unless you run tests with benchmarking software. You might detect a little bit of difference if you measure carefully but I don't think it will be a serious problem. Your operating system will work okay.

---

### Post by drink_stir on 2009-12-25
my appologies for bumbing to soon. and thank u for the reply. i just knuckled down and did the install. everything is working perfectly. no problems with the install. now i just need to find many many programs.

---

### Post by Herman on 2009-12-25
Okay, glad you got it installed without any problems, (most people do I think), I hope you enjoy Ubuntu. :)

---

### Post by drink_stir on 2009-12-25
actually i just hit a snag. i was using the empathy instant messenger and it just closed out, and wouldnt let me reopen it. then when i restarted my computer i got a message in the top left corner that said "install problem." and something about power management, contact administrator. it brought up the login screen but when i put in my password it kicked it out and just brought me back to the same screen. any help with this?

---

### Post by Herman on 2009-12-25
Well the right way to fix will probably be posted somewhere here in the forums and may just require using the search bar, or you could start a new thread with a suitable title calculated to attract experts in empathy instant messenger program.
I don't know anything about empathy myself. It's not a program I've used recently.

The wrong way, but the easiest and fastest, would be to simply delete your new installation and re-install. That would take about half an hour and you don't know how long it might take for someone to answer your thread and tell you how to fix it properly. If you had a lot of settings and added software already you'd probably rather avoid re-installing, but in this case my guess is it would be the simplest.

Did you update your system before you started using it? It could be that there may have been some fault in empathy that's been fixed by an update right after the CD was released. It's a good idea to update your system right away after you install. 

Oh, I just had a thought, you might be able to try fixing it by booting into recovery mode and running a few of the options in there, something there might help. You might be lucky, but I'm only guessing.

---

### Post by drink_stir on 2009-12-25
i dont know if it was the empathy that was the problem. i am running on battery and i never set up the power management. maybe its just im too low on power. i tried the recoverymode and nothing happened. i will do some digging and see whats up with it. im just gonna reinstall it. but thank u for ur help.

---

### Post by Herman on 2009-12-26
Okay. 
Normally with the laptops I have at least, if they run low on power they shut themselves down suddenly and I need to run a file system check on the file system before I boot them again. Sometimes they'll boot okay without a file system check, but unless I'm feeling particularly impatient at the time, I normally run a file system check on them anyway as a matter of course, just to be on the safe side.

I usually run something like,
```
sudo e2fsck -C0 -p -f -v /dev/sda1
```
from another operating system or a live CD.

I don't think that's your problem right now though, but I'm not sure.

---

### Post by drink_stir on 2009-12-27
well i dont know if i should start a new thread. but here goes. i reinstalled everything. did the update. and then when i rebooted i got the same error message. POWER MANAGEMENT FOR GNOME WAS NOT INSTALLED CORRECTLY. and after i reinstalled i set up the power management for a laptop. im lost... but i will try the file system check and see if that will help.

---

### Post by Herman on 2009-12-27
I don't know anything about Gnome Power Manager, but I googled it for you and I found: [GnomePowerManager/FAQ - *GNOME* Live!]("http://www.google.com.au/url?sa=t&source=web&ct=res&cd=6&ved=0CCMQFjAF&url=http%3A%2F%2Flive.gnome.org%2FGnomePowerManager%2FFAQ&rct=j&q=POWER+MANAGEMENT+FOR+GNOME+WAS+NOT+INSTALLED+CORRECTLY&ei=rR83S5-bKNCTkAWm780D&usg=AFQjCNEkULMUWrMqEZbq_Us5V2E5G6fGyw&sig2=93BsfBSToHIdjFK9DvJCeQ")
From that I get the impression it has something to do with ACPI, which is an acronym for 'Advanced Configuration and Power Interface.  [ACPI]("http://en.wikipedia.org/wiki/Advanced_Configuration_and_Power_Interface") - Wikipedia link.

From the looks of briefs  for the items that turned up in google, problems with Gnome Power manager affect users of other distros and not only Ubuntu.

I found the following links which are only about the problem affecting Ubuntu users, 
[SOLVED] 			 			[GNOME Power Manager not installed correctly]("http://ubuntuforums.org/showthread.php?t=1355880&highlight=gnome+power+manager")

			 			 			                         [COLOR=#980101]**[ubuntu]**[/COLOR] 			 			[gnome power manager not installed correctly]("http://ubuntuforums.org/showthread.php?t=1363731&highlight=gnome+power+manager")

[COLOR=#980101]**[ubuntu]**[/COLOR] 			 			[Can not log into Ubuntu GNOME Power Manger (9.10)]("http://ubuntuforums.org/showthread.php?t=1363623&highlight=gnome+power+manager")

[COLOR=#980101]**[ubuntu]**[/COLOR] 			 			[Hang on boot up....]("http://ubuntuforums.org/showthread.php?t=1363016&highlight=gnome+power+manager")

[COLOR=#980101]**[ubuntu]**[/COLOR] 			 			[do nothing when battery gets low]("http://ubuntuforums.org/showthread.php?t=1363093&highlight=gnome+power+manager")

[COLOR=#816447]**[gnome]**[/COLOR] 			 			[gnome-power-manager crashes when switching from AC power to battery]("http://ubuntuforums.org/showthread.php?t=1362446&highlight=gnome+power+manager")

                        [SOLVED] 			 			[Problem while installing gnome-power-manager (and many more!) manually]("http://ubuntuforums.org/showthread.php?t=1360585&highlight=gnome+power+manager")

Taking a look around, I see under 'System'-->'Preferences', there's an icon called 'Power Management' and opening it gives me a windows called 'Power Management Preferences' that looks like it probably has something to do with laptops and their batteries.

---


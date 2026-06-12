---
title: "Win 2k partially broken after installing Ubuntu"
date: 2005-04-18
forum: Installation &amp; Upgrades
---

### Post by Johank on 2005-04-18
Aww, I was so hoping this would go smoothly......

I installed UBUNTU last night on a PIII 1G system, 512M Ram, 2 HDD. Of course I just dived right in....
The second drive (40G) used to be the main drive but, a few months ago I installed a new 160G drive and used the Maxtor software to mirror the install from the smaller drive so I would not have to re-install windows.
So, with UBUNTU I let the patitioning SW use the whole of the secondary (40GB) drive but allowed GRUB to wr ti the MBR that I assume is on the main drive. 

UBUNTU came up fine, install looked good (some odd probs but that probably simply because I don't know Linux) BUT....damn.....no my windows boots up (VERY slowly), I can't get "My computer" to work (it just freezes and/or comes up blank) and trying to run CD burning software does not work, it simply hangs. Everything else 'seems' to work....

What did I do wrong and, more importantly, how do I fix it?

Can I somehow go back to a pre-Ubuntu setup and try the install again?

---

### Post by themindlessmatt on 2005-04-18
[QUOTE=Johank]Aww, I was so hoping this would go smoothly......

I installed UBUNTU last night on a PIII 1G system, 512M Ram, 2 HDD. Of course I just dived right in....
The second drive (40G) used to be the main drive but, a few months ago I installed a new 160G drive and used the Maxtor software to mirror the install from the smaller drive so I would not have to re-install windows.
So, with UBUNTU I let the patitioning SW use the whole of the secondary (40GB) drive but allowed GRUB to wr ti the MBR that I assume is on the main drive. 

UBUNTU came up fine, install looked good (some odd probs but that probably simply because I don't know Linux) BUT....damn.....no my windows boots up (VERY slowly), I can't get "My computer" to work (it just freezes and/or comes up blank) and trying to run CD burning software does not work, it simply hangs. Everything else 'seems' to work....

What did I do wrong and, more importantly, how do I fix it?

Can I somehow go back to a pre-Ubuntu setup and try the install again?[/QUOTE]
 I think I might have a similar problem

After installing Ubuntu Warty (Hoary CDs not arrived yet), Windows 2k now boots slowely. It insists on checking the various new partitions every boot, not recognising them and giving up. Further more, it apparently hangs for the odd minute during the boot up process (when before it didn't). Once started everythin works, but disc operations appear to be preceeded by a pause.

Might it be related to presence of unrecognised partitions? This should be easy to test, replace the linux partitions with FAT ones and see if the boot times improve. Haven't done it myself as have no desire to hose my lovely Ubuntu installation to pacify the microsoft piece of ****. On the occasions I need windows I put up with the boot time.

Anyone have any simple ideas on how to fix it?

Matt

---

### Post by wxlidar on 2005-04-18
[QUOTE=themindlessmatt]I think I might have a similar problem

After installing Ubuntu Warty (Hoary CDs not arrived yet), Windows 2k now boots slowely. It insists on checking the various new partitions every boot, not recognising them and giving up. Further more, it apparently hangs for the odd minute during the boot up process (when before it didn't). Once started everythin works, but disc operations appear to be preceeded by a pause.

Might it be related to presence of unrecognised partitions? This should be easy to test, replace the linux partitions with FAT ones and see if the boot times improve. Haven't done it myself as have no desire to hose my lovely Ubuntu installation to pacify the microsoft piece of ****. On the occasions I need windows I put up with the boot time.

Anyone have any simple ideas on how to fix it?

Matt[/QUOTE]
 Odd. So both of you can boot into windows, but it takes longer. I never had a problem with windows and linux partitions. Windows should simply ignore them. My dual boot machine at work has no problems booting either OS. 

I'm wondering if it is a setting in GRUB that is causing the problem. However, I'm a relative noob with bootloaders so hopefully some of the experienced users will chime in. 

Johank, I don't think you did anything wrong. Perhaps when you mirrored your drive, the Maxtor software didn't completely remove the dependence on the original drive. Maybe something to do with the boot loader on the MBR? I'm guessing here. Again, maybe someone with more experience will stop by and post.  A question: was the 40gb drive moved from primary to secondary when you installed the 160gb drive? Trying to get an idea of the device locations of each drive.

-Dave

---

### Post by Johank on 2005-04-18
Hey Guys, thanks for the response. Dave, yup, after mirroring I physically swopped the jumpers so the big drive became the primary. What I fiond odd is that using windows explorer I can go and look at the C drive but if I try use the My Computer shortcut....we'll it's ugly - it just sits there same as and CD burning software. It's almost as if windows is no longer able to detect the various drive parameters.

---

### Post by alastair on 2005-04-18
It's not "unknown" partitions - I've had loads of them over time, and never seen this.

Check the "My Computer/Manage" option - and look at :

a) event logs / system
b) disk management

Maybe you had drive letters attached to (now) "unknown" disks/partitions? Or some other s/w expecting the other disk to be available?

---

### Post by Johank on 2005-04-19
Thanks Alastair, I'll check that this evening. 

However, last nights sweating over the keyboard has brought a new snippet. If I wait long enough, eveything seemsd to work. However, whenever a new explorer comes up, or I change drives in explorer, or try to use CD burning software, or launch MyComputer, it takes about 5 to 10 minutes for windows to build the tree and list the drive content. It's all got to do with identifying the drives.....

In despration I tried to re-install windows using the 'upgrade' option - no change! It still behaves the same.

---

### Post by laka on 2005-04-19
[QUOTE=Johank]
In despration I tried to re-install windows using the 'upgrade' option - no change! It still behaves the same.[/QUOTE]

Sorry, we are not interested  [-X 

 ;-)

---

### Post by Johank on 2005-04-19
[QUOTE=laka]Sorry, we are not interested  [-X 

 ;-)[/QUOTE]
 Laka, I'll take that as a joke.....Seriously though, I'm sure a sollution to this may help other people as well. As to windows, I'd like to be able to live without it but I have some software that I rely on that is on my windows system that I have not seen the equivalent on Linux....yet ;)

---

### Post by alastair on 2005-04-19
This is a Windows problem it seems, but I /would/ like to know what's up. Have you :

a) check the system event log?
b) tried listing a drive via a CMD shell (dir c:, etc.)
c) check the process view/list in the task manager?

---

### Post by Johank on 2005-04-19
[QUOTE=alastair]This is a Windows problem it seems, but I /would/ like to know what's up. Have you :

a) check the system event log?
b) tried listing a drive via a CMD shell (dir c:, etc.)
c) check the process view/list in the task manager?[/QUOTE]
 Hi Alastair. I'll see what I can dig up this evening. Just always seem to not have enough hours in a day... :)  
REALLY appreciate your interest in this issue, Thanks.

---

### Post by Cancel on 2005-04-19
I don't know if this will help, but I had the exact same problem as you. It would take forever to get into My Computer. Everything was fine before I installed Ubuntu. I have W2K on the master, and Ubuntu on the slave drive. I installed Ubuntu on the slave drive which windows had assigned a drive letter to so everytime I would go to my computer, it would look for that drive. What I did to fix it was restart the computer, pick Windows in the grub menu. As soon as windows started loading, I mean as soon as I pressed enter when picking Windows, I unplugged the power to the hard drive Ubuntu is on (if you unplug the hard drive before grub loads, you will get an error). I let windows load, went to My Computer, changed the drive letter of the dvd burner to what the Ubuntu hard drive was. Then I shut the computer down, plugged the drive back in and haven't had a problem yet. I hope this helps you out!!!!!

---

### Post by Johank on 2005-04-20
Well, some new info. I had a look at the logs and, even though there were new messages, I think they were caused by the problem and not the cause of the problem. Most of the errors relate to RAS not being able to load (access denied and network requ not supported) but the last error says that the server was not registered with DCOM within the required timeout. I suspect that because the system is so slow, the vairous services are not loading properly and hence the errors. 

I did look at the task manager but it's hard to tell what is and isn't right. CPU usage was very low (5% or so). 

Then I looked at Disk management and found 3 logical drives, 2 physical and 2 of them was on the small drive I had dedicated to linux. This took a long time to come up but Windows indicated all theree healthy, the primary (windows dr) as 'system', the biggest partition on the second (linux) drive as 'active' but nothing on the last small (less than 1 G) logical drive AND this had no drive letter associated with it. I gave it a letter - no change. 

Then, after another few frustrating re-boots, I created another hardware profile and diabled the second drive in device manager. Windows is now happy again and linux boots fine. 

Obviously this is not ideal, it's just a work around but it does indicate that the problem is Windows not recognizing the drive format. I'm not sure how to get by that....

---


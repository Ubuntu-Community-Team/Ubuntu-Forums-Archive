---
title: "Virtualbox: Need to share a folder between Gutsy and XP!"
date: 2007-11-18
forum: Installation &amp; Upgrades
---

### Post by bokorpop on 2007-11-18
I have Virtualbox with the full license(not OSE). I read the manual section 4.4 on folder sharing, but it still leaves me clueless on how to create a folder with shared files between Ubuntu(host) and XP(guest) of my virtualbox.

Manual: "In the GUI of a running VM, you can select 'shared folders' from the 'Devices' menu, or click on the folder icon on the status bar in the bottom right corner of the VM window"
Me: Check, I selected the folder I want to share  which is /home/justin/VMshare and added it


After that, I am completely  effin confused. IS the next step to configure something from within my guest? If so, how do I do this? 




If you can solve this problem for me, you can take credit for bringing a Windows user permanently over to Linux! I'm serious, this is the final step on the arduous journey for me.

Edit: SOLVED 1minute after postin:  net use x: \\vboxsvr\VMshare did it!

---

### Post by Rinzwind on 2007-11-18
1. Machine, settings,shared folders.  Add a dir to 'machinefolders' and name it. Remember the name. I called it 'xdxdxd' as an example.


2. Inside the guest you need to add your share with the 'net' command (IF windows)

C:\> net use F: \\vboxsvr\xdxdxd

Here F: will connect to your share named 'xdxdxd'.

---

### Post by Vevmesteren on 2007-11-19
that tells me that the network folder(path) was not found. But the folder is well defined and I rechecked the path three times now. Any ideas? Do I need to install anything additions?

---

### Post by kukuku on 2007-11-25
I've been fighting against this same problem for days now, only getting error 53 and migraine for it. I'm running Ubuntu 7.10 host with winxp pro client, using Virtualbox 1.5.0_OSE. 

The net use command only started working after I reinstalled the Guest Applications a second time (on top of the previous installations). When its installation went through without a single error, the shared folders started working immediately. I didn't even need to shut down the VM, just added an existing folder from the Device menu and net use said OK.

---

### Post by mosaic2s on 2008-01-30
yes. it works by running the command

net use f: //vboxsvr/foldername

then it appears as a networked drive in my computer.

---

### Post by BLTicklemonster on 2008-06-10
My Gutsy has no shared folders in System>Administration> so where is it?

---

### Post by mlissner on 2008-06-10
It's in the menus of the guest client window. So, boot up Windows, and then look in the menus of the window that it is booted in. 

Sorry if that's vague - I'm not at my Linux computer at the moment...

---

### Post by chad2408m on 2008-06-15
Firstly, Id like to say that everyones posts suck because they're way too difficult.  Heres the easiest way.  Make a Shared Folder in Virtual box, then boot Windows (any version above Win 95).  Then, once loaded go to My Computer, and click Tools (at the top) and then 'Map Network Drive'.  Using the extremely easy walkthrough, assign it a Drive Letter, then click Browse.  It will bring up something like 'VirtualBox Shared Folders', click the expland button next to that, and click on whatever folder you want.  You can do this with as many drives as possible.

---

### Post by BLTicklemonster on 2008-06-16
No, I mean Hardy. It doesn't have the shared folders place in system>administration like gutsy did.

Okay, I just found it, you just right click on a folder, click to share it, click create share, then you're told:
> 
'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error Permission denied
You do not have permission to create a usershare. Ask your administrator to grant you permissions to create a share.

instead of being prompted for a password.

How close to having it right can they possibly get and STILL not have it right.

Jeez.

---

### Post by Victormd on 2008-06-16
You need to add ROOT as a user to the group SAMBASHARE, restart and you're ready to share...

But yeah, I agree with you. Initially, it asked me it I wanted Nautilus to set the permissions automatically (first time sharing a folder in Hardy) and I said yes... and got the same error you posted... Why it didn't set the proper permissions, as stated, I have no idea. Once I added root to the sambashare group and restarted, sharing was a piece of cake...

---

### Post by BLTicklemonster on 2008-06-16
So they make it look like you can share easily, but in all actuality, you can't. Great. Back to square one.

How does one add root to samba share?

If it's manually editing a file, don't bother telling me. 

I'll wait until the day that they get this as simple as it is to share a folder in Windows, thank you. I'm in on big hurry to share stuff. All I really need is access to the other machines, I can drag whatever they want from down here to their machines. Extra work, but I don't want to have to remember a bunch of editing stuff every time something changes, thank you.

---

### Post by Victormd on 2008-06-16
Go to SYSTEM>ADMINISTRATION>USERS AND GROUPS, click on the Unlock button, then click on Manage Groups, scroll until you see the SAMBASHARE group, select it, click on properties and check ROOT, Ok, close, close, restart... :)

---

### Post by BLTicklemonster on 2008-06-16
... at which point, I won't have to log in as root or anything? Just log in normally, and voila?


*Edit:

Bloody hell.

I wonder if it works from the xp machines?

They're off, and it's after 1 A.M. so I'll check later.

Thank you Victormd

---

### Post by Victormd on 2008-06-16
You won't have to login as root or anything, just login normally.
What happens is that when you share, nautilus tries to set the permissions as root (and asks for your password) but since root isn't a initially a user of that group, it won't set the permissions, therefore, no sharing... As soon as you set root as part of that group, then it will be able to set the proper permissions and you get to share the folder... :)

---

### Post by BLTicklemonster on 2008-06-16
Thanks, I'll turn on the xp boxes when I get home and see if I can get to my machine from them. I really hope it was that easy. (I clicked the two boxes to let users write to, and to use guest with no account so maybe they can just click and go)

---

### Post by Victormd on 2008-06-16
In theory, that's what's supposed to happen... :)

---

### Post by BLTicklemonster on 2008-06-18
It worked, but now I want the XP boxes to see it, but they don't. How do I set my ubuntu shared folder to be shared so computers on MSHOME will see it?

---

### Post by Victormd on 2008-06-18
can you succesfully ping your ubuntu box from the XP machines?
For me it works straight forward, I didn't have to do anything. Simply sharing the folder and on my xp machine, going to network places, my ubuntu box shows up and there's the shared folder.

---

### Post by BLTicklemonster on 2008-06-18
Dang, they're all off, and I'm going between this machine and a sick xp box on the other side of the room. How would I do this, anyway? Look up my ip address and just ping it from the command line in an xp box, right?

---

### Post by Victormd on 2008-06-18
```
ifconfig -a
``` should give you your ip address on the ubuntu box... then ping from xp

---

### Post by BLTicklemonster on 2008-07-14
It worked, by the way. Thanks!

---


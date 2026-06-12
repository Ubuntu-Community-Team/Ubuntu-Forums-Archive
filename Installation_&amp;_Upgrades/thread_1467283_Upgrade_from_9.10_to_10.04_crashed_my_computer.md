---
title: "Upgrade from 9.10 to 10.04 crashed my computer"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by bmathise on 2010-04-30
Hi.
I just upgraded from Ubuntu 9.10 to Ubuntu 10.04. Major mistake. Everything worked OK in 9.10. In 10.04 I have no mouse anymore (Logitech Bluetooth mouse), the screen doesn't work properly, the PS2 mouse doesn't doesn't work and I can't boot the newest kernel (10.04 seems to come with two different kernels) at all. Live CD doesn't work. Won't boot, just get's to the point where there is a Ubuntu logo and a progressbar. 
I am now forced to borrow computers from other people.
As 9.10 worked OK, I was wondering, is there a way to safely downgrade 10.04 to 9.10? If so, I can always upgrade again when all the problems have been sorted out.

If I can't downgrade, is it possible to reinstall 9.10 without destroying the /home directory ?

Thanks for any help.

Bjorn

---

### Post by dino99 on 2010-04-30
> **bmathise said:**
> Hi.
I just upgraded from Ubuntu 9.10 to Ubuntu 10.04. Major mistake. Everything worked OK in 9.10. In 10.04 I have no mouse anymore (Logitech Bluetooth mouse), the screen doesn't work properly, the PS2 mouse doesn't doesn't work and I can't boot the newest kernel (10.04 seems to come with two different kernels) at all. Live CD doesn't work. Won't boot, just get's to the point where there is a Ubuntu logo and a progressbar. 
I am now forced to borrow computers from other people.
As 9.10 worked OK, I was wondering, is there a way to safely downgrade 10.04 to 9.10? If so, I can always upgrade again when all the problems have been sorted out.

If I can't downgrade, is it possible to reinstall 9.10 without destroying the /home directory ?

Thanks for any help.

Bjorn

cold boot does not help ? if you can open a terminal (alt+f2): sudo dpkg --configure -a

---

### Post by bmathise on 2010-04-30
Cold boot doesn't help. I get the Grub menu and Grub seems to work. The newest kernel doesn't boot at all. The other kernel does boot, but too many things won't work. It's hard to navigate without a mouse and decent picture on the screen. I'll try your suggestion and get back with the result.

---

### Post by andreasdelpaso on 2010-04-30
Hello me too have an issue with the Upgrade.
It installed ok,new interface ok,but it keeps minimizing ANY window  open.Cant keep it open for more than 2 - 3 seconds.All programs seem to  load ok but they minimize immediately.
Help guys it's very frustrating.

---

### Post by bmathise on 2010-04-30
OK, Dino99,

I'm back to Ubuntu. Sort of.
I ran sudo dpkg --configure -a , but it didn't seem to do much.
The PS2 mouse is now working, must have been something else that was wrong.
I found another graphics driver that works (it is suggested by Ubuntu, but was hard to select when my mouse and screen didn't work properly).
Sound is working.
Webcam is working.
Microphone is working.

Bluetooth is  working and my Logitech MX1000 mouse is also working. It was a matter of setting it up correctly in the Bluetooth settings (choose the correct PIN-code).

So, perhaps the command you suggested did the trick, after all
Basically, everthing is now working, or so it seems. There is one more thing, though. The buttons for closing, minimizing and maximizing the windows are now located to the left. Yes, I know it is a "feature" in 10.04, but I've gotten so used to having them to the right, after some 15 years. Is there a way to get them back to the upper right corner again? 

Thanks for your help. Have a really nice weekend =)

---

### Post by lechien73 on 2010-04-30
Hi,

Yes, you can put the buttons back to the right if you wish.

[INDENT]Press ALT-F2 and type: gconf-editor
Go to apps -> metacity -> general
Right click on "button_layout" and select "Edit Key"
Change the value to: ":minimize,maximize,close" (without the quotes, obviously)
Click OK and the buttons will bounce back to the right.
[/INDENT]
Since I've been using a Mac recently, I've got used to the buttons on the left, but I hope this helps.

Regards

Matt

---

### Post by Frankiewizard on 2010-04-30
I down loaded 10.04 last night and am having a few teething problems with it but I should sort it out in a few days.It's the graphic card 'Nvidia' on a ToshibA G20 QosmiO.

Regards

---

### Post by bmathise on 2010-04-30
Great tip, Matt!
Worked as a charm =)
Now both Windows- and Mac users have a choice. Beautiful.
I wish you too a wonderful weekend. =)

Regards and thanks
Bjorn

---

### Post by fejao on 2010-04-30
Im having problems too...but my problem is that it dosent even start the computer after the upgrade...at least I still have the menu to boot with the old kernel to keep using the computer.

---

### Post by bmathise on 2010-04-30
Yes, I have to boot the old kernel, too, but I assume that is a problem that will go away by itself, as soon as the Ubuntu team has had time to do some more work. I just changed the setting 
default=0
in /boot/grub/menu.lst to
default=2
so Grub will select the old kernel every time. If you change the value to something else, just remember that the first choice is 0, the second is 1 and so on.
You have to be root to edit this file: sudo gedit /boot/grub/menu.lst or, if you're at the command line: sudo nano /boot/grub/menu.lst
This particular setting is located near the beginning of the file.

---

### Post by fjalars on 2010-05-01
My Ubuntu (amd64)  had some problems during this same upgrade and after the upgrade finished I rebooted the computer, but not boot option worked. 

I see no other way but reinstall 9.10 from scratch..  :(

This was a relatively fresh install so the damage is not great...

---

### Post by Linuks Dude on 2010-05-01
It's becoming apparent that the newest 10.04 release of Ubuntu, and all it's flavors, is "not ready for prime time".

After crashing two different installs of Kubuntu and Ubuntu 9.10 with 3 hour "upgrades", then downloading the iso and finding that it will not even finish booting to liveCD... well, you do the math.

I just wish I had checked the forums before completely trashing my network.  Back to openSUSE, I guess...

---

### Post by zzyzx1 on 2010-05-01
This is not "SOLVED" for me... I cant get to a boot/Grub screen. All I get is some purpleish glow and what looks to be trashed graphics at the top of screen, nothing more. Cant Alt-F2 it just goes black. I seriously hope I am not screwed here. It took me so long to get 9.04 working right I will have no choice but to go on a never ending rant if i cant fix.

What are my choices here folks? No text, no graphics... nadda...

Gracias.

---

### Post by drclue on 2010-05-03
Luckily I have two computers and this one I'm typing from
actually made it through the desert and came out the other side.

I have another machine that my other half uses that was
not so fortunate, as after it completed the reboot,
it offered up the error message.

Kernel panic - not syncing: VFS: unable to mount root fs on unknown wn-block(0,0)    /etc/default/grub

So , I figured , OK , I'll just select an older version 
and work my way back from that. Well, this machine only goes back as far as 9.10 which was originally installed from the CD
mailed to me from Ubuntu. Alas , the only thing I can get
to work is a shell prompt.

Even worse is that it has an old NetGear USB WiFi for acessing the network and it won't come up, so I have no way to drag in replacement files.

The only thing that does seem to work is using the CD to 
run Ubuntu in demo mode. In that instance the networking does work and the desktop can see the hard drive and it's contents.

Now I just need to know what to do to put the situation right.
Can I install 9.10 without it destroying the data on the drive?

Is there a way to maybe get the WiFi adapter to function
and grub to load things again. I'm sorta left scratching my head on this one.

Ubuntu needs to come out with a workflow to recover from this and post it in a prominent place as the answers I'm getting thus far 
are inconsistent and/or involve incomplete answers.

In the ubuntu irc , the conversation is flowing so fast
and the answers lack any detail.

Here in the Forums , lots of people asking questions 
and not many answers.

Somebody HELP us!!!!! PLEASE

---

### Post by as901 on 2010-05-10
I also "Upgraded", and now the only way to I could use this computer is to completely install Ubuntu 9.10 from scratch! I lost everything!:(

---


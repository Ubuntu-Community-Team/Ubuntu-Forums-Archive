---
title: "Unmount or safely remove ?"
date: 2009-12-02
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Kevbert on 2009-12-02
When a finish using my pen drive in Lucid there are three options that I can select (via right clicking the icon) before physically removing it. These are Unmount, Eject and Safely Remove Drive. What are the differences between these options ?

---

### Post by SeattleOtaku on 2009-12-02
Eject is supposed to be for CDs/DVDs, but perhaps sticks are also seen as removable media the same way.  On a mounted internal, I only see "Unmount"; a mounted USB-HD, only "Unmount" and "Safely remove"; and on sticks and mp3 players, all three.

Here's another thread discussing it:
[http://ubuntuforums.org/showthread.php?t=1301556](http://ubuntuforums.org/showthread.php?t=1301556)

---

### Post by Kevbert on 2009-12-03
Thanks for the link. This goes back to my question why have unmount and safely remove if they both do the same thing ?

---

### Post by wilee-nilee on 2009-12-03
Safely remove turns off the power to the USB device unmount doesn't, but either is okay to use.

---

### Post by phenest on 2009-12-03
> **wilee-nilee said:**
> Safely remove turns off the power to the USB device unmount doesn't, but either is okay to use.

That's interesting. Although I haven't tried the 'safely remove', unmount does leave the power on. My USB stick has an LED on it. I guess then, that using 'safely remove' makes more sense as I know when it's finished unmounting as the LED turns off. But I'm not sure about the wording, or if maybe, unmount should disconnect the power too. Too many options when there could be the only one appropriate option for that device.

---

### Post by Zoot7 on 2009-12-03
I think the better thing to do is umount and then safely remove or power down. Much of a muchness really.

---

### Post by phenest on 2009-12-03
> **Zoot7 said:**
> I think the better thing to do is umount and then safely remove or power down. Much of a muchness really.

And how do you do that? Once you've unmounted, the other options don't exist. This is about making it more intuitive.

3 options gives the impression of 3 actions. And if these 3 do roughly the same thing, then we only need one: unmount.

---

### Post by Grenage on 2009-12-03
It seems pretty logical to me.  *Unmount* has nothing to do with physically removing a device; *safely remove* however...

If you umount it and it kills the power, you would need to physically remove and reconnect it if you wanted to mount it again!

---

### Post by Zoot7 on 2009-12-03
> **phenest said:**
> And how do you do that? Once you've unmounted, the other options don't exist.
They're not for me in Nautilus under Karmic. I don't know about the Desktop icons.

---

### Post by ezsit on 2009-12-03
> It seems pretty logical to me. Unmount has nothing to do with physically removing a device; safely remove however...


+1

Same here, there are times when I want to unmount a device without actually removing it. For example, to format or repartition the device it would be necessary to unmount the device without ejecting it or powering it off. Unmounting, ejecting, and Safely Removing are three distinct actions with different applications and uses.

---

### Post by lewisforlife on 2009-12-03
My phone shows up as a mass storage device.  Sometimes I want to unmount the storage device without shutting off power, because I want to recharge my phone battery.  If all we had was a safely remove, I would not be able to charge my battery without the storage device being mounted.  I think it is great to have multiple choices, choices are always better.

---

### Post by Gina on 2009-12-03
> **ezsit said:**
> +1

Same here, there are times when I want to unmount a device without actually removing it. For example, to format or repartition the device it would be necessary to unmount the device without ejecting it or powering it off. Unmounting, ejecting, and Safely Removing are three distinct actions with different applications and uses.Agreed.  Though they do not all apply to everything.  Ejecting only applies to optical media (at least at present).  You can't eject a USB stick, for instance.  As I see it we have 3 main types of data storage device.  

1. Built in hard drives.  Only unmount applies to these.  

2. USB devices - USB hard drive, memory stick, memory cards etc.  All these may be unmounted to partition or format.  They may be removed so Safely Remove is useful separately.  They can't be ejected.  

3. Then there's optical media drives.  Re-writeable media may be partitioned (rarely used) or formatted for which they need unmounting.  They may be ejected, and although they are more usually ejected, they may be manually removed by pressing the button on the front so Safely Remove could apply.  So it could be said that Unmount, Eject and Safely Remove all apply to optical drives and mean totally different things.

---

### Post by lisati on 2009-12-03
> **Grenage said:**
> It seems pretty logical to me.  *Unmount* has nothing to do with physically removing a device; *safely remove* however...

I think historically there was a connection, e.g. removing a reel of tape or a disk platter from a device, and like the word "illegal" (as in "illegal instruction") the meaning isn't always too intuitive these days.

---

### Post by CarpKing on 2009-12-04
> **ezsit said:**
> Unmounting, ejecting, and Safely Removing are three distinct actions with different applications and uses.

But horribly confusing to the average user.  

Really, there should only be one right-click option.  I'm not sure if the name should change between types of media, but CDs should be ejected, hard drives unmounted, and USB media unmounted and powered down.  Special cases, such as unmounting a USB stick before formatting it, should be done automatically through the relevant tools, such as GParted.

---

### Post by Kevbert on 2009-12-04
That's right. The options should only be relevant to the media device in question.

---

### Post by ezsit on 2009-12-04
> Really, there should only be one right-click option. 

No. There should be three options since there are three different possible uses for various hardware under different circumstances. Dumbing down the UI is ridiculous when it means losing functionality. Let the new user LEARN how to use the system.

For christ's sake, next, some people will want to hide or change the Unix filesystem hierarchy because it can confuse the new user! What's next?

---

### Post by seeker5528 on 2009-12-04
As long as the 'safely remove' option insists on shutting down the device, you need the unmount option also.

If you have a card reader mounted in your case, want to take one card out and put in another, you can't use the 'safely remove' option or you won't get the device back until you reboot, unless you feel like opening the case and mucking around inside the computer.

Are there even any devices that 'safely remove' would apply to that actually need to be turned off before you unplug the device, take the disk out, or whatever? 

It seems to me if 'safely remove' stuck only to unmounting all the partitions on a device and left it at that, it would be good enough.

Later, Seeker

---

### Post by CarpKing on 2009-12-04
> **seeker5528 said:**
> As long as the 'safely remove' option insists on shutting down the device, you need the unmount option also.

If you have a card reader mounted in your case, want to take one card out and put in another, you can't use the 'safely remove' option or you won't get the device back until you reboot, unless you feel like opening the case and mucking around inside the computer.

Then "safely remove" has no place on the context menu for that device.  

> Are there even any devices that 'safely remove' would apply to that actually need to be turned off before you unplug the device, take the disk out, or whatever? 

As far as I know, the main purpose in powering off the device is so the indicator lights on USB thumb drives and such function as intended and expected (e.g. turn off when it is safe to remove the device).  There may be other applications, but I would have expected this feature earlier if there were any more important than that.

---

### Post by Gina on 2009-12-05
On my USB sticks the light is only on when they're accessed.  No data transfer - no light.

---

### Post by phenest on 2009-12-05
> **Gina said:**
> On my USB sticks the light is only on when they're accessed.  No data transfer - no light.

On mine, it's both for data transfer and power. It normally flashes, then flashes faster with data transfer, and flashes even slower when unmounted. I haven't tried 'safely remove' to see if it goes out completely, but I expect it does (as it does in Windows).

---

### Post by McDuff on 2009-12-05
> **phenest said:**
> And how do you do that? Once you've unmounted, the other options don't exist. This is about making it more intuitive.


here i still have “safely remove” after having unmounted.

---

### Post by ranch hand on 2009-12-06
You ned the safely remove option for a number of usb hard drives.  I use it quite often with my external enclosure.

---

### Post by alex2399 on 2009-12-07
> **ezsit said:**
> No. There should be three options since there are three different possible uses for various hardware under different circumstances. Dumbing down the UI is ridiculous when it means losing functionality. Let the new user LEARN how to use the system.

For christ's sake, next, some people will want to hide or change the Unix filesystem hierarchy because it can confuse the new user! What's next?

But the UI is not functional if it doesn't make any sense to the average user which is AFAIK the target group of Ubuntu. Even non-native english people know what eject is because it is on every cd-player, casette deck, DCC recorder, MD-disk, whatever. If you press eject you can see what it does, because it does something observable. It moves the tray out and you can take out the media. 

Safely remove is a slight bit harder if you are not educated in English, but to the most it makes sense. That a USB-stick does not remove itself can be seen and grasped by looking at its mechanical make-up. If you press "Safely remove" it conveys two things, that you do it safely (does not matter to the average user how it technically works, just that his data is safe) and that it can be removed afterwards by your own actions.

And now unmount, what does it do that the average user might need on his right click menu? I didn't know what it did when I started out with linux and only because I'm interested in computers and OS's do I know. Actually the meaning of mount was different for me, I knew it from a computer game where it were weapon launcher mounts. If I'd want to repartition the drive I use a program that has all this functionality and unmount it from there. It makes also more sense to me because mount is placed in the right "context". I want to partition a drive, there is an unmount option that I haven't seen before in the program I use, then it must have something to do with the functionality of partitioning. 
Though having unmount on the desktop when right clicking a USB device the average user will just go "huh?" because he doesn't know it and he doesn't have the right context to place it in.

Furthermore the less choices one has to make the better. A user wants to be productive and not have to worry about choices which in his view may be risky because he doesn't know the consequences. So less choice is better, unless it has a clear functionality to the user. 

To give you an example where too much choice can be bad. Suppose you're in supermarket A, they have two different kinds of meat, one is biological and the other industrially produced but cheaper. No further info is given. You go with one that has your preference in ethics and/or price.

Now the next day you go to supermarket B. They have abundant choice in meat. Actually 20 different choices. One is industrial, in the other the animals could walk around freely but where kept in sheds all winter, the other fed the animals with industrial food, the next one with grass, the other one with pink grass, the next one with purple grass, then again one walked with black sheep out in the field, the other one with pink sheep. The meat from the another supplier is ten months old, the other one nine months, another one eighteen months, yet another is eleven months old and walked around with pink sheep, but hey hey here is another freedom choice for you! This meat comes from animals that walked around with black and white sheep but got industrail food. But now here it comes, the meat from another supplier has gotten Ricolo food, the other Rarad food, yet another iFood, then another Unala food. (dunno if it's 20 but you get the point :P )

So how do you make the choice in this case and will you be satisfied with it? 

An analogy I'd like to make about knowing a system well enough to use it, one doesn't need to know how a car works, just that it works like you learned in driving school. You don't need to know what a Lambda sensor is, how your turbo works, what the dampening factors of your shocks are, The ARB balance, or that it uses a Linux system to regulate its fuel injection. You just want it to work like every other car. It's a tool to do a job or provide fun. And in my view an average home user-friendly computer should be the same. I know how to use a keyboard and a mouse, and I can read, but only comprehend what it does if it relates to knowledge I already have. Like eject that makes a tray go outward. And unmount does not relate to knowledge most people have about computers.

---

### Post by 23meg on 2009-12-07
> **ezsit said:**
> No. There should be three options since there are three different possible uses for various hardware under different circumstances. Dumbing down the UI is ridiculous when it means losing functionality.

A system that can work out which of the three choices apply to a specific piece of hardware, and only presents the choices that are actually meaningful for that device, is a smarter system, not a dumber one.

> **ezsit]Let the new user LEARN how to use the system.[/QUOTE]

Perpetuating unneeded sophistication is not a good way to encourage people to learn how to use the system.

[QUOTE=ezsit said:**
> For christ's sake, next, some people will want to hide or change the Unix filesystem hierarchy because it can confuse the new user! What's next?

There's really no need for a straw man to illustrate your point.

---

### Post by uBeer on 2009-12-07
Another use that wasn't mentioned (as far is I could see):

I have an USB drive with multiple partitions (always good to have a backup distribution on the disc :) ). If you unmount a partition the others will still be available (and you can still remount the unmounted partition from nautilus side bar).
If I choose Safely remove all partitions of the device will be unmounted and then I can really safely remove my device.

Very useful!

---

### Post by seeker5528 on 2009-12-07
> **ranch hand said:**
> You ned the safely remove option for a number of usb hard drives.  I use it quite often with my external enclosure.

You don't *need* the option, it's just more convenient if you have multiple partitions.

I much prefer the KDE mechanism for dealing with this. A panel plasmoid/widget/whatever they are calling them these days where the removable stuff is always shown, with an eject type of symbol if it is mounted, without an eject type symbol if it is not mounted. If you click the eject symbol, the partition is still listed and able to be mounted again. It would still be nice to have an option to unmount all the partitions on a device at once but not as big a deal because they are all listed together and you can go down the list unmounting the ones you want.

In Nautilus you would typically have places displayed on the left where you have a similar looking type of thing, but if I click the eject symbol there, I have to replug my flash drive to get it back again.

Later, Seeker

---

### Post by ezsit on 2009-12-08
> Furthermore the less choices one has to make the better.

Is this a Windows or Mac forum or a Linux forum? From your statement, I would question your knowledge of basic Linux/Unix philosophy.

> And in my view an average home user-friendly computer should be the same. 

But it ain't the same. No matter how much you want reality to conform to your whim, it will not. A computer is a highly technical piece of equipment and an operating system is a highly complex collection of software. No matter how little YOU would like to know to operate a computer and its operating system effectively, some knowledge, practice, patience, and learning IS required (Oh, but it hurts when I think!).

> Perpetuating unneeded sophistication is not a good way to encourage people to learn how to use the system.

The point is, having three choices: unmount, safely remove, and eject, is not unneeded sophistication. There is a need and use for each of these options and none of the terms are beyond comprehension for the average person IF they apply just a bare minimum of effort.

> You don't *need* the option, it's just more convenient if you have multiple partitions.

WTH!?! Is not convenience the definition of need you are applying to the "average" user who might be confused by computer terminology and multiple choices? It would be more "convenient" for the dumb user to not see confusing terms, therefore it is a need to eliminate those terms. However, when a slightly more advanced user demonstrates a "need" for multiple terms and options, you call that need a "convenience." How "convenient."

---

### Post by zekopeko on 2009-12-08
> **ezsit said:**
> Is this a Windows or Mac forum or a Linux forum? From your statement, I would question your knowledge of basic Linux/Unix philosophy.

And I would question your knowledge of basic programming philosophy. The more option you have, the more code you have. The more code you have, the more bugs you have, not to mention that it gets more difficult to maintain said code.

---

### Post by ezsit on 2009-12-08
> A user wants to be productive and not have to worry about choices which in his view may be risky because he doesn't know the consequences. So less choice is better, unless it has a clear functionality to the user. 

If this is the standard definition of a typical user, please have them buy a Windows machine. This typical user will want the comfort, convenience, and near market monopoly that ensures widespread compatibility with off-the-shelf equipment and software that Windows will provide. Please do not steer this user to Linux, any version of Linux, for they will eventually run screaming when the new video capture card or webcam they purchase a year from now does not work with their ancient (1 year old) version of Ubuntu that was installed for them by some well-intentioned friend.

---

### Post by Gina on 2009-12-08
> **ezsit said:**
> If this is the standard definition of a typical user, please have them buy a Windows machine. This typical user will want the comfort, convenience, and near market monopoly that ensures widespread compatibility with off-the-shelf equipment and software that Windows will provide. Please do not steer this user to Linux, any version of Linux, for they will eventually run screaming when the new video capture card or webcam they purchase a year from now does not work with their ancient (1 year old) version of Ubuntu that was installed for them by some well-intentioned friend.Well said there!!  My thoughts  entirely :)

---

### Post by Merk42 on 2009-12-08
> **ezsit said:**
> If this is the standard definition of a typical user, please have them buy a Windows machine. This typical user will want the comfort, convenience, and near market monopoly that ensures widespread compatibility with off-the-shelf equipment and software that Windows will provide. Please do not steer this user to Linux, any version of Linux, for they will eventually run screaming when the new video capture card or webcam they purchase a year from now does not work with their ancient (1 year old) version of Ubuntu that was installed for them by some well-intentioned friend.

So, Linux is supposed to be broken :confused:

---

### Post by ranch hand on 2009-12-08
> **Gina said:**
> Well said there!!  My thoughts  entirely :)
Me too.

---

### Post by Kevbert on 2009-12-09
> **Merk42 said:**
> So, Linux is supposed to be broken :confused:

New builds of linux will have bugs prior to release. Lucid is not even in Alpha build until tomorrow.
A blanket statement to say that Linux won't work with any capture card or webcam is wrong and also that Windows will work with all cards and webcams is also wrong.
We're wandering off topic here...

---

### Post by Merk42 on 2009-12-09
> **Kevbert said:**
> We're wandering off topic here...

Well still confused, but this much I agree with.

---

### Post by phenest on 2009-12-09
> **ezsit said:**
> If this is the standard definition of a typical user, please have them buy a Windows machine. This typical user will want the comfort, convenience, and near market monopoly that ensures widespread compatibility with off-the-shelf equipment and software that Windows will provide. Please do not steer this user to Linux, any version of Linux, for they will eventually run screaming when the new video capture card or webcam they purchase a year from now does not work with their ancient (1 year old) version of Ubuntu that was installed for them by some well-intentioned friend.

I take it you are using Linux via a terminal? I mean, a graphical environment is for Windows users. Did you build your own kernel?

As complex as computers are, they are there to make life easier, so what's wrong in making Linux easier to use for less able users. After all, if you want more choice you can always add it yourself.

As a developer myself, I have to agree with 23meg and zekopeko. It needs to be smarter, and less code means less bugs.

---

### Post by scaine on 2009-12-09
Personally pretty surprised that **ezsit **even uses Gnome.  Sounds like a terminal fanboy to me.

There's nothing wrong in making a GUI more intuitive.  It constantly amazes me how many people use Gnome and still have attitudes like this.  Gnome is the epitome of dumbing things down to make them more intuitive.

---

### Post by seeker5528 on 2009-12-09
> **ezsit said:**
> 
WTH!?! Is not convenience the definition of need you are applying to the "average" user who might be confused by computer terminology and multiple choices? It would be more "convenient" for the dumb user to not see confusing terms, therefore it is a need to eliminate those terms. However, when a slightly more advanced user demonstrates a "need" for multiple terms and options, you call that need a "convenience." How "convenient."

But in the current form of the 'safely remove' option, it is only more convenient if you don't want to use the device again until you reboot/replug, so the convenience is limited where if it didn't turn off the device it would be more convenient all the time.

How many partitions are you actually going to have on an external device?

If you look at the KDE solution you see if the solution is always present on the panel, makes it's self obvious when you plug in and external device, makes it quick and easy to unmount all the partitions on a device at any time no matter what else you have running and later you can mount them again just as easily.

Overall the KDE solution is more convenient to me, but in particular, for my personal usage, since my desk space is limited and I have to tuck my external drives away from me somewhere, the inconvenience of having to get up and mess with a USB or power switch/cable with the Gnome solution is much greater than the inconvenience of having 1 extra click for each partition with the KDE solution.

With the KDE solution it could be viewed as an inconvenience that when you click on a listed partition to mount it, it always starts the file manager or a minor annoyance that it always claims Dolphin will be started even though as an example in my case I have Nautilus set as the default file manager and so Nautilus is what actually gets started. 

Later, Seeker

---

### Post by 23meg on 2009-12-09
[QUOTE=ezsit]The point is, having three choices: unmount, safely remove, and eject, is not unneeded sophistication. There is a need and use for each of these options and none of the terms are beyond comprehension for the average person IF they apply just a bare minimum of effort.[/QUOTE]

There may be a need for *some* of the current options, in *some* use scenarios. That doesn't necessarily mean that displaying *all* three options in *all* cases is good behaviour, or even that listing options in a right-click context menu is good design. 

That there is a clear technical distinction between the different commands does not mean that this distinction needs to be used all the time, and thus displayed all the time. If it presents unneeded sophistication for a substantial amount of users (hint: usability testing is needed here), it's time for redesign in any case, and such a redesign would have to be done with the typical mental models of users when operating removable media in mind, rather than being based entirely on the technical implementation model, as is the case right now.

[QUOTE=ezsit]If this is the standard definition of a typical user, please have them buy a Windows machine. This typical user will want the comfort, convenience, and near market monopoly that ensures widespread compatibility with off-the-shelf equipment and software that Windows will provide. Please do not steer this user to Linux, any version of Linux, for they will eventually run screaming when the new video capture card or webcam they purchase a year from now does not work with their ancient (1 year old) version of Ubuntu that was installed for them by some well-intentioned friend.[/QUOTE]

I use computers for highly technical non-typical tasks, including programming computers themselves, and I fit in that definition. Almost every other experienced technical user I know, including developers and designers, also does. The belief that "new users need simplicity, and advanced users need complexity" is a false dichotomy. It's not necessarily new and technically inept users who are intimidated when presented with redundant choices and needless sophistication that does not help them in accomplishing their goals.

There's an orthodoxy formed around the idea that if an operating system consists of free software, and happens to use the Linux kernel, it must be sophisticated, riddled with options and choices to the greatest extent possible, and *necessarily require* its user to learn (rather than facilitating learning to whatever depth they desire) about its internals. Ubuntu's very reason of existence is opposed to that orthodoxy, thus people who side with it will likely have very frequent problems with different aspects of Ubuntu's design and policies.

---

### Post by ranch hand on 2009-12-09
You know, I have seen all three of these choices and use all three.  I have never really looked t osee what the options were because I know what I want.

Reading this thread got me to wondering about what just does come up.

I can't, for the life of me, figure out how to get all three at once.

If I right click on a DVD (movie), by itself I get teh option to "unmount" or "eject".

If I right click on a mounted partition I get the option to "safely remove drive" or "unmount".

If I highlight both the above I get the option to "unmount".

If I click on all of the mounted partitions I get the option to "unmount".

I really fail to see what we are bickering about here.  This does not seem tough to understand (I didn't think it could be or I would be confused).

---

### Post by Merk42 on 2009-12-09
I'm guessing the one situation you posted where the options were "Unmount or Safely Remove".

Tell me (anyone here not just Ranch Hand).  If you have something physically removable, like a CD, or in the case of the title, USB Drive, why would you want to unmount it but not physically remove it?

I know unmount let's you remount without physically touching the media, but why unmount it in the first place then?

---

### Post by Reiger on 2009-12-09
Question: was the device that triggers 3 actions by any chance a flash device which is also supposed to be able to autostart applications? (E.g. an U3 device?)

The U3 at least pretends to be a CD drive *as well* as an generic removable USB-device. It does this so you can use the Windows auto-start feature; which is of course useless on Linux ... :P

As far as the other two options go... I am not sure: on the one hand I like the idea of a quick-access Unmount option but on the other I do not find myself formatting USB kit all that often. I dunno but I think Gparted and the like can unmount these devices for you anyway...

---

### Post by VMC on 2009-12-09
> **Merk42 said:**
> I'm guessing the one situation you posted where the options were "Unmount or Safely Remove".

Tell me (anyone here not just Ranch Hand).  If you have something physically removable, like a CD, or in the case of the title, USB Drive, why would you want to unmount it but not physically remove it?

I know unmount let's you remount without physically touching the media, but why unmount it in the first place then?

I know some programs require a device to be unmounted in order to be written to. I ran across this as device busy.

---

### Post by phenest on 2009-12-10
> **Merk42 said:**
> I'm guessing the one situation you posted where the options were "Unmount or Safely Remove".

Tell me (anyone here not just Ranch Hand).  If you have something physically removable, like a CD, or in the case of the title, USB Drive, why would you want to unmount it but not physically remove it?

I know unmount let's you remount without physically touching the media, but why unmount it in the first place then?

Damn! You got me. I think it's true for every time time I have unmounted a device, I have also removed it too.

It is true for removable media, that having 'Unmount' amongst the options is somewhat superfluous. Perhaps this could be an option that could be hidden/shown in the same way as 'Delete' in Nautilus.

---

### Post by phenest on 2009-12-10
> **VMC said:**
> I know some programs require a device to be unmounted in order to be written to. I ran across this as device busy.

Which programs and why? Shouldn't those programs be doing the unmounting if that's the case?

---

### Post by ranch hand on 2009-12-10
If you have several partitions that have OS' on them and you go to install, the LiveCD partitioner will not work.  You need to unmount the mounted partitions first.  Removing them is not an option as they are on the drive that you are installing on.

---

### Post by blur xc on 2009-12-10
> **Merk42 said:**
> I'm guessing the one situation you posted where the options were "Unmount or Safely Remove".

Tell me (anyone here not just Ranch Hand).  If you have something physically removable, like a CD, or in the case of the title, USB Drive, why would you want to unmount it but not physically remove it?

I know unmount let's you remount without physically touching the media, but why unmount it in the first place then?

You have to unmount a drive to do any kind of disk management (such as using Gparted, etc)...  So, in that case, it's easy to umount /mount/disk (or whatver) do your work and remount it when you are done.  

Personally, I use the command line.  umount it, then enter the mount command to list all mounted partitions, verify the device as unmounted, and then remove it.  I don't trust the gui.  It's too ambigous.

Now, I'll admit I didn't read every word of every post, and it's pretty clear that half of the people slinging poo in this thread haven't either, but I didn't see any real response on what to do in the case of the internal usb card reader.  

I have a multi card reader in my case.  If I safely remove my compact flash card, rather than unmounting, I will need to reboot my computer before I can insert another memory card to transfer photos to the pc?  If that is true- that's an utterly useless option.  Is there any danger in removign an unmounted usb device that is still powered (unmounted, not safely removed)?  And as a beginning command line junkie- how do you safely remove from the command line?  Can you re-power a usb device (ie. internal card reader) from the command line (and not sudo reboot either)?

Thanks,
BM

---

### Post by Merk42 on 2009-12-10
> **ranch hand said:**
> If you have several partitions that have OS' on them and you go to install, the LiveCD partitioner will not work.  You need to unmount the mounted partitions first.  Removing them is not an option as they are on the drive that you are installing on.

Sounds more like a bug with the LiveCD Partioner. Isn't that scenario unmounting internal devices anyway though?

---

### Post by zekopeko on 2009-12-10
> **blur xc said:**
> You have to unmount a drive to do any kind of disk management (such as using Gparted, etc)...  So, in that case, it's easy to umount /mount/disk (or whatver) do your work and remount it when you are done.  

Personally, I use the command line.  umount it, then enter the mount command to list all mounted partitions, verify the device as unmounted, and then remove it.  I don't trust the gui.  It's too ambigous.

That's a bug on the Gparted,etc.. side. Disk management tools should do the whole unmounting thing for you.

> Now, I'll admit I didn't read every word of every post, and it's pretty clear that half of the people slinging poo in this thread haven't either, but I didn't see any real response on what to do in the case of the internal usb card reader.  

I have a multi card reader in my case.  If I safely remove my compact flash card, rather than unmounting, I will need to reboot my computer before I can insert another memory card to transfer photos to the pc?  If that is true- that's an utterly useless option.  Is there any danger in removign an unmounted usb device that is still powered (unmounted, not safely removed)?  And as a beginning command line junkie- how do you safely remove from the command line?  Can you re-power a usb device (ie. internal card reader) from the command line (and not sudo reboot either)?

Thanks,
BM

I don't fully understand this part. If you can't re-insert a new compact card etc. without rebooting then that's a bug. You should be able to to it.

As I see it, either have only Unmount or Safely Remove or Eject. Anything that isn't and internal disk shouldn't appear in the nautilus sidebar when unmounted.

USB drives, sticks, cameras etc. are removable storage and once you eject/umount them you have to physically reconnect them to register. If you do unmount/eject them the kernel should shut down the device if possible.
For more fine-grained control you have the command line.

---

### Post by seeker5528 on 2009-12-10
> **zekopeko said:**
> As I see it, either have only Unmount or Safely Remove or Eject.

Optimally it would be nice if the burning software would handle mounting/unmounting CDs/DVDs and disable automounting of optical devices while there is a burn and verify in progress, but since they haven't seemed to be able to figure that out yet, you need the option to unmount because it's not very reliable to format/wipe a rewritable DVD/CD or verify a burn if the disk is mounted.

Also not really sure you want to have the CD/DVD mounted if you want to do:

```
dd if=/dev/cdrom of=some.iso
``` 

On the card reader question, I have not seen any card readers that have an on/off switch and they have to be powered to sense when the card has been removed/inserted so if you have used the 'safely remove' option, causing the device to power down, it's a brick until it gets re-plugged or the system is rebooted, it's the same in Windows.

According the [this]( http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&dlc=en&cc=us&docname=bph07910#N989) in Windows you should use eject to signal Windows to stop accessing the card, looks like the eject option is what you want to use in Linux too based on [this]( https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/461795).

[sarcasm]
Nice how this stuff is so obviously intuitive to the casual observer. :-|:-|:-|
[/sarcasm]

Later, Seeker

---

### Post by zekopeko on 2009-12-10
> **seeker5528 said:**
> Optimally it would be nice if the burning software would handle mounting/unmounting CDs/DVDs and disable automounting of optical devices while there is a burn and verify in progress, but since they haven't seemed to be able to figure that out yet, you need the option to unmount because it's not very reliable to format/wipe a rewritable DVD/CD or verify a burn if the disk is mounted.

That's a burning app' bug. They should fix it.

> Also not really sure you want to have the CD/DVD mounted if you want to do:

```
dd if=/dev/cdrom of=some.iso
``` 

You are going to do that from the command line so nothing is stopping you to do "sudo unmount /media/cdrom".
I would even say that dd should auto-unmount before doing that. No reason for not having user friendly CLI tools.    

> On the card reader question, I have not seen any card readers that have an on/off switch and they have to be powered to sense when the card has been removed/inserted so if you have used the 'safely remove' option, causing the device to power down, it's a brick until it gets re-plugged or the system is rebooted, it's the same in Windows.

According the [this]( http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&dlc=en&cc=us&docname=bph07910#N989) in Windows you should use eject to signal Windows to stop accessing the card, looks like the eject option is what you want to use in Linux too based on [this]( https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/461795).

[sarcasm]
Nice how this stuff is so obviously intuitive to the casual observer. :-|:-|:-|
[/sarcasm]

Later, Seeker

This is just stupid. I guess that the reader should know when it has a card in it and power on.

---

### Post by seeker5528 on 2009-12-11
> **zekopeko said:**
> That's a burning app' bug. They should fix it.

In the case of not unmounting rewritable optical media, I would agree that this should be fixed in the burning applications.

For the verification part, even if it doesn't cause a problem it's annoying when the disk gets ejected and pulled back in, in between the burning and verification stages and something else pops up as a result, there should to be a more co-ordinated plan, the burning applications aren't the only ones that could benefit from having a standardized method for suppressing the automated response to the insertion of removable media.

If there is a standardized way, it doesn't seem to have gotten much traction so far.

Later, Seeker

---

### Post by Gina on 2009-12-11
I've always thought it daft to eject and immediately reload a CD/DVD in the act of burning!  With a laptop you have to reload the disc manually as the drive doesn't have a load/eject motor.  This means the process can no longer run unattended throughout.  Would it really take so much effort to sort out these annoying "features"?! :(

---

### Post by phenest on 2009-12-11
> **Gina said:**
> I've always thought it daft to eject and immediately reload a CD/DVD in the act of burning!  With a laptop you have to reload the disc manually as the drive doesn't have a load/eject motor.  This means the process can no longer run unattended throughout.  Would it really take so much effort to sort out these annoying "features"?! :(

Annoying to you maybe, whereas I have a slot drive on my laptop so it can reload it after ejecting.

---

### Post by Gina on 2009-12-11
> **phenest said:**
> Annoying to you maybe, whereas I have a slot drive on my laptop so it can reload it after ejecting.Fair enough, but is there some reason why the disc is ejected and reloaded by the burning app?  I don't use my laptop to burn as it's only a CD burner (though DVD reader).  I do all burning on a desktop.  It's not a problem but just seems unnecessary.

---

### Post by blur xc on 2009-12-11
> **zekopeko said:**
> This is just stupid. I guess that the reader should know when it has a card in it and power on.

How, if the usb port it's plugged in to is powered down?  And the usb port is on the motherboard- only accessible by opening up the case.  Hardly convienent.  As long as my computer is on- the menacing blue led on the front of my card reader stays lit.  It blinks when data is transferring, but stays lit the whole time.  If it's powered down (light is out) how can it sense when a card has been isnerted?

Still some of my questions are unanswered.  I know how to unmount from the command line- how do you eject and safely remove?  Also, once you safely remove a device, is there a way to power it back up from the command line w/o having the unplug/replug the device?  Is there any harm in removing a usb device (flash drive, hard drive, etc..) that's unmounted but not safely removed.

thanks,
BM

---

### Post by zekopeko on 2009-12-11
> **blur xc said:**
> How, if the usb port it's plugged in to is powered down?  And the usb port is on the motherboard- only accessible by opening up the case.  Hardly convienent.  As long as my computer is on- the menacing blue led on the front of my card reader stays lit.  It blinks when data is transferring, but stays lit the whole time.  If it's powered down (light is out) how can it sense when a card has been isnerted?

I'm no tech guru but I don't see why they couldn't have a sensor in the card reader that would be triggered when something blocks it e.g. a card.
IMO those are all hardware problems and shouldn't be dealt by the kernel. Shutting down (and powering up) a card reader is power management issue which would ideally be resolved in hardware.

> Still some of my questions are unanswered.  I know how to unmount from the command line- how do you eject and safely remove?  Also, once you safely remove a device, is there a way to power it back up from the command line w/o having the unplug/replug the device?  Is there any harm in removing a usb device (flash drive, hard drive, etc..) that's unmounted but not safely removed.

thanks,
BM

I remember in 6.06 that when you put files on a USB stick and the clicked eject it would still have to write them to it. That's good for the USB since it creates a more efficient file layout thereby lowering where and tear since USB' had a low number of read/write cycles before they got unreliable (this days it's in the millions so it would take you years of read/write operations to do some damage to it).

But it takes time so the current default is sync, that is, write immediately when I copy the file on the stick.
I think that once you unmount it's save to remove it (there is a little window pop up if it isn't ready that says to wait until it completes whatever it has to do).

Ideally you could un-plug anything without any problems but there are some limitations to buffers, filesystem on the stick etc, so for the time being it's prudent to have an eject button next to all removable media.

---

### Post by seeker5528 on 2009-12-11
> **Gina said:**
> I've always thought it daft to eject and immediately reload a CD/DVD in the act of burning!

In K3B they tried it for a while without ejecting in between and later started doing it again, I don't remember seeing the reason why, but I'm pretty sure it's a reliability thing.

In Windows I've seen some cases where the disk doesn't show up correctly until you eject and re-insert it. not sure how big of an issue that is in Linux, the main thing in Linux would probably be that if you don't eject and re-insert it everything may seem fine and the verification may pass, but then after you eject and re-insert it you discover there are problems with it.

> **blur xc said:**
> Still some of my questions are unanswered.  I know how to unmount from the command line- how do you eject and safely remove?

Don't know about safely remove, but there is an eject command.

```
eject /media/whatever
eject /dev/whatever

```

I tried eject from the command line with my flash drive a few times and it did unmount every time, but outside of that it seems unreliable in regard to if it could be remounted and for how long before it goes into suspend mode or whatever happens to it. Maybe it works more consistently for the card readers?

> Is there any harm in removing a usb device (flash drive, hard drive, etc..) that's unmounted but not safely removed.

For flash drives and hard drives I have not seen anything to indicate that this is a problem. I unplug mine all the time with it only being unmounted without giving it a second thought.

Unplugging the card reader also should not be a problem, if it is external. What the risks are of yanking the card out of the card reader is less clear. The link in my earlier post implied there was a risk of damage, but it is non-technical information so it may be talking physical damage to the card or they may just say that because of the risk of filesystem damage if there is activity when the card is yanked out.

Later, Seeker

---

### Post by mc4man on 2009-12-11
> Fair enough, but is there some reason why the disc is ejected and reloaded by the burning app

I believe the main reason is to clear the cache on the cd/dvdrom device which may interfere with verification if not done on some drives.

---

### Post by Gina on 2009-12-12
USB was designed with the idea of it being "hot pluggable".  In other words safe to plug and unplug without powering down.  But if you unplug while there is data flow you'll corrupt the data.  Unmounting will ensure that any data waiting to be written will be written - just wait for the light to stop flashing before unplugging.

---

### Post by zekopeko on 2009-12-12
> **Gina said:**
> USB was designed with the idea of it being "hot pluggable".  In other words safe to plug and unplug without powering down.  But if you unplug while there is data flow you'll corrupt the data.  Unmounting will ensure that any data waiting to be written will be written - just wait for the light to stop flashing before unplugging.

You're right. This has more to do with data safety than potential hardware damage.

---

### Post by phenest on 2009-12-12
> **mc4man said:**
> I believe the main reason is to clear the cache on the cd/dvdrom device which may interfere with verification if not done on some drives.

Yeah, I believe this is more to do with how the hardware works rather than software.

> **Gina said:**
> Unmounting will ensure that any data waiting to be written will be written - just wait for the light to stop flashing before unplugging.

The light won't stop flashing if you just unmount. It will, however, flash slower when there's no data flow.

---

### Post by Gina on 2009-12-12
> **phenest said:**
> The light won't stop flashing if you just unmount. It will, however, flash slower when there's no data flow.I guess some USB sticks are different - all mine (4 at present) stop flashing when data flow stops.

---

### Post by blur xc on 2009-12-12
> **seeker5528 said:**
> In K3B they tried it for a while without ejecting in between and later started doing it again, I don't remember seeing the reason why, but I'm pretty sure it's a reliability thing.

In Windows I've seen some cases where the disk doesn't show up correctly until you eject and re-insert it. not sure how big of an issue that is in Linux, the main thing in Linux would probably be that if you don't eject and re-insert it everything may seem fine and the verification may pass, but then after you eject and re-insert it you discover there are problems with it.



Don't know about safely remove, but there is an eject command.

```
eject /media/whatever
eject /dev/whatever

```I tried eject from the command line with my flash drive a few times and it did unmount every time, but outside of that it seems unreliable in regard to if it could be remounted and for how long before it goes into suspend mode or whatever happens to it. Maybe it works more consistently for the card readers?



For flash drives and hard drives I have not seen anything to indicate that this is a problem. I unplug mine all the time with it only being unmounted without giving it a second thought.

Unplugging the card reader also should not be a problem, if it is external. What the risks are of yanking the card out of the card reader is less clear. The link in my earlier post implied there was a risk of damage, but it is non-technical information so it may be talking physical damage to the card or they may just say that because of the risk of filesystem damage if there is activity when the card is yanked out.

Later, Seeker

I've ran into a few issues w/ removing usb devices that weren't unmounted.  In several cases, I couldn't reinsert the device.  Ubuntu would not recognize that it was isntalled.  Also, unmounting wouldn't work, but it still showed as mounted.  then, upon logging out or switching users, I have lost ALL usb ports, including the keyboard and mouse.  At that time I would have to do a hard reset.  It's all I could think of.  I did not try a ps/2 keyboard or mouse though.  It's been a while since I've had that happen, and don't remember the exact details.

Thanks for you reply.  Seems pretty straitforward- eject command to eject cd's..

BM

---

### Post by seeker5528 on 2009-12-13
> **blur xc said:**
> I've ran into a few issues w/ removing usb devices that weren't unmounted.  In several cases, I couldn't reinsert the device.  Ubuntu would not recognize that it was isntalled.  Also, unmounting wouldn't work, but it still showed as mounted.  then, upon logging out or switching users, I have lost ALL usb ports, including the keyboard and mouse.  At that time I would have to do a hard reset.  It's all I could think of.  I did not try a ps/2 keyboard or mouse though.  It's been a while since I've had that happen, and don't remember the exact details.

Losing all the ports sounds like a flaky USB controller to me, but for the rest of the stuff, if you unplug without unmounting first all bets are off.

PS/2 ports are not designed for hot plugging so plugging or unplugging things to the PS/2 ports does include some risk. 

Typically if you hit the power button Ubuntu should recognize it and do an orderly shutdown, unless you had to disable ACPI or the ACPI stuff is not working as expected for some reason.

Later, Seeker

---

### Post by blur xc on 2009-12-13
> **seeker5528 said:**
> Typically if you hit the power button Ubuntu should recognize it and do an orderly shutdown, unless you had to disable ACPI or the ACPI stuff is not working as expected for some reason.

Later, Seeker

How do I check this?  I don't think my system is working like this?

Thanks,
BM

---

### Post by seeker5528 on 2009-12-14
> **blur xc said:**
> How do I check this?  I don't think my system is working like this?

Not completely sure, but I think if '/sys/bus/acpi/' exists and:

```
ps -C acpid
```

returns a PID, then theoretically the basic support should be there and working.

In Gnome in power management options, there is setting for the power button, that has options 'Ask Me', 'Hibernate', 'Shutdown', of course, if it is set to 'Ask Me' it doesn't do much for you if your keyboard and mouse stop working.

There may be an option in the BIOS for it as well.

If you hit the key combination 'Ctrl+Alt+F1' and log in on the VT, there should be some output on the screen when you hit the power button.

Later, Seeker

---

### Post by seeker5528 on 2009-12-18
I found my way to [ejecter](http://packages.ubuntu.com/lucid/ejecter), it doesn't change anything relative to the complaints that have been expressed in this thread and I don't know what it's behavior is with card readers or external hard drives with multiple partitions relative to the unmount versus safely remove question it only provides a single eject button that doesn't give you a choice of action.

For my personal use, since I normally use a flash drives or external hard drives that only have a single partition, it gives me one part of what I like about the removable media applet in KDE, it would be nice if I could click on a listing and have it open my default file manager, but since you have the places menu it's not all that critical.

It appears that it isn't run automatically when installed, but is added somewhere to the list of applications to start, which must be Gnome specific since I don't see a .desktop file for it in '/usr/share/autostart' or '/usr/share/gnome/autostart', anyhow it should start at the next login.

Later, Seeker

---

### Post by phillw on 2009-12-19
As previously mentioned..

I use Safely Remove for USB sticks (and hard drives) - I guess I could use Eject.
Eject For CD's / DVD's

I'd only use unmount if, as noted earlier, I wanted to unmount a partition to do some work on it.

Phill.

---


---
title: "What can i do about the lack of auto arrange in desktop?"
date: 2010-02-28
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by aviramof on 2010-02-28
you might not have noticed it but every time you download files or create shortcut and etc on desktop the files go one on top of the other and you need to clean by name to fix it. 

now i don't know why no one have noticed it till now because i had the same problem in ubuntu 8.10 or maybe this problem only effect right to left languges i use hebrew. 

any way i still have not manage to find a solution to this problem the option keep align doesn't seem to do anything about it and i would like to see the same arrange items option
that exist inside my computer in files and folders on the right click menu of the desktop how can i do that?

and by the way how can i add tamplates of what ever it's called to create documents right click option on desktop?

thanks in advance.

---

### Post by zarthon on 2010-02-28
Create a new user on your comptuer then login as the new user and see if it has the same problem with the desktop icons. If it does not then you may want to consider ditching your settings files.
:KS
I am not sure where those settings are stored. I may research it if know one reading the thread just knows and throws it up.

---

### Post by aviramof on 2010-02-28
i don't need to create a new user i know thet this problem existed from day one and beside i'v only installed ubuntu again only a few days ago and it's not limited to lucid i had it in 8.10 and i guess 9.04 and 9.10 but i dind't stayed with the last two version long enaf to check them too much.
 
as a windows user i have noticed it almost immediatly that and other things that i was used to in windows and i don't have in ubuntu but the lack of auto arrange in desktop is one the of the things i miss most i mean why do i need all this desktop if all the files i download goes one on top of the other?
 
do you know what i mean?
 
by the whey when you download files to the desktop are they automaticly arrange them self one after the other?or like me one on top of the other?

if you would take a close look at the attacment you would see that there is more then one file there.

---

### Post by kansasnoob on 2010-02-28
I had noticed that at one time but it's OK now. I was less concerned about that than some other things but I have fiddled around a lot and removed things from my home folder like .nautilus, .gconf, .gnome, etc.

What I do is create a Projects folder first, copy those folders there, then delete those folders and reboot. If that doesn't work I then just send the newest folders to the trash and copy-n-paste the original folders back where they belong if it doesn't work out.

Clear as mud?

---

### Post by aviramof on 2010-02-28
i'm not sure that i understand what you mean but any way that's not the point of course i can create a folder on desktop put everything there then arrange it how i like the problem
is say i download several files at once they all go one on top of the other then i need to clean by name or drag them one by one before i can use them or move them to other places and etc. 

take a look at the picture i uploaded earlier it's a bit difficult to see because of the similer file names but there are four url links there to this thread one on top of the other.

and i don't want to remove nautilus i see that it's possible to do it i think that nautilus should be fixed that all.

---

### Post by joshd2189 on 2010-02-28
try this:

press alt-f2 and run gconf-editor
expand to /apps/nautilus/desktop-metadata/directory/
set icon_view_keep_aligned = true

---

### Post by aviramof on 2010-02-28
it's already like this and i'v also ticked the v in right click menu. 

maybe because i use RTL and not LTR meaning the icons are on the right side of the
screen and not the left side keep align don't work so well if i untick it then drag the files
then then tick it again it move them slightly to the left and that it.

if i untick it then put files one on the top of the other then it arrange the files properly 
but if i don't untick and tick again it doesn't do anything on he's own.

it's a bit difficult to explaine it but i guess it align them according to an invisible grid no matter where  
the file is so it doesn't arrange them one file after the other and that why i need auto arrange  first.

here is a better picture:

---

### Post by aviramof on 2010-03-04
anyone?

it's really is annoying every time i delete something from desktop i need to clean by name to rearrange the icons.

---

### Post by dino99 on 2010-03-04
> **aviramof said:**
> anyone?

it's really is annoying every time i delete something from desktop i need to clean by name to rearrange the icons.

Most of devs never come here to know about your wishes, so report on Launchpad or better on brainstorm, that's the good place.

---

### Post by aviramof on 2010-03-04
i already did but to be honest i'm starting to think that the developers are not really trying to fix things like that or add new features so easily and it's not good at all.

---

### Post by cyberkilla on 2010-03-04
> **aviramof said:**
> i already did but to be honest i'm starting to think that the developers are not really trying to fix things like that or add new features so easily and it's not good at all.

Auto-arrange works for me.

However, I agree that it could be a little more substantial. You can only clean up by name. It would be cool to clean up by type, date, size..

Actually, it's odd that they don't let you do it, because it is just another nautilus window. If you use globalmenu, you can access the menu bar for the desktop! It *may* just be as simple as adding it to the context menu, because the functionality appears to exist already.

Then again, this is all speculation:D

---

### Post by Polniy on 2010-03-04
> **aviramof said:**
> you might not have noticed it but every time you download files or create shortcut and etc on desktop the files go one on top of the other and you need to clean by name to fix it. 

now i don't know why no one have noticed it till now because i had the same problem in ubuntu 8.10 or maybe this problem only effect right to left languges i use hebrew. 

any way i still have not manage to find a solution to this problem the option keep align doesn't seem to do anything about it and i would like to see the same arrange items option
that exist inside my computer in files and folders on the right click menu of the desktop how can i do that?

and by the way how can i add tamplates of what ever it's called to create documents right click option on desktop?

thanks in advance.
It could be an issue, but using Desktop as a laucnher pane or as regular file storage is a nonsense. The right place for launchers is the top panel, desktop is only temporary file storage place.

---

### Post by philinux on 2010-03-04
I'm not seeing this behaviour at all.

---

### Post by wilee-nilee on 2010-03-04
If you have things download to a specific place beyond the desktop like home or downloads things are not piled on each other.

---

### Post by aviramof on 2010-03-04
> **philinux said:**
> I'm not seeing this behaviour at all.

Maybe it's because i use ubuntu in hebrew meaing RTL not LTR and wilee-nilee 

things don't pile up because of lack of room the auto arrange simply don't work so 

everything is going to the excat same place.

and unfortuanally not all software have .desktop file for top panel so it easier to create shortcut on desktop then remember 

commands or adding applications manually to top panel.

and it not just when downloading things even when i delete files from desktop i need to clean by name to rearange the icons.

---

### Post by philinux on 2010-03-04
> **aviramof said:**
> Maybe it's because i use ubuntu in hebrew meaing RTL not LTR and wilee-nilee 

things don't pile up because of lack of room the auto arrange simply don't work so 

everything is going to the excat same place.

Hows about changing your download destination in firefox from the Desktop to Downloads. Then just Places>Downloads and there you are, neat and tidy.

---

### Post by cariboo on 2010-03-04
By default since Karmic downloads have gone to ~/Downloads, the op may have changed the download location to the desktop.

---

### Post by philinux on 2010-03-04
> **cariboo907 said:**
> By default since Karmic downloads have gone to ~/Downloads, the op may have changed the download location to the desktop.

Thats what I was thinking.

---

### Post by aviramof on 2010-03-04
it's not a matter of downloads it's more then this is shortcuts to web sites it deleteing files from desktop and they don't auto arrange them self there is simply no auto arrange at all on desktop it's like it's on manual and there is no way to change it.

even create new document create it in the middle of the desktop and not at the right side of the screen below the last file there.

and i changed it to desktop not the op.

and it's not on manual not on places-desktop any way.

and it would have been very nice to have the arrange items in desktop right click menu any way.

---

### Post by aysiu on 2010-03-04
Vote it up on Brainstorm:
[Idea #14352: Auto Re-arrange Desktop Icons](http://brainstorm.ubuntu.com/ideatorrent/idea/14352)

Manually having to "clean up" each time is annoying.

---

### Post by Merk42 on 2010-03-04
> **aviramof said:**
> and i changed it to desktop not the op.


... you **are** the OP.
OP = Original Poster (or Original Post)


Something to keep in mind, GNOME plans to eliminate the ability to have icons of any sort on the Desktop in GNOME Shell.


EDIT: I'll put there here too since the last post of a page often gets lost
> **aysiu said:**
> Vote it up on Brainstorm:
[Idea #14352: Auto Re-arrange Desktop Icons](http://brainstorm.ubuntu.com/ideatorrent/idea/14352)

Manually having to "clean up" each time is annoying.

---

### Post by aviramof on 2010-03-04
i think that 128 votes should have been enaf so far but i guess the developers don't really care about this thing other wise this problem and others 

like no option in display to choose main or secondery screen or add url support would have been solved long before i even installed ubuntu.

---

### Post by aysiu on 2010-03-04
> **aviramof said:**
> i think that 128 votes should have been enaf so far What are you basing that judgment on? [The most popular Brainstorm ideas](http://brainstorm.ubuntu.com/most_popular_ever/) all have thousands of votes.

---

### Post by cyberkilla on 2010-03-04
> **philinux said:**
> Thats what I was thinking.

In my case, I've just been through one upgrade to the next - I don't have a Downloads folder. Perhaps the OP has a similar reason.

---

### Post by aysiu on 2010-03-04
> **cyberkilla said:**
> In my case, I've just been through one upgrade to the next - I don't have a Downloads folder. Perhaps the OP has a similar reason.
It really shouldn't matter. If people choose to save downloads to the desktop, why should Gnome *by default* pile the new file and device icons on top of each other. Is that part of [the Gnome Human Interface Guidelines](http://library.gnome.org/devel/hig-book/stable/)?

---

### Post by cyberkilla on 2010-03-04
> **aysiu said:**
> It really shouldn't matter. If people choose to save downloads to the desktop, why should Gnome *by default* pile the new file and device icons on top of each other. Is that part of [the Gnome Human Interface Guidelines](http://library.gnome.org/devel/hig-book/stable/)?

It DOESN'T do that for me, so it might be a bug because of him using RTL. Is someone having this issue with LTR alignment too?

Perhaps Nautilus doesn't like you.;)

---

### Post by katie-xx on 2010-03-04
> **aviramof said:**
> 
it's really is annoying every time i delete something from desktop i need to clean by name to rearrange the icons.
[SIZE=2]
Im struggling to understand what you mean. Could you maybe try describing problem differently?  
I will try to replicate once I understand your problem.

Kate[/SIZE]

---

### Post by aviramof on 2010-03-04
it's very simple there is no auto arrange on desktop what it's mean is that if i download several files to desktop they want result one file after the other they would simply be one on top of the other at the top right corner of the screen i'v uploaded pictures in this thread look them up the same goes for 
deleting files the other files stay where they are they don't move to fill the gap like when there is auto arrange. 

it's like the option manual in say the home folder right click menu arrange items the desktop doesn't automatily arrange the icons acroding to name or anything eles.

basicly the desktop don't do anything except keep align which means arrange the icons according to an invisible grid i guess but they stay at the excet same place.

here is a picture:

[http://img7.imageshack.us/img7/6673/46089394.png](http://img7.imageshack.us/img7/6673/46089394.png)

see the gaps i created?if there was auto arrange it would not have let me to do this it would have automatily closed the gaps and arrange them closer togetger and it doesn't not unless i clean by name.

---

### Post by Seventh Reign on 2010-03-04
Another way to explain this is to imagine plugging in 3 USB Drives, All 3 Desktop Icons for the 3 Drives will ALWAYS appear on top of eachother.  

This has been my biggest gripe with gnome for years.  I dont care if they get all disorganised, just keep the icons in a determined BOX like KDE4 does.

---

### Post by aysiu on 2010-03-04
> **Seventh Reign said:**
> Another way to explain this is to imagine plugging in 3 USB Drives, All 3 Desktop Icons for the 3 Drives will ALWAYS appear on top of eachother. I've had this behavior happen, and it's annoying. I'm on Karmic, by the way. I can't rightly click on anything on the desktop because I may accidentally select the wrong icon (they're all right on top of each other), so I have to "clean up" the desktop before I can select the icon I want.

---

### Post by andrewabc on 2010-03-04
The worst thing ever is when one icon (image preview icon usually) hides another icon underneath it.

I create a simple text file, and then go looking for it a couple hours later and it seems missing, but really it's just hiding under (or very close) another icon.
No idea how it moved there, I think because I had device icons appear and disappear that my newly created file moves somewhere else...

Icon desktop management sucks. My windows xp partition does a much better/simpler job.

I have keep aligned enabled. Yet icons don't keep aligned and I can put icons anywhere on desktop.

ubuntu 9.10

---

### Post by katie-xx on 2010-03-04
OK problem understood.
I cant replicate the download problem so cannot comment. You say if you download files to your desktop they end up stacked on top of each other?

The other problem you flag is actually normal behaviour. Its a snap to grid function and it does it rather well.
You would like to see an auto arrange enhancement if I understand you correctly.
Well, you have two options here.
1: You can write a little script to do the job.
2: You can ask for this feature to be included as an enhancement.
In relation to 1: I believe this has been addressed on this forum before. 

Kate

Edit: Interestingly some Windows 7 users are complaining the ability to disable auto arrange has been removed.

---

### Post by aysiu on 2010-03-04
Seems to have been filed as a Gnome bug for the past 4.5 years:
[https://bugzilla.gnome.org/show_bug.cgi?id=313563](https://bugzilla.gnome.org/show_bug.cgi?id=313563)

Oddly enough, the status is marked as *New*

Wonder what the "old" bugs are...

---

### Post by aviramof on 2010-03-04
i'v noticed it my self that the developers don't take care of bugs reports like this correctly 
if they do ubuntu was much better now especily for people who are use to microsoft os's

as for windows 7 the problem there is completly diffren is talks about the lack of the ability 
to disable auto arrange in files and folder which mean that you don't have manual option there and this is one of the reasons why i'v switch to ubuntu in the first place but on destop 
you still have the ability to choose between auto arrange or not and you can choose to arrange acording to name size type date and etc. 

i don't understand why ubuntu developers don't think about this sort of things what is so hard to copy the arrange items option from files and folder to the desktop or to add an option in display to choose what is the main screen and what is the secondery or add default url support and all sort of things like this that would make life easier for everyone and that i'm sure have already reported several times in the past.

---


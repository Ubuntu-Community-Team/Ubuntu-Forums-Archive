---
title: "Non Obvious Install"
date: 2008-10-07
forum: Installation &amp; Upgrades
---

### Post by NomadTW on 2008-10-07
Ok so I have a laptop that I want to put ubuntu on, currently the laptop has vista on it.
I want the laptop to appear and act to the untrained eye as though it only has vista installed. 
no grub loader loading
no default popping of any OS lists showing anything out of the ordinary on.
ideally to hide the ext3 partition so it doesn't show up in windows at all.
I would like it to just automatically boot to windows with no interaction, and perhaps a key to press during boot to choose to boot into ubuntu.

is any/all of this possible?

---

### Post by Catalyst2Death on 2008-10-07
You could do a normal install, and then exit grub to automatically boot to windows... (set wait time to 0, and make vista the default)

Why you would want to do this is beyond me, there would be no way to get into linux!  Oh well.

---

### Post by Partyboi2 on 2008-10-07
You can also change the
> ## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu section of your menu.lst so that the grub menu is hidden at boot unless you press Esc.
To hide:
> ## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

---

### Post by Catalyst2Death on 2008-10-07
Note that the hidden menu option displays something like:

Booting to default operating system in 3 2 1 ...

---

### Post by pieisgood4589 on 2008-10-07
You could use Wubi to install, (it's Ubuntu on your computer, but it acts like a Windows application- you can uninstall it with one click, it just takes a portion of your harddrive,) and set the Grub wait time to 0, or 1 second, so as you have enough time to press the "ESC" key to stop GRUB from booting. Then, put Windows first on your boot list so it will immediately boot into Vista afterwords. If you don't press "ESC," it'll just boot into Ubuntu. I'm not sure how to make it so it'll boot into Windows and only Linux by pushing a button, only vice-versa...?

---

### Post by NomadTW on 2008-10-07
ideally booting to ubuntu would be some way to make the computer actually see the ext3 partition as a seperate hard drive to boot from, so I could have two completely uninteracting operating systems that could be chosen by using the bios boot menu to choose where to boot from.

now i know that that is not actually a posibility, and installing a 2nd hard drive is not an option for a laptop.

but that's really where i'm hoping to go

the goal is if my boss were to pick up this laptop, power it on and do a light amount of poking around, making sure there's not porn, etc on the laptop, for her to not realize that ubuntu is installed unless she was specifically looking for it.

---

### Post by lisati on 2008-10-07
> **NomadTW said:**
> ideally booting to ubuntu would be some way to make the computer actually see the ext3 partition as a seperate hard drive to boot from, so I could have two completely uninteracting operating systems that could be chosen by using the bios boot menu to choose where to boot from.

now i know that that is not actually a posibility, and installing a 2nd hard drive is not an option for a laptop.

but that's really where i'm hoping to go

the goal is if my boss were to pick up this laptop, power it on and do a light amount of poking around, making sure there's not porn, etc on the laptop, for her to not realize that ubuntu is installed unless she was specifically looking for it.

If it's your own personal laptop, then it's up to you what you put on it - you shouldn't have to be sneaky. Fostering a good working relationship with your boss is a good idea too, where you can be open and honest without having to hide things.

---

### Post by snowpine on 2008-10-07
Boot from an Ubuntu Live CD or USB stick. No changes to your hard drive, no trace that you ever used Ubuntu...

---

### Post by NomadTW on 2008-10-08
> **lisati said:**
> If it's your own personal laptop, then it's up to you what you put on it - you shouldn't have to be sneaky. Fostering a good working relationship with your boss is a good idea too, where you can be open and honest without having to hide things.
it is more or less a personal laptop, but there are restrictions on what i can have on it to use for work to be able to use the laptop for work. 
there are many reasons that ubuntu is much better than windows for what i do, one thing that comes to mind is the fact that on plugging just about any printer into the computer it's ready to print in a minute or less instead of having to install every single HP printer i plug into seperately taking like 10 minutes a piece.
i do not not for sure that installing linux on the laptop would be a violation, but i would rather hide it and not have to find out than be flat out told no.

> **snowpine said:**
> Boot from an Ubuntu Live CD or USB stick. No changes to your hard drive, no trace that you ever used Ubuntu... 
running from the live CD will not work as there are several tweaks that i have to set up for things like pda tethering, and accessing hfs

---

### Post by cariboo on 2008-10-08
Why jeopardize your job, ask your boss if she minds if you install Ubuntu on your laptop.

Jim

---

### Post by Mark Phelps on 2008-10-08
> **NomadTW said:**
> Ok so I have a laptop that I want to put ubuntu on, currently the laptop has vista on it.
I want the laptop to appear and act to the untrained eye as though it only has vista installed. 
no grub loader loading
no default popping of any OS lists showing anything out of the ordinary on.
ideally to hide the ext3 partition so it doesn't show up in windows at all.
I would like it to just automatically boot to windows with no interaction, and perhaps a key to press during boot to choose to boot into ubuntu.

is any/all of this possible?

I have a laptop that has both Vista and Ubuntu on it, and I've experimented with what you want to do -- for different reasons, but with much the same result in mind.  

I'm not an Ubuntu "expert", but I'll pass along what I've learned ...

1) GRUB.  Menu is hidden, have to press Esc key to see it.  Tried timeout of zero but the boot was too fast to allow me to press the key before the machine dropped into Vista.  Had to end up allowing one second, and that displays the message on the screen about pressing the key.

2) Ubuntu file system.  Routine usage of Vista will not "see" the filesystem because Windows (currently) doesn't understand Ext3 filesystems.  So, Windows Explorer and other file manager tools will not show the Ubuntu partition.  However ... the Disk Management console plugin shows ALL the partitions, hidden or otherwise, regardless of format.   So, if the person using Vista knows about the console plugins, they will be able to find the Ubuntu partition(s).

3) Accessing your "private" stuff.  You can search in this forum for details about adding and using passwords to prevent booting into Ubuntu (to prevent launching Ubuntu if the person does press Esc).  That will at least keep folks out of the Ubuntu file system on a casual basis.

If they do get into Ubuntu (using a boot CD for example), you can encrypt files to prevent access.  But, they will be able to discover those files, and encrypting files on a machine you use at work could be in violation of some IT "policy".

Better solution would be to keep your files on a plugin external drive -- but then, you have to physically protect that.

One final thought ... if you connect your machine to the internet at work, it's common practice today for companies to monitor internet usage -- and when they do so, they do it silently.  While a history of accessing non-work-related sites is not likely to get you fired, on the other hand, IT policies are generally so vaguely worded, that such activity COULD be used to fire someone.

Hope some of this helps ...

---


---
title: "Holy **** my files? gone?"
date: 2007-08-05
forum: Installation &amp; Upgrades
---

### Post by lostitall on 2007-08-05
Today I installed ununtu,
and all my files are now GONE! 
I had a perfect  runnung vista.
but now i dont have C DRIVE 
and not D DRIVE just filesystem.
all my photos are gone and im sitting and crying
in front of my computer.
I am possibly the biggest idiot on earth.
so i ask you for help CAN SOMEONE TELL ME HOW TO RESTORE MY FILES???????????????????????

---

### Post by Warren Watts on 2007-08-05
I assume you installed from a Live CD?

Did you set up Ubuntu in a dual boot configuration?

---

### Post by musther on 2007-08-05
You're going to have to be more specific about what you did.  

So you started with a vista install, you put in the Ubuntu CD, was it the live CD?  Then you tried to install, did you ask it to resize windows partitions to give you space for Ubuntu?  Then what?

---

### Post by lostitall on 2007-08-05
I downloaded an .iso file to my desktop,
then i burned it on CD,
It told me to restart my computer,
I restarted it and pressed F12 (booting settings)
then ubuntu started working and there was a file named "install"
and a folder named "example" on my ubuntu desktop.
I double clicked install,
I filled all the info and it asked me if I want to put it on D (my vista windir)
or manually, in manually i didnt understand **** so I pressed D.
And then when the installing prosess stared I saw him writing "formatting..."
So I closed it restarted my computer and it said no operating system!
I turned ubuntu on and checked my hard drive and it was gone! 
so I filled all the **** again and now Im stuck with ubuntu.

---

### Post by dabl on 2007-08-05
Your files may or may not be gone.

Apparently you still have an ability to connect to the net.  If I were you, I would download the ISO and make myself a GParted Live CD, from here: [http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

Looks like the latest version is gparted-livecd-0.3.4-8.iso

Boot that, and it will show you your actual hard drives, partitions, and which one is bootable.  It may be that you changed the boot flag off of your Vista partition during your little adventure.  If so, you can change it back (if you know which partition is the Vista boot.  And depending on where your data files were, you may not have formatted that partition.

You really need to do just a wee bit of advance study of the recommended process, before just launching an installer on your computer, if you hope to retain your data.  Here is a good place to start:

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

But that's not the end of it -- Vista has introduced a couple of changes, and you need to search this forum on "Vista partitioning" so that you get a handle on how to use Vista to shrink it's partitions (if that is applicable to your setup), how many partitions Vista requires on its hard drive, etc. etc. so you don't bork your system even worse.  :)

---

### Post by lostitall on 2007-08-05
everyone is talking about this "Partition" what is it?????

---

### Post by Pumalite on 2007-08-05
Google it. [http://en.wikipedia.org/wiki/Partition_(computing](http://en.wikipedia.org/wiki/Partition_(computing))

---

### Post by musther on 2007-08-05
By the way, by default the Ubuntu installer will move your windows partitions to make room for itself, I assume that's what it did in this case.  Then, when it's made room it creates and formats partitions for itself, that's when you saw it say formatting.  Cancelling at this point (if I'm right about when you cancelled it) shouldn't loose any data, but your partitions will have changed and the correct one may not be set to boot, so windows doesn't start.

I agree with dabl that you should try gparted, but you don't need to download the gparted live cd, just boot the Ubuntu live CD and go to System>Administration>Gnome Partition Editor and that will start gparted for you.

Jon

---

### Post by lostitall on 2007-08-05
there is no such thing as System>Administration>Gnome Partition Editor
i open Administration and only see 
"keyring manager"
"language support"
"login window"
"network"
"network tools"
"printing"
"restricted driver manager"
"services"
"shared folders"
"software sources"
"synaptic package manager"
"system log"
"system monitor"
"time and date"
"update manager"
"users and groups"

cant find it

---

### Post by Pumalite on 2007-08-05
Download Gparted as dabl suggested. Here is something to help you use it: [http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)

---

### Post by wolfen69 on 2007-08-05
check your private messages.

---

### Post by scorp3000 on 2007-08-05
> **Pumalite said:**
> Download Gparted as dabl suggested. Here is something to help you use it: [http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)

[http://gparted.sourceforge.net/larry/livecd/main/livecd.htm](http://gparted.sourceforge.net/larry/livecd/main/livecd.htm)

---

### Post by steveneddy on 2007-08-05
> **lostitall said:**
> everyone is talking about this "Partition" what is it?????

You should really do a little more research before you go installing anything on your computer. Especially a new Operating System.

There are certain terms, like partition, or install, that a semi advanced user would need to know before trying to pull off what you attempted.

I hope that you get everything back ok.

Look at the bright side. You got rid of Vista.

---

### Post by musther on 2007-08-05
Gparted was on the Live CD before feisty, and I thought it still was (although it isn't installed).  I'll have to try my feisty live CD again.

---

### Post by Gremlinzzz on 2007-08-05
[http://blogs.msdn.com/winre/archive/2006/09/20/using-startup-repair-to-repair-a-boot-failure-due-to-a-missing-file.aspx](http://blogs.msdn.com/winre/archive/2006/09/20/using-startup-repair-to-repair-a-boot-failure-due-to-a-missing-file.aspx)
worth a try

---


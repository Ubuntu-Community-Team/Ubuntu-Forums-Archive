---
title: "Things I'd like to see added to Installation options + other stuff"
date: 2007-10-11
forum: Installation &amp; Upgrades
---

### Post by MR.UNOWEN on 2007-10-11
Hello, 

Some time ago I tried installing Ubuntu with no luck due to a few issues, so I'd like to offer a few suggestions.

The first Issue I encountered was partitioning my hard drive. It was either too automated or too complicated. It either partitioned the entire hard drive or it asked you to specify a bunch of things that I didn't understand. So I'd appreciate **a future version were you could partition a hard drive in with two simple categories:  storage(which can be more than one) or OS**, instead of asking for /this or /that. 

The second issue was the display, sadly I'm using an ATI card which has poor Linux support and being such I couldn't get the proper resolution for my display. So it would be great if there was a **simple user override option **to a particular resolution rather than having to modify some text file. Unfortunately when I tried to force a particular resolution, Ubuntu crashed due to the fact I modified a variable, which I thought to be the display value.

The third issue, which I know is just an ATI thing, was the desktop effects. I know there's not much that can be done on Ubuntu's end. Does anyone know when there's going to be a decent ATI driver for ubunto?

The fourth, which is not really an issue, but I'd really like to see an option where I can just right click on an image and set it as the back ground or be viewing and image and do the same. 

So far for now I'm still stuck with XP. If any of the developer of Ubunto have the time to take care of the first two issues, I'd appreciate it. Please reply if you guys are thinking about it.

---

### Post by Wicca on 2007-10-11
Hello too,

1st
I don't think that's a good idea. Even if you just choose the OS-option, there are so many variations possible: only 1 partition, or 3 or more, with different filesystems.... If the devs make it simple with let's say, 2 or 3 scenarios, the amount of choices you can make will decrease. And linux is all about choices, more: the freedom to choose. Some things might be difficult to understand, but it's better to put some energy in increasing your knowledge, than to let others decide what choices you have. One MS is more than enough. ):P
 
2nd
Yes, configure X is not real user-friendly, I agree.

3rd
I have read about ATI owners who got the desktop effects working with the fglrx-driver. I used to have an ATI 9800 PRO and with Edgy I got Beryl working without a problem, so it is possible, try searching the forums.

4th
This option is already there (Feisty here). If I doubleclick on an image, gThumb opens up and I can rightclick the image and choose "use as background".

greetings

---

### Post by phr0ze on 2007-10-11
1. During my install it gives me the option to resize the existing drive. I do not need to pick anything other than the new size. It creates the other partitions for me. You don't get this option? BTW: it helps if you disconnect any external USB drives not needed for the installation.

2. Gutsy has a nice new interface for this. In about 7 days you can upgrade to gutsy.

3. ATI just started cooperating with open source developers and has started to release specs and reference drivers. Give it another 6 months and it'll probably be standard. For now you can try to find the bleeding edge releases and tinker if you are that sort.

4.Somewhere this has got to be an add-on to nautilis. If not you can always try another file manager. I don't change my background so much that I really care, but there has to be an easy solution to this.

---

### Post by wpshooter on 2007-10-11
One of the main things I would like to see them change is to put "**the check Ubuntu CD** **integrity function**" as the number 1 thing on the Ubuntu boot screen menu.

This is the very first thing the user should always do with this installation CD and therefore it should be the FIRST thing on the menu NOT the start & installation option !!!

---

### Post by MR.UNOWEN on 2007-10-11
> **Wicca said:**
> Hello too,

1st
I don't think that's a good idea. Even if you just choose the OS-option, there are so many variations possible: only 1 partition, or 3 or more, with different filesystems.... If the devs make it simple with let's say, 2 or 3 scenarios, the amount of choices you can make will decrease. And linux is all about choices, more: the freedom to choose. Some things might be difficult to understand, but it's better to put some energy in increasing your knowledge, than to let others decide what choices you have. One MS is more than enough. ):P
 
greetings

Well the only two options I got was format all or manual, which I didn't know what to do (/root, /home, /this, /that).
What I would like see is a third option that allows multiple partition such that one is for os and the rest are storage and I don't have to deal with any "/". I found manual too complicated and confusing. When I asked for help, no one could explain what to do.

BTW whens GUTSY coming out?

---

### Post by Mark Phelps on 2007-10-12
Regarding the ATI display problems ...

I, too, have an ATI card, but I've had no problems at all with it.  I struggled with installing the ATI restricted drivers until I found out about Envy.  Downloaded that, installed it, and now use it to handle ATI drivers.  Am able to use 1600X1200 resolution with no problems and, it installs a version of the Catalyst Control Center.  Not as full-featured as the Windows version, but then, I only use 2-D graphics and watch movies. I also discovered that SMPlayer does a really good job of rendering movies.  The default Totem movie player is not so good.

So, try using Envy and SMPlayer -- I think you'll see a vast improvement in the graphics quality.

---

### Post by phr0ze on 2007-10-12
Gutsy is out in 6 days.

---

### Post by MR.UNOWEN on 2007-10-12
> **Mark Phelps said:**
> Regarding the ATI display problems ...

I, too, have an ATI card, but I've had no problems at all with it.  I struggled with installing the ATI restricted drivers until I found out about Envy.  Downloaded that, installed it, and now use it to handle ATI drivers.  Am able to use 1600X1200 resolution with no problems and, it installs a version of the Catalyst Control Center.  Not as full-featured as the Windows version, but then, I only use 2-D graphics and watch movies. I also discovered that SMPlayer does a really good job of rendering movies.  The default Totem movie player is not so good.

So, try using Envy and SMPlayer -- I think you'll see a vast improvement in the graphics quality.

Actually I tried Envy, but nothing happened No Catalyst or changes in resolution, but that was with Feisty Fawn. 

By the way, for those who have the beta of GUTSY. Is the display option user friendly? Friendlier than the Windows version?

---

### Post by rudeboyskunk on 2007-10-12
I understand your pain with trying to deal with the problem of "/this" and "/that".  The thing is, that is how UNIX-based operating systems work.  Windows isn't really UNIX-based, so it does not use that sort of file system hierarchy.

For different Linux distros there will be different partitions you need to make.  However, it is rather simple for Ubuntu.  The default partitioning scheme should look like this (**this is assuming your computer is x86, if not, just ignore me):

Mount Point-----Device--------Size------------------------------------File System Type
/swap-------------/dev/hda1---twice your ram---------------------swap
/--------------------/dev/hda2----however much is left over-----ext3

Now, a bunch of people who know better than I do will probably tell you not to do that, it is dependent upon your computer, etc etc.  They are very correct.  This is how it is for my computer.

The partition mount point "/" contains your OS AND all the free space that you need to store all your stuff.  The best place to store it is /home/*username*.

Now, if all that is confusing to you, look it up online.  Look at other forums.  Lots of people have this problem (and it is no easy one), but it is something anybody who wants to do special partitions and use Linux must go through.  You MUST know what "/" means and what "/root" and "/home" and "/boot" and "swap" and "ext2" and "ext3" and all that other good stuff means, otherwise you'll mess something up.

My best advice is this:  burn all of the important stuff you have to two CD-Rs or two DVD-Rs (two so in case one breaks or gets scratched, you have a second back up).  Then, install Ubuntu (wait for Gutsy Gibbon).  Let it partition the hard disk for you.  It will give you the partitioning scheme I laid out above most likely.  If you don't like it, keep trying it until you get a partitioning scheme you want to keep.

Now if you're trying to do a dual-boot with Windows, that's a different story... (hint: do a forum search for "dual boot ubuntu windows")

EDIT:  If you really really really really want a separate partition just of free space to put all your stuff on, rather than putting it into /home/*username*, then make a separate partition whose mountpoint is /home, that way you'll be able to still use /home/*username* to keep all your stuff, and it'll be on a separate partition (this is also safe in case your system gets screwed up; you won't lose any of your stuff).

---

### Post by MR.UNOWEN on 2007-10-12
So....  for those who've tried out the beta version, is there any change the installation process?

---

### Post by MR.UNOWEN on 2007-10-22
[SIZE="4"]I LOVE GUTSY!!![/SIZE]   Everything works so far. It automatically found my max resolution, desktop effects works and I'm love'n it.

Also rudeboyskunk, thanks for your advise.

Now that I got things working I have a few questions...

1. Where can I access the partitioning tool?
2. Is there an application that can monitor system temperature? I'm concerned some of my hardware may overheat.
3. What the closest Linux equivalent to Samurize (Samurize.com) that allows me to meter, widget, image on my desktop?
4. I have an Epson 600 how to I add this printer (it's a non-usb printer)?
5. Does Ubuntu recognize hot-swap, such that I can plug in any internal hard drive and it will see it?
6. I currently have it such that Windows and Ubuntu are installed on separate hard drives with their own mbr. If while already running one of the hard drives, I connect the other hard drive, is there the chance either OS will damage the other (assuming the partition tool is never touched)?
7. Does Ubuntu have  that Byrle cube effect and what button changes cube faces?
7b. If not how do I go about installing Byrle and where do I get it?

---

### Post by Soarer on 2007-10-22
> **MR.UNOWEN said:**
> [SIZE="4"]I LOVE GUTSY!!![/SIZE]   Everything works so far. It automatically found my max resolution, desktop effects works and I'm love'n it.

Also rudeboyskunk, thanks for your advise.

Now that I got things working I have a few questions...

1. Where can I access the partitioning tool?
2. Is there an application that can monitor system temperature? I'm concerned some of my hardware may overheat.
3. What the closest Linux equivalent to Samurize (Samurize.com) that allows me to meter, widget, image on my desktop?
4. I have an Epson 600 how to I add this printer (it's a non-usb printer)?
5. Does Ubuntu recognize hot-swap, such that I can plug in any internal hard drive and it will see it?
6. I currently have it such that Windows and Ubuntu are installed on separate hard drives with their own mbr. If while already running one of the hard drives, I connect the other hard drive, is there the chance either OS will damage the other (assuming the partition tool is never touched)?
7. Does Ubuntu have  that Byrle cube effect and what button changes cube faces?
7b. If not how do I go about installing Byrle and where do I get it?

1. Sorry, can't help. I partitioned at install.
2. Yes, several. You need to install 'lm-sensors' and 'hddtemp'. Then use the 'sensors' applet to display on your top bar.
3. Never used it, but 'gkrellm' and 'gdesklets' look similar.
4. Gutsy auto-installs printers it recognises, including for me an HP on the network. Try it & see. You could also look in [http://openprinting.org/printer_list.cgi](http://openprinting.org/printer_list.cgi) to check, but that may not be up-to-date.
5. Yes
6. Not usually, unless you share filesystems.
7. Gutsy has Compiz. It has lots of options, but ctrl+alt+left click will allow you to drag the cube around.

P.S. Google is your friend.

---

### Post by MR.UNOWEN on 2007-10-22
Well this is what I got from the site for my printer: gutenprint-5.0.1-1lsb3.1.i486.rpm
Now how to I access it? Ubuntu can't seem to read it. BTW is it a pre-compile or do I have to go through the whole process of compiling it and then running it?

---

### Post by Soarer on 2007-10-22
> **MR.UNOWEN said:**
> Well this is what I got from the site for my printer: gutenprint-5.0.1-1lsb3.1.i486.rpm
Now how to I access it? Ubuntu can't seem to read it. BTW is it a pre-compile or do I have to go through the whole process of compiling it and then running it?

Maybe you could read my reply to No 4? You don't need to download anything - just plug in the printer & if Gutsy recognises it, it will install it without you having to do anything.

You say its non-USB - what interface does it use?

---

### Post by MR.UNOWEN on 2007-10-22
First of all it's been pluged in and here's a picture that I got off google image showing the kind of connector my printer uses: [http://content.answers.com/main/content/wp/en-commons/thumb/a/ac/250px-Parallel_computer_printer_port.jpg](http://content.answers.com/main/content/wp/en-commons/thumb/a/ac/250px-Parallel_computer_printer_port.jpg)

BTW when you say auto detects, do I have to click on something for it to start up or should this be automatic?

---

### Post by MR.UNOWEN on 2007-10-22
Never mind.....  I finaly found where the add printer option was....

---


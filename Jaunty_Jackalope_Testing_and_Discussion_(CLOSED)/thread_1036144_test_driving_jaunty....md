---
title: "test driving jaunty..."
date: 2009-01-10
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by jimi_hendrix on 2009-01-10
i want to help the community so id figure id try jaunty...how can i help?

also theres no possibility of it rendering my machine unusable right...

also whats new in jaunty?

---

### Post by Slug71 on 2009-01-10
> **jimi_hendrix said:**
> i want to help the community so id figure id try jaunty...how can i help?

also theres no possibility of it rendering my machine unusable right...

also whats new in jaunty?


You can help by installing and testing and filing bugs to Launchpad.

Yes it can render your machine unusable but unlikely that it will be anything permanent. You may have to do reinstalls on occasion though.

New at the moment is Kernel 2.6.28, Ext4 filesystem, and a few other bit and pieces.

Still waiting for OOo-3, Packagekit and FF-3.1 to be default.

---

### Post by jimi_hendrix on 2009-01-10
link to install?

---

### Post by Slug71 on 2009-01-10
Alpha-3 comes out the 15th but if you dont want to wait you can download todays Daily Build which should be up to date.

Link for Daily Build:
[http://cdimage.ubuntu.com/daily/current/](http://cdimage.ubuntu.com/daily/current/)

Alpha-3 can be found here but still contains Alpha-2 of course:
[http://cdimage.ubuntu.com/releases/jaunty/alpha-2/](http://cdimage.ubuntu.com/releases/jaunty/alpha-2/)


Make sure you sign up for a Launchpad account too so that you can report bugs.
[https://launchpad.net/](https://launchpad.net/)

---

### Post by jimi_hendrix on 2009-01-10
ok thanks!

---

### Post by Slug71 on 2009-01-10
> **jimi_hendrix said:**
> ok thanks!

No problem, have fun! :)

I recommend using the Ext4 filesystem at installation.

---

### Post by BGFG on 2009-01-10
Once you install an alpha, will update-manager -d get you to the next alpha ? also, i know i can google, but what is the min disk size ? Using vmware and low on disk space..

---

### Post by jimi_hendrix on 2009-01-10
what does Ext4 provide over Ext3

---

### Post by Slug71 on 2009-01-10
> **BGFG said:**
> Once you install an alpha, will update-manager -d get you to the next alpha ? also, i know i can google, but what is the min disk size ? Using vmware and low on disk space..

No need for update-manager -d.
As long as you keep up with the updates you will have the next Alpha all the way through to Final. :)

---

### Post by Bachstelze on 2009-01-10
> **jimi_hendrix said:**
> link to install?

Why install? Just upgrade from Intrepid. ;)

---

### Post by Slug71 on 2009-01-10
> **jimi_hendrix said:**
> what does Ext4 provide over Ext3

Not to sure exactly, could probably google it but i know speed is one of them.
Also its new and since Jaunty is in development it should be tested. 
VERY stable for me so far.

---

### Post by BGFG on 2009-01-10
Grabbing the amd64 torrent now....5gig vm enough ?

I assume the defrag utility will be invoked via the terminal ?:)

---

### Post by Slug71 on 2009-01-10
> **BGFG said:**
> Once you install an alpha, will update-manager -d get you to the next alpha ? also, i know i can google, but what is the min disk size ? Using vmware and low on disk space..

Space should be the same as Intrepid but im not even sure what that is.
I have it installed on a separate partition so never checked.

---

### Post by Slug71 on 2009-01-10
> **BGFG said:**
> Grabbing the amd64 torrent now....5gig vm enough ?

I assume the defrag utility will be invoked via the terminal ?:)

Oh yeh. im sure that will be enough.
and yes about the Terminal. :)

---

### Post by BGFG on 2009-01-10
> **Slug71 said:**
> Oh yeh. im sure that will be enough.
and yes about the Terminal. :)

general Linux tech is racing ahead, I just wish the GUI's could keep pace though :)

Lemme check my torrent progress.....upgraded to a 1meg connection from a 512.

---

### Post by SunnyRabbiera on 2009-01-10
you can also try it in virtualbox.

---

### Post by Old_Grey_Wolf on 2009-01-10
> **BGFG said:**
> Grabbing the amd64 torrent now....5gig vm enough ?


I just checked, and I'm using 3GB of disk space for the virtual machine image. I have been playing with it for a while so the file may have grown some from the original download.

---

### Post by Slug71 on 2009-01-10
> **BGFG said:**
> general Linux tech is racing ahead, I just wish the GUI's could keep pace though :)

Lemme check my torrent progress.....upgraded to a 1meg connection from a 512.

Yeh the GUIs are a little behind but they are getting there.
Hopefully you dont have a problem with X in Jaunty that some people are having.
I havent had a single one yet other than messing with Grub2.
Gnome has a new Partitioner coming out with a nice GUI i guess but i dont think it will be in 2.26 which means it probably wont make Jaunty unless its patched in. 
Also have a new Volume Control.

---

### Post by Slug71 on 2009-01-10
> **Old_Gray_Wolf said:**
> I just checked, and I'm using 3GB of disk space for the virtual machine image. I have been playing with it for a while so the file may have grown some from the original download.

Im using 2.8GB.
Dont have much installed though other than Packagekit, Java, Startup Manager and Flash.

---

### Post by Old_Grey_Wolf on 2009-01-10
> **jimi_hendrix said:**
> i want to help the community so id figure id try jaunty...how can i help?


Here is a link to Ubuntu's Wiki about testing alphas [https://wiki.ubuntu.com/Testing](https://wiki.ubuntu.com/Testing)

---

### Post by BGFG on 2009-01-10
Think i can spare 4 or 5 gigs....As for virtualbox, i find that vmware isn't as resource needy. Only have 1 gig of ram and a 2.1 X2

Torrent Only on 30%. :(

---

### Post by samjh on 2009-01-10
> **jimi_hendrix said:**
> what does Ext4 provide over Ext3

See: [http://kernelnewbies.org/Ext4](http://kernelnewbies.org/Ext4)

:)

Bewarned, Ext4 has only just been adopted by the kernel project.  Torvalds reckons it's stable enough though.

---

### Post by Slug71 on 2009-01-10
> **samjh said:**
> See: [http://kernelnewbies.org/Ext4](http://kernelnewbies.org/Ext4)

:)

Bewarned, Ext4 has only just been adopted by the kernel project.  Torvalds reckons it's stable enough though.

Very stable so far. All the more reason to test it with Jaunty since Jaunty is in Development.

---

### Post by samjh on 2009-01-10
Hmmm... I might give Jaunty a spin too.  I've been wondering how stable the Alpha is. :)

---

### Post by Slug71 on 2009-01-10
> **samjh said:**
> Hmmm... I might give Jaunty a spin too.  I've been wondering how stable the Alpha is. :)

VERY for me. I havent had to file or add to a single bug yet except Grub2 which i was messing with.

Some people are having issues with X though.

---

### Post by jimi_hendrix on 2009-01-10
downloading now

---

### Post by samjh on 2009-01-11
> **Slug71 said:**
> VERY for me. I havent had to file or add to a single bug yet except Grub2 which i was messing with.

Some people are having issues with X though.

Yup, the installation was reasonably smooth, booted to desktop, installed Nvidia drivers, reboot, then uh oh...

For anyone who is wanting to make the upgrade: do not install the Nvidia proprietary drivers yet!  It will remove Xorg.

---

### Post by Bachstelze on 2009-01-11
> **samjh said:**
> 
For anyone who is wanting to make the upgrade: do not install the Nvidia proprietary drivers yet!  It will remove Xorg.

A workaround is available, see the Jaunty section of the forums.

Another approach is to not use the Ubuntu packages for the nvidia drivers altogether, and use the nvidia installers instead. That's what I do and it works just as well.

---

### Post by treesurf on 2009-01-11
I'm pretty newbie, but I'd like to try my hand at testing an alpha.

I'm dual booting Vista and Hardy right now.  Should I just make a new blank partition (say about 8-10GB) and install Jaunty to that?  Will it automatically appear in my grub menu or will I have to manually enter it?  If so how do I do that?

Or am I too newbie to even attempt this? :D

---

### Post by treesurf on 2009-01-12
I will take the deafening silence to indicate a "yes" to my last question.

---

### Post by samjh on 2009-01-12
If you have to ask that question, treesurf, then you shouldn't be testing an Alpha. ;)

The NORMAL behaviour for Ubuntu is that the installer will automatically configure grub to dual-boot.  However, Jaunty is still in Alpha, so the behaviour might turn out quite differently.  If it does go haywire, can you fix it by yourself?

Perhaps it might be better for you to run Jaunty on VirtualBox or VMWare.

Problems I've had so far:
- XSane crash.
- Various Gnome applet and popup crashes.
- Firefox rendering problem (workaround is available, it's an X problem).
- PulseAudio muting the front speaker by default (Launchpad bug report filed).
- PulseAudio volume settings not maintained after power-off (Another person has reported this).
- Xorg fails to start (because NVidia proprietary drivers remove it... not much Ubuntu devs can do about this one).
- NVidia drivers fail to install and remove correctly (I think the devs are working on a fix).

It's very apparent that Jaunty has a long way to go until it is stable. :)

---

### Post by dragos240 on 2009-01-12
I recommend using virtualbox. No need to install on your system, just get the iso, and load it, pretty easy.

---

### Post by treesurf on 2009-01-12
Thanks, I'm off to do some reading about virtualbox.

---

### Post by Thelasko on 2009-01-12
> **dragos240 said:**
> I recommend using virtualbox. No need to install on your system, just get the iso, and load it, pretty easy.

As I understand, it's more useful to the community if Jaunty is installed on physical hardware.  Installing in VirtualBox won't test new drivers.

---


---
title: "Problem running from Live CD."
date: 2008-02-22
forum: Installation &amp; Upgrades
---

### Post by DarkWater on 2008-02-22
When I try to run from the Live CD, I get a bouncing sign that says "Input Not Supported" on my monitor.  I'm using an Acer al1706...it's just not working.  Anybody have advice?

---

### Post by DarkWater on 2008-02-22
Oh, by the way, I'm on a Dell Dimension 2300 (old, I know, I'm buying a new one soon) with an Intel Pentium 4.

---

### Post by kool_kat_os on 2008-02-22
what type of connector is the monitor?

---

### Post by kool_kat_os on 2008-02-22
> **DarkWater said:**
> Oh, by the way, I'm on a Dell Dimension 2300 (old, I know, I'm buying a new one soon) with an Intel Pentium 4.

I would build a computer....not buy one. :)

---

### Post by DarkWater on 2008-02-22
> **kool_kat_os said:**
> I would build a computer....not buy one. :)

I have one that I built and it works fine.  I'm installing Ubuntu on another machine and it's not working.  The monitor has a VGA connector.

---

### Post by kool_kat_os on 2008-02-22
> **DarkWater said:**
> I have one that I built and it works fine.  I'm installing Ubuntu on another machine and it's not working.  The monitor has a VGA connector.
what is the graphics card?

---

### Post by DarkWater on 2008-02-22
> **kool_kat_os said:**
> what is the graphics card?

I'll tell you in a minute or two.  I'm trying one more thing.  If it doesn't work, I'll just boot my Windows and check dxdiag for the graphics card.  One minute.

---

### Post by kool_kat_os on 2008-02-22
ok....

EDIT: i just realized that this was my 300th post!!!

---

### Post by DarkWater on 2008-02-22
> **kool_kat_os said:**
> ok....

EDIT: i just realized that this was my 300th post!!!

Congrats! :D  

Hmm...I tried running the Ubuntu net-installer and it's working so far.  It's installing the system this time instead of killing my monitor.  Yay.  Let's hope it works. D:

---

### Post by uberlube on 2008-02-22
During GRUB add "vga=791" to the boot process.

---

### Post by DarkWater on 2008-02-22
> **uberlube said:**
> During GRUB add "vga=791" to the boot process.

D'oh. >_<  Okay.  I'll do that if thise doesn't work, but it seems to be considering it grabbed all the necessary packages and is installing the kernel.  I wasn't sure what VGA setting to put in the boot process for this monitor, so I didn't put one. =P

---

### Post by kool_kat_os on 2008-02-22
> **uberlube said:**
> During GRUB add "vga=791" to the boot process.

for some odd reason i dont know what that does...

---

### Post by DarkWater on 2008-02-22
> **kool_kat_os said:**
> for some odd reason i dont know what that does...

Tells the installer what type of monitor drivers to boot with I think.  If I remember correctly.  Damn Acer...messing with my Ubuntu install...*grumble*

---

### Post by DarkWater on 2008-02-22
Okay, it installed.  Now I logged in, what should I type at the command line first?

---

### Post by DarkWater on 2008-02-22
Annnnnd never mind.  I'm installing GNOME.  D:  Wow, turns out I solved my own problems on this thread.  @_@  I'll post again if anything breaks. =)

---

### Post by uberlube on 2008-02-22
Also, if you make sure to install your graphics driver right away using ENVY, you wont have to worry about future graphical booting problems. Not sure if you knew that already but I thought id throw it in there.

---

### Post by DarkWater on 2008-02-22
> **uberlube said:**
> Also, if you make sure to install your graphics driver right away using ENVY, you wont have to worry about future graphical booting problems. Not sure if you knew that already but I thought id throw it in there.

How exactly do I do that? =D

---

### Post by uberlube on 2008-02-22
Either grab envy from the repositories using Synaptic Package Manager or download and install from his site:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Once its installed look or it in your menu and launch, then install the ATI or nVIDIA driver.

Eazy Cheezy:)

---

### Post by DarkWater on 2008-02-22
I just finished installing GNOME...and now my screen is just like, blank.  Should I reboot? =P

---

### Post by uberlube on 2008-02-23
Are you positives that the instillation finished. Did you exit the installer back into the desktop, or did it just freeze?

---

### Post by DarkWater on 2008-02-23
> **uberlube said:**
> Are you positives that the instillation finished. Did you exit the installer back into the desktop, or did it just freeze?

Woops, I think I forgot to get x-window-system-core and xserver-xorg.  Which other packages should I get?

---

### Post by DarkWater on 2008-02-23
Eep.  I guess all these problems are because I used some net installer.  I'm DLing the alternate CD image right now.  That should work. =P

---

### Post by uberlube on 2008-02-23
I was just going to suggest that. The alternate has always worked best for me.

---

### Post by DarkWater on 2008-02-23
Do I need to add vga=791 to the boot process on the alternate?

---

### Post by uberlube on 2008-02-23
nope, shouldn't have to. Text mode doesnt use x server.

---

### Post by DarkWater on 2008-02-23
> **uberlube said:**
> nope, shouldn't have to. Text mode doesnt use x server.

Wonderful.  I'm burning the disc image right now. =)  Thanks for the idea of using alternate.  Great help.  Hope it works.  I'll report back with any problems.

---

### Post by uberlube on 2008-02-23
no problem. If , after your done installing, you have video problems logging in do this:

1) At GRUB where it gives you the booting options, press 'E' to edit the boot routine.
2) Press 'E' again on the line that says Kernal
3) Add 'vga=791' as you did before

---

### Post by DarkWater on 2008-02-23
> **uberlube said:**
> no problem. If , after your done installing, you have video problems logging in do this:

1) At GRUB where it gives you the booting options, press 'E' to edit the boot routine.
2) Press 'E' again on the line that says Kernal
3) Add 'vga=791' as you did before

Okay, I'm currently on the partitioning step of the installer.  Seems to be working well so far.

---

### Post by uberlube on 2008-02-23
What are the partitions you are makeing?

---

### Post by DarkWater on 2008-02-23
> **uberlube said:**
> What are the partitions you are makeing?

Guided - Entire disk.  I have a 250 GB HD.  Should I have partitioned it with the first option?

---

### Post by uberlube on 2008-02-23
Has it made a SWAP partition for you?

---

### Post by DarkWater on 2008-02-23
> **uberlube said:**
> Has it made a SWAP partition for you?

I believe so.  I'm already well into the Select and Install Software steps.  It seems to be working. =)

---

### Post by uberlube on 2008-02-23
Good stuff. We'll just wait and see if you can load into the desktop alright and then get your graphics card installed.

---

### Post by DarkWater on 2008-02-23
> **uberlube said:**
> Good stuff. We'll just wait and see if you can load into the desktop alright and then get your graphics card installed.

Thanks for bearing with me this whole time.  Not sure what time zone you live in, but it's 1:01 AM here. o-O  Good thing I don't have much to do tomorrow morning.

---

### Post by uberlube on 2008-02-23
Hey not a problem dude that whats the community is all about. And its 11:06 where i am.

---

### Post by DarkWater on 2008-02-23
Hmm...I finished installing, but uhh....I booted it again and it said "Input Not Supported" again.  I tried adding vga=791 on a new line on GRUB, but it didn't work.  What now?

---

### Post by uberlube on 2008-02-23
OK so when you took the alternate CD  out and rebooted did you go into the Kernal line and add it there or what exactly did you do?

---

### Post by DarkWater on 2008-02-23
> **uberlube said:**
> OK so when you took the alternate CD  out and rebooted did you go into the Kernal line and add it there or what exactly did you do?

I took the CD out and rebooted, I went pressed ESC to go to the menu, I pressed e, then I press o for a new line.  Then, I added vga=791 on the line and pressed enter to add it, then I pressed b to boot. D:

---

### Post by uberlube on 2008-02-23
Ok once you press on 'E' on the line that boots you into ubuntu it should take oyu into a different menu with 2 or 3 options of lines to edit. highlight the one that says keral at the beggining and add 'vga=791' at the end of it. then press enter and the press 'b' to boot.

---

### Post by DarkWater on 2008-02-23
It says that I passed an undefined mode number when I do that.  Is there another vga mode that works?

---

### Post by uberlube on 2008-02-23
What kind of monitor do you have?

---

### Post by DarkWater on 2008-02-23
Acer al1706

---

### Post by uberlube on 2008-02-23
Sorry i meant whats the native resolution.

---

### Post by DarkWater on 2008-02-23
1280x1024 I believe. =X

According to [this.]("http://reviews.cnet.com/lcd-monitors/acer-al1706-ab-flat/4505-3174_7-31966776.html")

---

### Post by uberlube on 2008-02-23
ok try 'vga=775'

---

### Post by DarkWater on 2008-02-23
It says that I passed an undefined mode number again.  I just tack vga=775 on the end, right?  No quotation marks on it?

---

### Post by uberlube on 2008-02-23
ya dont use the quotations

---

### Post by DarkWater on 2008-02-23
I didn't.  This is very odd.  D:  It just says "Input Not Supported" if I don't put a VGA mode, and it says undefined mode when I use 775.

---

### Post by uberlube on 2008-02-23
post the whole line that that you are editing so i can see it.

---

### Post by DarkWater on 2008-02-23
grub edit> kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=ed0bfefx-4689-4a4c-4a44-94aa-784360ddc565 ro quiet splash vga=775

That's what it looks like after I put on vga=775.

---

### Post by uberlube on 2008-02-23
try deleting quite splash but keep vga=775 and try again.

---

### Post by DarkWater on 2008-02-23
I tried that a while ago.  Still get "You passed an undefined mode."  =(

---

### Post by uberlube on 2008-02-23
well thats a real pickle. ill try to do some searching around check back in a bit.

---

### Post by DarkWater on 2008-02-23
Thanks a bunch.  I might try using a different monitor and report back if that works.  I'd love to use my Acer, but... =(

---

### Post by uberlube on 2008-02-23
kk ill be here.:)

---

### Post by uberlube on 2008-02-23
also try vga=794 before anything

---

### Post by DarkWater on 2008-02-23
I switched out the Acer with the Dell monitor that came with my comp...and it works.  It's a problem with the monitor.  I think it has something to due with the frequencies being off.  I did some Googling. =P  Any advice?

---

### Post by toa on 2008-02-23
> **DarkWater said:**
> I tried that a while ago.  Still get "You passed an undefined mode."  =(


I got the same poblem before, then you pass a number and it says cant and you keep geeting this message and choosing between a list of reolutions yeah yeah!, your problem is passing a wrong screen refreshrate over what your monitor can handle _OR_ you are using a screen resolution bigger than your monitor can handle.

make sure you have basic colors for boot as showingin the ubuntu startup mamanger screen, and make sure you use the default screen resolution, reconfigure xserver vaues to the default with 

sudo dpkg-reconfigure xserver-xorg

[[IMG]http://img32.picoodle.com/img/img32/4/2/22/t_Screenshot2m_7acbfa9.png[/IMG]](http://www.picoodle.com/view.php?img=/4/2/22/f_Screenshot2m_7acbfa9.png&srv=img32)

---

### Post by uberlube on 2008-02-23
I think that I gave you the wrong vga number before, try the one that i gave you in the last post hopefully that will work. Or just stick with the dell :) anyway are you getting ENVY for the driver? If you have it installed you can probably use that finicky monitor without tampering.

---

### Post by DarkWater on 2008-02-23
I'll try switching the monitors back after I start using Ubuntu a bit.  Any packages you recommend?

---

### Post by uberlube on 2008-02-23
Well first off get ENVY for graphics card. 2nd i don't use gnome i use KDE (kubuntu) its way better. All the preinstalled programs are way better. As far as recommending programs, it all depends on what you want to do. Also I dont use ubuntu anymore, i use linux Mint. It is based on debian and ubuntu but much nicer looking and has alot of helpful features. You might want to check it out :)

---

### Post by DarkWater on 2008-02-23
Okay, I'll check it out.  And you were such a big help today. @_@ At least it works now, albeit with another monitor.  Maybe it'll work with a new Ubuntu version. =P

---

### Post by uberlube on 2008-02-23
I recommend it. Ubuntu's still awesome and everything but check out your options and find what is right for you. They are pretty much all here:
[http://distrowatch.com/](http://distrowatch.com/)

---

### Post by DarkWater on 2008-02-23
Thanks for the link.  I'll be sure to check it out after I finish updating and situating myself with Ubuntu.

---

### Post by uberlube on 2008-02-23
K enjoy and dont hesitate to PM me if you have any other questions.:guitar:

---

### Post by DarkWater on 2008-02-23
Thanks. =D

---

### Post by uberlube on 2008-02-23
Hey feel free to click the ribbon with the star, lol.:lolflag:

---

### Post by johnap on 2008-02-23
> **uberlube said:**
> During GRUB add "vga=791" to the boot process.

I have installed Java but my pluginreg.dat file is not updated
what should we do to update the same.

---


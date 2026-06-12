---
title: "Live CD keeps going back to login screen?"
date: 2007-02-03
forum: Installation &amp; Upgrades
---

### Post by MetaBrain on 2007-02-03
So, I burned the Ubuntu 6.10 CD with Infrared like I was told, but in BIOS to boot  from it, really easy.

It autoran, I choose Start and Install Ubuntu (I've also done Safe grafics mode with same results).

I get to the title scren in like 5 minutes, everything ok, no errors or anything. I tryed a FEW of the examples (the presentations) and it was awsome :)

After, I close the window and pressed twice in install in the desktop. The intall window opened, but no letters. I waited a few secs and then the screen goes black, my monitor (ACER LCD) starts it's AUTO mode (like when you change resolutions or enter WindowsXP or a game with dif video setting, the screeen flickers, goes black again, and goes BACK to the title scren (the login thingy).

Help, I've wasted over 4Gbs of downlaod yesterday to get a bloody Linux GUI working. Desbian WASN'T GUI after all, but at least I got the GRUB that I wanted in the MBR, and Ubuntu isn't working. (the other 3gbs refer to me downloading the discs that aren't the intall one for debian >_<'')

I think this might be a grafical glitch due to my **** old video card, Voodoo3 PCI 16mb.

Thanks in advance




Specs if you need (kinda old, I know):
- OS: XP Pro
- P3 1Ghz
- 256RAM
- Voodoo3
- generic OEM Sound Blaster
- Mobo I don't know the name, but it's an Ali something.

---

### Post by MetaBrain on 2007-02-03
PS: I'll download the alternate CD this night, I don't know, maybe my PC isn't strong enough for Live install. (I'm downloading Alternate CD from ubuntu 6.06, I heard it was more stable, and I could upgrade easilly).

---

### Post by MetaBrain on 2007-02-03
Please help :(

I wanna try Linux soo bad :(

---

### Post by MetaBrain on 2007-02-03
I tryed again and got this little window when it relogined for the 2nd time:
"I've detected another (something) is open. (something) close (something)."
I forgot >_>

I though it was funny because the OS was speaking in first person :) 


Any help would be greatly apreciated.

---

### Post by MetaBrain on 2007-02-04
Is this problem that weird?

Bump for Linux <3.

---

### Post by MetaBrain on 2007-02-04
Please help me :(

---

### Post by MetaBrain on 2007-02-10
Bump again...:popcorn:

---

### Post by MetaBrain on 2007-02-17
Still no posts? Why everyone hates me :(

---

### Post by pebkac on 2007-02-17
> **MetaBrain said:**
> Still no posts? Why everyone hates me :(

I can't help you, sorry... I was never able to get my PC install of Ubuntu to work, all I wanted was to run from the Live CD. It just freezes some time after you press "Start or Install Ubuntu".  No one could help me, either. I tried on 3 computers and burned the disc twice. When you insert the CD there is an option that says "Check CD for errors" I did this and it didn't find any errors. It just never worked. I used Mandrake. (an old 9.2 version)

And when I tried to get the server version, I couldn't even download the ISOs. It kept on hanging up. I didn't get any real help for that one either, but I did eventually get a DVD iso.

Hope you get your problem fixed.

---

### Post by rr9966 on 2007-02-17
I am having the same problem where it keeps taking me back to the login screen.  It is very frustrating.  I have tried Ubuntu and Xubuntu both and they do the same thing.  The screen usually blinks twice before it does it.  I have a 566Mhz Celeron with a 3dfx Voodoo3 AGP graphics card.

---

### Post by MetaBrain on 2007-02-18
Maybe it's a Voodoo3 related glitch?

Since we both have... Thanks for the replyes guys :)


BUMP

---

### Post by tijean on 2007-02-18
Hey, 
I am having the same problems: Ubuntu6.10, Xubuntu6.10 live cds and even after installation  with the alternate cd, I always get login screen. 
And...      .... I am using an 3dFX Voodoo3 3500 graphics card. 

Anyone a solution?

---

### Post by MetaBrain on 2007-02-18
Hmmm... More and more evidence this is a glitch related to Voodoo Linux drivers!

Let's wait for someone like a dev to post.

---

### Post by MetaBrain on 2007-02-18
I've done a little searcg and so far, 80% of the guys with this problem are using voodoo's...

Here is the links:

[http://www.ubuntuforums.org/showthread.php?t=346205&highlight=live+cd+login+screen+problem](http://www.ubuntuforums.org/showthread.php?t=346205&highlight=live+cd+login+screen+problem)

---

### Post by MetaBrain on 2007-02-20
Bump

---

### Post by MetaBrain on 2007-03-06
I'm not giving up.

BUMP

---

### Post by MetaBrain on 2007-03-11
yet another bump

---

### Post by RupertHenry on 2007-03-17
I also have the same problem with a 3dfx Voodoo3 card in a P3 machine. If anyone manages to figure this one out, please post it to the discusson. RH

---

### Post by Stric on 2007-03-18
I have exactly the same problem, with Ubuntu and Edubuntu. Also 3dfx Voodoo3...

---

### Post by RupertHenry on 2007-03-18
So I pulled the 3dfx Voodoo card and swapped it with a bog standard video card fro another PC...

Ubuntu is now installing and Windoze is happy with the 3dfx card.

---

### Post by travm on 2007-03-20
I have this problem too,
temporary fix is to change your driver to vesa, I did find a thread here
[http://www.ubuntuforums.org/showthread.php?t=387771](http://www.ubuntuforums.org/showthread.php?t=387771)
that tells you how to change the driver to vesa for the livecd
otherwise you set it in your xorg.conf file which, by default is in /etc/X11/xorg.conf
This can also be done using 
dkpg-reconfigure xserver-xorg
I recommend doing it manually.
There does seem to be a patch for the tdfx driver, but im too new to know how to use it.  

There clearly is a bug in the tdfx driver in edgy eft.  Dont you love how upgrades and new versions break things.

When i get this problem solved I will post here with how to fix it

---

### Post by lyndaj70 on 2008-04-24
Hi!
Just stumbled across this thread..

I have this exact same problem, however I am running an ati video card.  Also, I can successfully boot into gnome failsafe mode.

When the login screen appears, can you change your session to gnome-failsafe and login?  If so then we're in the same boat. ](*,)

I've so far tried several proposed solutions, including using the alternate CD, video safe mode refuses to work on my monitor (LCD), and once I hosed my gnome entirely by following a post to uninstall something that was attached to it.  The post said to reinstall piece by piece, but failed to list what to reinstall, so I am just reinstalling the whole kit and kaboodle again (sigh). Can't blame the poster for my mistake - should have read it all before typing in the commands...

I gather that there is a bug report concerning this, but I am far from expert and am not sure which bug applies, as most posters seem to be running nVidia cards or something besides ati.

Peace,
Lynda

---

### Post by Wish4Me on 2008-04-24
Same problem but with Radeon Xpress 200M card. Going for Fedora. It actually works for me.

---


---
title: "GRUB SPLASH PRO install with splash link!"
date: 2007-04-06
forum: Installation &amp; Upgrades
---

### Post by Neobuntu on 2007-04-06
Now as easy as 1, 2, 3 after download.
You may simply paste my quotes into your terminal/console and everything will match and it's FAST! 

Before we start, CLICK THIS if you would like to see (uncompressed) what we are adding to the Grub menu: 
[http://fabrizio.ciacchi.it/guide/grub/emoblue-splash.png](http://fabrizio.ciacchi.it/guide/grub/emoblue-splash.png)
(It looks even better installed, and it has good title/text alignment too.)
This one is independent of any brand so if you switch to Kubuntu-desktop (or whatever) , you will not have to touch it..

You may wish to set Firefox to save on your "/Desktop".

Download it (compressed for GRUB) by clicking here...
[http://fabrizio.ciacchi.it/guide/grub/emoblue-splash.xpm.gz](http://fabrizio.ciacchi.it/guide/grub/emoblue-splash.xpm.gz)

Save it specifically on your "Desktop" folder ! (For use with these following quotes.) 

*** START YOUR ENGINES *** (and your stop watch.):

1) Next, we'll copy it to the Grub folder and rename it to just "splash.xpm.gz" as root, like so...> sudo cp /home/*/Desktop/emoblue-splash.xpm.gz /boot/grub/splash.xpm.gz

2) Then, unless you are already sure; using this method, issue a...
> sudo nano /boot/grub/menu.lst...and make sure the line... > splashimage=/boot/grub/splash.xpm.gz ...is exactly as that (paste it) and is NOT COMMENTED OUT with a proceeding "#".

Save your changes.

3) Now, just...> sudo update-grub
Time! YOU'RE DONE. If it found your default named image, you're good to go.

This way, you do not have to edit the menu again.

If you try other (renamed and copied) specially prepared grub splash images, don't forget to run "sudo update-grub" again (using this method) and check the results.

Be sure to reboot and test grub(soon). Be careful. If you get a blank screen (at GRUB boot), you can hit the [Esc] key and arrow down as needed one or two taps) to boot your preference. Of course, you can boot a live CD and correct the GRUB "menu.lst" that way too.

This image looks good during the actual boot. Many do not. I know you'll enjoy this one.

This image is hard to find. If the this link goes down, use the name "emoblue" (and "GRUB splash"  with Google) to find another copy.

Obviously, this easy method can be used (with modification) for any working GRUB splash, now that you know what to rename it, how and where to place it and to check(ONCE and for all) using "sudo gedit /boot/grub/menu.lst" for a matching image command "splashimage=/boot/grub/splash.xpm.gz".

Obviously, changes can now be done by altering the...> sudo cp /home/*/Desktop/emoblue-splash.xpm.gz /boot/grub/splash.xpm.gz command and NOT "menu.lst" (for image changes) once checked.

 I hope you enjoy.

---

### Post by Neobuntu on 2007-04-06
More GRUB tweakin' stuff...

Other tips are, you might edit the "menu.lst" file (don't do too much at one time). 

> sudo nano /boot/grub/menu.lst

I find a time out of 8 seconds works best.

Plus, you might set the default to:
> default		saved
Instead of a number.

This way, if you run a dual boot, whichever OS you were in last, reboots automatically. Unless (of course) you hit an arrow key before the eight seconds is up. Windows REALLY needs this because it needs rebooting incessantly.

Also (a bit more advanced), you could move the whole title section that activates Windows ABOVE the > # Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST section; instead of below the > ### END DEBIAN AUTOMAGIC KERNELS LIST  Then you will also want to comment out additional title category headers that at default, dual-boot installation setup has added (and maybe "#" the Memory tester too). This way, Windows will simply show up at the top of your grub menu, which is probably the partition order that it is installed (MS Windows is dumb that way) and that makes Windows convert, newbies feel better. 

Done this way, it will not interfere with *ubuntu advanced, automatic, grub menu, management; when it adds new (test) Kernel for you. Old kernel will then be listed last, not between ubuntu kernels and Windows. These changes make new dual boot converts feel they have gained; upon seeing the GRUB menu. Not shocked with newbie terror. LOL

Let me know if you like your new GRUB. Unfortunately, if you do a (recommended) clean install to get a new release, you'll have to do this (custom tweak) again.

You don't have to update-grub after you manually edit the menu yourself. (With LILO you do.)  

BE CAREFUL. If you toast your GRUB "menu.lst" file and can not get back into boot *ubuntu. Boot a live CD and fix the "/boot/grub/menu.lst" file. Boot and test it again. Always test the change.

---

### Post by Neobuntu on 2007-04-06
Did it work for you?

---

### Post by Neobuntu on 2007-04-06
I had to add...

> Make sure the line...
Quote:
splashimage=/boot/grub/splash.xpm.gz
...is in your menu.lst files and NOT commented with a proceeding "#".

---

### Post by Neobuntu on 2007-04-06
Here's a link to changing the kernel boot splash (instead of GRUB) to ubuntu, kubuntu or xubuntu.

Note also: > For those who don't know, I think of them in this order.

1. Grub splash screen(optional limited graphic).

2. Boot splash (kernel). Ubuntu, Kubuntu,Xubuntu or custom. (link below)

3. GDM or KDM login theme (NOT SEEN until "Log Out", IF you use auto login).

4. Optional start up Gnome or KDE splash (I turn this off).
So for step two see:
[http://ubuntuforums.org/showthread.php?p=2411785#post2411785](http://ubuntuforums.org/showthread.php?p=2411785#post2411785)

---

### Post by Neobuntu on 2007-04-07
Did this work for you?

How fast did you do it?

After rebooting did it work the first time?

Don't do the other tips until you test the GRUB splash.

How did those extra tips work for you, especially dual when booting?

Thanks

---

### Post by Neobuntu on 2007-04-15
I changed to nano because I don't then have to mention gedit for GNOME or kate for Kubuntu. 

They would better need gksudo and kdesu respectively.

Mainly, sudo is better suited to nano because gksu or kdesu goes properly with gedit and/or kate (being in X), 

and it's faster.

I think everyone would have nano but if not...> sudo aptitude install nano

---

### Post by randell6564 on 2007-04-20
> Next, you'll need root access, so use......to move/drag it into the "/boot/grub" folder.
Did this.
> Then, unless you are already sure, pop open a terminal console and issue a...
...and make sure the line...  ...is in your menu.lst files and NOT commented out, with a #
Did this too, but it's not there.  Where exactly do I enter it?  (On what line?)
I ran
```
sudo update-grub
```
Output is:
> Searching for GRUB installation directory ... found: /boot/grub
Testing for an existing GRUB menu.list file ... found: /boot/grub/menu.lst
**Searching for splash image ... none found, skipping ...**
Found kernel: /boot/vmlinuz-2.6.17-11-386
Found kernel: /boot/vmlinuz-2.6.15-28-386
Found kernel: /boot/vmlinuz-2.6.15-23-386
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done
Sure would like to see this work!  BTW, I'm running 6.10
Thanks!

---

### Post by Neobuntu on 2007-04-26
Yeah, at one time I suggested to put it after the default color line but I removed it for breavity.  

Plus, I may update the tools (quotes) used to work around some bug issues.

---

### Post by Neobuntu on 2007-04-26
If you see any more errors. Please let me know.

It's NEW and IMPROVED. :lolflag:

---

### Post by Neobuntu on 2007-04-26
Made minor adjustments so it would work with everyone.

---

### Post by randell6564 on 2007-04-26
> **Neobuntu said:**
> Made minor adjustments so it would work with everyone.

Actually, I spoke too soon!  It was my fault that It did not work.  I was identifiying hd0 as the partition with the .xpm.gz, but it is actually hd01.  SO.,it works after all!

Cheers!

---

### Post by Neobuntu on 2007-04-27
I'm glad it works. Please let me know. 

My goal was to leave a fast trail that can be followed. This one, in order to quickly and systematically get it done. You can use it over and over on any system and/or new install that you want. 

By fast, I wanted my exact quotes to work for everyone; without modification.

It's testing well for me.:popcorn:

---

### Post by randell6564 on 2007-04-27
> **Neobuntu said:**
> I'm glad it works for someone. 
My goal was to leave a fast trail that can be followed. This one, in order to quickly and systematically get it done. You can use it over and over on any system and/or new install that you want. 
By fast, I wanted my exact quotes to work for everyone; without modification.
It's testing well for me.:popcorn:
You're doing a FINE job my friend!  I will need to read this thread from start to finsih in order to give any further feedback, but so far as I am concerned, the only thing that needs to be stressed is what is entered or pasted into /boot/grub/menu.lst. 

It's fun isn't it?  Thats why I Love Linux!

---

### Post by Ateo on 2007-04-27
Hello,

This might save some people headache. But every grub install I've ever done, regardless of distribution, my splash image line in menu.1st has always read as such:```
splashimage=/grub/splash.xpm.gz
```

And, as such, it is the same with my installation of Ubuntu... I wonder why.

In any case, this is here as an alternative in case anyone has issues of grub not finding the image.

---

### Post by randell6564 on 2007-04-28
> every grub install I've ever done, regardless of distribution, my splash image line in menu.1st has always read as such:
```
splashimage=/grub/splash.xpm.gz
```
> And, as such, it is the same with my installation of Ubuntu... I wonder why.
Well.,THAT would be because you have not EDITED your /boot/grub/menu.lst!
What 'neobuntu' is describing in this thread is how to install a DIFFERENT splash image.

"splash.xpm.gz" is the name of the splash image.  If you want to install a different splash, you will need to first create, and install one, or  download and install one!

And THEN you will have to EDIT your /boot/grub/menu.lst, entering the name of your desired splash.

---

### Post by Ateo on 2007-04-28
@randell6564

You miss my point. It doesn't matter whether this is a NEW splash image install or an existing. My point is the path given, as instructed by the original poster, does not work for me. Nor has that path ever worked for me under any distribution.

I'm not confused with how to install a splash image. It's the splash imag path I am referring to, directly.

Regards

---

### Post by randell6564 on 2007-04-28
> **Ateo said:**
> @randell6564

You miss my point. It doesn't matter whether this is a NEW splash image install or an existing. My point is the path given, as instructed by the original poster, does not work for me. Nor has that path ever worked for me under any distribution.

I'm not confused with how to install a splash image. It's the splash imag path I am referring to, directly.

Regards
Please provide me with the exact post that you are refering to.  What "path" are you talking about that doesn't work for you?

Ateo, please post your /boot/grub/menu.lst  

This is not making any sense.

---

### Post by Ateo on 2007-04-28
I'm not sure I mentioned an post for reference.

Allow me to explain it again.

I wanted a nice grub splash. So I did a search for assistance and I found this guide. However, the part in which the original poster says to add:> splashimage=/boot/grub/splash.xpm.gzto menu.1st does not work. I get an error when the system reboots that it can't find the splash image but continues to load grub with my choices (with a block screen, the default).

That (the syntax) does not work for me nor has it ever worked for me under ANY distribution. This is what works for me, and perhaps others:> splashimage=/grub/splash.xpm.gz

If this doesn't make sense, i'll post my menu.1st file then... =)

---

### Post by randell6564 on 2007-04-28
> I get an error when the system reboots that it can't find the splash image but continues to load grub with my choices (with a block screen, the default).
If this doesn't make sense, i'll post my menu.1st file then... 

It makes PERFECT sense now, and I know EXACTLY what your problem is! 
Please post your /boot/grub/menu.lst

---

### Post by randell6564 on 2007-04-29
Ateo, I had the same [problem.]("http://ubuntuforums.org/showpost.php?p=2542941&postcount=12"), grub could not find my slash screen because I entered the wrong path to it.  So, lets start from the begining.

Create a folder in your /boot/grub directory and name it 'images'. (This might be the reason for things not working for you)
```
sudo mkdir /boot/grub/images
```
Now place your .xpm.gz splash into it. (you probably know already, but you can only do this as 'root'). 

NOW open your /boot/grub/menu.lst with whatever text editor that you use.  I use 'gedit'.
```
sudo gedit /boot/grub/menu.lst
```
THIS is where I believe that you went wrong. I'll show you a portion of MY menu.lst.  This is the top entry:
> menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.
splashimage (hd1,0)/boot/grub/images/emoblue-splash.xpm.gz
My mistake was that I told grub to look for my splash in (hd0,0). I got the same error as you are getting. I changed it to what it needed to be, (hd1,0) and now it works.
But do not assume that you need to enter the same thing as I did. Depending on how your drive is setup will determine the path needed.  I figured it out by scrolling down my menu.lst and seeing an entry like this:
> title		Ubuntu, kernel 2.6.20-15-386
**root		(hd1,0)**
kernel		/boot/vmlinuz-2.6.20-15-386 root=UUID=6a316831-0b44-4f7b-bf21-af209f470762 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-386
savedefault
Hope this helps!

---

### Post by Ateo on 2007-04-30
Ok. Let's start over all again... I am *not* having any issues what so over. I am not asking for any assistance. In fact, my post is meant to help others.

I simply stated that [my installed] grub cannot find [COLOR="Red"]splashimage=/boot/grub/image.xpm.gz[/COLOR] so I change it [COLOR="DarkGreen"]splashimage=/grub/image.xpm.gz[/COLOR] and the issue is resolved.

---

### Post by ss87 on 2007-04-30
Worked fine for me, followed it step by step but used a splash screen from [www.gnome-look.org](www.gnome-look.org)

Thanks!

---

### Post by Neobuntu on 2007-05-01
OK, my guide was meant to work on as many systems as possible (without modification). That's why I changed it to 'nano' instead of 'gedit' or 'kate'. 

Also, the splash command is meant to work everywhere but it looks like you may need to add more detail if you have two hard drives. 

I haven't tested the shorter command line and that might work better for you (as kindly stated). I have tested my version posted guide (revised over and over).

I'm glad it's working and saving time.

Please do post any suggestions where it could be made more universal.

Note too that I have played with having multiple images; in their own (root permission) folder (like the extras in the repository)  and I have learned that having directories inside /boot/grub (and re-editing the "menu.lst" for a different named image) are a troublesome place to put them.

First, they're compressed and you can't view them easily; in that form, anyway. 

Second, that would be in a root folder and it's better for your candidates to be in a home folder and IMHO copy(and rename to a default as root) the one you want into place (using my command posted).

Quite frankly, I'm still a little confused about exactly what "sudo update-grub" does to the splash image. I had hoped it would do it all for us but actual testing, it seems to need the method that I have devised/verified.

Perhaps the problem is; the image must be registered and some of our testing did not take into account that it was "registered" (or set) by an earlier "sudo update-grub". I haven't tested that yet but what I posted works (for me); for sure. It also takes into account, past installs that may have been done(or not).

Please let me know the deal with what "sudo update-grub" exactly does with the image. Either it's just saying it will find it or it actually places(sets) it, in a manner where it will load until the next update.

---

### Post by Neobuntu on 2007-05-01
> splashimage=/grub/image.xpm.gz

...works fine too (For me; with one hard drive).

---

### Post by Neobuntu on 2007-05-01
OK, I have a THEORY. Perhaps; unless you designate the exact and full image location, you'll need update-grub, so it will assume and find (from the general location) what you mean.

> splashimage=(hd0,1)/boot/grub/splash.xpm.gzWould be the full thing. Depending on the drive and partition.

Anybody test this theory already?

---


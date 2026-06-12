---
title: "Black Screen while booting Gusty (Not live CD!)"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by TheMarex on 2007-10-18
Hi,
I just installed Gusty through the live CD (which worked except of fglrx nicely), but I'm having a rather strange problem.
As I already mentioned the live CD with manually installed fglrx driver works great, including X + boot splash.
Well, after the installation finished without problems, I rebooted.Grub boots up as normal, but when I try booting Gusty I'll just get a completely black screen. No error message, no splash screen. Nothing.
I also experience a black screen when I try to reconfigure the x server through the recovery session. After it tries to detect my monitor, the screen goes black. Just like when I try booting Gusty up.

Some description of my hardware:
Notebook Asus A6J
Radeon X1600 Mobility
Intel Core Duo

Anyone an idea what could cause this problems?
Until this problem isn't fixed I can't use my working machine....

---

### Post by ruggersway on 2007-10-18
Have you successfully booted at all since you completed the installation?  Was this a new installation or were you using the alternate installer to perform an upgrade?

-rugger

---

### Post by pilotet on 2007-10-19
Hi,
I have an ASUS A8J and I have exactly the same problem.

I've installed ubuntu gusty and I have done a reboot after install. The laptop boots with no problem.

The problem it comes when I activate the restricted driver for ATI cards. After activating the driver and rebooting only I can see GRUB and after that only a black screen.

The laptop seems to load something but I can't do any CTRL+ALT+Sup or CTRL+BCKSPACE. Only I can see the black screen.

Any idea?

---

### Post by gvoima on 2007-10-19
Your monitor is probably out of sync, try to manually add the sync rates in your xorg.conf.
Atleast I had to, with Edgy.

And I had the same problem this morning I quickly installed Gusty. I'll try to solve it when I get home.

The thing is, that one of the sync values was in the correct range, but my monitor can't handle range that wide so I had to narrow it down and it worked. E.g. 30-60 to 50-60. But I have to check this.

[EDIT]
Well, changing of refreshrates didn't work :/
[/EDIT]

---

### Post by TheMarex on 2007-10-19
I could successfully boot into gusty with disabling the splash and the quiet option in grub. Then I installed fglrx and changed xorg.conf. After rebooting I of course got the black screen again, but after waiting 2 or 3 min GDM suddently shows up and everything is fine. No idea what really is the problem. Probably usplash does something wrong? :confused:

---

### Post by bfury on 2007-10-19
Hi,
I have a similar problem with a fresh Kubuntu 7.10 Final install (and with a fresh install of the RC before)  : Just after the "Starting..." message, the screen goes black instead of showing the graphical boot screen. The boot seems to hang, and nothing happens.

If i try to change to another terminal (ctrl+Alt+F1, as an example), it "wakes up" the boot procedure, in text mode, and then i finally get my KDM connection screen.

This only occurs with a fresh install from the live CD : if i make a fresh install of Feisty (that has always worked fine) ans that I use the Upgrade tool, the Gusty system i get has no boot problem and works as a charm...

Hope that these clues will help to get a solution.

---

### Post by lakhif on 2007-10-19
Installed Gutsy today. Awesome distro i must add.

I also had the blank screen while booting up. Installed a package called "startupmanager" from the repositories.

 Under "Boot Options" i changed the "Resolution" to "1024x768" and changed the 
 "Color Depth" to "16 bit"

Let the post configuration complete and then rebooted and the ubuntu usplash came up.

Hope this works.

Please excuse as this is my first post (also a newbie)

Have a great weekend.

Adios :)

IBM T40:^o

---

### Post by davidshere on 2007-10-19
I had this problem when I upgraded from Edgy to Feisty.  Now I have it again after upgrading from Feisty to Gutsy.  What's wrong with that statment?

Anyway... I also used startupmanager when I had Feisty and I think I eventually tracked down the problem, although I don't remember the details.  I got a new boot splash and got it to actually display.  Maybe I'll try that again.

Hmm... I tried that... still blank.  It says "You have passed an invalid mode number".  I hate it when I do that.

---

### Post by Kawayanan on 2007-10-19
I have the same problem.  Live CD runs fine, I do the install, but just get a black screen after grub when I reboot.  This happened without me changing any video drivers.

Compaq Presario V2400
AMD Tution64
ATI Radeon Xpress M200

I could do the safe mode login.

This was with the Desktop i386 CD.  I also tried the AMD 64 version, but it locks up and dies during the install.

Kawayanan

---

### Post by leetcharmer on 2007-10-19
[http://ubuntuforums.org/showpost.php?p=3569987&postcount=4](http://ubuntuforums.org/showpost.php?p=3569987&postcount=4)

Answer is here :D

---

### Post by pilotet on 2007-10-19
May be this helps too.
Now I'm able to boot Gusty and use Compiz with my ASUS a8js.

1. Enable ATI restricted driver but don't reboot.
2. Just follow the steps mentioned in [https://help.ubuntu.com/community/CompositeManager/CompizFusionATI?highlight=%28compiz%29](https://help.ubuntu.com/community/CompositeManager/CompizFusionATI?highlight=%28compiz%29)

Enjoy!

---

### Post by davidshere on 2007-10-19
> **leetcharmer said:**
> [http://ubuntuforums.org/showpost.php?p=3569987&postcount=4](http://ubuntuforums.org/showpost.php?p=3569987&postcount=4)

Answer is here :D

Tried this.  Still no love.  This is just like it was last time.

Anyway... it's a small problem.

---

### Post by sandpaperback on 2007-10-19
> **leetcharmer said:**
> [http://ubuntuforums.org/showpost.php?p=3569987&postcount=4](http://ubuntuforums.org/showpost.php?p=3569987&postcount=4)

Answer is here :D

This half-fixed the problem.  I get a shutdown progress screen now, but still no boot screen.  I got an error running that last command.

---

### Post by alfredska on 2007-10-19
> **leetcharmer said:**
> [http://ubuntuforums.org/showpost.php?p=3569987&postcount=4](http://ubuntuforums.org/showpost.php?p=3569987&postcount=4)

Answer is here :D

This fully resolved my problem (and as another user on that thread mentioned, my boot speed is considerably faster as well, wasn't expecting that)  Thanks for passing the goods.

---

### Post by zelsuk on 2007-10-19
> **leetcharmer said:**
> [http://ubuntuforums.org/showpost.php?p=3569987&postcount=4](http://ubuntuforums.org/showpost.php?p=3569987&postcount=4)

Answer is here :D

its also worked for me.. thanks

---

### Post by bfury on 2007-10-19
> **leetcharmer said:**
> [http://ubuntuforums.org/showpost.php?p=3569987&postcount=4](http://ubuntuforums.org/showpost.php?p=3569987&postcount=4)

Answer is here :D

That solved the problem for me too.

Thanks a lot, Leetcharmer.

---

### Post by Eric the Grey on 2007-10-19
> **leetcharmer said:**
> [http://ubuntuforums.org/showpost.php?p=3569987&postcount=4](http://ubuntuforums.org/showpost.php?p=3569987&postcount=4)

Answer is here :D

Unfortunately, this did not work for me, but that's perhaps because I didn't understand the following instruction: 

> 3) sudo update-initramfs -u -k `uname -r`

It gave me an error when I did it exactly like that, and if I replace uname with Linux (type uname at the ommand prompt and that was the response) it still gave an error.

However...

> **lakhif said:**
> Installed Gutsy today. Awesome distro i must add.

I also had the blank screen while booting up. Installed a package called "startupmanager" from the repositories.

 Under "Boot Options" i changed the "Resolution" to "1024x768" and changed the 
 "Color Depth" to "16 bit"

Let the post configuration complete and then rebooted and the ubuntu usplash came up.

Hope this works.

Please excuse as this is my first post (also a newbie)

Have a great weekend.

Adios :)

IBM T40:^o

Worked like  a charm and I now have both startup and shutdown splash screens!  \\:D/

Thanks for all the advice.  Great thread!


:cool: Eric the Grey

---


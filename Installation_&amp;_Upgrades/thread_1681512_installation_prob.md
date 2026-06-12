---
title: "installation prob"
date: 2011-02-04
forum: Installation &amp; Upgrades
---

### Post by p4nth3r on 2011-02-04
someone plz help...............

i  installed ubuntu 10.04 everything went like a charm during installation but at the end after completing installation when i press reset button of last dialogue window. cd ejected and a lot of errors was appeared and system halted there. i pressed ctrl+c  after waiting almost 30min and it continued the reset process.

i encounter no errors during booting. but a lot of files are missing. 

i tried re-installing 5 to 6 times but no luck. always same results.

---

### Post by sahilsameer on 2011-02-04
what error u mean
after installing ubuntu cd will be ejected that is natural
then they will be showing some errors 
wait for some seconds close the tray and then press enter
what file miss u are talking about

---

### Post by Rubi1200 on 2011-02-04
Hi and welcome to the forums p4nth3r :-)

As sahilsameer asked, what errors? Are you able to boot into Ubuntu?

Please try and be more verbose in describing the problem so we can help you solve it.

Thanks.

---

### Post by p4nth3r on 2011-02-05
thanx guys i found out that my drive have bad sectors and thats the prob.

but the only thing i can't understand is that bad sectors are on windows partition, nix drive is clean then why it is behaving like that.

things like gdmsetup and gnome-control-center and others report errors about missing files while executing.

cd ejecting is normal but as soon the cd is ejected file copy type errors flooded my screen.
 
many conf files are missing like of x server.

---

### Post by kansasnoob on 2011-02-05
The I/O errors mean nothing:

[https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#I/O%20error%20after%20CD%20is%20ejected%20at%20end%20of%20install](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#I/O%20error%20after%20CD%20is%20ejected%20at%20end%20of%20install)

> I/O error after CD is ejected at end of install

In some cases, ejecting the CD at the end of installation will leave errors on the screen such as:

end_request: I/O error, dev sr0, sector 437628

these error messages indicate that the system is still trying to access some files on the CD, and are harmless except that they obscure the message asking the user to press Enter to reboot. You can safely remove the CD from the tray and press Enter at this point to reboot to your new Ubuntu system.

What files appear to be missing?

What doesn't work right?

What other errors do you see?

---

### Post by kansasnoob on 2011-02-05
> many conf files are missing like of x server.

If you're talking about "etc/X11/xorg.conf" it went bye-bye clear back around Jaunty or Karmic.

So, if you're having display/resolution problems you'll need to be much more specific.

> things like gdmsetup and gnome-control-center and others report errors about missing files while executing.

You need to tell us exactly what you're trying to do. What version of Ubuntu did you last run? There have been lots of changes since about 8.10 or 9.04.

---

### Post by p4nth3r on 2011-02-10
kansasnoob thanx for your help

here what i got when i run gdmdetup:


```

** (gdmsetup:1655): WARNING **: Error calling GetValue('daemon/TimedLoginEnable'): Key not found

** (gdmsetup:1655): WARNING **: Error calling GetValue('daemon/TimedLoginDelay'): Key not found
** (gdmsetup:1655): DEBUG: init delay=30
** (gdmsetup:1655): DEBUG: "/usr/share/xsessions/guest-restricted.desktop" is hidden or contains non-executable TryExec program

** (gdmsetup:1655): DEBUG: "/usr/share/xsessions/une-guest-restricted.desktop" is hidden or contains non-executable TryExec program

** (gdmsetup:1655): DEBUG: "/usr/share/xsessions/une-efl-guest-restricted.desktop" is hidden or contains non-executable TryExec program


** (gdmsetup:1655): WARNING **: Error calling GetValue('daemon/DefaultSession'): Key not found
** (gdmsetup:1655): DEBUG: Init default session found:'(null)'
** (gdmsetup:1655): DEBUG: GdmUserManager: Found current seat: /org/freedesktop/ConsoleKit/Seat1
** (gdmsetup:1655): DEBUG: GdmUserManager: running 'ck-history --frequent --seat='Seat1' --session-type='''
** (gdmsetup:1655): DEBUG: GdmUserManager: explicitly skipping user: nobody
** (gdmsetup:1655): DEBUG: GdmUserManager: user icon changed
** (gdmsetup:1655): DEBUG: adding monitor for '/home/mab/.face'
** (gdmsetup:1655): DEBUG: Getting list of sessions for user 1000
** (gdmsetup:1655): DEBUG: Found 1 sessions for user mab
** (gdmsetup:1655): DEBUG: GdmUser: adding session /org/freedesktop/ConsoleKit/Session2
** (gdmsetup:1655): DEBUG: GdmUserManager: sessions changed user=mab num=1
** (gdmsetup:1655): DEBUG: GdmUserManager: added session for user: mab
** (gdmsetup:1655): DEBUG: GdmUserManager: history output: mab      23


** (gdmsetup:1655): WARNING **: Error calling GetValue('daemon/AutomaticLoginEnable'): Key not found

** (gdmsetup:1655): WARNING **: Error calling GetValue('daemon/TimedLoginEnable'): Key not found

** (gdmsetup:1655): WARNING **: Error calling GetValue('daemon/TimedLogin'): Key not found
** (gdmsetup:1655): DEBUG: init user='(null)' auto=False


```as you may have noticed i m new to ubuntu. and believe me its getting so much hard to learn ubuntu in this kind of behavior. i mean errors fly here and there and after spending a lot of time on Internet you find out this is normal don't give a ****. (well errors are normal....OKAY). but after a while problems start to arise.

like i want to remove drive icons from my desktop so i did gconf-editior thing and uncheck volume visible and they were vanished but this only worked for few days and now they are back. no matter what i do they are not leaving the desktop.

okay drive icons are not a big problem so i have a better one. A week ago when i logged in i see my Internet disabled. i check every thing and every thing(router,cable etc) seems fine so i decided to boot into window and check if it is disabled there and guess what every thing was fine there.things happen right? i googled this and found some fixes but after playing with certain commands and files related to the network manager (gathered from different forums) for almost 5-6 hours and no progress i reinstalled ubuntu and it was fixed.  funny thing is today the same thing happened again and i reinstalled ubuntu again. :lolflag:
not to mention i have to reinstall all the apps again after fresh install which is such a pain.

is it same for everyone else who uses ubuntu? like they reinstall ubuntu after a week and if they don't ubuntu makes this personal and force them to do this.

and please somebody explain to me that why in ubuntu if a file is flooding your screen with errors then its working fine and if not it must be corrupted? i mean thats what i found on every bug report of ubuntu.

---

### Post by p4nth3r on 2011-02-11
hey! anyone plz help

---

